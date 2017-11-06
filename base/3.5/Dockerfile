FROM alpine:3.5

RUN echo http://mirrors.aliyun.com/alpine/v3.5/main > /etc/apk/repositories && \
    echo http://mirrors.aliyun.com/alpine/v3.5/community >> /etc/apk/repositories && \
    apk update && apk upgrade && \
    apk add --no-cache ca-certificates bash tzdata && \
    rm -rf /var/cache/apk/*
