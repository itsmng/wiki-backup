# ITSM-NG docker installation

## Introduction

ITSM-NG dev team provide a docker image in order to install our product without having to manage dependencies and basic configuration.
We'll review how to setup and maintain the ITSM-NG application via docker.

## List of all image tags

| Tag    | Description                         | Images                     | Usage      |
|--------|-------------------------------------|----------------------------|------------|
| 1.3.0  | Stable ITSM-NG version              | Alpine 3.17 / MariaDB 10.6 | Production |
| 1.4.0  | Stable ITSM-NG version              | Alpine 3.17 / MariaDB 10.6 | Production |
| latest | Use the last stable ITSM-NG version | Alpine 3.17 / MariaDB 10.6 | Production |

## Pull image from docker hub

To pull the latest ITSM-NG image, launch the following command :

    docker pull itsm-ng/itsmng:latest

To pull a specific version replace `latest` by the desired version.

    docker pull itsm-ng/itsmng:1.3.0

## Pull image from sources and build it locally

To build the image locally pull the git repository :

    git clone https://github.com/itsmng/itsmng-docker

Docker build command :

    docker build --rm -f "MY_TAG/Dockerfile" -t itsm-ng/itsmng:MY_TAG "MY_TAG"

## Run ITSM-NG using docker

We have a docker-compose example in every folder for each tag of our image.

To get these examples / templates, clone our git repository :

    git clone https://github.com/itsmng/itsmng-docker
    cd itsmng-docker/latest

If you want a specific version replace `latest` by the desired version.

### Secure the installation

By default, the MariaDB user, password and database are set as `itsmng`.
To update these settings, edit the `docker-compose.yml` and change the following settings :

* MARIADB_USER
* MARIADB_PASSWORD
* MARIADB_DATABASE

`Note: these settings are set in the itsmweb and itsmdb container parts.`

### Start the container

To start the ITSM-NG application container, run the following command :

    docker-compose up -d

You can check if the containers is running correctly with the next command :

    docker container ls -a

The container status is `Up` if it works.

Now, your ITSM-NG application is available at the following address [http://localhost](http://localhost).

### Volumes information

Below you will find the volumes list created by ITSM-NG docker application and their description :

| Volume           | Description                                                                      |
|------------------|----------------------------------------------------------------------------------|
| `itsmng-config`  | It contains the `itsm-ng/config` directory                                       |
| `itsmng-plugins` | It contains the `itsm-ng/plugins` directory                                      |
| `itsmng-files`   | It contains the `itsm-ng/files` directory (application logs, cache, attachments) |
| `itsmng-data`    | It contains the MariaDB instance datas                                           |

`Note: these volumes are created directly in your docker-compose directory.`

## Update ITSM-NG docker instance

To update your application to the newest version, go to the current running instance folder and run the following command :

    docker-compose down

Retrieve the latest `itsmng-docker` updates with the `pull` command :

    git pull origin main

Edit the `docker-compose.yml` with your custom settings and run :

    docker-compose up -d

## Crontab implementation

To implement a crontab outside of the container, you can configure it directly on your server following the example below :

    0 0 * * * root docker exec <your_container_name> bash -c 'cd /var/www/itsm-ng && php front/cron.php'

## View logs

You can check the containers logs with the two following commands :

For ITSM-NG application container :

    docker container logs itsmweb

For MariaDB container :

    docker container logs itsmdb

