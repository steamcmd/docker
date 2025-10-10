[![Build Status](https://github.com/steamcmd/docker/actions/workflows/build.yml/badge.svg)](https://github.com/steamcmd/docker/actions)
[![CodeFactor](https://www.codefactor.io/repository/github/steamcmd/docker/badge)](https://www.codefactor.io/repository/github/steamcmd/docker)
[![Discord Online](https://img.shields.io/discord/928592378711912488.svg)](https://discord.steamcmd.net)
[![Mastodon Follow](https://img.shields.io/mastodon/follow/109302774947550572?domain=https%3A%2F%2Ffosstodon.org&style=flat)](https://fosstodon.org/@steamcmd)
[![Docker Pulls](https://img.shields.io/docker/pulls/steamcmd/steamcmd.svg)](https://hub.docker.com/r/steamcmd/steamcmd)
[![Image Size](https://img.shields.io/docker/image-size/steamcmd/steamcmd/latest.svg)](https://hub.docker.com/r/steamcmd/steamcmd)
[![GitHub Sponsors](https://img.shields.io/github/sponsors/steamcmd)](https://github.com/sponsors/steamcmd)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

# SteamCMD Docker Image

SteamCMD on various Docker base images for downloading and running Steam games
and game server software. The images are rebuild daily with
[Github Actions](https://github.com/steamcmd/docker/actions) and tagged on type
of base image.

For detailed information about SteamCMD,
see the official [wiki](https://developer.valvesoftware.com/wiki/SteamCMD).
If you are looking for a programmatic way to retrieve information via SteamCMD,
have a look at [steamcmd.net](https://www.steamcmd.net).

## Tags

*   [`ubuntu-24`, `ubuntu-noble`, `ubuntu`, `latest`](dockerfiles/ubuntu-24/Dockerfile)
*   [`ubuntu-22`, `ubuntu-jammy`](dockerfiles/ubuntu-22/Dockerfile)
*   [`ubuntu-20`, `ubuntu-focal`](dockerfiles/ubuntu-20/Dockerfile)
*   [`ubuntu-18`, `ubuntu-bionic`](dockerfiles/ubuntu-18/Dockerfile)
*   [`ubuntu-16`, `ubuntu-xenial`](dockerfiles/ubuntu-16/Dockerfile)
*   [`debian-12`, `debian-bookworm`, `debian`](dockerfiles/debian-12/Dockerfile)
*   [`debian-11`, `debian-bullseye`](dockerfiles/debian-11/Dockerfile)
*   [`debian-10`, `debian-buster`](dockerfiles/debian-10/Dockerfile)
*   [`alpine-3`, `alpine`](dockerfiles/alpine-3/Dockerfile)
*   [`rocky-9`, `rocky`](dockerfiles/rocky-9/Dockerfile)
*   [`rocky-8`](dockerfiles/rocky-8/Dockerfile)
*   [`centos-9`, `centos`](dockerfiles/centos-9/Dockerfile)
*   [`cachyos-3`](dockerfiles/cachyos-3/Dockerfile)
*   [`cachyos`](dockerfiles/cachyos/Dockerfile)
*   [`windows-1809`](dockerfiles/windows-1809/Dockerfile) *(unavailable)*
*   [`windows-core-2025`](dockerfiles/windows-core-2025/Dockerfile) *(unavailable)*
*   [`windows-core-2022`](dockerfiles/windows-core-2022/Dockerfile) *(unavailable)*
*   [`windows-core-2019`](dockerfiles/windows-core-2019/Dockerfile) *(unavailable)*
*   [`windows-core-1809`](dockerfiles/windows-core-1809/Dockerfile) *(unavailable)*

All the tags are pushed to both the Docker Hub and the GitHub Container Registry:

- `docker.io/steamcmd/steamcmd:<tag>`
- `ghcr.io/steamcmd/steamcmd:<tag>`

> ***Note:***
> *The Windows tags are not available because they either cannot be build on*
> *the current Github Actions Windows Platform or are simply broken. The Dockerfiles*
> *are added to this repository to be able to build manually and for the moment when*
> *the builds can be ran succesfully. See*
> *[this article](https://docs.microsoft.com/en-us/virtualization/windowscontainers/deploy-containers/version-compatibility)*
> *on the Microsoft docs for more information on the subject.*

> ***Note:***
> *The Debian images are based on the `slim` images.*

> ***Note:***
> *The CentOS images are based on CentOS Stream images seeing the old images are*
> *deprecated. If the "old style" of CentOS images are needed, the Rocky Linux*
> *are recommended as an alternative.*

## Usage

### Pull latest image
```shell
docker pull steamcmd/steamcmd:latest
```
### Test interactively
```shell
docker run --entrypoint /bin/sh -it steamcmd/steamcmd:latest
```
### Download CSGO
```shell
docker run -it steamcmd/steamcmd:latest +login anonymous +app_update 740 +quit
```
### Download CSGO to local mounted directory "data"
```shell
docker run -it -v $PWD:/data steamcmd/steamcmd:latest +login anonymous +force_install_dir /data +app_update 740 +quit
```

## License

[MIT license](LICENSE)
