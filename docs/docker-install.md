# ITSM-NG docker installation

## Introduction

ITSM-NG dev team provide a docker image in order to install our product without having to manage dependencies and basic configuration.
We'll review how to setup and maintain the ITSM-NG application via docker.

## List of all image tags

| Tag    | Description                         | Images                         | Usage      |
|--------|-------------------------------------|--------------------------------|------------|
| 1.3.0  | Stable ITSM-NG version              | Debian Bookworm / MariaDB 10.6 | Production |
| 1.4.0  | Stable ITSM-NG version              | Debian Bookworm / MariaDB 10.6 | Production |
| latest | Use the last stable ITSM-NG version | Debian Bookworm / MariaDB 10.6 | Production |

## Pull image from docker hub

To pull the latest ITSM-NG image, launch the following command :

    docker pull itsmng/itsm-ng:latest

To pull a specific version replace `latest` by the desired version.

    docker pull itsmng/itsm-ng:1.3.0

## Pull image from sources and build it locally

To build the image locally pull the git repository :

    git clone https://github.com/itsmng/itsmng-docker

Docker build command :

    docker build --rm -f "MY_TAG/Dockerfile" -t itsmng/itsm-ng:MY_TAG "MY_TAG"

## Run ITSM-NG using docker

You currently have two options : 

* Run the image alone using `docker run`.
* Run the image along with a MariaDB server using `docker-compose`.

### ITSM-NG image without MariaDB

ITSM-NG image doesn't come with MariaDB instance, if you want one, please check the documentation below (docker-compose)

To run an ITSM-NG instance with the most basics settings, you can use the following command 

    docker run \
    --name [MY_CONTAINER_NAME] \
    -e MARIADB_HOST=[DB_HOST] \
    -e MARIADB_DATABASE=[DB_NAME] \
    -e MARIAD_USER=[DB_USER] \
    -e MARIADB_PASSWORD=[DB_PASSWORD] \
    -idt itsmng/itsm-ng:MY_TAG

See `List of all image tags` for more information.

### ITSM-NG image with MariaDB

We have a docker-compose example in every folder for each tag of our image.

To get these examples / templates, clone our git repository :

    git clone https://github.com/itsmng/itsmng-docker
    cd itsmng-docker/latest

If you want a specific version replace `latest` by the desired version.

`Note: in production environment, we recommend to use a specific tag and not the latest tag in order to avoid any unwanted upgrade process upon container restart`

#### Secure the installation

By default, the MariaDB user, password and database are set as `itsmng`.
To update these settings, edit the `docker-compose.yml` and change the following settings :

* MARIADB_USER
* MARIADB_PASSWORD
* MARIADB_DATABASE

`Note: these settings are set in the itsmweb and itsmdb container parts.`

#### Start the stack

To start the ITSM-NG application stack, run the following command :

    docker-compose up -d

By default, volume names use the current version as a prefix (i.e. 1.3.0 => 130_volumename). You can set a custom prefix with the next command :

    docker-compose -p MY_PREFIX up -d

You can check if containers are running correctly with the next command :

    docker container ls -a

The container status is `Up` if it works.

Now, your ITSM-NG application is available at the following address [http://localhost:8080](http://localhost:8080).

#### Volumes information

Below you will find the volumes list created by ITSM-NG docker application and their description :

| Volume           | Description                                                      |
|------------------|------------------------------------------------------------------|
| `itsmng-config`  | It contains the application configuration                        |
| `itsmng-plugins` | It contains the application plugins                              |
| `itsmng-files`   | It contains the application extra data (logs, cache, attachment) |
| `itsmng-data`    | It contains the MariaDB instance data                            |

## Update ITSM-NG docker instance

### Update ITSM-NG without MariaDB (docker run)

In the case of `docker run`, to update to the newest version run the following command :

    docker stop

Retrieve the latest ITSM-NG image with the `pull` command :

    docker pull itsmng/itsm-ng:MY_TAG

Then, restart your container :

    docker run \
    --name [MY_CONTAINER_NAME] \
    -e MARIADB_HOST=[DB_HOST] \
    -e MARIADB_DATABASE=[DB_NAME] \
    -e MARIAD_USER=[DB_USER] \
    -e MARIADB_PASSWORD=[DB_PASSWORD] \
    -idt itsmng/itsm-ng:MY_TAG

### Update ITSM-NG with MariaDB (docker-compose)

To update your application to the newest version, go to the current running instance folder and run the following command :

    docker-compose down

Retrieve the latest `itsmng-docker` updates with the `pull` command :

    git pull origin main

Edit the `docker-compose.yml` with your custom settings and run :

    docker-compose up -d

By default, volume names use the current version as a prefix (i.e. 1.3.0 => 130_volumename). 

You can set a custom prefix with the next command :

    docker-compose -p MY_PREFIX up -d

`Note: in the case you don't use custom prefix, don't forget to rename your old volumes with the new prefix version. You can also use docker cp command to copy old volumes data in the new volumes.`

## Crontab implementation

To implement a crontab outside of the container, you can configure it directly on your server following the example below :

    0 0 * * * root docker exec `itsmng_web` bash -c 'cd /var/www/itsm-ng && php front/cron.php'

## View logs

You can check the containers logs with the two following commands :

For ITSM-NG application container :

    docker container logs itsmweb

For MariaDB container :

    docker container logs itsmdb

When using `docker-compose` : 

    docker-compose logs -f 

