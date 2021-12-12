FROM         ghcr.io/damagex/yolks:debian-buster

LABEL        author="Dave Mol" maintainer="dave@digimol.net"

## install required packages
RUN         dpkg --add-architecture i386
RUN         apt install --install-recommends wine wine32 wine64 -y
RUN         apt install bind9-host -y
RUN         apt install busybox -y
RUN         apt install console-setup -y
RUN         apt install console-setup-linux -y
RUN         apt install discover -y
RUN         apt install discover-data -y
RUN         apt install dmidecode -y
RUN         apt install ifupdown -y
RUN         apt install iputils-ping -y
RUN         apt install busybox -y




USER        container	     
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
