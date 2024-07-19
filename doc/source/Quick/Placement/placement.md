# Download testing datasets 
The assembled prokaryotic genome ('PROK1') can be downloaded from https://zenodo.org/uploads/12699159.
The unassembled prokaryotic genome ('PROK1') can be downloaded from https://zenodo.org/records/12730077.
Or use your own data, here we suppose your genome path is 'PROK1'. Or directly take a genome file 'PROK1/GCF_001228905.1_7038_3_46_genomic.fna.gz' as input.
Note: 'PROK1' should be a folder, and the folder should contain only genome files (*.fasta or *.fastq).


# One-step implementation (Recommended)
```
import kssdtree

kssdtree.quick(shuf_file='L3K9.shuf', genome_files='PROK1', output='PROK31', database='gtdbr214', method='nj', mode='r', N=30)
```


# Multi-step implementation
```
import kssdtree

# Step1. Sketch the query genomes 
kssdtree.sketch(shuf_file='L3K9.shuf', genome_files='PROK1', output='PROK1_sketch', set_opt=True)

# Step2. Retrieve N closest genomes from the remote gtdbr214 database for each of the query genomes and compute the distance matrix and construct the phylogenetic tree. It will create 'output.newick' and 'output_accession_taxonomy.txt' in the output folder (e.g., ‘PROK31’ here).
kssdtree.retrieve(database='gtdbr214', genome_sketch='PROK1_sketch', output='PROK31', N=30, method='nj')

# Step3. Visualize tree 
kssdtree.visualize(newick='./PROK31/output.newick', taxonomy='./PROK31/output_accession_taxonomy.txt', mode='r')
```
