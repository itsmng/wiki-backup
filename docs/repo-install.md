## Introduction

ITSM-NG dev team provide DEB and RPM repository in order to install our product without having to manage dependencies and basic configuration.
We'll review how to setup repository on debian based and redhat based systems.

## DEB repository 

In order to setup the Debian repository, you need to add our repository to your sources list.

First import the GPG key : 
`curl -sS http://deb.itsm-ng.org/pubkey.gpg | sudo apt-key add -`

Please note that some newer OS are deprecating `apt-key add` (ubuntu 22.04 for example). In that case please use the following command :
`curl -fsSL http://deb.itsm-ng.org/pubkey.gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/itsm-ng-keyring.gpg`

Then add the repository : 
```
echo "deb http://deb.itsm-ng.org/<repository>/ <distribution> main" | sudo tee /etc/apt/sources.list.d/itsm-ng.list
sudo apt update
```
You need to replace `repository` accordingly with the linux distrubution you are using : 
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
`sudo apt install itsm-ng`

On the first installation, it will generate a default MySQL user named itsmng wit the password itsmng only accessible from localhost.

After installing the package, navigate to `http://myserver/itsm-ng`

When a new update is available, update itsm-ng using : 
`sudo apt update && sudo apt upgrade`

## RPM repository 

*Coming soon*