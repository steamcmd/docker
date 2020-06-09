######## BUILDER ########

# Set the base image
FROM steamcmd/steamcmd:ubuntu-18 as builder

# Set environment variables
ENV USER root
ENV HOME /root/installer

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
FROM centos:7

# Set environment variables
ENV USER root
ENV HOME /root

# Install prerequisites
RUN yum -y install glibc.i686 libstdc++.i686 \
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

# Set default command
ENTRYPOINT ["steamcmd"]
CMD ["+help", "+quit"]
