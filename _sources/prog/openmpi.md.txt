# OpenMPI

[OpenMPI](https://www.open-mpi.org/) is a High Performance Message Passing Library

## Download
Download specified version in [download page](https://www.open-mpi.org/software/ompi/v4.1/)

## Compilation with intel compiler

### Module load intel compiler
Load intel compiler first, and activate enveronment variables. write following commands to `.bashrc`
```
module load intel/2018u4
source /usr/local/intel/2018u4/bin/compilervars.sh intel64
```

### Run configure 
Change directory to `openmpi-3.1.4` and run

```
./configure --prefix=/path/to/openmpi-3.1.4 --enable-mpirun-prefix-by-default --without-psm CC=icc CXX=icpc FC=ifort F77=ifort
```

### Run make

```
make -j && make install
```

