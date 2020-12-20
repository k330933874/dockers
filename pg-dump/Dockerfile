FROM postgres:11-alpine

RUN \
    apk add --no-cache coreutils && \
    apk add --no-cache ca-certificates && \
    apk add --no-cache --virtual .build-deps curl && \
    curl https://dl.minio.io/client/mc/release/linux-amd64/mc > /usr/bin/mc && \
    chmod +x /usr/bin/mc && apk del .build-deps

