FROM         tianon/steamos

LABEL        author="Dave Mol" maintainer="dave@digimol.net"

LABEL        org.opencontainers.image.source="https://github.com/damagex/pterodactyl/yolks"
LABEL        org.opencontainers.image.licenses=MIT

RUN          useradd -m -d /home/container -s /bin/bash container

RUN          ln -s /home/container/ /nonexistent

ENV          USER=container HOME=/home/container

## Update base packages
RUN          apt update \
             && apt upgrade -y
	     
## Install dependencies
RUN          apt install -y  git wget curl tar zip unzip cabextract -y

## Configure locale
RUN          update-locale lang=en_US.UTF-8 \
             && dpkg-reconfigure --frontend noninteractive locales
			 
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
