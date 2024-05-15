DOCKER = podman

CLEANFILES = *~

IMAGE_NAME = localhost/compile_emdros_ubuntu_latest_image

CONTAINER_NAME = compile_emdros_ubuntu_latest_container

#
# These are passed to the Emdros configure script when building Emdros.
#
# You can change them to suit your needs.
#
# The file INSTALL in the root of the Emdros sources tells you what
# switches you can pass.
#
EMDROS_CONFIGURE_SWITCHES = \
     --with-sqlite3=yes \
     --with-mysql=no \
     --with-postgresql=no \
     --with-bpt=no \
     --with-swig-language-csharp=no \
     --with-swig-language-java=no \
     --with-swig-language-python=no \
     --with-swig-language-python3=no \
     --with-swig-language-php7=no \
     --with-swig-language-php8=no \
     --with-swig-language-nodejs=yes


# Inside the container
OUTPUT_DIR_HOST = emdros_deb_ubuntu_latest
OUTPUT_DIR_CONTAINER = /tmp/$(OUTPUT_DIR_HOST)


all: rmi build run cp stop rm


build:
	$(DOCKER) build -t $(IMAGE_NAME) . 

run:
	$(DOCKER) run --env 'OUTPUT_DIR=$(OUTPUT_DIR_CONTAINER)' --env 'EMDROS_CONFIGURE_SWITCHES=$(EMDROS_CONFIGURE_SWITCHES)' --name $(CONTAINER_NAME) $(IMAGE_NAME)

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


