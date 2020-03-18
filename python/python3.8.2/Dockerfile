FROM python:3.8.2-alpine3.11

# set work directory
WORKDIR /usr/src/app

# copy requirements file
COPY pip.conf /root/.pip/

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install dependencies
RUN echo http://mirrors.aliyun.com/alpine/v3.11/main > /etc/apk/repositories && \
  echo http://mirrors.aliyun.com/alpine/v3.11/community >> /etc/apk/repositories && \
  set -eux && \
  apk update && apk upgrade && \
  apk add --no-cache --virtual .build-deps build-base libressl-dev libffi-dev gcc musl-dev python3-dev && \
  pip install --upgrade pip setuptools wheel pipenv && \
  rm -rf /root/.cache/pip

# -- Adding Pipfiles
ONBUILD COPY Pipfile Pipfile
ONBUILD COPY Pipfile.lock Pipfile.lock

# -- Install dependencies:
ONBUILD RUN set -ex && pipenv install --deploy --system
