[![Build Status](https://img.shields.io/github/workflow/status/steamcmd/docker/Build%20and%20Push%20Container.svg?logo=github)](https://github.com/steamcmd/docker/actions)
[![Docker Pulls](https://img.shields.io/docker/pulls/steamcmd/steamcmd.svg)](https://hub.docker.com/repository/docker/steamcmd/steamcmd)
[![Image Size](https://img.shields.io/docker/image-size/steamcmd/steamcmd.svg)](https://hub.docker.com/repository/docker/steamcmd/steamcmd)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE.md)

# SteamCMD Docker Image

SteamCMD with different Docker base images for downloading and running Steam games and game server software. Currently the images are build every day and only tagged on type of base image.

## Tags

- [`ubuntu-18`, `ubuntu`, `latest`](dockerfiles/ubuntu-18)
- [`ubuntu-16`](dockerfiles/ubuntu-16)
- [`alpine`](dockerfiles/alpine)
- [`busybox`, `lite`](dockerfiles/busybox)

## Usage

#### Pull latest image
```
docker pull steamcmd/steamcmd:latest
```
#### Test interactively
```
docker run -it steamcmd/steamcmd:latest /bin/sh
```
#### Download CSGO
```
docker run -it steamcmd/steamcmd:latest steamcmd +login anonymous +app_update 740 +quit
```
#### Download CSGO to local mounted directory "data"
```
docker run -it -v "$(pwd)":/data steamcmd/steamcmd:latest steamcmd +login anonymous +force_install_dir /data +app_update 740 +quit
```

## License

[MIT license](LICENSE.md)
