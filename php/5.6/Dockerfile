FROM repo.coloseo.io/base:edge

RUN echo '@testing http://nl.alpinelinux.org/alpine/edge/testing' >> /etc/apk/repositories
RUN apk update && apk upgrade \
  && apk add php5 php5-openssl php5-phar php5-json php5-curl php5-dev composer@testing \
  && rm -rf /var/cache/apk/*
