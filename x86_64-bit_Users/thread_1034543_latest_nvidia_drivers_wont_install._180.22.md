---
title: "latest nvidia drivers wont install. 180.22"
date: 2009-01-08
forum: x86 64-bit Users
---

### Post by spencerhc on 2009-01-08
It will not install from the nvidia installer or repositories. 

Through Nvidia I get a message saying that this file /.../.../extensions/libglx.so is missing and the install of it does not complete. Upon reboot I get low graphics mode. 177 is still working fine for me.

advice?

if you need specifics for the error messages i will go through the installer and write them down.


running 8.10 with latest kernel.

NVIDIA XFX 8800gt 512mbs ddr3

---

### Post by ibbuntu on 2009-01-09
Same problem here. I ran the installer successfully but when I restarted X I got an error message saying that it failed to load the NVIDIA module. I have an 8600GT.

---

### Post by Liviu-Theodor on 2009-01-09
For me, it was the driver 177 that did not work, and described [here]("http://ubuntuforums.org/showthread.php?t=993767") a solution. Maybe you will find the advice there useful, and install what works for you.

---

### Post by dadozgb on 2009-01-09
Try to extraxt *.run archive and compile module manualy. Probably you don't have kernel source of running kernel and module didn't compile. Run ./*.run --help for list of avaliable options.

---

### Post by spencerhc on 2009-01-09
> **Liviu-Theodor said:**
> For me, it was the driver 177 that did not work, and described [here]("http://ubuntuforums.org/showthread.php?t=993767") a solution. Maybe you will find the advice there useful, and install what works for you.

I am not wanting to use the propriety drivers. I want to use the nvidia drivers from the nvidia installer because i like being able to use nvclock/nvidia-settings

---

### Post by monkeyboy00 on 2009-01-09
A point that may help in your search for a solution. First, the Nvidia driver you are trying to install is a proprietary driver.
 A couple of other suggestions, first check the Nvidia forum site for help and be prepared to provide a list of your hardware, copies of any error messages you receive and copies of your various configurat5ion files. Sounds like a lot to provide but it will save you time in the long run. Good Luck

---

### Post by punischdude on 2009-01-09
> **spencerhc said:**
> It will not install from the nvidia installer or repositories. 

Through Nvidia I get a message saying that this file /.../.../extensions/libglx.so is missing and the install of it does not complete. Upon reboot I get low graphics mode. 177 is still working fine for me.



I got it working by doing following steps:

1. Stop gdm and unload nvidia module: ```
sudo /etc/init.d/gdm stop && sudo modprobe -r nvidia
```

2. Uninstall previous driver: ```
sudo sh nvidia.run --uninstall
```

3. Extract the new driver files: ```
sudo sh nvidia.run -x
```

4. Copy and link libglx.so.180.22: 
```
sudo cp NVIDIA-Linux-x86_64-180.22-pkg2/usr/X11R6/lib/modules/extensions/libglx.so.180.22 /usr/lib/xorg/modules/extensions/

sudo ln -s /usr/lib/xorg/modules/extensions/libglx.so.180.22 /usr/lib/xorg/modules/extensions/libglx.so
```

5. Run Installer: ```
sudo sh nvidia.run
```

6. Load nvidia module and start gdm again: ```
sudo modprobe nvidia && sudo /etc/init.d/gdm start
```

7. Enjoy!

---

### Post by spencerhc on 2009-01-09
I will try that asap when i can get to my box. thanks punischdude.

I apologize monkey boy that I did not have the time in my life to get everything done to your satisfaction. And I did check nvidia forums.

---

### Post by spencerhc on 2009-01-09
I followed instructions word for word. The file libglx.so.180.22 is in the correct location but I get the same error.


I renamed libglx.so.180.22 to just libglx.so to make it easier. I still need something called libglx.so.xserver-xorg-core to go in /usr/bin/nvidia/

---

### Post by paulisdead on 2009-01-09
I've had the same problem with the official 180.22 drivers, but strangely enough, all the betas have worked well for me.  I've been on 180.17 for a little while now, and not had any issues with that driver.

I haven't had time to try any of the suggestions in this thread, and probably won't for a bit.  I get to have lots of fun with microsoft exchange tonight and tomorrow.  Grrr... Exchange...

---

### Post by Trueno22 on 2009-01-10
Did you guys pick the pckg2 driver?  I did and got the libgblahbalh.so message.  I installed the 32bit compatibility libraries via synaptic and reinstall the driver.  NO error messages after that.

---

### Post by spencerhc on 2009-01-10
beta drivers work. Posts in nvdia forums are popping up. 


(ps. I hate Microsoft their stupid BETA dl site wont let me dl WDOS 7)

---

### Post by oobuntoo on 2009-01-10
Following instruction from here should get the driver to work:

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Here is what I did:

1. Get into console mode with Ctrl+Alt+F1

2. Stop GDM or KDM with 
sudo /etc/init.d/gdm stop or  
sudo /etc/init.d/kdm stop

3. Edit xorg.conf to use "nv" driver:
sudo nano /etc/X11/xorg.conf

4. Uninstall previous nvidia driver(my was 180.16):
sudo sh NVIDIA-Linux-x86-180.16-pkg0.run --uninstall

5. Get back into GUI destop:
sudo /etc/init.d/gdm start or  
sudo /etc/init.d/kdm start

6. Uninstall completely, through Synaptic, linux-restricted-modules and linux-restricted-modules-common (and whatever else that gets remove along with them).

7. Remove these files if you have them:
sudo rm /etc/init.d/nvidia-glx 
sudo rm /etc/init.d/nvidia-kernel

8. Repeat steps 1 and 2

9. Install the new driver (180.22):
 sudo sh NVIDIA-Linux-x86-180.22-pkg1.run

10. Edit xorg.conf to use "nvidia" driver:
sudo nano /etc/X11/xorg.conf

11. Get back to GUI destop:
sudo /etc/init.d/gdm start or  
sudo /etc/init.d/kdm start

---

### Post by loomsen on 2009-01-10
Make sure you have the pkg xserver-xorg-core installed.
libglx.so is part of this package.

Then stop gnome and run the steps above.

You may use any package to clean old installs, actually this is a part of the installation process anyway.

---

### Post by hexilum on 2009-01-14
Doesn't work.

> **punischdude said:**
> 
1. Stop gdm and unload nvidia module: ```
sudo /etc/init.d/gdm stop && sudo modprobe -r nvidia
```

* Stopping Gnome Display Manager...
FATAL: Module nvidia not found

> **punischdude said:**
> 
2. Uninstall previous driver: ```
sudo sh nvidia.run --uninstall
```

sh: Can't open nvidia.run

> **punischdude said:**
> 
3. Extract the new driver files: ```
sudo sh nvidia.run -x
```

sh: Can't open nvidia.run

> **punischdude said:**
> 
4. ```
Copy and link libglx.so.180.22: 
sudo cp NVIDIA-Linux-x86_64-180.22-pkg2/usr/X11R6/lib/modules/extensions/libglx.so.180.22 /usr/lib/xorg/modules/extensions/
```


cp: cannot stat `NVIDIA-Linux-x86_64-180.22-pkg2/usr/X11R6/lib/modules/extensions/libglx.so.180.22-pkg2/usr/X11R6/lib/modules/extensions/libglx.so.180.22': No such file or directory

---

### Post by spencerhc on 2009-01-14
yea his post pretty much didn't work/help at all, neither did his symbolic links

---

### Post by hexilum on 2009-01-14
Ok I was able to successfully install 180.22, I used this method:

1.)```
cd ~/Desktop
```
2.)```

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-4.4.0 xserver-xorg-dev
```
3.)```
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
```
4.)```
sudo rm /etc/init.d/nvidia-*
```
5.)```
sudo /etc/init.d/gdm stop
```
6.)```
sudo sh NVIDIA-Linux-x86_64-180.22-pkg2.run
```
7.)```
sudo /etc/init.d/gdm start
```

---

### Post by gdp77 on 2009-01-18
when canonical is going to add the new driver to the repositories, so we can have a normal and painless update to 180.22 ?

---

### Post by mgranet on 2009-01-18
> **gdp77 said:**
> when canonical is going to add the new driver to the repositories, so we can have a normal and painless update to 180.22 ?

9.04

---

### Post by moneymaker on 2009-01-18
after many failed attempts I managed to install by removing the nvidia module before running the install script
```

sudo /etc/init.d/gdm stop
sudo rm -f /lib/modules/`uname -r`/kernel/drivers/video/nvidia.ko
sudo sh NVIDIA-Linux-x86_64-180.22-pkg2.run
sudo /etc/init.d/gdm start

```

this worked for me :)

---

### Post by paulisdead on 2009-01-18
I finally got around to having time to troubleshoot my own stuff.  I tried everything else mentioned in this thread and it didn't work for me.  I found another nvidia.ko module buried in the /lib/modules directory that was being loaded when modprobe nvidia was run, instead of the 180.22 module.  I had removed everything to do with restricted drivers and nvidia via apt-get, and run --uninstall on the nvidia drivers, and it still didn't clean up that module.  I deleted it and since it probes the right module now, all works.  I found it by doing

find /lib/modules -iname nvidia*

I think it was in a DKMS folder somewhere in the running kernel for me.  I figured out something wasn't right when I looked at dmesg, and it complained that the module was still 17x but the rest of the software was 180.22.

---

### Post by moneymaker on 2009-01-18
I think you're right paulisdead.

Now I remember I had removed every nvidia.ko file inside the running kernel module directory. Something like that should work for everybody:

```

sudo /etc/init.d/gdm stop
k=`uname -r`
sudo rm -f `find /lib/modules/$k -iname nvidia.ko`
sudo sh NVIDIA-Linux-x86_64-180.22-pkg2.run
sudo /etc/init.d/gdm start
```

---

### Post by leemstradamus on 2009-01-21
Total noob here, I downloaded the 180.22 drivers to my desktop and I have no freaking clue how to install them. I have used the auto update feature to get the 177 drivers but that always leads to me being unable to have the gui when I restart which will make me have to reload linux. I am getting quite frustrated in this seeing that this is my 5th or 6th time reloading 8.10! Any help would be appreciated.

---

### Post by BGFG on 2009-01-21
> **leemstradamus said:**
> Total noob here, I downloaded the 180.22 drivers to my desktop and I have no freaking clue how to install them. I have used the auto update feature to get the 177 drivers but that always leads to me being unable to have the gui when I restart which will make me have to reload linux. I am getting quite frustrated in this seeing that this is my 5th or 6th time reloading 8.10! Any help would be appreciated.

This is basically what you need but first i suggest you open synaptic, search 'nvidia' and remove all installed nvidia drivers.

Then:

1) Locate and uninstall your distro NVIDIA drivers (You can list drivers using these commands: ```
dpkg -l | grep -i nvidia 
```

(Debian/Ubuntu) OR in RPM based distro: ```
rpm -qa | grep -i nvidia
```

2) Locate and remove all nvidia.ko files in /lib/modules


NVIDIA DRIVER INSTALL:

1) ctrl alt f1
2) ```
sudo etc/init.d/gdm stop
```
3) ```
 cd Desktop
``` if you saved the 180.22 driver installation package to the desktop

4) ```
sudo sh ./nvidia....-linux.run
```
5) ```
sudo etc/init.d/gdm start
```

Incase of xserver errors:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
Will get you back to a working graphical desktop

---

### Post by stchman on 2009-01-21
> **spencerhc said:**
> It will not install from the nvidia installer or repositories. 

Through Nvidia I get a message saying that this file /.../.../extensions/libglx.so is missing and the install of it does not complete. Upon reboot I get low graphics mode. 177 is still working fine for me.

advice?

if you need specifics for the error messages i will go through the installer and write them down.


running 8.10 with latest kernel.

NVIDIA XFX 8800gt 512mbs ddr3

If the 177 drivers work why try the 180.xx drivers?  You have an 8800GT and those drivers are probably not going to give you a performance increase.

I would stick with the drivers in the repositories.  I have an 8800GT on Hardy and the 169.12 drivers run the card very well.

---

### Post by godfree2 on 2009-01-21
there appears to be no ubuntu nvidia packages for kernel 2.6.27-x only for 2.6.24-x
am I correct?

---

### Post by 4levels on 2009-01-31
@oobuntoo & hexilum
Great tutorial! 

I managed to get the driver 180.22 permanently installed on Ubuntu 8.04 2.6.24-23.  It was running before but after every reboot X started in low-graphics mode.  I didn't had to reinstall the driver every time, I just needed to run the installer, accept the license and then abort on the warning that a previous driver will be uninstalled.  This somehow fixed my kernel module or X settings and I could start X properly again.  This annoying issue (as X tries to start 3 times initially before showing you the configure dialog) is now soved thanx to you ;-)

I find the thing with Ubuntu that configuration goes maybe a bit too easy, coming from gentoo..

Thanx a lot!

---

### Post by spencerhc on 2009-01-31
helium gets a cookie, you guide works

---

### Post by TheLions on 2009-02-07
i tried installing the new driver and when i kill gdm and run
[HTML]sudo su
./NVIDIA-Linux-x86_64-180.22-pkg2.run [/HTML]
i get:
[HTML]
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 180.22...........................................................................................................................................................
./NVIDIA-Linux-x86_64-180.22-pkg2.run: 864: ./nvidia-installer: Permission denied
[/HTML]

please help!

---

