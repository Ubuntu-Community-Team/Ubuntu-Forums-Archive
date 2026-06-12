---
title: "virtualbox setup guide?"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by digisoft on 2008-04-26
Can someone point me to a good how-to for setting up virtualbox, I want to use it to run windows XP. Also, is there any limitations on the XP or windows apps when run in virtualbox?

---

### Post by thekat on 2008-04-26
I too am looking for some more info as to what packages are needed..

I built this box with 8 GIG of RAM so I **could do several**
Virtual Machines at once..

tk

---

### Post by pixel :-) on 2008-04-26
sudo apt-get install virtualbox-ose virtualbox-ose-modules-2.6.24-16-generic

put your self in the group vboxusers", reboot (or load the module vboxdrv,if you know the command)

You follow the built in wizard and you install the os of your dreams.

For programs in XP under virtuallbox.No 3D, speed penalty, some programs have anti reverse engineering tricks built in,and can guess that they are running in a virtual desktop,and refuse to start.

any way i think you prefer seeing this thread instead 
[http://ubuntuforums.org/forumdisplay.php?f=308]("http://ubuntuforums.org/forumdisplay.php?f=308")

:KS

---

### Post by caver1 on 2008-04-26
The above is true but if you want usb capability stay away from Virtualbox-ose. Go to Virtualbox web site and download their free non-ose version. Works great. Easy. 
caver1

---

### Post by OldGaf on 2008-04-26
I prefer the non-open source flavor....

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI")

Hopefully they will update for 8.04 soon.

---

### Post by digisoft on 2008-04-26
yeah, just noticed there is no 8.04 vrsion, will one of the other version work? I need USB.

Also, with the OSE version when I try and install windows it tells me no bootable media found. I know for a fact the cd boots and I know its looking at the right drive. Any ideas?

Digi

---

### Post by digisoft on 2008-04-26
I figured it out, even though the drive was mounted and I could access it, I had to mount it inside of virtualbox and then I was able to install XP with no problems. I'll have to wait and see if someone knows a way to install the other version of virtualbox on 8.04 so I can access my USB drives.

digi

---

### Post by seamuso on 2008-04-27
Here's what I'm running in hardy .. I haven't had any problems. 

virtualbox_1.5.6-28266_Ubuntu_gutsy_amd64.deb

Closed source version so I can have USB support.

---

### Post by digisoft on 2008-04-27
thanks, I'll give that a try

---

### Post by thekat on 2008-04-27
> **seamuso said:**
> Here's what I'm running in hardy .. I haven't had any problems. 

virtualbox_1.5.6-28266_Ubuntu_gutsy_amd64.deb

Closed source version so I can have USB support.

What OS(s) are you running in VirtualBox.?

I tried virtualbox-ose and tried to load Hardy-server but got some
weird error.. 

On my Gusty-32 bit box I could run:
- XP 
- OpenBSD 4.1 (randomly crashed)
- Gutsy-Server-32
- ClarkConnect 4.2
- SME (can't remember the version but it was Fall 2007)

thx
tk

---

### Post by inphektion on 2008-04-27
I had the virtualbox installed from gutsy and it wouldn't start in hardy.  I have the non ose version from the deb virtualbox gutsy.  I even tried an aptitude reinstall.  Then I did a remove and a clean install through aptitude and it popped up with:
The following NEW packages will be automatically installed:
  bridge-utils libsdl-ttf2.0-0 uml-utilities 

Once these installed from hardy repo's and the vbox reinstalled its all back up now.  Just my experience in case it helps someone...

---

### Post by lwvmobile on 2008-04-28
Hey guys, got virtualbox installed the general route using apt-get(the same mentioned in this thread) and got my virtual machine running. Problem is my virtual machines do not recognize keyboard input and after I capture the mouse and keyboard, I cannot uncapture my keyboard and mouse using right ctrl. I've hard virtualbox working great in the past, but for some reason when trying to install either Windows XP or Ubuntu 8.04 Server, I cannot use the keyboard and when captured, I basically cannot uncapture and just have to kill by xorg server via ctrl-alt-backspace. Any help or has anybody else had this issue?

Update:

OK, figured out my own issue. If you have support to enter complex characters enabled in Language Support, then the keyboard input doesn't work in Virtual Box. Luckily I don't need to use Virtual Box too often, just for testing, so I can just re-enable complex character input when I'm not using it.

---

### Post by digisoft on 2008-04-28
I installed the virtualbox from 7.10 with no problem, but I can't get the USB to work. I found instructions on uncommenting a few lines in a file, adding a line to fstab and restarting linux. I did that but still no USB in virtualbox with XP installed. Any ideas?

---

### Post by famous3warriors on 2008-04-28
You have to create usbusers and tick your <username> restart your computer and then you should be able to use your usb devices.

---

### Post by bluelamp999 on 2008-04-29
This totally worked for me in 7.10

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

Totally worked just now in 8.04 too!

---

### Post by sadohert on 2008-04-29
> **digisoft said:**
> Can someone point me to a good how-to for setting up virtualbox, I want to use it to run windows XP. Also, is there any limitations on the XP or windows apps when run in virtualbox?

I've had some solid success with virtualizing XP on Gutsy using the non-opensource version of VirtualBox.  The only points/snags I've encountered so far are:

-I wanted to use shared folders to store my music collection so that iTunes (in the guest XP OS) could access a location for mp3s that was totally visible to Gutsy (the host OS).  I was having this really annoying Blue Screen of Death issue whenever I tried to download a new track through iTunes, and ultimately I found a number of threads with other people having similar issues.  Apparently it's a known issue with the VirtualBox shared folders.  My solution was to do everything through a samba share on the host, that XP could see.  I believe this is a slower option, but it does what I need it to do.... as a side note, I originally tried Vista, and things seemed fine at first, but from what I read shared folders on vista don't work yet.
-I can't seem to get my blackberry to sync.  I setup the USB filter I"m supposed to setup for the Blackberry device, but when I went to connect I got an error message.  I'm not sure what I'm going to do at this point.

Thanks to virtualization I can get rid of all dedicated windows boxes in my house, and just open up VB to sync my iTUnes (and hopefully my Blackberry soon too).

---

### Post by AndThenWhat on 2008-04-29
I have been using both VBs all day trying to get my iPod touch to sync to no avail.  Upon doing so I have become familiar with both and here is what I found was best:

**Go to the virtualbox website to get VirtualBox PUEL (Which has USB): **
*[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)*

then click on **Binaries (all platforms)**

For Hardy and Gutsy, which most people have, just use the **Ubuntu 7.10** download.  Once downloaded, install the .deb.

Next, to enable USB, open a terminal and type:
```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

You need to find this section:
```
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
```

Once you find that section uncomment the lines so it looks like this:
```
#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
```

Now that that is done make sure you have a group called **vboxusers** and **usbusers** and that you are a member of those two groups.  You can do that by going to System>Administration>Users and Groups .

then you may need to restart your computer. Next, open VirtualBox and go to the USB settings for your Virtual Machine and tick the two checkboxes.  Then, plug in whatever you want to use with USB. After you turn USB on you have to add USB filters by clicking on the little green plus button and add your iPod or whatever.

**THE END**

PS. I am running a Windows Vista VM in VB 1.5.6 and it works very well. The only issue I found is that it detects my iPod Touch, but gives an error when trying to sync.

---

### Post by Stian on 2008-04-30
Hardy packages:
[http://www.virtualbox.org/download/1.5.6/](http://www.virtualbox.org/download/1.5.6/)

---

### Post by OldGaf on 2008-05-03
> **seamuso said:**
> Here's what I'm running in hardy .. I haven't had any problems. 

virtualbox_1.5.6-28266_Ubuntu_gutsy_amd64.deb

Closed source version so I can have USB support.

Yes, I am using that as well. Right now I just have XP in it.

---

### Post by Jenga-kun on 2008-06-04
> **pixel :-) said:**
> sudo apt-get install virtualbox-ose virtualbox-ose-modules-2.6.24-16-generic

put your self in the group vboxusers", reboot (or load the module vboxdrv,if you know the command)

You follow the built in wizard and you install the os of your dreams.

For programs in XP under virtuallbox.No 3D, speed penalty, some programs have anti reverse engineering tricks built in,and can guess that they are running in a virtual desktop,and refuse to start.

any way i think you prefer seeing this thread instead 
[http://ubuntuforums.org/forumdisplay.php?f=308]("http://ubuntuforums.org/forumdisplay.php?f=308")

:KS
How do I put myself in the vboxusers group?

---

### Post by eshant_engineer on 2009-09-30
> **AndThenWhat said:**
> I have been using both VBs all day trying to get my iPod touch to sync to no avail.  Upon doing so I have become familiar with both and here is what I found was best:

**Go to the virtualbox website to get VirtualBox PUEL (Which has USB): **
*[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)*

then click on **Binaries (all platforms)**

For Hardy and Gutsy, which most people have, just use the **Ubuntu 7.10** download.  Once downloaded, install the .deb.

Next, to enable USB, open a terminal and type:
```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

You need to find this section:
```
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
```


I could not found this section. The content i have in that file is -
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac
```

---

### Post by eshant_engineer on 2009-09-30
So what to do then to have USB support in virtual machine ?

---

### Post by tymek666 on 2009-09-30
> **eshant_engineer said:**
> So what to do then to have USB support in virtual machine ?
Just install the latest VB non-OS version follow this guide:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Works great, at least WinXp guest.

---

