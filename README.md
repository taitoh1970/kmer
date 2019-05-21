## Programs for the k-mer analysis
This repository provides programs for the k-mer analysis to detect unintended external DNA in a host genome.

## How to install
Move to the directory of this program and type `make` to create the programs.

## How to use the programs
There are two programs. The first one is `countmer` that count the numbers of the k-mers.

    ./countmer vector.fasta mutant_read1.fastq.gz mutant_read2.fastq.gz kmer mutant
    ./countmer vector.fasta wildtype_read1.fastq.gz wildtype_read2.fastq.gz kmer wildtype

The input files needed are as follows:

`vector.fasta` Vector sequence (FASTA format)  
`read1.fastq.gz` R1 (forward) read  
`read2.fastq.gz` R2 (reverse) read  
`kmer` # of k  
`out_prefix` Prefix of an output file  
