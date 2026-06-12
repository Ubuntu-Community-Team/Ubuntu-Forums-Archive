---
title: "can't install wine"
date: 2017-12-31
forum: Wine
---

### Post by cmcanulty on 2017-12-31
I am running Xubuntu 16.04 64bit. I have spent all morning trying to install wine 2. I have completely removed, purged wine  and still hundreds of wine files show after find command. I even deleted the .wine directory in /home and then reinstalled but it isn't in menu and won't run from terminal. Please tell me how to _completely_ remove wine and install wine 2. Thank you.

---

### Post by #&amp;thj^% on 2017-12-31
Did you install the PPA?
And sometimes using aptitude instead of apt for depends.
```
sudo aptitude install winehq-stable
```

---

### Post by cmcanulty on 2017-12-31
I did install a ppa but maybe it was a wrong one. It seems to install but won't run. I tried several tutorials

---

### Post by #&amp;thj^% on 2017-12-31
Just to be sure>>This is the method I use.
To get the Key:
```
wget -nc https://dl.winehq.org/wine-builds/Release.key && sudo apt-key add Release.key
```

And Add wine repository via command:
```
sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/
```

Or even this for Xenial:
```
sudo apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main'
```
Forgot to add:
```
sudo apt update
```
And just to try to prevent dep errors I use:
```
sudo apt install --install-recommends winehq-stable
```
And  If you get the unmet dependencies issue while installing Wine 2.0, try aptitude instead (As i have already suggested) via command:
```
sudo aptitude install winehq-stable
```
Post back any errors you might see.

---

### Post by cmcanulty on 2017-12-31
```

cmcanulty@Dell580s:~$ wget -nc https://dl.winehq.org/wine-builds/Release.key && sudo apt-key add Release.key
File ‘Release.key’ already there; not retrieving.

[sudo] password for cmcanulty: 
OK
cmcanulty@Dell580s:~$ sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/
cmcanulty@Dell580s:~$ sudo apt-add-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main'
cmcanulty@Dell580s:~$ ud
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Hit:5 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Hit:7 http://ppa.launchpad.net/i-nex-development-team/daily/ubuntu xenial InRelease
Hit:8 http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu xenial InRelease
Get:9 https://dl.winehq.org/wine-builds/ubuntu xenial InRelease [4,701 B]    
Hit:10 http://ppa.launchpad.net/ricotz/unstable/ubuntu xenial InRelease
Get:11 https://dl.winehq.org/wine-builds/ubuntu xenial/main amd64 Packages [24.6 kB]
Get:12 https://dl.winehq.org/wine-builds/ubuntu xenial/main i386 Packages [24.4 kB]
Fetched 360 kB in 1s (247 kB/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cmcanulty@Dell580s:~$ sudo apt install --install-recommends winehq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-wine libosmesa6 libwine libwine:i386 wine32:i386 wine64
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libcapi20-3:i386 libexif12:i386 libgd3:i386 libgphoto2-6:i386
  libgphoto2-port12:i386 libieee1284-3:i386 libsane:i386 libusb-1.0-0:i386
  libv4l-0:i386 libv4lconvert0:i386 libvpx3:i386 libxpm4:i386 wine-stable:i386
  wine-stable-i386:i386
Suggested packages:
  isdnutils-doc:i386 libgd-tools:i386 gphoto2:i386 hplip:i386
  libsane-extras:i386
The following packages will be REMOVED:
  wine-stable
The following NEW packages will be installed:
  libcapi20-3:i386 libexif12:i386 libgd3:i386 libgphoto2-6:i386
  libgphoto2-port12:i386 libieee1284-3:i386 libsane:i386 libusb-1.0-0:i386
  libv4l-0:i386 libv4lconvert0:i386 libvpx3:i386 libxpm4:i386 wine-stable:i386
  wine-stable-i386:i386 winehq-stable
0 upgraded, 15 newly installed, 1 to remove and 0 not upgraded.
Need to get 27.8 MB of archives.
After this operation, 198 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libexif12 i386 0.6.21-2 [76.2 kB]
Get:2 https://dl.winehq.org/wine-builds/ubuntu xenial/main i386 wine-stable-i386 i386 2.0.3~xenial [22.7 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libieee1284-3 i386 0.2.11-12 [23.7 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libvpx3 i386 1.5.0-2ubuntu1 [676 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libxpm4 i386 1:3.5.11-1ubuntu0.16.04.1 [35.5 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libgd3 i386 2.1.1-4ubuntu0.16.04.8 [129 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libusb-1.0-0 i386 2:1.0.20-1 [46.0 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libgphoto2-port12 i386 2.5.9-3 [50.4 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libgphoto2-6 i386 2.5.9-3 [823 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 libcapi20-3 i386 1:3.27-1 [29.0 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libsane i386 1.0.25+git20150528-1ubuntu2.16.04.1 [2,125 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libv4lconvert0 i386 1.10.0-1 [75.7 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial/main i386 libv4l-0 i386 1.10.0-1 [41.8 kB]
Get:14 https://dl.winehq.org/wine-builds/ubuntu xenial/main i386 wine-stable i386 2.0.3~xenial [1,062 kB]
Get:15 https://dl.winehq.org/wine-builds/ubuntu xenial/main amd64 winehq-stable amd64 2.0.3~xenial [3,178 B]
Fetched 27.8 MB in 3s (8,166 kB/s)         
(Reading database ... 423826 files and directories currently installed.)
Removing wine-stable (2.0.3-0ubuntu1~16.04~ricotz0) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Selecting previously unselected package libexif12:i386.
(Reading database ... 423782 files and directories currently installed.)
Preparing to unpack .../libexif12_0.6.21-2_i386.deb ...
Unpacking libexif12:i386 (0.6.21-2) ...
Selecting previously unselected package libieee1284-3:i386.
Preparing to unpack .../libieee1284-3_0.2.11-12_i386.deb ...
Unpacking libieee1284-3:i386 (0.2.11-12) ...
Selecting previously unselected package libvpx3:i386.
Preparing to unpack .../libvpx3_1.5.0-2ubuntu1_i386.deb ...
Unpacking libvpx3:i386 (1.5.0-2ubuntu1) ...
Selecting previously unselected package libxpm4:i386.
Preparing to unpack .../libxpm4_1%3a3.5.11-1ubuntu0.16.04.1_i386.deb ...
Unpacking libxpm4:i386 (1:3.5.11-1ubuntu0.16.04.1) ...
Selecting previously unselected package libgd3:i386.
Preparing to unpack .../libgd3_2.1.1-4ubuntu0.16.04.8_i386.deb ...
Unpacking libgd3:i386 (2.1.1-4ubuntu0.16.04.8) ...
Selecting previously unselected package libusb-1.0-0:i386.
Preparing to unpack .../libusb-1.0-0_2%3a1.0.20-1_i386.deb ...
Unpacking libusb-1.0-0:i386 (2:1.0.20-1) ...
Selecting previously unselected package libgphoto2-port12:i386.
Preparing to unpack .../libgphoto2-port12_2.5.9-3_i386.deb ...
Unpacking libgphoto2-port12:i386 (2.5.9-3) ...
Selecting previously unselected package libgphoto2-6:i386.
Preparing to unpack .../libgphoto2-6_2.5.9-3_i386.deb ...
Unpacking libgphoto2-6:i386 (2.5.9-3) ...
Selecting previously unselected package wine-stable-i386:i386.
Preparing to unpack .../wine-stable-i386_2.0.3~xenial_i386.deb ...
Unpacking wine-stable-i386:i386 (2.0.3~xenial) ...
Selecting previously unselected package wine-stable:i386.
Preparing to unpack .../wine-stable_2.0.3~xenial_i386.deb ...
Unpacking wine-stable:i386 (2.0.3~xenial) ...
Selecting previously unselected package libcapi20-3:i386.
Preparing to unpack .../libcapi20-3_1%3a3.27-1_i386.deb ...
Unpacking libcapi20-3:i386 (1:3.27-1) ...
Selecting previously unselected package libsane:i386.
Preparing to unpack .../libsane_1.0.25+git20150528-1ubuntu2.16.04.1_i386.deb ...
Unpacking libsane:i386 (1.0.25+git20150528-1ubuntu2.16.04.1) ...
Selecting previously unselected package libv4lconvert0:i386.
Preparing to unpack .../libv4lconvert0_1.10.0-1_i386.deb ...
Unpacking libv4lconvert0:i386 (1.10.0-1) ...
Selecting previously unselected package libv4l-0:i386.
Preparing to unpack .../libv4l-0_1.10.0-1_i386.deb ...
Unpacking libv4l-0:i386 (1.10.0-1) ...
Selecting previously unselected package winehq-stable.
Preparing to unpack .../winehq-stable_2.0.3~xenial_amd64.deb ...
Unpacking winehq-stable (2.0.3~xenial) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for udev (229-4ubuntu21) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libexif12:i386 (0.6.21-2) ...
Setting up libieee1284-3:i386 (0.2.11-12) ...
Setting up libvpx3:i386 (1.5.0-2ubuntu1) ...
Setting up libxpm4:i386 (1:3.5.11-1ubuntu0.16.04.1) ...
Setting up libgd3:i386 (2.1.1-4ubuntu0.16.04.8) ...
Setting up libusb-1.0-0:i386 (2:1.0.20-1) ...
Setting up libgphoto2-port12:i386 (2.5.9-3) ...
Setting up libgphoto2-6:i386 (2.5.9-3) ...
Setting up wine-stable-i386:i386 (2.0.3~xenial) ...
Setting up wine-stable:i386 (2.0.3~xenial) ...
Setting up libcapi20-3:i386 (1:3.27-1) ...
Setting up libsane:i386 (1.0.25+git20150528-1ubuntu2.16.04.1) ...
Setting up libv4lconvert0:i386 (1.10.0-1) ...
Setting up libv4l-0:i386 (1.10.0-1) ...
Setting up winehq-stable (2.0.3~xenial) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
cmcanulty@Dell580s:~$ sudo aptitude install winehq-stable
winehq-stable is already installed at the requested version (2.0.3~xenial)
winehq-stable is already installed at the requested version (2.0.3~xenial)
The following packages will be REMOVED:
  fonts-wine{u} libosmesa6{u} libwine{u} libwine:i386{u} wine32:i386{u} 
  wine64{u} 
0 packages upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 366 MB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 426157 files and directories currently installed.)
Removing fonts-wine (2.0.3-0ubuntu1~16.04~ricotz0) ...
Removing libosmesa6:amd64 (17.0.7-0ubuntu0.16.04.2) ...
Removing wine64 (2.0.3-0ubuntu1~16.04~ricotz0) ...
Removing libwine:amd64 (2.0.3-0ubuntu1~16.04~ricotz0) ...
Removing wine32:i386 (2.0.3-0ubuntu1~16.04~ricotz0) ...
Removing libwine:i386 (2.0.3-0ubuntu1~16.04~ricotz0) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for man-db (2.7.5-1) ...
                                         
cmcanulty@Dell580s:~$ wimecfg
No command 'wimecfg' found, did you mean:
 Command 'winecfg' from package 'wine1.6' (universe)
wimecfg: command not found
cmcanulty@Dell580s:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
cmcanulty@Dell580s:~$ wine PROGRAM
wine: '/home/cmcanulty/.wine' is a 64-bit installation, it cannot be used with a 32-bit wineserver.
cmcanulty@Dell580s:~$ 
```

---

### Post by #&amp;thj^% on 2017-12-31
There is a Typo "wimecfg
No command 'wimecfg' found, did you mean:"
Maybe try this instead 
```
winecfg
```
I'm on a newer version ATM but did not remember any problems with 2.12
```
wine 3.0rc4-1

```

---

### Post by cmcanulty on 2017-12-31
same error  

```
cmcanulty@Dell580s:~$ winecfg
wine: '/home/cmcanulty/.wine' is a 64-bit installation, it cannot be used with a 32-bit wineserver.
cmcanulty@Dell580s:~$ 

```

---

### Post by #&amp;thj^% on 2017-12-31
> **cmcanulty said:**
> same error  

```
cmcanulty@Dell580s:~$ winecfg
wine: '/home/cmcanulty/.wine' is a 64-bit installation, it cannot be used with a 32-bit wineserver.
cmcanulty@Dell580s:~$ 

```
What??: Error "wine is a 64-bit installation, it cannot be used with a 32-bit wineserver." wine should never point to winesever>>Just wine.

When: This occurs when there is a mixture of 32-bit and 64-bit files in a wine installation

Try now:
 ```
rm -r .wine/
 winecfg

```
One line at a time. ;)

---

### Post by cmcanulty on 2017-12-31
funny I did that before and it didn't work. Now wine will install exes but it is still missing from menu libra, thanks for all your help and Happy New Year!

---

