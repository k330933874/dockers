FROM repo.coloseo.io/alpine:3.5

RUN apk update && apk upgrade \
    && apk add --no-cache nodejs curl gnupg \
    && npm uninstall -g npm

RUN curl -o- -L https://yarnpkg.com/install.sh | bash \
    && apk del curl gnupg \
    && rm -rf /var/cache/apk/*

ENV PATH /root/.yarn/bin:$PATH
