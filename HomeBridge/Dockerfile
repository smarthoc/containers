FROM aymanam/base-pip-npm:3.8.8-6.14.12

ENV HOMEBRIDGE_VERSION=1.3.4 \
    CONFIG_UI_VERSION=4.41.0 \
    HOMEBRIDGE_CONFIG_UI=1 \
    HOMEBRIDGE_CONFIG_UI_PORT=8581

ARG AVAHI
ENV ENABLE_AVAHI="${AVAHI:-0}"

USER root

RUN apk add --no-cache make gcc g++ avahi-compat-libdns_sd avahi-dev dbus \
    iputils sudo nano net-tools \
  && mkdir /homebridge \
  && npm set global-style=true \
  && npm set audit=false \
  && npm set fund=false

RUN npm install -g --unsafe-perm homebridge@${HOMEBRIDGE_VERSION}
RUN npm install -g --unsafe-perm homebridge-config-ui-x@${CONFIG_UI_VERSION}

RUN hb-service install --user homebridge

WORKDIR /homebridge
VOLUME /homebridge


