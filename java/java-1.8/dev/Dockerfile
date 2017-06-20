FROM repo.coloseo.io/alpine:3.6

RUN  apk update \
  && apk upgrade \
  && apk add openjdk8 \
  && apk add maven \
  && rm -rf /var/cache/apk/*

# puts javac in the PATH
ENV PATH=/usr/lib/jvm/java-1.8-openjdk/bin:$PATH
