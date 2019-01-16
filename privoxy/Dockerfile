FROM alpine:latest

RUN apk --no-cache --update add privoxy && \
    sed -i -e "s/listen-address\s\+127\.0\.0\.1:8118/listen-address\t0\.0\.0\.0:8118/" /etc/privoxy/config && \
    echo "forward-socks5 / tor:9050 ." >> /etc/privoxy/config

EXPOSE 8118

RUN chown -R privoxy /etc/privoxy

USER privoxy

ENTRYPOINT [ "privoxy" ]
CMD [ "--no-daemon", "/etc/privoxy/config" ]
