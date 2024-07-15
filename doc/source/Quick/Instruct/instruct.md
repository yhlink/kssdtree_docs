```
def quick(shuf_file, genome_files, output, reference=None, database=None, method='nj', mode='r', N=0):
# Parameters shuf_file, genome_files, and output are required, and the other parameters are optional.
if reference is None and database is None:
# Routine Pipeline
elif reference is not None and database is None:
# Reference Subtraction Pipeline
elif reference is None and database == 'gtdbr214':
# GTDB-based Phylogenetic Placement Pipeline
else:
# Pipeline Error
```
