# Axelor Dockerfiles

This repository provides [Dockerfiles](https://docs.docker.com/engine/reference/builder/) and samples to build [Docker](https://www.docker.com/what-docker) images for [Axelor](https://axelor.com) apps.

## Build Images

It assumes you have Docker installed on your system.

### Build base image

```sh
$ cd aio-base
$ docker build -t axelor/aio-base .
```

### Build builder image

```sh
$ cd aio-builder
$ docker build -t axelor/aio-builder .
```

### Build app image

First : 

```sh
$ cd aio-erp
```

And modify the application.properties with your instructions

```sh
$ nano application.properties
```

For information, visit : https://docs.axelor.com/adk/5.2/dev-guide/application/config.html#example-configuration

AFTER :

```sh
$ docker build -t axelor/aio-erp .
```

## Run app container AXELOR with SLL

After build all, Go to the folder aio-erp

edit .env
```
nano .env
```
And modify with your domain or subdomain and register email Let's Encrypt
```
DOMAIN_AXELOR=write_your_domain_of_AXELOR
LETSENCRYPT_EMAIL=write_your_email_for_LETSENCRYPT
```

Configure the port of your AXELOR

```
PORT_AXELOR=your_port
# Example : PORT_AXELOR=6969
```

Save the file and :

* `sudo docker-compose up`

Or

* `sudo docker-compose up -d`

Once app completes database initialization, it can be access at: https://yourdomain.com or your subdomain https://subdomain.yourdomain.com

## VERY IMPORTANT

This version of container app must use a network connected to the webproxy from projet "evertramos"

Please, See the link : https://github.com/evertramos/docker-compose-letsencrypt-nginx-proxy-companion
