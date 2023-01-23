# Introduction
Thank you for downloading the ITSM-NG docker setup !

# Installation
```
git clone https://github.com/itsmng/itsmng-docker
cd itsmng-docker
```
To chose your version you go simply on the directory version exemple 1.4 directory or latest for the last version.
```
cd latest
```

Start the container
```
docker-compose up -d
```
You ITSM-NG is available on the address http://localhost

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
