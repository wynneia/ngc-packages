FROM archlinux:base as base
MAINTAINER Martchus <martchus@gmx.net>

RUN mkdir -p /startdir /build && \
    groupadd -g 1000 builduser && \
    useradd -m -d /build -u 1000 -g 1000 -s /bin/bash builduser && \
    chown -R builduser:builduser /startdir /build && \
    echo 'builduser ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers && \
    pacman-key --init && \
    pacman-key --recv-keys B9E36A7275FC61B464B67907E06FE8F53CDC6A4C && \
    pacman-key --finger    B9E36A7275FC61B464B67907E06FE8F53CDC6A4C && \
    pacman-key --lsign-key B9E36A7275FC61B464B67907E06FE8F53CDC6A4C && \
    pacman -Sy --verbose --noconfirm --needed archlinux-keyring && \
    pacman -Syu --verbose --noconfirm --needed base-devel pacman-contrib ccache && \
    pacman -Scc --noconfirm && \
    paccache -r -k0 && \
    rm -rf /usr/share/man/* /tmp/* /var/tmp/*
