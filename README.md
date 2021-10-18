[![test](https://github.com/wtsi-hpag/PretextGraph/actions/workflows/test.yml/badge.svg)](https://github.com/wtsi-hpag/PretextGraph/actions/workflows/test.yml)
[![Anaconda-Server Badge](https://anaconda.org/bioconda/pretext-suite/badges/installer/conda.svg)](https://conda.anaconda.org/bioconda)
[![Anaconda-Server Badge](https://anaconda.org/bioconda/pretextgraph/badges/downloads.svg)](https://anaconda.org/bioconda/pretextgraph)
# PretextGraph
Converts bedgraph formatted data and embeds inside a Pretext contact map.

# Bioconda
All commandline Pretext tools for Unix (Linux and Mac) are available on [bioconda](https://bioconda.github.io/).<br/>

The full suite of Pretext tools can be installed with
```sh
> conda install pretext-suite
```
Or, just PretextGraph can be installed with
```sh
> conda install pretextgraph
```

# Usage
PretextGraph reads bedgraph formatted data from `stdin`, e.g:<br/>
```bash
> zcat bedgraph.file.gz | PretextGraph -i input.pretext -n "graph name"
> bigWigToBedGraph bigwig.file /dev/stdout | PretextGraph -i input.pretext -n "graph name"
```
Important: only non-negative integer data is supported.

# Options
-i input Pretext file, required. Sequence names in the Pretext file must match sequence names in the bedgraph data; although relative sort order is unimportant.<br/>
-n graph name, required. A name for the graph.<br/>

-o output Pretext file, optional. If no output is specified the graph data will be appended to the input file.<br/>

# Requirments, running
4 cpu cores <br/>
128M RAM <br/>

# Viewing graphs
[PretextView](https://github.com/wtsi-hpag/PretextView) version 0.1.2 or later.

# Third-Party acknowledgements
PretextGraph uses the following third-party libraries:<br/>
* [libdeflate](https://github.com/ebiggers/libdeflate)<br/>
* [stb_sprintf.h](https://github.com/nothings/stb/blob/master/stb_sprintf.h)

# Installation
Requires:
* clang >= 11.0.0
* meson >= 0.57.1
```bash
git submodule update --init --recursive
env CXX=clang meson setup --buildtype=release --unity on --prefix=<installation prefix> builddir
cd builddir
meson compile
meson test
meson install
