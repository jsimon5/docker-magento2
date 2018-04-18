![Magento 2](https://cdn.rawgit.com/rafaelstz/magento2-snippets-visualstudio/master/images/icon.png)

#  Magento 2 Docker

### NGINX + PHP 7 + OPCache + Percona + Magerun 2 + XDebug + Redis

[![Build Status](https://travis-ci.org/Imagination-Media/docker-magento2.svg?branch=master)](https://travis-ci.org/Imagination-Media/docker-magento2)
[![Docker Build](https://img.shields.io/docker/build/imaginationmedia/magento2.svg)](https://hub.docker.com/r/rafaelcgstz/magento2/)
[![Docker Pulls](https://img.shields.io/docker/pulls/imaginationmedia/magento2.svg)](https://hub.docker.com/r/imaginationmedia/magento2/)
[![](https://images.microbadger.com/badges/image/imaginationmedia/magento2:php7.1-fpm.svg)](https://microbadger.com/images/imaginationmedia/magento2:php7.1-fpm)
[![Releases](https://img.shields.io/github/release/Imagination-Media/docker-magento2.svg)](https://github.com/Imagination-Media/docker-magento2/releases)

### Requirements

**MacOS:**

Install [Docker](https://download.docker.com/mac/stable/Docker.dmg) and run:

```
    gem install docker-sync
    brew install unison
    brew install eugenmayer/dockersync/unox

```

**Windows:**

Install [Docker](https://docs.docker.com/docker-for-windows/install/) and [Docker-sync](https://github.com/EugenMayer/docker-sync/wiki/docker-sync-on-Windows).

**Linux:**

Install [Docker](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/) and [Docker-compose](https://docs.docker.com/compose/install/#install-compose).

### How to use?

#### Automatic method

Just run these commands below in your terminal, change the MYMAGENTO2 to use the name of your project:

```

curl -s https://raw.githubusercontent.com/Imagination-Media/docker-magento2/master/init | bash -s MYMAGENTO2 clone
cd MYMAGENTO2
rm -rf src/*
./shell install-magento2

```

#### Or cloning this repository

You can also clone this repository and run these commands:

```

./init MYMAGENTO2
rm -rf src/*
./shell install-magento2

```

### Panels

Enjoy your new panels!

**Web server:** http://dev.local/

**PHPMyAdmin:** http://dev.local:8080

**Local emails:** http://dev.local:8025

### Features commands

| Commands  | Description  | Options & Examples |
|---|---|---|
| `./init`  | If you didn't use the CURL setup command above, please use this command changing the name of the project.  | `./init MYMAGENTO2` |
| `./start`  | If you continuing not using the CURL you can start your container manually  | |
| `./stop`  | Stop your project containers  | |
| `./kill`  | Stops containers and removes containers, networks, volumes, and images created to the specific project  | |
| `./shell`  | Access your container  | `./shell root` or `./shell ls` | |
| `./magerun`  | Use the Magerun and Magento CLI commands as you want | |
| `./xdebug`  |  Enable / Disable the XDebug | |

### License

Apache © 2018 [Imagination Media](https://github.com/Imagination-Media) and [contributors](https://github.com/Imagination-Media/docker-magento2/graphs/contributors).
