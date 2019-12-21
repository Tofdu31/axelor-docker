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

```sh
$ cd aio-erp
$ docker build -t axelor/aio-erp .
```

## Run app container AXELOR with SLL

First : modify the application.properties with your instructions

After build all, Go to the folder aio-erp and edit .env
```
nano .env
```
And modify with your domain or subdomain and register email Let's Encrypt
```
DOMAIN_AXELOR=write_your_domain_of_AXELOR
LETSENCRYPT_EMAIL=write_your_email_for_LETSENCRYPT
```
And after :

* `sudo docker-compose up`

Or

* `sudo docker-compose up -d`

Once app completes database initialization, it can be access at: https://yourdomain.com or your subdomain https://subdomain.yourdomain.com

