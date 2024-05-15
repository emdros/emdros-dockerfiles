# Compile Emdros on Ubuntu latest

## What?

A Dockerfile for compiling Emdros on Ubuntu latest, creating a .deb
file.

Tested on Fedora Linux.

## How to use?

1. Install podman or docker.
2. If you installed podman, do `alias docker=podman`, or change the
   DOCKER variable in the Makefile.
3. Run in the shell:
```
make all
```

## Targets available?

```
make all         -- Runs all the requisite targets
make build       -- Build an image
make run         -- Run the actual compilation
make cp          -- Copy the built .deb into ./emdros_deb_ubuntu_2204/
make rm          -- Remove the container
make rmi         -- Remove the image
make clean       -- Clean up most things, including running target rmi
make distclean   -- Clean up everything
```

## Outputs

A directory containing the build .deb of Emdros:

```
./emdros_deb_ubuntu_latest/emdros*.deb
```

