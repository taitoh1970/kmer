# Programs for the k-mer analysis
This repository provides programs for k-mer analysis to detect unintended external DNA in a host genome.

For the latest version, visit:
[https://github.com/hirsakai/GenEditScan](https://github.com/hirsakai/GenEditScan)

## Installation

### Linux
Navigate to the directory containing the k-mer analysis programs and execute the `make` command.

### Mac
First, install Homebrew by following the instructions on the official website: [https://brew.sh/](https://brew.sh/)

Next, install LLVM.

`brew install llvm`

In the directory containin the k-mer analysis programs, simply run `make`. If `make` is not installed on your system, you will need to install it as well.

## How to use the programs
There are two programs:
1. `countmer` - Counts the number of k-mers.
2. `gtest` - Perform a G-test.

### `countmer` (k-mer counting)

    ./countmer vector.fasta mutant_read1.fastq.gz mutant_read2.fastq.gz kmer mutant > mutant.out
    ./countmer vector.fasta wildtype_read1.fastq.gz wildtype_read2.fastq.gz kmer wildtype > wildtype.out

Input files and options:

`vector.fasta`: Vector sequence (FASTA format)  
`read1.fastq.gz`: R1 (forward) read  
`read2.fastq.gz`: R2 (reverse) read  
`kmer`: k-mer size (must be 16 or greater; 20 is recommended)  
`mutant/wildtype`: Prefix used for output file names  
`*.out`: Fiie containing the total k-mer count, used used as input for `gtest`.

### `gtest` (G-test)

    ./gtest mutant.posFreq.txt wildtype.posFreq.txt #mutantMers #wildtypeMers out_prefix

Command-line options:

`mutant.posFreq.txt`: Output file from `countmer`  
`wildtype.posFreq.txt`: Output file from `countmer`  
`#mutantMers`: The number from `mutant.out`  
`#wildtypeMers`: The number from `wildtype.out`  
`out_prefix`: Prefix for the output file name.

### Output file
`out_prefix.result`: File containing the following columns:
- Position on the vector
- k-mer count in mutant
- k-mer count in wild type
- G statistic with Williams collection
- `*` (if G > 6.634)

## Citation
If you use these programs in your work, please cite the following paper:

Itoh T, Onuki R, Tsuda M, Oshima M, Endo M, Sakai H, Tanaka T, Ohsawa R, Tabei Y.
"Foreign DNA detection by high-throughput sequencing to regulate genome-edited agricultural products"
Sci Rep. 2020 Mar 18;10(1):4914.
doi: [10.1038/s41598-020-61949-5](https://doi.org/10.1038/s41598-020-61949-5)
