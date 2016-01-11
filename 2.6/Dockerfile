# VERSION 2.6.0
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    portefaix/grafana

FROM portefaix/base:3.3
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV GRAFANA_VERSION v2.6.0
ENV GOPATH /go

RUN apk add --update build-base go nodejs git mercurial

RUN mkdir -p /go/src/github.com/grafana && cd /go/src/github.com/grafana && \
    git clone https://github.com/grafana/grafana.git -b ${GRAFANA_VERSION} && \
    cd grafana && \
    go run build.go setup && \
    /go/bin/godep restore && \
    go run build.go build
    # npm install && \
    # npm install -g grunt-cli && \
    # grunt && \
    # npm uninstall -g grunt-cli && \
    # npm cache clear && \
    # mkdir -p /usr/share/grafana/bin/ && \
    # cp -a /go/src/github.com/grafana/grafana/bin/grafana-server /usr/share/grafana/bin/grafana-server && \
    # cp -ra /go/src/github.com/grafana/grafana/public_gen /usr/share/grafana && \
    # mv /usr/share/grafana/public_gen /usr/share/grafana/public && \
    # cp -ra /go/src/github.com/grafana/grafana/conf /usr/share/grafana && \
    # apk del --purge build-base nodejs go git mercurial && \
    # rm -rf /go /tmp/* /var/cache/apk/* /root/.n*

RUN mkdir /etc/grafana
ADD grafana.ini /etc/grafana/grafana.ini

VOLUME ["/var/lib/grafana", "/var/log/grafana", "/etc/grafana"]

EXPOSE 3000

CMD ["/usr/share/grafana/bin/grafana-server", "-config=/etc/grafana/grafana.ini", "-homepath=/usr/share/grafana/"]
