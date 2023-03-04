FROM docker.io/alpine:3.17

ARG DHCP_VERSION=4.4.3_p1-r1

LABEL \
    org.opencontainers.image.title="homelab-dhcp-server" \
    org.opencontainers.image.description="Alpine DHCP Server Container" \
    org.opencontainers.image.source="https://github.com/Remkio/homelab/containers/dhcp-server" \
    org.opencontainers.image.version=${DHCP_VERSION}

RUN apk --no-cache --update add \
    dhcp-server-vanilla=${DHCP_VERSION} \
    && touch /var/lib/dhcp/dhcpd.leases

VOLUME /var/lib/dhcp /etc/dhcp

EXPOSE 67/udp

CMD ["/usr/sbin/dhcpd", "-4", "-f", "-d", "--no-pid", "-cf", "/etc/dhcp/dhcpd.conf"]
