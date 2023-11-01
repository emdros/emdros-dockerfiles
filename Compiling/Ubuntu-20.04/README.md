# Compile Emdros on Ubuntu 20.04 LTS

## What?

A Dockerfile for compiling Emdros on Ubuntu 20.04 LTS, creating a .deb
file.

Tested on Fedora Linux.

## How to use?

1. Install podman or docker.
2. Run in the shell:
```
make build run
```

## Targets available?

```
make all
make build
make run
make clean
make distclean
```

## Outputs

A directory containing the build .deb of Emdros:

```
./emdros_deb_ubuntu_2004/emdros*.deb
```

