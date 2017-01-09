FROM alpine:edge

RUN echo http://mirrors.aliyun.com/alpine/edge/main > /etc/apk/repositories && \
    echo http://mirrors.aliyun.com/alpine/edge/community >> /etc/apk/repositories && \
    echo @testing http://mirrors.aliyun.com/alpine/edge/testing >> /etc/apk/repositories && \
    apk update && apk upgrade && \
    apk add --no-cache ca-certificates bash && \
    rm -rf /var/cache/apk/*
