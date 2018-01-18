# https://github.com/varnish/hitch/blob/master/docs/installation.md
# https://github.com/varnish/hitch/blob/master/docs/configuration.md

FROM ubuntu:16.04

ARG ver=1.4.6
ARG pem=test.example.com.pem
ENV BACKEND=varnish
ENV BACKEND_PORT=6081
ENV FRONTEND=*
ENV FRONTEND_PORT=443

WORKDIR /tmp
RUN \
  apt-get update && \
  apt-get install -y apt-transport-https curl gnupg && \
  apt-get install -y libev-dev libssl-dev automake python-docutils flex bison pkg-config && \
  rm -rf /var/lib/apt/lists/* && \
  curl -L https://hitch-tls.org/source/hitch-${ver}.tar.gz | tar xz && \
  cd /tmp/hitch-${ver} && \
  ./configure && \
  make && \
  make install && \
  rm -rf *

COPY ${pem} /hitch.pem

RUN useradd -s /sbin/nologin hitch

EXPOSE 443

CMD /usr/local/sbin/hitch -u hitch --backend=[$BACKEND]:$BACKEND_PORT --frontend=[$FRONTEND]:$FRONTEND_PORT /hitch.pem