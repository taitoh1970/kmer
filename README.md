# Programs for the k-mer analysis
This repository provides programs for the k-mer analysis to detect unintended external DNA in a host genome.

## Installation

### Linux
Move to the directory of these programs and type `make`.

### Mac
First of all, install Homebrew. See the following page for installation.

https://brew.sh/

Next, install llvm.

`brew install llvm`

In the directory of the programs, just type `make`. If you don't have `make` in your computer, you also have to install it.

## How to use the programs
There are two programs. The first one is `countmer` that counts the numbers of the k-mers.

    ./countmer vector.fasta mutant_read1.fastq.gz mutant_read2.fastq.gz kmer mutant > mutant.out
    ./countmer vector.fasta wildtype_read1.fastq.gz wildtype_read2.fastq.gz kmer wildtype > wildtype.out

The input files and options to be specified are as follows:

`vector.fasta`: Vector sequence (FASTA format)  
`read1.fastq.gz`: R1 (forward) read  
`read2.fastq.gz`: R2 (reverse) read  
`kmer`: # of k (This value must be 16 or more and 20 is recommended)  
`mutant/wildtype`: Names used as a prefix of output files  
`*.out`: The total # of the k-mers, which is used in the second program.

The second program is `gtest` that conducts a G-test.

    ./gtest mutant.posFreq.txt wildtype.posFreq.txt #mutantMers #wildtypeMers out_prefix

The command line options are:

`mutant.posFreq.txt`: An output file of `countmer`  
`wildtype.posFreq.txt`: An output file of `countmer`  
`#mutantMers`: The number written in `mutant.out`  
`#wildtypeMers`: The number written in `wildtype.out`  
`out_prefix` is a string used as a prefix of an output file.

The output file is `out_prefix.result` and its contents are: `position on the vector`, `k-mer count in mutant`, `k-mer count in wild type`, `G statistic with Williams collection`, and `* (if G > 6.634)`.
