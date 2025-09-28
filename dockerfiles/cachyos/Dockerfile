FROM steamcmd/steamcmd:ubuntu-22 AS builder

USER root
ENV USER=root
ENV HOME=/root/installer

RUN apt-get update && apt-get install -y --no-install-recommends curl tar

WORKDIR $HOME

RUN curl http://media.steampowered.com/installer/steamcmd_linux.tar.gz --output steamcmd.tar.gz --silent
RUN tar -xvzf steamcmd.tar.gz && rm steamcmd.tar.gz

FROM cachyos/cachyos:latest

USER root
ENV USER=root
ENV HOME=/root

RUN sed -i 's/^#\[multilib\]/[multilib]/' /etc/pacman.conf && sed -i 's|^#Include = /etc/pacman.d/mirrorlist|Include = /etc/pacman.d/mirrorlist|' /etc/pacman.conf

RUN pacman --noconfirm --needed -Syu \
    && pacman --noconfirm --needed -S bash dbus gcc-libs sdl2 lib32-glibc lib32-dbus lib32-gcc-libs lib32-sdl2 \
    && pacman --noconfirm -Scc \
    && rm -rf /tmp/* && rm -rf /var/tmp/*

COPY --from=builder /root/installer/steamcmd.sh /usr/lib/games/steam/
COPY --from=builder /root/installer/linux32/steamcmd /usr/lib/games/steam/
COPY --from=builder /usr/games/steamcmd /usr/bin/steamcmd

RUN steamcmd +quit

RUN mkdir -p $HOME/.steam \
    && ln -s $HOME/.local/share/Steam/steamcmd/linux32 $HOME/.steam/sdk32 \
    && ln -s $HOME/.local/share/Steam/steamcmd/linux64 $HOME/.steam/sdk64 \
    && ln -s $HOME/.steam/sdk32/steamclient.so $HOME/.steam/sdk32/steamservice.so \
    && ln -s $HOME/.steam/sdk64/steamclient.so $HOME/.steam/sdk64/steamservice.so \
    && chown -R $USER:$USER $HOME

ENTRYPOINT ["steamcmd"]
CMD ["+help", "+quit"]