FROM alpine:edge

RUN echo http://mirrors.aliyun.com/alpine/edge/main > /etc/apk/repositories && \
    echo http://mirrors.aliyun.com/alpine/edge/community >> /etc/apk/repositories && \
    echo @testing http://mirrors.aliyun.com/alpine/edge/testing >> /etc/apk/repositories && \
    apk update && \
    apk add --no-cache ca-certificates bash tzdata && \
    rm -rf /var/cache/apk/*
