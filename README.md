# Bioinformatica_y_Metagenomica_en_los_Andes-2023
## Herramientas bioinformáticas y flujos de trabajo para el procesamiento, edición y análisis de datos WMS.

**Leonardo R. Rocabado-Villegas.** Área de Bioquímica Molecular, Instituto de Investigaciones Fármaco - Bioquímicas.
### Contacto:
email: lrocabado22@gmail.com

### Sistema operativo
Para esta sección es recomendable la particion del disco duro con una distribución de Unix.
### Secuencias
Para disponer de los archivos que seran análisados en este curso, será necesario que abran una Terminal, unstalen el prdoama:
```
https://github.com/ncbi/sra-tools
```
Y descarguen 10 de los siguientes codigos de acceso SRA.



Ante cualquier duda consulten a los docentes. 

## Control de calidad de los reads
Es el primer paso en el flujo de trabajo en un analisis metagenomico el cual tiene por objetivo evaluar la calidad de todos los reads de las secuencias.
Para realizar el control de calidad de las secuencias, utilizaremos la herramienta FastQC.
```
https://www.bioinformatics.babraham.ac.uk/projects/fastqc/
```
La evaluación y visualización de los parametros de calidad seran ejecutadas mediante el siguiente comando:
``` bash

fastqc read1.fastq.gz read2.fastq.gz 
```
## Trimming
El trimming consiste en la remosion de los adaptadores y reads de baja calidad; este se realiza mediante programas bioinformáticos especiales para esta tarea.
Para este fin instalaremos el programa TrimGalore.
```
https://github.com/FelixKrueger/TrimGalore
```
Para la realizar el proceso de trimming, configuraremos el programa para secuencias de illumina, paired y control de calidad de la salida.
``` bash

trim_galore --paired --fastqc --illumina read1.fastq.gz read2.fastq.gz
```
## Taxonomía basada en reads
Identificación y cuantificación de las especies en una muestra metagenómica determinada basada en la distribución y secuencia de todos los reads.
Para este proceso crearemos una cuenta en Galaxy.
```
https://usegalaxy.org/
```
Y submitiremos los archivos read1 y read2 posterior al trimming. A continuación ejecutaremos la herramienta Kraken2 con los datos cargados.

## Herramientas de viusalización
Para la visualización de la diversidad de la muestra metagenómica, ejecutaremos la herramienta Krona pie chart en Galaxy con los datos de salida del paso anterior.

## Ensamblaje de metagenomas
Es el proceso de descifrar y reconstruir la secuencia de todos los genomas correspondientes a una muestra a partir de pequeños fragmentos de ADN haciendo uso de algoritmos informaticos. 
Con este fin instalaremos la herramienta MEGAHIT.
```
https://github.com/voutcn/megahit
```
Y ejecutaremos el siguiente codigo
``` bash

megahit -1 read1.fastq.gz -2 read2.fastq.gz -o out 
```

## Control de calidad del metagenoma
Consiste en evaluar la calidad del metagenoma ensamblado previamente basándose principalmente en alineamientos con referencias cercanas.
Para este fin instalaremos y ejecutaremos la herramienta metaquast.
```
https://github.com/ablab/quast
```
Y ejecutaremos el siguiente codigo
``` bash

metaquast.py contigs.fasta -o contigs_metaquast
```

## Predicción de genes
La predicción de genes consiste en identificar regiones codificantes en una secuencia de ADN. Al tratarse de un metagenoma, existe una alta posibilidad de encontrar fragmentos de genes.
Para esta tarea, haremos uso del sitio weg MetaGene donde submitiremos el metagenoma ensamblado.
```
http://metagene.nig.ac.jp/metagene/metagene.html
```

## Bases de datos
Para el análisis de los genes obtenidos es importante compararlos con una base de datos de referencia.
Las mas comunes son:
RefSeq: NCBI Reference Sequence Database
```
https://www.ncbi.nlm.nih.gov/refseq/
```
Uniprot
```
https://www.uniprot.org/
```
Interpro
```
https://www.ebi.ac.uk/interpro/
```
CARD
```
https://card.mcmaster.ca/
```




