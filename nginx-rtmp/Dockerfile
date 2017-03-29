FROM repo.coloseo.io/alpine:3.4
MAINTAINER Ging Wu <ging.wu@coloseo.cn>

# Install prerequisites and update certificates
RUN apk --update --no-cache add \
        nginx-rtmp \
        ffmpeg && \
        rm -rf /var/cache/apk/*

# Forward logs to Docker
RUN ln -sf /dev/stdout /var/log/nginx/access.log && \
    ln -sf /dev/stderr /var/log/nginx/error.log

# Set up config file
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80 1935

CMD ["nginx", "-g", "pid /tmp/nginx.pid; daemon off;"]
