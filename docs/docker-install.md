## Introduction

Thank you for downloading the ITSM-NG docker installator!

## Donwload 

Download the version of your choice at the following link : https://github.com/itsmng/itsm-ng/releases

However, we recommend using the latest version available.


## Pre installation

When you have finished to download, navigate to your folder where setup.sh is located, open a terminal there and run this command.

```
./setup.sh
```
 
## Installation
```
ITSM-NG SETUP: Install or Upgrade ? (I/U)
```
Choose whether you want to install or update ITSM-NG by writing **I** to install or **U** to update.

```
Database user (empty for default):
```
Write the user but if you leave it empty it will be **itsmng**.
```
Database password (empty for default):
```
Write the password but if you leave it empty it will be **itsmng**.
```
Database name (empty for default):
```
Write the name of the database but if you leave it empty it will be **itsmng**.

```
➤   ITSM-NG version: v1.0.1
➤   Database user: itsmng
➤   Database name: itsmng
➤   Container name: itsmdb
Press any key to continue.
```
You will get a summary, so if all is well then press **enter**, otherwise press **ctrl+c** to exit.\

The installation and the downloading of file is started, it will take few minutes.

```
Do you want to continue ? [Yes/no]
```
You will see that at the end of the installation, do not touch anything, the script have already pressed **yes**, please wait...
```
Go to: http://127.0.0.1:9080
```
Now, you can connect to ITSM-NG at http://localhost/itsm-ng with the default user itsm/itsm.

Enjoy ITSM-NG :-)