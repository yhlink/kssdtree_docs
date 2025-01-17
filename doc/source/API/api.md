# shuffle function
```
def shuffle(k=None, s=None, l=None, o=None):
    """
       Generate a k-mer substring space shuffled file.

       Args:
           k (int): Half-length of k-mer. k=x means using k-mer of length 2x.
           s (int): Half-length of k-mer substring. s=x means the whole space is the collection of all 2x-mers. Make sure l < s < k. Default is -s 6, usually there's no need to change this setting.
           l (int): The level of dimensionality-reduction. l=x means the expected rate of dimensionality-reduction is 16^x.
           o (str): Output filename of the .shuf file.

       Returns:
           bool: True

       Example:
           >>> kssdtree.shuffle(k=10, s=6, l=3, o='L3K10.shuf')
           True
            
    """
    return True
```
# sketch function
```
def sketch(shuf_file=None, genome_files=None, output=None, set_opt=None):
    """
    
       Sketch genomes and generate sketch files.

       Args:
           shuf_file (str): Path to the .shuf file. Kssdtree provides optional .shuf files which specifies different parameters of k-mer length and dimensionality-reduction level ('L3K9.shuf', 'L3K10.shuf', etc.) . If the .shuf file does not exist in current path, it will be automatically generated or downloaded. Default .shuf file is 'L3K10.shuf'. Other .shuf files will automatically generated by called shuffle function.
           genome_files (str): Path for the genome files. Kssdtree supports genome files of both fasta or fastq format.
           output (str): Output folder path for the sketch generated.
           set_opt (bool): Perform set operations (subtract and retrieve) if needed. Default is False. To perform set operations, set set_opt=True.

       Returns:
           bool: True

       Example:
           >>> kssdtree.sketch(shuf_file='L3K10.shuf', genome_files='ES29', output='ES29_sketch')
           True
           >>> kssdtree.sketch(shuf_file='../shuf_file/L3K10.shuf', genome_files='../data/ES29', output='ES29_sketch')
           True
           >>> kssdtree.sketch(shuf_file='L3K10.shuf', genome_files='hg38.fa.gz', output='Ref_sketch', set_opt=True)
           True
           >>> kssdtree.sketch(shuf_file='L3K10.shuf', genome_files='HG43', output='HG43_sketch', set_opt=True)
           True
           >>> kssdtree.sketch(shuf_file='L3K9.shuf', genome_files='PROK1', output='PROK1_sketch', set_opt=True)
           True
           
    """
    return True
```
# dist function
```
def dist(genome_sketch=None, output=None, flag=None):
    """
    
       Compute the distance matrix for the input genome sketches.

       Args:
           genome_sketch (str): Path to the folder of genome sketch.
           output (str): Filename for the output distance matrix.
           flag (int): Specifies the way to generate the distance matrix, where 0 is for NJ algorithm (with zeros on the diagonal), and 1 is for DNJ algorithm (without the diagonal elements).

       Returns:
           bool: True

       Example:
           >>> kssdtree.dist(genome_sketch='ES29_sketch', output='ES29.phylip', flag=0)
           True
           >>> kssdtree.dist(genome_sketch='ES29_sketch', output='ES29.phylip', flag=1)
           True
           
    """
    return True
```
# retrieve function
```
def retrieve(database=None, genome_sketch=None, output=None, N=None, method=None):
    """
    
       Retrieve the N closest genomes from the gtdbr214 database, compute the distance matrix for the query and the retrieved genomes, and construct the phylogenetic tree. The resulted files 'output.newick' and 'output_accession_taxonomy.txt' will be placed in the folder specified by the argument ��output�� .

       Args:
           database (str): gtdbr214.
           genome_sketch (str): Path to the folder containing sketch result files of genomes.
           output (str): Path to the result files.
           N (int): Maximum number of nearest reference genomes to retrieve.
           method (str): Method for constructing the tree, either 'nj' (NJ) or 'dnj' (DNJ). Defaults to 'nj'.

       Returns:
           bool: True

       Example:
           >>> kssdtree.retrieve(database ='gtdbr214', genome_sketch='PROK1_sketch', output='PROK31', N=30, method='nj')
           True
           
    """
    return True

```
# build function
```
def build(phylip=None, output=None, method=None):
    """
    
        Construct the phylogenetic tree in newick format using the NJ or DNJ method.

        Args:
            phylip (str): Path to the distance matrix file in phylip format.
            output (str): Filename for the output tree in newick format.
            method (str): Method for constructing the tree, either 'nj' (NJ) or 'dnj' (DNJ). Defaults to 'nj'.

        Returns:
            bool: True

        Example:
            >>> kssdtree.build(phylip='ES29.phylip', output='ES29.newick', method='nj')
            True
            >>> kssdtree.build(phylip='ES29.phylip', output='ES29.newick', method='dnj')
            True

    """
    return True

```
# visualize function
```
def visualize(newick=None, taxonomy=None, mode=None):
    """
    
       Visualize a tree using the ETE3 toolkit.

       Args:
           newick (str): Path to the tree file in newick format.
           taxonomy (str): For phylogenetic placement pipeline, should set the path for 'output_accession_taxonomy.txt' . Default is None.
           mode (str): Visualization mode, either 'r' (rectangle) or 'c' (circle). Default is 'r'.

       Returns:
           bool:True

       Example:
           >>> kssdtree.visualize(newick='ES29.newick', mode='r')
           True
           >>> kssdtree.visualize(newick='ES29.newick', mode='c')
           True
           >>> kssdtree.visualize(newick='./PROK31/output.newick', taxonomy='./PROK31/output_accession_taxonomy.txt', mode='r')
           True

    """
    return True
```
# subtract function
```
def subtract(ref_sketch=None, genome_sketch=None, output=None):
    """

       Subtract the reference sketches from the genome sketches and create the remainder sketch files.

       Args:
           ref_sketch (str): Path to the reference genome sketch.
           genome_sketch (str): Path to the folder of the genome sketches.
           output (str): Path to the remainder sketch.

       Returns:
           bool: True

       Example:
           >>> kssdtree.subtract(ref_sketch='Ref_sketch', genome_sketch='HG43_sketch', output='HG43_sub_sketch')
           True
            
    """
    return True
```

# quick function
```
def quick(shuf_file=None, genome_files=None, output=None, reference=None, database=None, method=None, mode=None,
          N=None):
    """
    
       Simplify the pipeline and eliminate the necessity of organizing intermediate files.

       Args:
           shuf_file (str): Path to the .shuf file. Kssdtree provides optional .shuf files which specifies different parameters of k-mer length and dimensionality-reduction level ('L3K9.shuf', 'L3K10.shuf', etc.) . If the .shuf file does not exist in current path, it will be automatically generated or downloaded. Default .shuf file is 'L3K10.shuf'. Other .shuf files will automatically generated by called shuffle function. For GTDB-based phylogenetic placement pipeline, only 'L3K9.shuf' can be used.
           genome_files (str): Path to the folder containing genome files. It supports input of genome files in fasta or fastq format.
           output (str): For routine and reference subtraction pipelines, the output is a .newick format file. For the GTDB-based phylogenetic placement pipeline, the output is a folder, including 'output.newick' and 'output_accession_taxonomy.txt'.
           reference (str): For reference subtraction pipeline, it is the file or folder path to the reference genome.
           database (str): For GTDB-based phylogenetic placement pipeline, set to 'gtdbr214'.
           method (str): Method for constructing the tree, either 'nj' (NJ) or 'dnj' (DNJ). Default is 'nj'.
           mode (str): Visualization mode, either 'r' (rectangle) or 'c' (circle). Default is 'r'.
           N (int): Maximum number of nearest reference genomes. Default is 0 for routine and reference subtraction pipelines. For GTDB-based phylogenetic placement pipeline should set N > 0.
       
       Instructions:
           Parameters shuf_file, genome_files, and output are required, and the other parameters are optional.
           if reference is None and database is None:
           # Routine Pipeline
           elif reference is not None and database is None:
           # Reference Subtraction Pipeline
           elif reference is None and database == 'gtdbr214':
           # GTDB-based Phylogenetic Placement Pipeline
           else:
           # Pipeline Error
       
       Returns:
           bool: True

       Example:
           >>> kssdtree.quick(shuf_file='L3K10.shuf', genome_files='ES29', output='ES29.newick',  method='nj', mode='r')
           True
           >>> kssdtree.quick(shuf_file='L3K10.shuf', genome_files='HG43', output='HG43.newick', reference='hg38.fa.gz', method='nj', mode='r')
           True
           >>> kssdtree.quick(shuf_file='L3K9.shuf', genome_files='PROK1', output='PROK31', database='gtdbr214', method='nj', mode='r', N=30)
           True
            
    """
    return True
```

