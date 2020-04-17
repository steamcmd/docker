######## BUILDER ########

# Set the base image
# hadolint ignore=DL3007
FROM steamcmd/steamcmd:latest as builder

# Update SteamCMD
RUN steamcmd +quit

######## INSTALL ########

# Set the base image
FROM centos:7

# Install prerequisites
RUN yum -y install glibc.i686 libstdc++.i686 \
 && yum -y clean all

# Set environment variables
ENV LD_LIBRARY_PATH /usr/sbin

# Copy steamcmd and required files from builder
COPY --from=builder /root/.steam/steamcmd/linux32 /usr/sbin
COPY --from=builder /etc/ssl/certs /etc/ssl/certs

# Update SteamCMD and verify latest version
# hadolint ignore=SC2216,DL4006
RUN steamcmd +quit | true

# Set default command
ENTRYPOINT ["steamcmd"]
CMD ["+help", "+quit"]
