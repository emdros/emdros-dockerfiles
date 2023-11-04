CLEANFILES = *~

CONTAINER_NAME = compile_emdros_ubuntu_2204

OUTPUT_DIR = /tmp/emdros_deb_ubuntu_2204/


all: build run


build:
	podman build -t $(CONTAINER_NAME) . 

run:
	podman run --env=OUTPUTDIR=$(OUTPUT_DIR) -t $(CONTAINER_NAME)
	podman cp $(CONTAINER_NAME):$(OUTPUT_DIR) - | tar xfv -

clean:
	rm -f $(CLEANFILES)

distclean: clean
	rm -rf emdros_deb/
