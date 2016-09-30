FROM alpine:3.4
MAINTAINER Ging.Wu <ging.wu@coloseo.cn>

ENV NGINX_VERSION 1.11.1

RUN apk add --no-cache --virtual .build-deps \
    	build-base \
	curl \
	git \
	pcre-dev \
	openssl-dev \
	&& mkdir /usr/local/src \
	&& cd /usr/local/src \
	&& git clone git://github.com/arut/nginx-rtmp-module.git \
	&& curl -fSL http://nginx.org/download/nginx-$NGINX_VERSION.tar.gz -o nginx.tar.gz \
	&& tar -zxC /usr/local/src -f nginx.tar.gz \
	&& cd /usr/local/src/nginx-$NGINX_VERSION \
	&& ./configure --prefix=/usr/local/nginx --add-module=/usr/local/src/nginx-rtmp-module \
	&& make \
	&& make install \
	&& cp /usr/local/src/nginx-rtmp-module/stat.xsl /usr/local/nginx/html/ \
	&& apk del build-base curl git \
	&& rm -rf /var/cache/apk/* /var/tmp/* /tmp/* /usr/local/src/*

# forward request and error logs to docker log collector
RUN  ln -sf /dev/stdout /usr/local/nginx/logs/access.log \
     	&& ln -sf /dev/stderr /usr/local/nginx/logs/error.log 

COPY ./conf/nginx.conf /usr/local/nginx/conf/nginx.conf

EXPOSE 80 1935

CMD [ "/usr/local/nginx/sbin/nginx" ]
