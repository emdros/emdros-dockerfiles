FROM ubuntu:22.04

MAINTAINER ulrikp

# Make the installation Noninteractive, so as to not stop, e.g., when
#  configuring tzdata.
#
# See https://github.com/phusion/baseimage-docker/issues/58#issuecomment-47995343
#
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

RUN apt-get update && apt-get upgrade -y 

RUN apt-get install -y \
        emacs-nox \
        git \
	wget \
        g++ make binutils build-essential \
        re2c \
        fakeroot debhelper \
        pkg-config \
        python3 python3-dev \
        virtualenv python3-virtualenv \
        mono-devel mono-mcs mono-tools-devel \
        automake autoconf libtool autotools-dev \
        zip \
        zlib1g zlib1g-dev \
        libxml2-utils \
        groff imagemagick \
        texlive-latex-base latex2html \
   && apt-get install -y \
	mysql-server \
	mysql-client \
        libmysqlclient-dev \
   && apt-get install -y \
        postgresql \
	postgresql-client \
	libpq-dev \
   && apt-get install -y \
        openjdk-17-jdk \
   && apt-get install -y \
        python3-dev \
   && apt-get install -y \
        mono-devel \
	mono-mcs \
	mono-tools-devel \
   && apt-get install -y \
        nodejs \
	node-gyp \
	npm \
   && apt-get install -y \
        php-dev

# Add locally compiled version of SWIG
ADD https://raw.githubusercontent.com/emdros/emdros/master/SWIG/download_and_make_local_swig.sh /root/
RUN bash /root/download_and_make_local_swig.sh 4.2.1 

# Add script to build a .deb
ADD https://raw.githubusercontent.com/emdros/emdros/master/build-deb.sh ./root/

CMD export PATH=/root/opt/bin:${PATH} && \
    export EMDROS_CONFIGURE_SWITCHES && \
    bash /root/build-deb.sh && \
    install -m 755 -d ${OUTPUT_DIR}/ && \
    install -m 644 /root/build/emdros-build-2/emdros/emdros*.deb ${OUTPUT_DIR}/


