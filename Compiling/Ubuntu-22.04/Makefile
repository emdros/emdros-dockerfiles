DOCKER = docker

CLEANFILES = *~

IMAGE_NAME = localhos/compile_emdros_ubuntu_2204_image

CONTAINER_NAME = compile_emdros_ubuntu_2204_container


# Inside the container
OUTPUT_DIR_HOST = emdros_deb_ubuntu_2204
OUTPUT_DIR_CONTAINER = /tmp/$(OUTPUT_DIR_HOST)


all: rmi build run cp stop rm


build:
	$(DOCKER) build -t $(IMAGE_NAME) . 

run:
	$(DOCKER) run --env 'OUTPUT_DIR=$(OUTPUT_DIR_CONTAINER)' --name $(CONTAINER_NAME) $(IMAGE_NAME)

cp:
	$(DOCKER) cp $(CONTAINER_NAME):$(OUTPUT_DIR_CONTAINER) - | tar xfv -

stop:
	-$(DOCKER) stop $(CONTAINER_NAME)

rm:
	$(DOCKER) rm $(CONTAINER_NAME)

rmi:
	-$(DOCKER) rmi --force $(IMAGE_NAME)

clean: rmi
	rm -f $(CLEANFILES)

distclean: clean
	rm -rf $(OUTPUT_DIR_HOST)/


