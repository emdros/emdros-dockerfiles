FROM alpine:latest

LABEL MAINTAINER KimiChen

RUN apk add --upgrade bash alpine-sdk
RUN apk add git zip
# Add C complier
RUN apk add gcc musl-dev 
RUN apk add pcre2-dev
RUN apk add sqlite
RUN apk add nodejs npm

# Add locally compiled version of SWIG

ADD https://raw.githubusercontent.com/emdros/emdros/master/SWIG/download_and_make_local_swig.sh /root/
RUN bash /root/download_and_make_local_swig.sh 4.1.1

# Add script to build a .deb

ADD https://raw.githubusercontent.com/emdros/emdros/master/build-deb.sh ./root/

CMD export PATH=/root/opt/bin:${PATH} && bash /root/build-deb.sh

# EXPOSE 3000 <-- emdros process port
# ENTRYPOINT ["emdros"] <-- not sure how to start emdros
