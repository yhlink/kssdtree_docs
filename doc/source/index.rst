.. Test documentation master file, created by
   sphinx-quickstart on Fri May 10 11:16:08 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Kssdtree
================================
Welcome to the Kssdtree documentation!

Kssdtree is a versatile Python package for phylogenetic analysis, offering three distinct pipelines: the routine pipeline, the reference subtraction pipeline, and the phylogenetic placement pipeline.

Routine Pipeline: A general-purpose tool for phylogenetic analysis of user genomic data.
Reference Subtraction Pipeline: Designed for population-level phylogenetic analysis.
GTDB-based Phylogenetic Placement Pipeline: Facilitates the search for similar genomes in the Genome Taxonomy Database (GTDB), conducting phylogenetic analysis alongside these genomes and positioning the input genomes within the entire prokaryotic tree of life.
Kssdtree also provides one-stop tree construction and visualization. It can handle DNA sequences in both fasta and fastq formats, whether gzipped or not. Additionally, Kssdtree is compatible with multiple platforms (Linux, Windows, and MacOS) and can be run using Jupyter notebooks.
.. toctree::
   :maxdepth: 1

   Install/index
   Quick/index
   API/index
