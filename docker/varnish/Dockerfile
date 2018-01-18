# https://packagecloud.io/varnishcache/varnish5/install#manual-deb
# https://varnish-cache.org/docs/trunk/reference/varnishd.html

FROM ubuntu:16.04

# install varnish 5 for ubuntu 16.04 xenial
RUN \
  apt-get update && \
  apt-get install -y apt-transport-https curl gnupg && \
  curl -L https://packagecloud.io/varnishcache/varnish5/gpgkey | apt-key add - && \
  echo "deb https://packagecloud.io/varnishcache/varnish5/ubuntu/ xenial main" >> /etc/apt/sources.list.d/varnishcache_varnish5.list && \
  echo "deb-src https://packagecloud.io/varnishcache/varnish5/ubuntu/ xenial main" >> /etc/apt/sources.list.d/varnishcache_varnish5.list && \
  apt-get update && \
  apt-get install -y varnish && \
  rm -rf /var/lib/apt/lists/*

WORKDIR /etc/varnish

COPY default.vcl /etc/varnish/default.vcl

EXPOSE 80

CMD /usr/sbin/varnishd -F -f /etc/varnish/default.vcl -a :80 -a :6081,proxy