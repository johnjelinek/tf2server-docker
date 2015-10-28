# Team Fortress 2 Server Dockerfile

This repository contains **Dockerfile** of [Team Fortress 2 Server](http://gameservermanagers.com/lgsm/tf2server/) for [Docker](https://www.docker.com/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).

### Base Docker Image

* [ubuntu:14.04](https://hub.docker.com/_/ubuntu/)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/johnjelinek/tf2server/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull johnjelinek/tf2server`

   (alternatively, you can build an image from Dockerfile: `docker build -t="johnjelinek/tf2server" github.com/johnjelinek/tf2server-docker`)

### Usage

    docker run -dt --name tf2 -v /var/docker/tf2server:/home/tf2server -p 27015:27015 \
    -p 27015:27015/udp --entrypoint /home/tf2server/serverfiles/srcds_run johnjelinek/tf2server \
    -game tf -strictportbind -ip 0.0.0.0 -port 27015 +clientport 27005 +tv_port 27020 \
    +map cp_badlands +servercfgfile tf2-server.cfg -maxplayers 16

#### Preparation (Downloading the files onto your volume)

  1. Copy `/tf2server` to `~/tf2server`

  2. `./tf2server install`

  3. Answer some questions

  4. You can test everything went well with `./tf2server start` followed by `./tf2server details`.

  5. If everything looks good, run with the command listed under `Usage`.

From Steam Menu, View > Servers > Add `yourServerIP` server as a favorite and double click to join.
