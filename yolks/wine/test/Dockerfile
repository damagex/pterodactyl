# ----------------------------------
# Generic Wine 6 image
# ----------------------------------
FROM    ghcr.io/parkervcp/yolks:debian

LABEL   author="Torsten Widmann" maintainer="info@goover.de"

## install required packages
RUN     dpkg --add-architecture i386
RUN     apt update
RUN     apt install -y --no-install-recommends gnupg2 software-properties-common libntlm0 winbind xvfb xauth python3 libncurses5:i386 libncurses6:i386 libgdiplus

# Install winehq-stable and with recommends
RUN     wget -nc https://dl.winehq.org/wine-builds/winehq.key
RUN     apt-key add winehq.key
RUN     apt-add-repository 'deb http://dl.winehq.org/wine-builds/debian/ bullseye main'
#RUN     apt update
#RUN     wget -O- -q https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Debian_11/Release.key | apt-key add -
#RUN     echo "deb http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Debian_11 ./" | tee /etc/apt/sources.list.d/wine-obs.list
RUN     apt update
RUN     apt install --install-recommends winehq-devel cabextract -y
RUN    apt install -y python3-httplib2
RUN    apt install -y libmagic-mgc
RUN    apt install -y libmagic1
RUN    apt install -y libnetfilter-conntrack3
RUN    apt install -y libuchardet0
RUN    apt install -y libtext-wrapi18n-perl
RUN    apt install -y libnftnl11
RUN    apt install -y libfastjson4
RUN    apt install -y libnfnetlink0
RUN    apt install -y libfuse2
RUN    apt install -y libbind9-161
RUN    apt install -y klibc-utils
RUN    apt install -y python3-urllib3
RUN    apt install -y libisccfg163
RUN    apt install -y libefiboot1
RUN    apt install -y libtext-iconv-perl
RUN    apt install -y liblockfile-bin
RUN    apt install -y liblwres161
RUN    apt install -y libpipeline1
RUN    apt install -y libiptc0
RUN    apt install -y libefivar1
RUN    apt install -y libidn11
RUN    apt install -y libtext-charwidth-perl
RUN    apt install -y libdiscover2
RUN    apt install -y liblognorm5
RUN    apt install -y libjson-c3
RUN    apt install -y libestr0
RUN    apt install -y libmpdec2
RUN    apt install -y libgeoip1
RUN    apt install -y libklibc
RUN    apt install -y libpolkit-backend-1-0
RUN    apt install -y liblocale-gettext-perl

# Set up Winetricks
RUN	    wget -q -O /usr/sbin/winetricks https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks
RUN     chmod +x /usr/sbin/winetricks

ENV     HOME=/home/container
ENV     WINEPREFIX=/home/container/.wine
ENV     WINEDLLOVERRIDES="mscoree,mshtml="
ENV     DISPLAY=:0
ENV     DISPLAY_WIDTH=1024
ENV     DISPLAY_HEIGHT=768
ENV     DISPLAY_DEPTH=16
ENV     AUTO_UPDATE=1
ENV     XVFB=1

USER    container
WORKDIR	/home/container

COPY    ./entrypoint.sh /entrypoint.sh
CMD	    ["/bin/bash", "/entrypoint.sh"]
