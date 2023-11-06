CLEANFILES = *~

IMAGE_NAME = localhos/compile_emdros_ubuntu_2004_image

CONTAINER_NAME = compile_emdros_ubuntu_2004_container


# Inside the container
OUTPUT_DIR_HOST = emdros_deb_ubuntu_2004
OUTPUT_DIR_CONTAINER = /tmp/$(OUTPUT_DIR_HOST)


all: rmi build run cp stop rm


build:
	podman build -t $(IMAGE_NAME) . 

run:
	podman run --env 'OUTPUT_DIR=$(OUTPUT_DIR_CONTAINER)' --name $(CONTAINER_NAME) $(IMAGE_NAME)

cp:
	podman cp $(CONTAINER_NAME):$(OUTPUT_DIR_CONTAINER) - | tar xfv -

stop:
	-podman stop $(CONTAINER_NAME)

rm:
	podman rm $(CONTAINER_NAME)

rmi:
	-podman rmi --force $(IMAGE_NAME)

clean: rmi
	rm -f $(CLEANFILES)

distclean: clean
	rm -rf $(OUTPUT_DIR_HOST)/


