FROM hub.coloseo.io/node:6

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        xfonts-wqy \
        ttf-wqy-zenhei \
        ca-certificates \
        libsqlite3-dev \
        libfontconfig1-dev \
        libicu-dev \
        libfreetype6 \
        libssl-dev \
        libpng-dev \
        libjpeg-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
