FROM alpine:latest

LABEL MAINTAINER KimiChen

ARG emdros_version
ENV EMDROS_VERSION ${emdros_version}

RUN apk add --upgrade bash alpine-sdk

# Add tools to build Emdros
RUN apk add gcc musl-dev g++ make binutils \
	    zlib zlib-dev \
	    git zip \
	    python3

# Node.js -- perhaps not needed... Remove?
# 
# Could Kimi add a node.js server to expose the Emdros REST API on a port?
#
RUN apk add nodejs npm

# Do we need these?
RUN apk add wget

# Just while Ulrik is building the image... Remove when finalized.
RUN apk add emacs-nox

# Add locally compiled version of SWIG
#
# Only needed if we want to build Emdros from a bare git checkout.
# Not for building a released source tarball...
#
#ADD https://raw.githubusercontent.com/emdros/emdros/master/SWIG/download_and_make_local_swig.sh /root/
#RUN bash /root/download_and_make_local_swig.sh 4.1.1

# Add Emdros sources
ADD https://emdros.org/downloads/emdros/emdros-${EMDROS_VERSION}.tar.gz /root/

# Compile Emdros sources
RUN EMDROS_VERSION=${EMDROS_VERSION} cd /root/ && tar xfzv emdros-${EMDROS_VERSION}.tar.gz && cd emdros-${EMDROS_VERSION} && ./configure --prefix=/usr/local --with-swig-nodejs=yes && make && make install

# Start a shell for now
CMD bash

# EXPOSE 3000 <-- emdros process port
# ENTRYPOINT ["emdros"] <-- not sure how to start emdros
