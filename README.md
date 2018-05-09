# Bacterial RNA-seq Analysis
The simplest and fastest RNA-seq analysis pipeline for *Pseudomonas aeruginosa* (or any bacterium with a reference genome) using Rockhopper system. This software was developed by [Brian Tjaden](http://www.wellesley.edu/cs/faculty/tjaden) at the Department of Computer Science, Wellesley College.

The example provided here is done using *Pseudomonas aeruginosa* strain UCBPP-PA14. For any other bacteria that already has a reference genome, you can simply modify the -g argument with your reference genome.
Rockhopper can run on any platform, but herein I providing an example using UNIX because I had many files. Rockhopper needs Java to run, so make sure you have it first. Then download the JAR file of [Rockhopper]( https://cs.wellesley.edu/~btjaden/Rockhopper/download.html) and run it.

You can use either FASTQ or FASTA as input. Here I have 2 experiemntal groups, control and treatment, and in each group I have 3 replicates. Notice that for each sample there are 2 files (one ending with R1 and the other with R2) because they resulted from paired-end sequencing. You need to separate each pair of files with "%", the samples with ",", and the 2 groups with a " ".

```
java -Xmx4096m -cp ~/Rockhopper.jar Rockhopper -o output/ -g genomes/Pseudomonas_aeruginosa_UCBPP_PA14/ C1_R1.fastq%C1_R2.fastq,C2_R1.fastq%C2_R2.fastq,C3_R1.fastq%C3_R2.fastq T1_R1.fastq%T1_R2.fastq,T2_R1.fastq%T2_R2.fastq,T3_R1.fastq%T3_R2.fastq -v true -L control,treatment
```

The main output file is a CSV file that includes, raw count, normalized count for each gene, p-value and q-value (corrected p-value). The other file "summary" will show you the percentage of reads that were aligned to each strand, protein-coding, non-coding regions, and ribosomal RNA.

## References
[Rockhopper](https://cs.wellesley.edu/~btjaden/Rockhopper/index.html)

[Pseudomonas](http://www.pseudomonas.com/)
