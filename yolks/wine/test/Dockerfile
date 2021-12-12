FROM         ghcr.io/parkervcp/yolks:alpine

LABEL        author="Dave Mol" maintainer="dave@digimol.net"

## install required packages
RUN         apk update && apk add wine && ln -s /usr/bin/wine64 /usr/bin/wine

USER        container	     
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
