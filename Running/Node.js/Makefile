DOCKER = podman

CLEANFILES = *~ emdros.deb

PATH_TO_EMDROS_DEB = ../../Compiling/Ubuntu-22.04/emdros_deb_ubuntu_2204/

IMAGE_NAME = localhost/run_emdros_node_ubuntu_2204_image

CONTAINER_NAME = run_emdros_node_ubuntu_2204_container

# Inside the container
OUTPUT_DIR_HOST = emdros_deb_ubuntu_2204
OUTPUT_DIR_CONTAINER = /tmp/$(OUTPUT_DIR_HOST)


all: build run

build: emdros.deb
	$(DOCKER) build --env PATH_TO_EMDROS_DEB=${PATH_TO_EMDROS_DEB} -t $(IMAGE_NAME) . 

run:
	$(DOCKER) run --detach --tty -p 8080:8080 --name $(CONTAINER_NAME) $(IMAGE_NAME)

stop:
	-$(DOCKER) stop $(CONTAINER_NAME)

rm:
	$(DOCKER) rm $(CONTAINER_NAME)

rmi:
	-$(DOCKER) rmi --force $(IMAGE_NAME)

clean: rmi
	rm -f $(CLEANFILES)

distclean: clean


emdros.deb: ${PATH_TO_EMDROS_DEB}/*.deb
	cp $< $@
