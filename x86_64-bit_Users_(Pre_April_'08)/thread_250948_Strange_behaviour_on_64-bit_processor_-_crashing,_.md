---
title: "Strange behaviour on 64-bit processor - crashing, ignoring keystrokes, apps closing.."
date: 2006-09-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by h6w on 2006-09-04
Hello,

I installed a fresh install of Ubuntu 64-bit a couple of weeks ago after upgrading my computer.  

Since installing it I have had strange problems with using Ubuntu.

e.g.  
- Firefox ignores the enter key when in the web search bar.
- Apps close sometimes immediately after showing the splash screen (OpenOffice in particular)
- The whole system crashes when logging out/shutting down/restarting (goes to text mode with 3 white ASCII text blocks on the screen.

I have tried a memory test which came up clean.

Your help is greatly appreciated.

Cheers,
Tudor.


Here are the specs:

Intel Pentium 4 Processor 630 3GHz, 800 FSB, 2M L2 Cache EM64T LGA775
Asus P5P800-MX Motherboard
80GB IDE disk

Mount info:
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-amd64-generic/volatile type tmpfs (rw)
/dev/hda3 on /home type xfs (rw)
/dev/hda1 on /media/windows type vfat (rw,utf8,umask=007,gid=46)

---

### Post by SlCKB0Y on 2006-09-05
> **h6w said:**
> Hello,

Intel Pentium 4 Processor 630 3GHz, 800 FSB, 2M L2 Cache EM64T LGA775

lrm on /lib/modules/2.6.15-26-amd64-generic/volatile type tmpfs (rw)


I dont know much on the subject, but could it be because you are running an AMD optimised kernel on intel hardware?

---

### Post by John.Michael.Kane on 2006-09-05
@h6w if your still having this issue. 

Please try installing this kernel:
```
sudo aptitude install linux-amd64-xeon
```

It will install all the dependent files in the process,

reboot using this kernel. post back any issues after re-loging on.

---

