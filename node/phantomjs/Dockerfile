FROM repo.coloseo.io/alpine:3.6

RUN apk update && apk upgrade \
    && apk add --no-cache nodejs curl fontconfig \
    && mkdir -p /usr/share

RUN cd /usr/share \
    && curl -L https://github.com/Overbryd/docker-phantomjs-alpine/releases/download/2.11/phantomjs-alpine-x86_64.tar.bz2 | tar xj \
    && ls -al

RUN ln -s /usr/share/phantomjs/phantomjs /usr/bin/phantomjs \
    && phantomjs --version
