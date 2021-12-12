FROM         ghcr.io/damagex/yolks:steamos-test

LABEL        author="Dave Mol" maintainer="dave@digimol.net"

## install required packages
RUN         dpkg --add-architecture i386
RUN         apt install --install-recommends wine wine64 -y

USER        container	     
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
