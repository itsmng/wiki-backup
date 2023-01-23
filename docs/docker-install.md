# Introduction
Thank you for downloading the ITSM-NG docker setup !

# Create and config the Docker-Compose config

Create docker-compose.yml file and add content

```
version: '3'
services:
  itsmweb :
    image : itsm-ng
    depends_on:
      - itsmdb
    container_name : itsmweb
    restart: always
    ports :
      - "80:80"
    volumes :
      - ./itsmng-config:/var/www/itsm-ng/config
      - ./itsmng-plugins:/var/www/itsm-ng/plugins
      - ./itsmng-files:/var/www/itsm-ng/files
    environment:
      MARIADB_USER : itsmng
      MARIADB_PASSWORD : itsmng
      MARIADB_DATABASE : itsmng
  itsmdb :
    image: mariadb
    container_name: itsmdb
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    volumes :
      - ../itsmdata:/var/lib/mysql
    environment:
      MARIADB_AUTO_UPGRADE: "yes"
      MARIADB_ALLOW_EMPTY_ROOT_PASSWORD: "yes"
      MARIADB_USER : itsmng
      MARIADB_PASSWORD : itsmng
      MARIADB_DATABASE : itsmng
    healthcheck:
      test: ["CMD", "mysqladmin" ,"ping", "-h", "localhost", "-u", "root", "-p$MYSQL_ROOT_PASSWORD"]
      timeout: 20s
      retries: 10
```

# Securize your Installation
By default in this exemple the MariaDB user,password and datase is itsmng. To change this setting you can edit the ***MARIADB_USER,MARIADB_PASSWORD*** and the ***MARIADB_DATABASE*** variable.

# Launch the container
Now you can launch the container with this command

```
docker-compose up
```

Docker-Compose is automatically download the images of MariaDB and ITSM-NG. And then launch the MariaDB and ITSM-NG container, and launch the installation of ITSM-NG

Now ITSM-NG is completely install

# What files need to be backup 
The docker volume created need to be backup to not lose your data

| Volumes        | Description                                                                   |
|----------------|-------------------------------------------------------------------------------|
| itsmng-config  | He contain the database Information, the name and the login of MySQL database |
| itsmng-plugins | He contain all of the ITSM-NG plugins files                                   |
| itsmng-files   | He contain all of the attachments, and profile picture                        |
| itsmdata       | He contain all of the files of MariaDB.                                       |

This volume is a folder in your docker-compose directory.
