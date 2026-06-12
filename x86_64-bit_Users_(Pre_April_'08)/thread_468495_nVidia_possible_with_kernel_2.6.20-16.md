---
title: "nVidia possible with kernel 2.6.20-16 ?"
date: 2007-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by aikishugyo on 2007-06-08
Hi all, I've been using Ubuntu Dapper/Edgy/Feisty with nVidia, and it has always just "worked" with the restricted modules installed. However, with the 2.6.20-16 from, let me see, this week Monday or so, generic kernel, there do not seem to be such modules.

Therefore, I used module-assistant to build the nVidia module and install it. That process worked fine, no error messages about GPL variables like on my Debian system(!). But, when I try to start the X server (after rebooting) I get an error that there is no nVidia module loaded. I tried modprobe, and find that there is an error loading the nVidia module. Very strange.

I could not find any thread on the 2.6.20-26 kernel. Any known issues with nVidia here?

---

### Post by Cappy on 2007-06-09
Here is my small installation script:
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```

I'm using "2.6.20-16-generic". I think you might be missing "linux-restricted-modules-`uname -r`" - I got that error yesterday when reinstalling my Ubuntu and that fixed it. Sometimes after running that code X still fails to load but a 
```

sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```
always fixes it for me.

This assumes that you have don't use a legacy video card.

You might also consider Envy:
[http://ubuntuforums.org/showthread.php?t=432056](http://ubuntuforums.org/showthread.php?t=432056)

---

### Post by Sockerdrickan on 2007-06-09
If you want to install latest unstable from nVidia, go get it and

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

### Post by Unit01 on 2007-06-09
I've tried using the .16 kernel with the nvidia-glx-new and the one from nvidia.com but i just couldn't get it to work.
The errors were
driver mismatch, that the one in the driver and kernel(not sure if said kernel) was the same
and to check if the driver was correctly installed.
I had already disabled the nv module and my xorg.conf was configured for nvidia
So now i'm running on the .15 kernel and at least got x to work, now i hope to get 3d acceleration again. And i've installed the nvidia-glx-new again

---

### Post by steveneddy on 2007-06-09
Don't forget that in order to install new video drivers, one must uninstall the old drivers first.

There is a great driver in the repos

```
nvidia-glx-new
```

this is the 9755 nvidia driver that seems to work very well on my lappie.

I have a geforce 7600 GO w/ 256 MB RAM that smokes with this driver.

I put a thread about how to upgrade to the new driver through Synaptic [here]("http://ubuntuforums.org/showthread.php?t=464540").

My kernel version is 2.6.20-16-generic.

---

