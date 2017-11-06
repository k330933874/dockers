FROM repo.coloseo.io/alpine:edge

RUN apk update && apk upgrade \
    && apk add --no-cache nodejs curl fontconfig chromium yarn udev ttf-freefont wqy-zenhei@testing\
    && mkdir -p /usr/share
