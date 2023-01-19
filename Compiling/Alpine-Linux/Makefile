# Download and compile this Emdros version from the
# https://emdros.org/downloads/emdros/
# directory.
#
# (You can go there and see which versions are available.)
EMDROS_VERSION = 3.8.0


CLEANFILES = *~



all:


build:
	podman build --build-arg emdros_version=$(EMDROS_VERSION) -t compile_emdros_alpine .

run:
	podman run -t compile_emdros_alpine

clean:
	rm -f $(CLEANFILES)
