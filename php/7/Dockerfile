FROM repo.coloseo.io/base:edge

RUN apk --update add wget \
    		     git \
    		     curl \
		     php7 \
		     php7-dev \
		     php7-curl \
		     php7-openssl \
		     php7-iconv \
		     php7-json \
		     php7-mbstring \
		     php7-phar \
		     php7-dom && rm /var/cache/apk/*

RUN ln -s /usr/bin/php7 /usr/bin/php

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer 
