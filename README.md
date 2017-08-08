# reverse-proxy-ripcord:

This repository is meant as a companion repository to [kobo-docker-ripcord](https://github.com/jpstaub/kobo-docker-ripcord).
However, it can be used on its own to set up a reverse-proxy environment for other docker containers. The docker-compose files are structured to provide **WEB** (https) or **LAN** (http) network connectivity to services running in docker containers. `reverse-proxy-ripcord` can be used in the following ways with little in the way of configuration on the part of the end user:

## Option 1 - Reverse Proxy with SSL support:
This repository can be used as a stand alone repository to set up a [jwilder reverse proxy](https://github.com/jwilder/nginx-proxy) server with [companion SSL](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion) support. This option would be taken by doing something like the following at the command line:
```
$ ln -s docker-compose.web.yml docker-compose.yml
$ docker-compose up -d
```
The first line above forms a [symlink](https://kb.iu.edu/d/abbe) so that the user can use [docker-compose commands](https://docs.docker.com/compose/reference/) against **docker-compose.web.yml** as shown in the second line above. If there is a need to remove the symlink it would be done with the following:

    $ rm docker-compose.yml

## Option 2 - Reverse Proxy withouth SSL support:
This repository can be used as a stand alone repository to set up a [jwilder reverse proxy](https://github.com/jwilder/nginx-proxy) server. This option would be taken by doing something like the following at the command line:
```
$ ln -s docker-compose.lan.yml docker-compose.yml
$ docker-compose up -d
```
The first line above forms a [symlink](https://kb.iu.edu/d/abbe) so that the user can use [docker-compose commands](https://docs.docker.com/compose/reference/) against **docker-compose.lan.yml** as shown in the second line above. If there is a need to remove the symlink it would be done with the following:

    $ rm docker-compose.yml

# Usage

1. Decide which option is appropriate for your use case. **Option 1** is meant for **WEB** deployment where there is a need to provide secure communication between clients and servers with SSL. However, it also maintains the ability to serve http traffic depending on the configuration of containers added to the Docker host. **Option 2** is meant for **LAN** deployment where there is NO need to provide secure communications between clients and servers with SSL. Both **Option 1** and **Option 2** are configured with a test web server that will display the image below if successfully deployed. 