FROM repo.coloseo.io/base:edge

RUN echo http://mirrors.aliyun.com/alpine/edge/main > /etc/apk/repositories && \
    echo http://mirrors.aliyun.com/alpine/edge/community >> /etc/apk/repositories && \
    echo @testing http://mirrors.aliyun.com/alpine/edge/testing >> /etc/apk/repositories && \
    apk update && \
    apk add --no-cache git build-base nodejs-dev nodejs python && \
    npm install --registry=https://registry.npm.taobao.org -g npm yarn && \
    rm -rf /var/cache/apk/*
