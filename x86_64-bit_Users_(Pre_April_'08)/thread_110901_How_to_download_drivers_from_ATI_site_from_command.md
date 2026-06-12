---
title: "How to download drivers from ATI site from command line?"
date: 2005-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by nbhaskar on 2005-12-31
Hi,

I loaded Breezy AMD64 version 2 weeks ago and I keep getting the display error. When I changed "ati" to "vesa" in the config file, I keep getting blank screen while booting up. At this point I can not do any thing else but push the power button to reboot.

I would like to get the new drivers loaded for my ATI X700 graphics card from ATI site and try booting again. Currently I can not get the x server started and only command line available.

How to download drivers from ATI site from command line? Is there a way?

Any help would be appreciated.
:confused:

---

### Post by ruudiculus on 2006-01-01
What you can do is install *lynx* a command line internet browser. I've just tried it and browsing through websites works great. I could not download any driver file, but I'm sure lynx must be capable of downloading from a link.

I'll play around with lynx for a while now and come back when  know how to download a file (something with the letter 'd' :p) , okay?

---

### Post by ruudiculus on 2006-01-01
Well,

The lynx manual says that you might use cURL for downoading from https sites, so you might download and try that if the driver you're searching for is on a secure http site. If not you should be able to use lynx.

I'm wondering: why don't you just download the driver from the computer you're working on now (graphically, posting on this forum), burning it on a disc for use on the other computer?

Good luck!

---

### Post by ruudiculus on 2006-01-01
Once you know the URL of the file you want to download you can also use wget (which is installed by default). Therefore type:

```
wget "http://www.ati.com"
```

for example

---

### Post by acidlacedpenguin on 2006-01-01
I don't mean to hijack or anything but I found out that I have the same problem only with nvidia, so I guess wget and then the location of the file seems like it will work, I'll try it out on my machine and see what happens. . .

---

### Post by klett on 2006-01-02
Hi,

I'm a complete newbie, but I finally got my XWindows working. What I did was:

sudo -s
apt-get install xorg-driver-fglrx
fglrxconfig
startx
and it worked. Previously I've tried to configure it using dpkg-reconfigure but it didn't modify the /etc/X11/xorg.conf properly.
After checking that startx works, just reboot. You'll get an error message "Your session lasted 10 seconds" or something similar. Log in text-mode and delete .ICEauthority file in your /home/user and reboot.

---

### Post by nbhaskar on 2006-01-02
[QUOTE=ruudiculus]Well,

The lynx manual says that you might use cURL for downoading from https sites, so you might download and try that if the driver you're searching for is on a secure http site. If not you should be able to use lynx.

I'm wondering: why don't you just download the driver from the computer you're working on now (graphically, posting on this forum), burning it on a disc for use on the other computer?

Good luck![/QUOTE]

I took your advice and put the files in a CD-R. After booting up in breezy I went to /media/cdrom to look at the files. I could not see any files, ls -l reports 0 files.

I'm new to Linux, can somebody tell what am I doing wrong?

Once I figure out how to look at the files from cdrom, how do I install the ATI driver from the cdrom using apt-get?

thanks for all the help.
:D

---

### Post by nbhaskar on 2006-01-02
I'm not able to start synaptic since my x server fails all the time. Is there a way to install the driver I downloaded from the ATI site using wget from the command line?

thanks.

---

### Post by ruudiculus on 2006-01-03
You have to mount the cdrom. To do so go to the root and type:
```
cd /
mount cdrom
```

Now you should be able to view the cdrom contents by typing either:
```
cd cdrom
```

or

```
cd media/cdrom
```

To install things from your repositories you can use aptitude (the command line synaptics) Type:
```
aptitude
```

Good luck!

---

### Post by koverg on 2006-01-03
Did you try to change the driver name from "ati" to "radeon" in the xorg.config?
This solved my problem with ATI Radeon X700.

Cheers,

Gabor

---

### Post by nbhaskar on 2006-01-03
I'm getting the following error message when I boot breezy.

```
loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a
```

thanks for any help.

---

### Post by nbhaskar on 2006-01-03
[QUOTE=koverg]Did you try to change the driver name from "ati" to "radeon" in the xorg.config?
This solved my problem with ATI Radeon X700.

Cheers,

Gabor[/QUOTE]

I'm typing this from firefox running in Breezy AMD64 bit version.

I changed from "ati" to "radeon" in the xorg.config and it worked like a charm. I've been trying to make the system work for 3 weeks and whatever I tried did not work.
 
Thanks a bunch Gabor.
:D

---

### Post by koverg on 2006-01-04
[QUOTE=nbhaskar]
Thanks a bunch Gabor.
:D[/QUOTE]
You are welcome!
I am also new to Ubuntu and reading this list helped me a lot. I am happy I can return something.

Gabor

---

### Post by skillzdatkillzholmes on 2006-01-04
Hi!

I've got a weird problem, I also sent this to the Debian Bug Reporter email server:

Package: Debian-31r0a-amd64-binary
Version: 2.6.11.6

My problem is that when I boot Debian 64 from GRUB, after it's done loading everything, an error message saying "I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

I select yes and the following comes up:

XFree86 Version 4.3.0.1 (Debian 4.3.0.dfsg.1-14sarge1 20050915192417
[email]root@bester.farm.ftbfs.de[/email])
Release Date: 15 August 2003
X Protocol Version II, Revision 0, Release 6.6
Build Operating System: Linux 2.6.11.6-vs195-farm1.0 x86_64 [ELF]
Build Date: 15 September 2005

My system contains the following hardware:
Motherboard: Asus A8N-E nForce 4 Ultra
CPU: AMD Athlon 64 3000+ 1998MHz
RAM: OCZ Premium-Series 1gb (2x512mb) 2 DIMMS Dual Channel PC3200 DDR400
Video: Asus Extreme N6600 Silencer (nVidia GeForce 6600 256mb)
HDD: Maxtor 250gb IDE HDD (6Y250P0)
Optical: Pioneer DVR-110D DVD-RW
Monitor: NEC MultiSync 75

What led to this was a Debian "Sarge" AMD64 installation from DVD. I had mostly defaults, with an nForce 2 Ethernet Driver instead of an nForce 4 since I didn't have a floppy and it was the only nForce driver there. (It worked though, it downloaded everything it needed and setup the Network Config successfully) I chose all of the packages available (except for the manually select packages) and when it came to it, I select non-LCD mode, with an "nv" display driver and 1280x1024x60hz resolution/refresh rate. Finally the installation finished and the above problem came to be, it also turns out that my video card is known to have problems with Debian's X Server, so they made a driver that contains a work-around. It is called NVIDIA-Linux-x86_64-1.0-8178-pkg2.run now I only have one problem, installing it. I have no idea how Linux command works, I've only worked with DOS Command *slaps self* so if someone could help me out that would be great, thanks once again in advance.

Skillz

---

### Post by ruudiculus on 2006-01-05
As root, set the permissions right of the file:
```
su
[type you root password]
chmod 777 NVIDIA-Linux-x86_64-1.0-8178-pkg2.run
```

Then run the file by typing:
```
./NVIDIA-Linux-x86_64-1.0-8178-pkg2.run
```

I think you should run the file from a location where you also want to install it, in case the file creates directories etc. in the process.

---

