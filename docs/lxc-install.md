# ITSM-NG LXC container installation

## Introduction

ITSM-NG dev team provide a LXC image in order to install our product without having to manage dependencies and basic configuration. We'll review how to setup and maintain the ITSM-NG application via LXC container.

## How to add ITSM-NG LXC template in Proxmox

To use our LXC template, you need to add the template in Proxmox.

You will find all released templates at the following link : [https://github.com/itsmng/itsm-lxc/releases](https://github.com/itsmng/itsm-lxc/releases).

![](img/lxc/step1.png)

Then, follow the next steps to integrate the LXC template in Proxmox :

* Select the LXC template storage.

![](img/lxc/step2.png)

* Click on `CT Templates`.

![](img/lxc/step3.png)

* Click on `Upload`.

![](img/lxc/step4.png)

* Click on `Select File` and select the LXC template.

![](img/lxc/step5.png)

* Click on `Upload`.

![](img/lxc/step6.png)

The template is now added in Proxmox. You can use it to create a container.

## Create ITSM-NG LXC container in Proxmox

Go to your Proxmox administration panel and create a new CT.

On the `Template` tab, choose the ITSM-NG template.

![](img/lxc/step9.png)

Once your container is created and started, connect to the command line console and log in with the root user.

Next, complete the ITSM-NG installation by following the on-screen instructions.

Set a MySQL user for ITSM-NG.

![](img/lxc/step19.png)

Set a MySQL password.

![](img/lxc/step20.png)

Then, set a database name for ITSM-NG.

![](img/lxc/step21.png)

The installation can take several minutes.

![](img/lxc/step22.png)

When the installation is completed, you can access to your ITSM-NG instance at the following address : [http://my-itsmng-ip](http://my-itsmng-ip)

![](img/lxc/step23.png)

## How to add ITSM-NG LXC template in other hypervisor

This template can be used in other hypervisor than Proxmox. But we don't currently offer an installation guide.

If you manage to configure and use our LXC template in other context / hypervisor, feedback are welcomed.