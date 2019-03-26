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
`tblastx -db Ec_K12.ffn -quert My_sequences.ffn -out My_sequences.tblastx -evalue le-05`
