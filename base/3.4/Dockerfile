FROM alpine:3.4

RUN echo http://mirrors.aliyun.com/alpine/v3.4/main > /etc/apk/repositories && \
    echo http://mirrors.aliyun.com/alpine/v3.4/community >> /etc/apk/repositories && \
    apk update && apk upgrade && \
    apk add --no-cache ca-certificates bash && \
    rm -rf /var/cache/apk/*
