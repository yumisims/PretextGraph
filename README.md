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
zcat bedgraph.file.gz | PretextGraph -i input.pretext -n "graph name"<br/>
bigWigToBedGraph bigwig.file /dev/stdout | PretextGraph -i input.pretext -n "graph name"

Important: only non-negative integer data is supported.

# Options
-i input Pretext file, required. Sequence names in the Pretext file must match sequence names in the bedgraph data; although relative sort order is unimportant.<br/>
-n graph name, required. A name for the graph.<br/>

-o output Pretext file, optional. If no output is specified the graph data will be appended to the input file.<br/>

# Requirments, running
4 cpu cores <br/>
2M RAM <br/>

# Viewing graphs
[PretextView](https://github.com/wtsi-hpag/PretextView) version 0.1.2 or later.

# Mac and Linux builds
Prebuilt binaries for Mac and Linux are available<br/>
The Mac binary was build on MacOS 10.13.6<br/>
The Linux binary was build on kernel 3.13<br/>
Prebuilt binaries now come in 4-different varieties: AVX2, AVX, SSE4.2 and SSE4.1 along with a wrapper program. Just keep all the binaries on the same path and run the wrapper (PretextGraph); the correct binary for your architecture will be executed.

# Third-Party acknowledgements
PretextGraph uses the following third-party libraries:<br/>
    libdeflate (https://github.com/ebiggers/libdeflate)<br/>
    stb_sprintf.h (https://github.com/nothings/stb/blob/master/stb_sprintf.h)

# Requirments, building via script (Mac and Linux)
make<br/>
python (2 or 3) to run the installation script<br/>
clang or gcc to compile<br/>

Tested on Ubuntu linux kernel 3.13 with clang-10, gcc-5.5<br/>
Tested on MacOS 10.13.6 with clang-10<br/>

PretextGraph requires libdeflate (https://github.com/ebiggers/libdeflate). By default the install script will clone and build the libdeflate.a static library for compilation with PretextGraph. You can specify your own version to the install script if you wish (you'll have to specify appropriate linking flags as well if you specify a shared library).

run ./install to build (run ./install -h to see options)

# Requirments, building on Windows
Only recomended you know how to compile executables for Windows.<br/>

Tested on Windows 10 using the Visual Studio 2019 toolchain<br/>
Tested with clang-9<br/>
Requires at least SSE4.1 support. 

Requires libdeflate (https://github.com/ebiggers/libdeflate)<br/>

Compile PretextGraph.cpp and link against libdeflate<br/>
