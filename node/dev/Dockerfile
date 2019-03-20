FROM repo.coloseo.io/alpine:3.9

RUN apk update && \
    apk add --no-cache git build-base nodejs-dev nodejs python npm yarn && \
    rm -rf /var/cache/apk/*
