# ----------------------------------
# Generic Wine 6 image
# ----------------------------------
FROM    debian:10

LABEL   author="Dave Mol" maintainer="dave@digimol.net"

## install required packages
RUN     dpkg --add-architecture i386
RUN     apt update -y && apt upgrade -y
RUN     apt install --install-recommends wine wine64 -y

USER    container
WORKDIR	/home/container

COPY    ./entrypoint.sh /entrypoint.sh
CMD	    ["/bin/bash", "/entrypoint.sh"]
