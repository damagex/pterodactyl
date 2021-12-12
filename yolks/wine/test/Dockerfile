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
RUN     apt install --install-recommends -y python3-httplib2 libmagic-mgc libmagic1 libperl5.28 libnetfilter-conntrack3
RUN     apt install --install-recommends -y libuchardet0 libip6tc0 libtext-wrapi18n-perl libnftnl11 libfastjson4 libnfnetlink0 libfuse2 libbind9-161 klibc-utils
RUN     apt install --install-recommends -y python3-urllib3 libisccfg163 libapt-inst2.0 libefiboot1 libtext-iconv-perl liblockfile-bin
RUN     apt install --install-recommends -y libpython3.7-minimal liblwres161 libpipeline1 libpython3.7-stdlib libiptc0 libefivar1 libdns-export1104
RUN     apt install --install-recommends -y libidn11 libdns1104 libtext-charwidth-perl libprocps7 libdiscover2 libip4tc0 liblognorm5 libjson-c3 libisccc161

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
