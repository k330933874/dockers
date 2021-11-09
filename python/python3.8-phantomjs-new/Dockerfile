FROM python:3.8

# PhantomJS
ENV PHANTOMJS_VERSION 1.9.7
RUN wget --no-check-certificate -q -O - https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 | tar xjC /opt
RUN ln -s /opt/phantomjs-$PHANTOMJS_VERSION-linux-x86_64/bin/phantomjs /usr/bin/phantomjs
RUN apt-get -y update && \
    apt-get -y upgrade && \
    apt-get -y -q install xfonts-wqy


# set display port to avoid crash
ENV DISPLAY=:99

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
# ONBUILD COPY Pipfile Pipfile
# ONBUILD COPY Pipfile.lock Pipfile.lock

# -- Install dependencies:
# ONBUILD RUN set -ex && pipenv install --deploy --system
