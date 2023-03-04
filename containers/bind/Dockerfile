FROM docker.io/alpine:3.17

ARG BIND_VERSION=9.18.11-r0

LABEL \
    org.opencontainers.image.title="homelab-bind" \
    org.opencontainers.image.description="Alpine Bind Container" \
    org.opencontainers.image.source="https://github.com/Remkio/homelab/containers/bind" \
    org.opencontainers.image.version="${BIND_VERSION}"

RUN apk --no-cache --update add \
    bind=${BIND_VERSION} \
    bind-tools=${BIND_VERSION} \
    bind-dnssec-tools=${BIND_VERSION}

VOLUME /var/named /etc/bind

EXPOSE 53/tcp 53/udp

CMD ["named", "-c", "/etc/bind/named.conf", "-g", "-u", "named"]


