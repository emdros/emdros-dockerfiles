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
        git \
	wget \
   && apt-get install -y \
        nodejs \
	npm 

# Install Emdros .deb package.
#
ADD emdros.deb /root/emdros_deb/
RUN dpkg -i /root/emdros_deb/emdros.deb

#
# Set up the test script
#
RUN install -v 777 -d /test
ADD test/test_Emdros_Node.js /test/


#
# Set up Node project
#
# [FIXME: Do it]


# [FIXME: Do something more useful]
CMD cd /test && \
    node test_Emdros_Node.js ; \
    /bin/bash



