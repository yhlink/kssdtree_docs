# Prepare the testing datasets 
The 29 assembled E.coli/Shigella genomes dataset ('ES29') can be downloaded from https://zenodo.org/uploads/12699159.
The 29 unassembled E.coli/Shigella genomes dataset ('ES29'), simulated by DWGIM, can be downloaded from https://zenodo.org/records/12730077.
Or you can use your own data. Here we suppose your genomes path is 'ES29'. 
Note: 'ES29' should be a folder, not a file. The folder should contain at least two genome files in *.fasta or *.fastq format. No other format files should be included.  

# One-step implementation (Recommended)
```
import kssdtree
kssdtree.quick(shuf_file='L3K10.shuf', genome_files='ES29', output='ES29.newick',  method='nj', mode='r')
```

# Multi-step implementation
```
import kssdtree
# Step1、Sketch 29 E.coli/Shigella genomes ('ES29') using k-mer length of 20 and 4,096 fold dimensionality reduction ( imposed by the parameter file L3K10.shuf)
kssdtree.sketch(shuf_file='L3K10.shuf', genome_files='ES29', output='ES29_sketch')

# Step2、Compute the pairwise distance matrix in a NJ compatible format
kssdtree.dist(genome_sketch='ES29_sketch', output='ES29.phylip', flag=0)
# Or in a DNJ compatible format (no diagonal elements)
kssdtree.dist(genome_sketch='ES29_sketch', output='ES29.phylip', flag=1)

# Step3、Construct tree with NJ
kssdtree.build(phylip='ES29.phylip', output='ES29.newick', method='nj')
# Or with DNJ
kssdtree.build(phylip='ES29.phylip', output='ES29.newick', method='dnj')

# Step4、Visualize tree in rectangle mode
kssdtree.visualize(newick='ES29.newick', mode='r')
# Or visualize tree in circle mode
kssdtree.visualize(newick='ES29.newick', mode='c')
```