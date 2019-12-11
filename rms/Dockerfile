FROM jenkins/jenkins:lts-alpine
MAINTAINER awataki <awataki1206@gmail.com>
USER root

# install build deps
RUN apk add make mariadb mariadb-client

# setup db
#RUN /etc/init.d/mariadb setup
#RUN service mariadb start

# download thrift file
RUN cd /usr/bin/ && wget  https://archive.swkoubou.com/RMS/bin/thrift
RUN chmod a+x /usr/bin/thrift

# link to ld to musl golang is using /lib64/ld-linux-x86-64.so.2  for dynamic link.
RUN mkdir /lib64 && ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2
WORKDIR /tmp
RUN wget https://dl.google.com/go/go1.13.5.linux-amd64.tar.gz
RUN tar xf ./go1.13.5.linux-amd64.tar.gz
RUN cp ./go/bin/go /usr/bin
RUN rm -r ./go*
WORKDIR /var/jenkins_home

#USER jenkins
