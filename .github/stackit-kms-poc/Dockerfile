FROM alpine:3.22

RUN apk add --no-cache ca-certificates dumb-init libcap su-exec tzdata \
    && addgroup -S vault \
    && adduser -S -G vault vault \
    && mkdir -p /vault/config /vault/data /vault/logs \
    && chown -R vault:vault /vault

COPY vault /bin/vault
COPY .release/docker/docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh

RUN chmod 0755 /bin/vault /usr/local/bin/docker-entrypoint.sh

EXPOSE 8200 8201
ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["server"]
