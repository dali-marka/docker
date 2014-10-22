FROM resin/rpi-raspbian:wheezy
MAINTAINER chadrien <chadrien@chadrien.fr>

RUN apt-get update && \
  apt-get install -y irssi && \
  apt-get clean &&  \
  rm -rf /var/lib/apt/lists/*

RUN groupadd irssi && \
  useradd -d /home/irssi -m -g irssi irssi

USER irssi
VOLUME "/home/irssi/.irssi"

ENV TERM screen
CMD ["/usr/bin/irssi"]
