FROM ubuntu:16.04

ENV NODE_VERSION 14.16.1
ENV NODE_ARCH='x64'

RUN apt-get -y update

RUN apt-get install -y --no-install-recommends --no-install-suggests curl wget tzdata locales psmisc procps iputils-ping logrotate apt-transport-https python3-setuptools

RUN set -x \
  && curl -SLO  --insecure "http://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-$NODE_ARCH.tar.gz" \
  && tar -xzf "node-v$NODE_VERSION-linux-$NODE_ARCH.tar.gz" -C /usr/local --strip-components=1 --no-same-owner \
  && rm "node-v$NODE_VERSION-linux-$NODE_ARCH.tar.gz" \
  && ln -s /usr/local/bin/node /usr/local/bin/nodejs \
  && npm set prefix /usr/local \
  && npm config set unsafe-perm true


RUN addgroup node && adduser --disabled-password --gecos "" --ingroup node node

RUN mkdir /home/node/code

WORKDIR /home/node/code

RUN npm set prefix /usr/local \
  && npm config set unsafe-perm true
