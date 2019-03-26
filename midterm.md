# Code for Midterm:
## Blast
### Make database:
`makeblastdb -in Ec_k12.ffn -dbtype nucl`

`makeblastdb -in Ec_K12.faa -dbtype prot` 

### Run Blast:
Nucletotide:

`blastn -db Ec_K12.ffn -query My_sequences.ffn -out My_sequences.blastn -evalue 1e-05`

Protein:

`blast- -db Ec_K12.faa -query My_sequences.faa -out My_sequences.blastp -evalue 1e-05`

Blastx:

`blast- -db Ec_K12.faa -query My_sequences.ffn -out My_sequences.blastx -evalue 1e-05`

Other:

`tblastn -db Ec_K12.ffn -query My_sequences.faa -out My_sequences.tbalstn -evalue 1e-05`

`tblastx -db Ec_K12.ffn -query My_sequences.ffn -out My_sequences.tblastx -evalue le-05`

Flags:

`-outfmt 8` outputs as a table with no alignments.

## Genome Assemblies:

### Velvet:

`velveth Ypestis_velvet21 21 -fastq -shortPaired -separate SRR133640_1.fastq SRR133640_2.fastq`

Then `velvetg` is run on the output folder of `velveth` and assembles the sequences:

`velvetg Ypestis_velvet21 -exp_cov auto -cov_cutoff auto`

## Fetching from SRA

`ftp://ftp-trace.ncbi.mln.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR133/SRR133640/Srr133640.sra`

## SRA to fastq: `fastqdump`:
```
% fastq-dump \
    --split-files --split-spot --skip-technical \
    --minReadLen 64 \
    --defline-seq  @\$ac.\$si \
    --defline-qual "+" \
    ./SRR133640.sra
```
    
https://edwards.sdsu.edu/research/fastq-dump/



ftp://ftp-trace.ncbi.mln.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR805/SRR8053472/SRR8053472.sra

ftp://ftp-trace.ncbi.mln.nih.gov/sra/sra-instant/reads/ByRun/sra/SRR/SRR855/SRR8550118/SRR8550118.sra
