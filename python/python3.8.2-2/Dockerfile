FROM python:3.8.2-slim-buster

# set work directory
WORKDIR /usr/src/app

COPY pip.conf /root/.pip/
# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV PYTHONPATH /usr/src/app

# install dependencies
RUN pip install --upgrade pip setuptools wheel pipenv && \
  rm -rf /root/.cache/pip

# -- Adding Pipfiles
ONBUILD COPY Pipfile Pipfile
ONBUILD COPY Pipfile.lock Pipfile.lock

# -- Install dependencies:
ONBUILD RUN set -ex && pipenv install --deploy --system
