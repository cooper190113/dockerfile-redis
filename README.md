## Redis Dockerfile


This repository contains **Dockerfile** of [Redis](http://redis.io/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/dockerfile/redis/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [ubuntu16.04]
RUN apt-get install -y
RUN apt-get update --fix-missing -y
RUN apt-get install wget -y

RUN apt-get install gcc -y
RUN apt-get install build-essential -y
RUN apt-get update -y


### Installation

1. Install [Docker](https://www.docker.com/).
    
   eg：docker build -t redis/ubuntu:latest .


### Usage

#### Run `redis-server`

    docker run -d --name redis -p 6379:6379 redis/ubuntu:latest

#### Run `redis-server` with persistent data directory. (creates `dump.rdb`)

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis redis/ubuntu:latest

#### Run `redis-server` with persistent data directory and password.

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis redis/ubuntu:latest redis-server /etc/redis/redis.conf --requirepass <password>

#### Run `redis-cli`

    docker run -it --rm --link redis:redis redis/ubuntu:latest bash -c 'redis-cli -h redis'
