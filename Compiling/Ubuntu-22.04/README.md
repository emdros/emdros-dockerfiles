# Compile Emdros on Ubuntu 22.04 LTS

## What?

A Dockerfile for compiling Emdros on Ubuntu 22.04 LTS, creating a .deb
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
./emdros_deb_ubuntu_2204/emdros*.deb
```

