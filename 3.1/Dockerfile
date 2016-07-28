# VERSION 3.1.0
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    portefaix/grafana

FROM portefaix/base:3.4
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV GRAFANA_VERSION v3.1.0

ENV GOPATH /go
ENV GLIBC_VERSION=2.23-r1
ENV GLIBC_FILE=glibc-${GLIBC_VERSION}.apk

WORKDIR /tmp
RUN apk add --update curl openssl \
    && curl -Ls https://github.com/andyshinn/alpine-pkg-glibc/releases/download/${GLIBC_VERSION}/${GLIBC_FILE} > /tmp/${GLIBC_FILE} \
    && apk add --allow-untrusted /tmp/${GLIBC_FILE} \
    && curl -Ls  http://grafanarel.s3.amazonaws.com/builds/grafana-3.1.0-1468321182.linux-x64.tar.gz > /tmp/grafana.tar.gz \
    && tar xvfz /tmp/grafana.tar.gz \
    && mv /tmp/grafana-3.1.0-1468321182 /usr/share/grafana \
    && rm /tmp/grafana.tar.gz \
    && apk del curl \
    && rm -rf /tmp/* /var/cache/apk/*

RUN mkdir /etc/grafana
ADD grafana.ini /etc/grafana/grafana.ini

VOLUME ["/var/lib/grafana", "/var/log/grafana", "/etc/grafana"]

EXPOSE 3000

CMD ["/usr/share/grafana/bin/grafana-server", "-config=/etc/grafana/grafana.ini", "-homepath=/usr/share/grafana/"]
