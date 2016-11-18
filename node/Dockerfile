FROM repo.coloseo.io/base:edge

RUN echo http://mirrors.aliyun.com/alpine/edge/main > /etc/apk/repositories && \
    echo http://mirrors.aliyun.com/alpine/edge/community >> /etc/apk/repositories && \
    echo @testing http://mirrors.aliyun.com/alpine/edge/testing >> /etc/apk/repositories && \
    apk update && apk upgrade \
    && apk add nodejs \
    && npm uninstall -g npm \
    && rm -rf /var/cache/apk/*
