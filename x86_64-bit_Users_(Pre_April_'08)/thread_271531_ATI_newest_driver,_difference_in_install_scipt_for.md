---
title: "ATI newest driver, difference in install scipt for 64bit"
date: 2006-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by mattyj on 2006-10-04
Hello,

The installation of the newest ATI driver is well documented as below, but I am curious to know the exact changes in the filenames necessary for 64bit.   Thank You.

Installing the new driver 
Download the ATI driver installer: ati-driver-installer-8.29.6.run (this installer is for 32bit and 64bit systems) 

This guide refers to the 32bit version of the driver. The installation procedure for 64bit should be the same as for 32bit, except some filenames will differ slightly. 

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps. 

Install necessary tools: 

sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
Create .deb packages: 

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
Install .deb packages: 

sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb
Remove any old fglrx debs from /usr/src/: 

sudo rm /usr/src/fglrx-kernel*.deb
Compile the kernel module: 

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
Note: You have to recompile the kernel module after each kernel update! 

Update the xorg.conf file: 

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot: 

sudo shutdown -r now
[edit]Confirm that it worked 
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.6065 (8.29.6)

---

### Post by xstaticxgpx on 2006-10-04
> **mattyj said:**
> Hello,

The installation of the newest ATI driver is well documented as below, but I am curious to know the exact changes in the filenames necessary for 64bit.   Thank You.

Installing the new driver 
Download the ATI driver installer: ati-driver-installer-8.29.6.run (this installer is for 32bit and 64bit systems) 

This guide refers to the 32bit version of the driver. The installation procedure for 64bit should be the same as for 32bit, except some filenames will differ slightly. 

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps. 

Install necessary tools: 

sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
Create .deb packages: 

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
Install .deb packages: 

sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb
Remove any old fglrx debs from /usr/src/: 

sudo rm /usr/src/fglrx-kernel*.deb
Compile the kernel module: 

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
Note: You have to recompile the kernel module after each kernel update! 

Update the xorg.conf file: 

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot: 

sudo shutdown -r now
[edit]Confirm that it worked 
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.6065 (8.29.6)

are you aware that you have Ubuntu/edgy instead of Ubuntu/dapper ? If you want edgy support you should go to the edgy development forum.

--

i currently have 8.29.6 installed, and i only had to do the following steps

1. sudo ./ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper

2. sudo dpkg -i xorg-driver-fglrx_8.29.6-1_amd64.deb
sudo dpkg -i fglrx-kernel-source_8.29.6-1_amd64.deb
sudo dpkg -i fglrx-control_8.29.6-1_amd64.deb

3. sudo rm /usr/src/fglrx-kernel*.deb

4. sudo module-assistant prepare,update
sudo module-assistant build,install fglrx

5. sudo depmod

6. sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

7. reboot, check to see if it worked (fglrxinfo)


worked perfectly for me, idk where they got the "sudo ln -sf /bin/sh" from... thats unnecessary, aswell as the -a after depmod

---

### Post by mattyj on 2006-10-04
Sorry.  I went to copy the link and must have clicked Edgy.  Probably about the same for this though.

Thank You for your help.

MJ

---

### Post by xstaticxgpx on 2006-10-04
No problem

---

