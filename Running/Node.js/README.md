# Running Emdros + Node.js on Ubuntu 22.04 LTS

## What?

A template Dockerfile for Running Emdros and Node.js on Ubuntu 22.04
LTS.

Tested on Fedora Linux.

# Not complete

NOTE: This is just an example to be modified. It does not actually run
Emdros on Node. You will have to write some code to make this happen.

# Test script

There is a test script in test/test_Emdros_Node.js which you are free
to modify.

## How to use?

1. Install podman.
2. Run in a shell:
```
make all
```

## Targets available?

```
make all         -- Runs all the requisite targets
make build       -- Build an image
make run         -- Run the actual compilation
make rm          -- Remove the container
make rmi         -- Remove the image
make clean       -- Clean up most things, including running target rmi
make distclean   -- Clean up everything
```

