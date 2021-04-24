FROM aymanam/ubuntu-py-node:3.5.2-4.2.6

ENV HOMEBRIDGE_VERSION=1.3.4 \
    CONFIG_UI_VERSION=4.41.0 \
    HOMEBRIDGE_CONFIG_UI=1 \
    HOMEBRIDGE_CONFIG_UI_PORT=8581

ARG AVAHI
ENV ENABLE_AVAHI="${AVAHI:-0}"

RUN apt-get -y update && apt-get install -y git make g++ libnss-mdns avahi-discover libavahi-compat-libdnssd-dev \
    net-tools iproute2 sudo nano \
  && mkdir /homebridge \
  && npm set global-style=true \
  && npm set audit=false \
  && npm set fund=false


RUN npm install -g --unsafe-perm homebridge@${HOMEBRIDGE_VERSION}
RUN npm install -g --unsafe-perm homebridge-config-ui-x@${CONFIG_UI_VERSION}

RUN hb-service install --user homebridge

WORKDIR /homebridge
VOLUME /homebridge


