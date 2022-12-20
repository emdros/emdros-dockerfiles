FROM ubuntu:20.04 AS ubuntu-deb-builder-env

MAINTAINER ulrikp

RUN apt-get update && apt-get upgrade -y 

RUN apt-get install -y \
        emacs-nox \
        git \
	wget \
        g++ make binutils build-essential \
        swig re2c \
        fakeroot debhelper \
        pkg-config \
        python3 python3-dev \
        virtualenv python3-virtualenv \
        mono-devel mono-mcs mono-tools-devel \
        automake autoconf libtool autotools-dev \
        swig zip \
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
	npm \
   && apt-get install -y \
        php-dev 

# Add SWIG
ADD https://raw.githubusercontent.com/emdros/emdros/master/SWIG/download_and_make_local_swig.sh /root/
RUN bash /root/download_and_make_local_swig.sh 4.1.1

ADD https://raw.githubusercontent.com/emdros/emdros/master/build-deb.sh ./root/

CMD bash /root/build-deb.sh


