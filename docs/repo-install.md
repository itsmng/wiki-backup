## Introduction

ITSM-NG dev team provide DEB and RPM repository in order to install our product without having to manage dependencies and basic configuration.
We'll review how to setup repository on debian based and redhat based systems.

## DEB repository 

In order to setup the Debian repository, you need to add our repository to your sources list.

First import the GPG key : 

    curl -sS http://deb.itsm-ng.org/pubkey.gpg | sudo apt-key add -

Please note that some newer OS are deprecating `apt-key add` (ubuntu 22.04 for example). 

In that case please use the following command :

    curl -fsSL http://deb.itsm-ng.org/pubkey.gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/itsm-ng-keyring.gpg

Then add the repository : 

    echo "deb http://deb.itsm-ng.org/<repository>/ <distribution> main" | sudo tee /etc/apt/sources.list.d/itsm-ng.list
    sudo apt update

You need to replace `repository` accordingly with the linux distribution you are using : 

* debian
* ubuntu

The `distribution` also need to be changed with the correct distribution.

With debian we provide the following distributions : 

* bullseye (11)
* buster (10)
* sid (unstable)

With ubuntu we provide the following distributions : 

* jammy (22.04)
* focal (20.04)
* bionic (18.04)

Then install itsm-ng : 

    sudo apt install itsm-ng

On the first installation, it will generate a default MySQL user named itsmng wit the password itsmng only accessible from localhost.

After installing the package, navigate to `http://myserver/`

Below are the locations of the different ITSM-NG files/folders :

* Application php files : `/usr/share/itsm-ng/`
* Application configuration files : `/etc/itsm-ng/`
* Other application files (attachment, logs, cache) : `/var/lib/itsm-ng/`
* Apache configuration file : `/etc/apache2/site-availables/itsm-ng.conf`

When a new update is available, update itsm-ng using : 

    sudo apt update && sudo apt upgrade


## RPM repository 
### On CentOS / AlmaLinux / Rocky Linux

First, install dnf-utils :

    sudo dnf install dnf-utils

You will need to install and enable the remi repository. To do so :

    sudo dnf -y install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
    sudo yum-config-manager --enable remi

Next step is modifying the PHP version used by the system : 

    sudo dnf module reset php
    sudo dnf module install php:remi-8.1

Once done, add the repository for itsm-ng :

    sudo yum-config-manager --add-repo http://rpm.itsm-ng.org/itsm-el8.repo

Then, launch the install :

    sudo dnf install itsm-ng

On first installation, a default MySQL user named itsmng (password: itsmng) is generated and only accessible from localhost.

After installing the package, navigate to `http://myserver/` and follow the instructions.

Below are the locations of the different ITSM-NG files/folders :

* Application php files : `/usr/share/itsm-ng/`
* Application configuration files : `/etc/itsm-ng/`
* Other application files (attachment, logs, cache) : `/var/lib/itsm-ng/`
* Apache configuration file : `/etc/httpd/conf.d/itsm-ng.conf`

When a new update is available, update itsm-ng using : 

    sudo dnf update

### On Fedora systems

On Fedora systems, install dnf-utils : 

    sudo dnf install dnf-utils

Then add the repository (fc35 in example) : 

    sudo yum-config-manager --add-repo http://rpm.itsm-ng.org/itsm-fc35.repo

Available system versions :

* `fc35` for Fedora 35
* `fc36` for Fedora 36
* `fc37` for Fedora 37
* `fc38` for Fedora 38

To install itsm-ng, run :

    sudo dnf install itsm-ng

On first installation, a default MySQL user named itsmng (password: itsmng) is generated and only accessible from localhost.

After installing the package, navigate to `http://myserver/` and follow the instructions.

Below are the locations of the different ITSM-NG files/folders :

* Application php files : `/usr/share/itsm-ng/`
* Application configuration files : `/etc/itsm-ng/`
* Other application files (attachment, logs, cache) : `/var/lib/itsm-ng/`
* Apache configuration file : `/etc/httpd/conf.d/itsm-ng.conf`

When a new update is available, update itsm-ng using : 

    sudo dnf update
