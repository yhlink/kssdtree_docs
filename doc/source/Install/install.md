Kssdtree require the python 3.6 or lower version and the dependent packages `pyqt5`, `ete3`, and `requests`. If Kssdtree is installed using the pip command, these dependencies should be installed automatically. For Windows, it also requires the installation of the gzip tool for sequence decompression and the GCC (Microsoft Visual C++) compiler.
# Linux
```
pip install kssdtree
```

# MacOS
```
# Install gcc
brew install gcc

# Install Kssdtree (x86_64 architecture)
pip install kssdtree

# Install Kssdtree (arm64 architecture)
arch -x86_64 $(which python3) -m pip install kssdtree
```

# Windows
```
# Create a virtual environment
conda create --name=kssdtree python=3.6.13

# Activate the virtual environment
conda activate kssdtree

# Install libpython and m2w64-toolchain 
conda install libpython m2w64-toolchain -c msys2

# Install Kssdtree
pip install kssdtree
```
