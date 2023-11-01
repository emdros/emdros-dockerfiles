FROM alpine:latest

MAINTAINER ulrikp

RUN apk add --upgrade bash alpine-sdk

# Add tools to build Emdros
RUN apk add alpine-sdk \
            gcc musl-dev g++ make binutils \
	    zlib zlib-dev \
	    git zip \
	    python3 python3-dev \
	    pcre2 pcre2-dev \
	    autoconf automake libtool \
	    wget \
	    re2c

RUN apk add emacs-nox

#
# Add locally compiled version of SWIG
ADD https://raw.githubusercontent.com/emdros/emdros/master/SWIG/download_and_make_local_swig.sh /root/
RUN bash /root/download_and_make_local_swig.sh 4.1.1

# Add script to build a .apk
#ADD https://raw.githubusercontent.com/emdros/emdros/master/build-apk.sh ./root/

ADD build-apk.sh /root/



CMD /bin/bash


# Build Emdros, using the swig binary installed in /root/opt/bin,
# Then copying the 
#CMD export PATH=/root/opt/bin:${PATH} && \
#    install -m 755 -d ${OUTPUT_DIR} && \
#    install -m 644 /root/build/emdros-build-2/emdros/emdros*.deb ${OUTPUT_DIR}/
