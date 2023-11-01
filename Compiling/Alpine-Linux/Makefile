CLEANFILES = *~

CONTAINER_NAME = compile_emdros_alphine_latest

OUTPUT_DIR = /tmp/emdros_deb_aline_latest


all: build run


build:
	podman build -t $(CONTAINER_NAME) . 

run:
	podman run --env=OUTPUTDIR=$(OUTPUT_DIR) -t $(CONTAINER_NAME)
	podman cp $(CONTAINER_NAME):$(OUTPUT_DIR) - | tar xfv -


run2:
	podman run --detach --tty --env=OUTPUTDIR=$(OUTPUT_DIR) -t $(CONTAINER_NAME) /bin/bash


clean:
	rm -f $(CLEANFILES)


distclean: clean
	rm -rf emdros_deb/
