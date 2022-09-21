# Singularity Flux

This will reproduce the example [here](https://docs.sylabs.io/guides/3.10/user-guide/mpi.html).

## Usage

Pull the container with Singularity and oras:

```bash
$ singularity pull oras://ghcr.io/rse-ops/singularity-mpi:mpich
```

You might want an allocation (with or without userns):

```bash
$ salloc --userns
```

Try running the container:

```bash
$ mpirun -n 6 singularity exec singularity-mpi_mpich.sif /opt/mpitest
```
```console
Hello, I am rank 1/6
Hello, I am rank 2/6
Hello, I am rank 3/6
Hello, I am rank 4/6
Hello, I am rank 0/6
Hello, I am rank 5/6
```

And then try running with flux

```bash
$ flux start mpirun -n 6 singularity exec singularity-mpi_mpich.sif /opt/mpitest
```
