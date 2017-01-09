FROM repo.coloseo.io/alpine:3.5

RUN apk update && \
    apk add --no-cache git build-base nodejs-dev nodejs python && \
    npm install -g cnpm yarn --registry=https://registry.npm.taobao.org && \
    rm -rf /var/cache/apk/*
