FROM jenkinsci/blueocean:1.21.0
LABEL  maintainer "awataki <awataki1206@gmail.com>"
USER root

ENV HTTP_PROXY="http://ccproxy.kanagawa-it.ac.jp:10080"
ENV HTTPS_PROXY="http://ccproxy.kanagawa-it.ac.jp:10080"

# install build deps
RUN apk add make git mariadb-client

# set proxy to git
RUN git config --global http.proxy $HTTP_PROXY
RUN git config --global https.proxy $HTTPS_PROXY


# download thrift file
WORKDIR /usr/bin/
RUN curl -L https://archive.swkoubou.com/RMS/linux/alpine/3.9.4/bin/thrift -O
RUN chmod a+x /usr/bin/thrift

# link ld to musl as golang is using /lib64/ld-linux-x86-64.so.2 for dynamic link.
RUN mkdir /lib64 && ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2
WORKDIR /usr/local/
RUN curl -L https://dl.google.com/go/go1.13.5.linux-amd64.tar.gz -O
RUN tar xf ./go1.13.5.linux-amd64.tar.gz
RUN rm ./go1.13.5.linux-amd64.tar.gz
RUN cp ./go/bin/go /usr/bin

WORKDIR $JENKINS_HOME

USER jenkins
