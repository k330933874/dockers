FROM repo.coloseo.io/alpine:3.6

RUN apk update \
  && apk upgrade \
  && apk add openjdk8-jre-base \
  && rm -rf /var/cache/apk/*
