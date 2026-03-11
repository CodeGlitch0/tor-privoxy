FROM alpine:latest

RUN apk --no-cache --update add privoxy

RUN mkdir -p /etc/privoxy && \
    echo "listen-address 0.0.0.0:8118" >> /etc/privoxy/config && \
    echo "forward-socks5 / tor:9050 ." >> /etc/privoxy/config && \
    echo "toggle 1" >> /etc/privoxy/config && \
    echo "enable-remote-toggle 0" >> /etc/privoxy/config && \
    echo "enable-edit-actions 0" >> /etc/privoxy/config && \
    echo "enable-remote-http-toggle 0" >> /etc/privoxy/config && \
    echo "buffer-limit 4096" >> /etc/privoxy/config

EXPOSE 8118

RUN chown -R privoxy /etc/privoxy

USER privoxy

ENTRYPOINT [ "privoxy" ]
CMD [ "--no-daemon", "/etc/privoxy/config" ]
