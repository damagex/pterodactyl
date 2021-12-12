# ----------------------------------
# Generic Wine 6 image
# ----------------------------------
FROM    ghcr.io/parkervcp/yolks:ubuntu

LABEL   author="Dave Mol" maintainer="dave@digimol.net"

## install required packages
RUN     dpkg --add-architecture i386

RUN     apt update
RUN     apt install wine64 -y

USER    container
WORKDIR	/home/container

COPY    ./entrypoint.sh /entrypoint.sh
CMD	    ["/bin/bash", "/entrypoint.sh"]
