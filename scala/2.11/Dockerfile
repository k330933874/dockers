FROM repo.coloseo.io/java:1.8

RUN apk update && apk upgrade
RUN apk add bash

ADD scala-2.11.8 /usr/local/share/scala
ADD sbt /usr/local/share/sbt
ENV SCALA-HOME=/usr/local/share/scala
ENV SBT_HOME=/usr/local/share/sbt
ENV PATH=/usr/local/share/scala/bin:/usr/local/share/sbt/bin:$PATH

# Clean APK cache
RUN rm -rf /var/cache/apk/*
