FROM resin/rpi-raspbian:wheezy
MAINTAINER chadrien <chadrien@chadrien.fr>

RUN apt-get update \
  && apt-get install -y \
    curl \
    ca-certificates \
    python \
    build-essential \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# verify gpg and sha256: http://nodejs.org/dist/v0.10.32/SHASUMS256.txt.asc
# gpg: aka "Timothy J Fontaine (Work) <tj.fontaine@joyent.com>"
RUN gpg --keyserver pgp.mit.edu --recv-keys 7937DFD2AB06298B2293C3187D33FF9D0246406D

ENV NODE_VERSION 0.10.32
ENV NPM_VERSION 2.1.4

RUN curl -SLO "http://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION.tar.gz" \
  && curl -SLO "http://nodejs.org/dist/v$NODE_VERSION/SHASUMS256.txt.asc" \
  && gpg --verify SHASUMS256.txt.asc \
  && grep " node-v$NODE_VERSION.tar.gz\$" SHASUMS256.txt.asc | sha256sum -c - \
  && mkdir -p /tmp/node \
  && tar -xzf "node-v$NODE_VERSION.tar.gz" -C /tmp/node --strip-components=1 \
  && cd /tmp/node \
  && ./configure \
  && make \
  && make install \
  && cd \
  && rm -rf /tmp/node

CMD ["node"]
