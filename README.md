[![Build Status](https://img.shields.io/github/workflow/status/steamcmd/docker/Build%20Images.svg?logo=github)](https://github.com/steamcmd/docker/actions)
[![CodeFactor](https://www.codefactor.io/repository/github/steamcmd/docker/badge)](https://www.codefactor.io/repository/github/steamcmd/docker)
[![Service Status](https://img.shields.io/static/v1?label=service&message=status&color=blue)](https://status.steamcmd.net)
[![Docker Pulls](https://img.shields.io/docker/pulls/steamcmd/steamcmd.svg)](https://hub.docker.com/r/steamcmd/steamcmd)
[![Image Size](https://img.shields.io/docker/image-size/steamcmd/steamcmd/latest.svg)](https://hub.docker.com/r/steamcmd/steamcmd)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

# SteamCMD Docker Image

SteamCMD on various Docker base images for downloading and running Steam games
and game server software. The images are build automatically every 6 hours with
[Github Actions](https://github.com/steamcmd/docker/actions) and tagged on type
of base image.

For detailed information about SteamCMD,
see [wiki](https://developer.valvesoftware.com/wiki/SteamCMD).
Are you looking for a programmatic way to retrieve information via SteamCMD,
have a look at [steamcmd.net](https://www.steamcmd.net).

## Tags

*   [`ubuntu-20`](dockerfiles/ubuntu-20/Dockerfile)
*   [`ubuntu-18`, `ubuntu`, `latest`](dockerfiles/ubuntu-18/Dockerfile)
*   [`ubuntu-16`](dockerfiles/ubuntu-16/Dockerfile)
*   [`alpine-3`, `alpine`](dockerfiles/alpine-3/Dockerfile)
*   [`centos-8`, `centos`](dockerfiles/centos-8/Dockerfile)
*   [`centos-7`](dockerfiles/centos-7/Dockerfile)
*   [`windows-1909`](dockerfiles/windows-1909/Dockerfile) *(unavailable)*
*   [`windows-1903`](dockerfiles/windows-1903/Dockerfile) *(unavailable)*
*   [`windows-1809`, `windows`](dockerfiles/windows-1809/Dockerfile)
*   [`windows-core-2019`, `windows-core`](dockerfiles/windows-core-2019/Dockerfile)
*   [`windows-core-1909`](dockerfiles/windows-core-1909/Dockerfile) *(unavailable)*
*   [`windows-core-1903`](dockerfiles/windows-core-1903/Dockerfile) *(unavailable)*
*   [`windows-core-1809`](dockerfiles/windows-core-1809/Dockerfile)

> ***Note:*** *Some Windows tags are not available (yet) because they cannot be build on the current Github Actions Windows Platform.*
> *The Dockerfiles are added to this repository to be able to build manually and for the moment when Github Actions supports newer Windows versions.*
> *See [this article](https://docs.microsoft.com/en-us/virtualization/windowscontainers/deploy-containers/version-compatibility) on the Microsoft docs for more information on the subject.*

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
