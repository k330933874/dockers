FROM repo.coloseo.io/alpine:3.6

RUN apk update \
    && apk upgrade \
    && apk add --no-cache git build-base nodejs-dev nodejs nodejs-npm python curl \
    && npm install -g yarn cnpm --registry=https://registry.npm.taobao.org

RUN mkdir -p /usr/share \
    && cd /usr/share \
    && curl -L https://github.com/Overbryd/docker-phantomjs-alpine/releases/download/2.11/phantomjs-alpine-x86_64.tar.bz2 | tar xj \
    && ls -al

RUN ln -s /usr/share/phantomjs/phantomjs /usr/bin/phantomjs \
    && phantomjs --version

RUN rm -rf /var/cache/apk/*
