FROM jenkinsci/blueocean:1.21.0
MAINTAINER awataki <awataki1206@gmail.com>
USER root

# install build deps
RUN apk add make

# download thrift file
WORKDIR /usr/bin/
RUN curl -L https://archive.swkoubou.com/RMS/linux/alpine/3.9.4/bin/thrift -O
RUN chmod a+x /usr/bin/thrift

# link to ld to musl golang is using /lib64/ld-linux-x86-64.so.2  for dynamic link.
RUN mkdir /lib64 && ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2
WORKDIR /tmp
RUN curl -L https://dl.google.com/go/go1.13.5.linux-amd64.tar.gz -O
RUN tar xf ./go1.13.5.linux-amd64.tar.gz
RUN cp ./go/bin/go /usr/bin
RUN rm -r ./go*
WORKDIR /var/jenkins_home

USER jenkins