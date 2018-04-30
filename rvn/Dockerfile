FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive
ENV HOME /root
ENV TERM linux

RUN apt-get update && \
    apt-get upgrade -qy && \
    apt-get install -qy apt-transport-https curl git && \
    echo 'deb https://deb.nodesource.com/node_4.x jessie main' | tee /etc/apt/sources.list.d/nodesource.list && \
    curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
RUN apt-get update && \
    apt-get -qy install nodejs python make build-essential devscripts dh-systemd
RUN npm install -g yarn
ADD ravencore-rvn/ /root/ravencore-rvn
RUN ( cd /root/ravencore-rvn && debuild -uc -us )
