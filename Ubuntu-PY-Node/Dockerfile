FROM ubuntu:16.04

ENV NODE_VERSION 14.16.1

RUN apt-get -y update

RUN apt-get install -y --no-install-recommends --no-install-suggests nodejs npm curl wget tzdata locales psmisc procps iputils-ping logrotate apt-transport-https python3-setuptools

RUN addgroup node && adduser --disabled-password --gecos "" --ingroup node node

RUN mkdir /home/node/code

WORKDIR /home/node/code

RUN npm set prefix /usr/local \
  && npm config set unsafe-perm true
