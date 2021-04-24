FROM alpine:3.13.5

ENV NODE_VERSION 14.16.1

RUN apk add --update nodejs npm

RUN set -x && apk add --no-cache libgcc libstdc++ curl curl-dev coreutils tzdata shadow libstdc++ logrotate py3-pip \
  && apk add --update nodejs nodejs-npm \
  && pip3 install tzupdate \
  && apk del --purge \
  && rm -rf /tmp/* \
  && sed -i "s#/var/log/messages {}.*# #g" /etc/logrotate.conf

RUN addgroup -S node && adduser -S node -G node

USER node

RUN mkdir /home/node/code

WORKDIR /home/node/code

RUN npm set prefix /usr/local \
  && npm config set unsafe-perm true
