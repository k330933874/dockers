FROM repo.coloseo.io/alpine:3.5

RUN apk update && apk upgrade \
    && apk add --no-cache nodejs \
    && npm uninstall -g npm
