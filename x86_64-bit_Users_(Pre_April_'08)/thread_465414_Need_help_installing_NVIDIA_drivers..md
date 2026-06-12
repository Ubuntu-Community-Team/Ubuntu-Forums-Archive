---
title: "Need help installing NVIDIA drivers."
date: 2007-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by teknic111 on 2007-06-05
I just put a clean install of ubuntu (x86-64) on my laptop.  After installing the video drivers Gnome will not start.  Here is the exact list of things I did up to the point of installing the video drivers...

1) Install Ubuntu 7.04 (x86-64).
2) Ran software update.
3) Installed build-essential
4) Installed NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
5) Rebooted system and got error message saying...
         Failed to start the X server.  It is likely that it is not set up correctly.  The X server is now disabled.

I would also like to note that these are the same steps I used when installing Kubuntu on the same laptop.  That install went perfectly.  I'm not sure why this one is not.  Any help you guys can offer would be greatly appreciated.  Thanks.

---

### Post by loserboy on 2007-06-05
I can't help you fix your problem, but envy is an awesome script that can (hopefully)

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Alberto is also really helpful if you have any questions.

I've only used envy on a new system before having tried to install anything on my own, but may still work ok in your case

---

### Post by teknic111 on 2007-06-05
I just did another clean install of Ubuntu.  I tried installing the drivers with Envy, but am still experiencing the same problem with X not starting upon reboot.  Now I'm going to try and do it with the 32 bit version of Ubuntu.  We'll see if that makes any difference.

---

### Post by loserboy on 2007-06-06
sorry to hear that...  if you post a comment on Alberto's blog he's very good about answering questions when he gets time, I hate to see you go back to 32-bit empty handed

btw what's the card model?

---

### Post by teknic111 on 2007-06-06
I just tried installing the drivers on 32bit Ubuntu, and they won't take either.  So I've had no choice but to go back to Kubuntu 64 (which is not bad at all).  Its just funny that the same drivers work on Kubuntu and not Ubuntu.

My Laptop is a Lenovo 3000 N100.  It uses a Geforce Go 7300.

---

### Post by dabl on 2007-06-06
> **teknic111 said:**
>  Its just funny that the same drivers work on Kubuntu and not Ubuntu.


It's funny all right, but I can confirm it's true.  For my GeF 7900 GS PCI card, Envy works great on Ubuntu 64-bit, but the nvidia-glx-new package works better on Kubuntu 32-bit, all on the same hardware platform.  Have you tried the nvidia-glx-new package?  Make sure you have first installed the package linux-restricted-modules-`uname -r` and don't install any other nvidia package except nvidia-glx-new.  If others are installed, remove them first.

Your GO 7300 should run fine with the -9755 driver.  :)

---

### Post by capecove on 2007-06-06
Well, I've got Ubuntu 7.04 64 bit and an NVIDIA based card but it's a desktop so can't help you there. I didn't have any problem with it myself so I know it must work for at least some NVIDIA equipment. There is a forum that may be of help...

[http://www.nvnews.net/vbulletin/showthread.php?t=90079](http://www.nvnews.net/vbulletin/showthread.php?t=90079) should get you going in the right direction if we can't help you here.

---

### Post by LeftShift on 2007-06-06
I've had moderate luck getting the linux drivers for my GeForce 440MX working. Theres alot of confusion here.

If you xserver wont restart, theres no need to reinstall the ubuntu to get it working again. Before you go messing with you video drivers, make make a backup copy of you xorg.conf file:

# sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Once thats done, you can always restore the backup and boot using the vesa drivers (assuming they worked for you in the first place)

As far as I know there are 4 different nvidia drivers that may be the correct one for your card. Some nvidia cards have very limited support and require the legacy drivers (mine for instance). I had to reboot alot before I found the one that worked for my system.

From here you can:

1.) install the drivers yourself via the package manager

You can install any of the (4?) restricted nvidia drivers, from the package manager. Do a search for packages named nvidia. And youll get a list of all the glx drivers you can install. Depending on your card, you either have to install the legacy driver, the stable driver, or the new driver. it appears that only one of these drivers can be installed at any given time.

Once installed they can be enabled in the restricted drivers manager program. Once enabled restart. If you computer faisl to start X, you can from the GRUB loader load up recover mode and from terminal and restore your backup xorg.conf file

#sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Don't get it backwards, or you'll loose your backup for good. and you'll need to run dpkg-reconfigure to reconfigure your video card settings.

Or, 2.) run ENVY, a program which automatiicaly configures you nvidia drivers, settings and xorg.conf file for you.

BTW. The first time I ran Evny I encountered permissions problems. I had to login as root before envy would install the drivers correctly.

---

### Post by Sockerdrickan on 2007-06-06
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALL, JUST PRESS ENTER ALL THE TIME

sudo /etc/init.d/gdm start

---

### Post by fakie_flip on 2007-06-09
> **Tux0r said:**
> GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALL, JUST PRESS ENTER ALL THE TIME

sudo /etc/init.d/gdm start

After

```
sudo rm /etc/init.d/nvidia-*
```

You should do this.

```
chris@ubuntu:/etc/init.d$ sudo update-rc.d nvidia-kernel remove
 Removing any system startup links for /etc/init.d/nvidia-kernel ...
   /etc/rc1.d/K20nvidia-kernel
   /etc/rc2.d/S20nvidia-kernel
   /etc/rc3.d/S20nvidia-kernel
   /etc/rc4.d/S20nvidia-kernel
   /etc/rc5.d/S20nvidia-kernel
chris@ubuntu:/etc/init.d$ 
```

---

### Post by Sockerdrickan on 2007-06-09
Seems to work anyway :P

---

### Post by fakie_flip on 2007-06-09
> **Tux0r said:**
> GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALL, JUST PRESS ENTER ALL THE TIME

sudo /etc/init.d/gdm start

Doing that command will remove the kernel. Why? The package is conflicting with the driver I downloaded from nvidia.com, but if I remove the package, the linux kernel gets removed as well. I say it is conflicting because when I reboot my computer, x wont start. I can get it to start by doing these commands.

```
sudo modprobe -r nvidia
sudo modprobe nvidia
sudo /etc/init.d/gdm restart
```

This is really frustrating and bugging me. I hope someone can help.

```
chris@ubuntu:~$ sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
Package nvidia-settings is not installed, so not removed
The following packages will be REMOVED:
  linux-generic* linux-restricted-modules-2.6.20-16-generic*
  linux-restricted-modules-generic* nvidia-kernel-common*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 48.9MB disk space will be freed.
Do you want to continue [Y/n]?
```

linux-generic is the linux kernel, and the apt wants to remove it if I remove ubuntu's nvidia package.

---

