[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE.md)

# SteamCMD Docker Image

SteamCMD on Ubuntu and BusyBox for downloading and running Steam games and game server software. Currently the images are build every day and only tagged on type of base image (because of the unknown `steamcmd` versions/releases).

## Tags

- [`ubuntu-18`, `ubuntu`, `latest`](https://github.com/steamcmd/docker/blob/master/dockerfiles/ubuntu-18)
- [`ubuntu-16`](https://github.com/steamcmd/docker/blob/master/dockerfiles/ubuntu-16)
- [`alpine`](https://github.com/steamcmd/docker/blob/master/dockerfiles/alpine)
- [`busybox`, `lite`](https://github.com/steamcmd/docker/blob/master/dockerfiles/busybox)

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
