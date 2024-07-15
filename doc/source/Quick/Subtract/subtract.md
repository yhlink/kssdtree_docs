# Prepare the testing datasets
The reference genome 'hg38.fa.gz', 43 human genomes dataset ('HG43') can be downloaded from https://zenodo.org/uploads/12699159. 
Or use your own data, here we suppose the reference genome is 'hg38.fa.gz' and your genome files path is 'HG43'.
Note: 'HG43' should be a folder containing 43 human genome files (*.fasta), 

# One-step implementation (Recommended)
```
import kssdtree

kssdtree.quick(shuf_file='L3K10.shuf', genome_files='HG43', output='HG43.newick', reference='hg38.fa.gz', method='nj', mode='r')
```
# Multi-step implementation
```
import kssdtree

# Step1、Sketch the human reference genome ('hg38.fa.gz') and 43 individual genomes ('HG43') kssdtree.sketch(shuf_file='L3K10.shuf', genome_files='hg38.fa.gz', output='Ref_sketch', set_opt=True)
kssdtree.sketch(shuf_file='L3K10.shuf', genome_files='HG43', output='HG43_sketch', set_opt=True)

# Step2、Subtract reference sketches (Ref_sketch) from input sketches (HG43_sketch)
kssdtree.subtract(ref_sketch='Ref_sketch', genome_sketch='HG43_sketch', output='HG43_sub_sketch')

# Step3、Compute the pairwise distance matrix in a NJ compatible format
kssdtree.dist(genome_sketch='HG43_sub_sketch', output='HG43.phylip', flag=0)

# Step4、Construct tree with NJ
kssdtree.build(phylip='HG43.phylip', output='HG43.newick', method='nj')

# Step5、Visualize tree 
kssdtree.visualize(newick='HG43.newick', mode='r')
```
