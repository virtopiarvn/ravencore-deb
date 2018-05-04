FROM debian:xenial

ENV DEBIAN_FRONTEND noninteractive
ENV HOME /root
ENV TERM linux

RUN apt-get update && \
    apt-get upgrade -qy && \
    apt-get install -qy apt-transport-https curl git && \
    echo 'deb http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu xenial main' | tee /etc/apt/sources.list.d/nodesource.list && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8842CE5E
    echo 'deb https://deb.nodesource.com/node_10.x xenial main' | tee -a /etc/apt/sources.list.d/nodesource.list && \
    curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
RUN apt-get update && \
    apt-get -qy install nodejs python3 make build-essential devscripts dh-systemd
RUN npm install npm@latest -g
ADD ravencore-rvn/ /root/ravencore-rvn
RUN ( cd /root/ravencore-rvn && debuild -uc -us )
