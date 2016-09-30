FROM hub.coloseo.io/alpine:edge
MAINTAINER Ging Wu <ging.wu@coloseo.cn>

ENV NGINX_RTMP_VERSION 1.1.9
ENV NGINX_VERSION 1.11.4

RUN echo http://dl-cdn.alpinelinux.org/alpine/edge/testing >> /etc/apk/repositories \
        && apk update \
        && apk add --no-cache build-base \
    	curl \
	git \
	pcre-dev \
	openssl-dev \
	logrotate \
	yasm \
	x264 \
	fdk-aac \
	libavc1394 \
	&& rm -rf /var/cache/apk/* /var/tmp/* /tmp/* /usr/local/src/*


RUN addgroup nginx \
    && adduser -G nginx -D nginx 
RUN mkdir -p /var/log/nginx /var/cache/nginx

RUN cd /root && curl -L https://github.com/arut/nginx-rtmp-module/archive/v$NGINX_RTMP_VERSION.tar.gz > nginx-rtmp.tgz \
    && mkdir nginx-rtmp && tar xzf nginx-rtmp.tgz -C nginx-rtmp --strip 1 

RUN mkdir /www && cp /root/nginx-rtmp/stat.xsl /www/info.xsl && chown -R nginx:nginx /www

RUN cd /root \
    && curl -L -O http://nginx.org/download/nginx-$NGINX_VERSION.tar.gz \
    && curl -L -O http://nginx.org/download/nginx-$NGINX_VERSION.tar.gz.asc \
    && tar xzf nginx-$NGINX_VERSION.tar.gz && cd nginx-$NGINX_VERSION \
    && ./configure \
        --prefix=/etc/nginx \
        --sbin-path=/usr/sbin/nginx \
        --conf-path=/etc/nginx/nginx.conf \
        --error-log-path=/var/log/nginx/error.log \
        --http-log-path=/var/log/nginx/access.log \
        --pid-path=/var/run/nginx.pid \
        --lock-path=/var/run/nginx.lock \
        --http-client-body-temp-path=/var/cache/nginx/client_temp \
        --http-proxy-temp-path=/var/cache/nginx/proxy_temp \
        --http-fastcgi-temp-path=/var/cache/nginx/fastcgi_temp \
        --http-uwsgi-temp-path=/var/cache/nginx/uwsgi_temp \
        --http-scgi-temp-path=/var/cache/nginx/scgi_temp \
        --user=nginx \
        --group=nginx \
        --with-http_ssl_module \
        --with-http_realip_module \
        --with-http_addition_module \
        --with-http_sub_module \
        --with-http_dav_module \
        --with-http_flv_module \
        --with-http_mp4_module \
        --with-http_gunzip_module \
        --with-http_gzip_static_module \
        --with-http_random_index_module \
        --with-http_secure_link_module \
        --with-http_stub_status_module \
        --with-http_auth_request_module \
        --with-mail \
        --with-mail_ssl_module \
        --add-module=/root/nginx-rtmp \
        --with-ipv6 \
   && make install

RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

RUN apk add --update bash perl confd ffmpeg

ADD templates/nginx.conf.tmpl /etc/confd/templates/nginx.conf.tmpl
ADD conf.d/nginx.toml /etc/confd/conf.d/nginx.toml


EXPOSE 80
EXPOSE 1935

ADD sbin/entrypoint.sh /usr/sbin/entrypoint.sh
ADD sbin/confd-reload-nginx.sh /usr/sbin/confd-reload-nginx.sh

ENTRYPOINT ["/usr/sbin/entrypoint.sh"]
CMD ["/usr/sbin/nginx", "-c", "/etc/nginx/nginx.conf"]
