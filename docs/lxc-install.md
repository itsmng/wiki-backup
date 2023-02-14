# Install ITSM-NG in LXC container

## Install LXC template in Proxmox

Download the LXC template

![](img/lxc/step1.png)

Select the LXC template storage

![](img/lxc/step2.png)

Click on ***CT Modeles***

![](img/lxc/step3.png)

Click on ***Upload***

![](img/lxc/step4.png)

Click on ***Select*** and select the lxc template

![](img/lxc/step5.png)

Click on ***Upload***

![](img/lxc/step6.png)

## Create LXC container in Proxmox

![](img/lxc/step7.png)
![](img/lxc/step8.png)


Select your ITSM-NG LXC template 

![](img/lxc/step9.png)


Choose how much storage do you allocate to the container
![](img/lxc/step10.png)

Choose how much processor do you allocate to the container
![](img/lxc/step11.png)

Choose how much memory do you allocate to the container
![](img/lxc/step12.png)

Select your network card et chose DHCP or Static address
![](img/lxc/step13.png)

Write which DNS server your container use
![](img/lxc/step14.png)

Click on start container now et Finish
![](img/lxc/step15.png)

Et close the window
![](img/lxc/step16.png)

Your container is create
![](img/lxc/step17.png)

Go to the console, log in with the root user and the password you have defined
![](img/lxc/step18.png)

Write your MySQL username
![](img/lxc/step19.png)

Write your MySQL password
![](img/lxc/step20.png)

Write your database name
![](img/lxc/step21.png)

Installation can take several minutes
![](img/lxc/step22.png)

Your ITSM-NG is completely install
![](img/lxc/step23.png)

Your ITSM-NG is available on http://YOUR_IP/

![](img/lxc/step24.png)

## Install in other hypervisor
This container can be use in other hypervisor other than Promox. But we do not currently offer an installation guide