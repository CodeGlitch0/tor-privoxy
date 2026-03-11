FROM alpine:latest

RUN apk add --update --no-cache tor

COPY torrc.default /etc/tor/torrc.default

# Create data directory for Tor
RUN mkdir -p /var/lib/tor && \
    chown -R tor:tor /var/lib/tor && \
    chown -R tor:tor /etc/tor

VOLUME ["/var/lib/tor"]

USER tor
EXPOSE 9050

ENTRYPOINT [ "tor" ]
CMD [ "-f", "/etc/tor/torrc.default" ]

