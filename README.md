## Decred Daemon Dockerfile

This is a basrebone docker container build using busybox


This repository contains **Dockerfile** of [Decred daemon](http://decred.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/reiuiji/dcrd/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [progrium/busybox](https://github.com/progrium/busybox)


### Installation

1. Install [Docker](https://www.docker.com/).
    emerge -va docker
    pacman -S docker
    apt-get install docker
    yum install docker

2. Download [automated build](https://registry.hub.docker.com/u/reiuiji/dcrd/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull reiuiji/dcrd`

   (alternatively, you can build an image from Dockerfile)

### Building
docker build -t="reiuiji/dcrd" .
docker run -d --name="dcrd" reiuiji/dcrd
docker kill --signal="SIGINT" dcrd


### Usage
This docker image can either be configured before build or attach the config.

#### If you want to change the provided dcrd.conf, you should do the following:

    docker cp /path/to/your/dcrd.conf:/root/.dcrd/dcrf.conf

#### If you only want to tweak the dcrd.conf, you can run a temp link:

    docker run -d -p 9109:9109 -name dcrd -v /path/to/your/dcrd.conf:/root/.dcrd/dcrf.conf reiuiji/dcrd

#### Run your dcrd container

    docker run -d -p 9109:9109 -name dcrd reiuiji/dcrd

### Checking if it works
To check if dcrd is working you can check the docker logs

    docker logs dcrd

### Shutting down the docker container
If you need to close down the docker you can run the following:

    docker kill --signal=SIGINT dcrd

### Donation
If you like this and want to see more, please donate :)
DsXSh151DsJpEA8mrAW5gCfVVqNCK8vQAss
