Kssdtree requires the Python 3 environment and the dependent packages `pandas`, `pyqt5`, `ete3`, and `requests`. If Kssdtree is installed using the pip command, these dependencies will be installed automatically. For MacOS, it requires Python 3.8 or higher version. For Windows, it requires Python 3.6 version and the installation of the gzip tool for sequence decompression.
# Linux
```
pip install kssdtree
```
# MacOS
```
# Install gcc (/opt/homebrew/bin/gcc-12) 
brew install gcc@12

# Create a virtual environment
conda create --name=kssdtree python=3.10

# Activate the virtual environment
conda activate kssdtree

# Install kssdtree
pip install kssdtree
```
# Windows
```
# Create a virtual environment
conda create --name=kssdtree python=3.6.13

# Activate the virtual environment
conda activate kssdtree

# Install libpython and m2w64-toolchain
conda install libpython m2w64-toolchain -c msys2

# Install kssdtree
pip install kssdtree
```
