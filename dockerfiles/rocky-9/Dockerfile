######## BUILDER ########

# Set the base image
FROM steamcmd/steamcmd:ubuntu-22 as builder

# Set environment variables
ENV USER=root
ENV HOME=/root/installer

# Set working directory
WORKDIR $HOME

# Install prerequisites
RUN apt-get update \
    && apt-get install -y --no-install-recommends curl tar

# Donload and unpack installer
RUN curl http://media.steampowered.com/installer/steamcmd_linux.tar.gz \
    --output steamcmd.tar.gz --silent
RUN tar -xvzf steamcmd.tar.gz && rm steamcmd.tar.gz

######## INSTALL ########

# Set the base image
FROM rockylinux/rockylinux:9

# Set environment variables
ENV USER=root
ENV HOME=/root

# Install prerequisites
RUN yum -y install glibc.i686 libgcc.i686 glibc-langpack-en \
    && yum -y clean all

# Copy steamcmd files from builder
COPY --from=builder /root/installer/steamcmd.sh /usr/lib/games/steam/
COPY --from=builder /root/installer/linux32/steamcmd /usr/lib/games/steam/
COPY --from=builder /usr/games/steamcmd /usr/bin/steamcmd

# Copy required files from builder
COPY --from=builder /etc/ssl/certs /etc/ssl/certs
COPY --from=builder /root/installer/linux32/libstdc++.so.6 /lib/

# Update SteamCMD and verify latest version
RUN steamcmd +quit

# Fix missing directories and libraries
RUN mkdir -p $HOME/.steam \
    && ln -s $HOME/.local/share/Steam/steamcmd/linux32 $HOME/.steam/sdk32 \
    && ln -s $HOME/.local/share/Steam/steamcmd/linux64 $HOME/.steam/sdk64 \
    && ln -s $HOME/.steam/sdk32/steamclient.so $HOME/.steam/sdk32/steamservice.so \
    && ln -s $HOME/.steam/sdk64/steamclient.so $HOME/.steam/sdk64/steamservice.so

# Set default command
ENTRYPOINT ["steamcmd"]
CMD ["+help", "+quit"]
