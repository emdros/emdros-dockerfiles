# Compile Emdros on Ubuntu 20.04 LTS

## What?

A Dockerfile for compiling Emdros on Ubuntu 20.04 LTS, creating a .deb
file.

Tested on Fedora Linux.

## Useful?

Currently, the generated container is only able to compile the .deb
and show you on the console whether it succeeded.

## How to use?

1. Install podman or docker.
2. Run in the shell:
```
make build run
```

## Targets available?

```
make build
make run
make clean
```



## What still needs to be done?

- Enable extracting the generated .deb and/or the generated source tarball.


