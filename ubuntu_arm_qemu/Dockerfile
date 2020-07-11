FROM ubuntu:18.04

# make sure manpages get downloaded
RUN sed -i 's:^path-exclude=/usr/share/man:#path-exclude=/usr/share/man:' \
        /etc/dpkg/dpkg.cfg.d/excludes

RUN apt-get update \
 && apt-get -y install man manpages-posix \
 && apt-get -y install build-essential \
 && apt-get -y install git \
 && apt-get -y install gcc-arm-linux-gnueabihf \
 && apt-get -y install gcc-arm-linux-gnueabi \
 && apt-get -y install binutils-arm-linux-gnueabi \
 && apt-get -y install gdb-multiarch \
 && apt-get -y install qemu \
 && apt-get -y autoremove --purge