FROM hub.coloseo.io/amancevice/pandas:0.18.1-python3
MAINTAINER Ging.Wu <ging.wu@coloseo.cn>

# Install
ENV CARAVEL_VERSION=0.10.0 \
    CARAVEL_HOME=/home/caravel 

RUN apk update && \
    apk upgrade && \
    apk add --no-cache \
        curl \
        g++ \
        libffi-dev \
        mariadb-dev \
        postgresql-dev && \
    pip3 install \
        caravel==$CARAVEL_VERSION \
        mysqlclient==1.3.7 \
        psycopg2==2.6.1 \
	redis==2.10.5 && \
   rm -rf /var/cache/apk/*

    
ENV LANG=C.UTF-8 \
    LC_ALL=C.UTF-8 \
    PATH=$PATH:$CARAVEL_HOME/.bin \
    PYTHONPATH=$CARAVEL_HOME:$PYTHONPATH
    
# Run as caravel user
WORKDIR $CARAVEL_HOME
COPY caravel .

# since this can be used as a base image adding the file /docker-entrypoint.sh
# is all you need to do and it will be run *before* Caravel is set up

RUN addgroup caravel && \
    adduser -h $CARAVEL_HOME -G caravel -D caravel && \
    mkdir $CARAVEL_HOME/db && \
    chown -R caravel:caravel $CARAVEL_HOME
USER caravel

# Deploy
VOLUME $CARAVEL_HOME
EXPOSE 8088
HEALTHCHECK CMD ["curl", "-f", "http://localhost:8088/health"]
ENTRYPOINT ["caravel"]
CMD ["runserver"]
