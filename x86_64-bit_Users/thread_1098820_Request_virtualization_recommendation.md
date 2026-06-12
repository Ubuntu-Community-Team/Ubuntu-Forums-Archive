---
title: "Request virtualization recommendation"
date: 2009-03-17
forum: x86 64-bit Users
---

### Post by TomB19 on 2009-03-17
I need to run XP in a virtual box on my Kubuntu x86-64 v8.10 system.

I have run vmWare in the past.  Now I hear about Virtual Box and others.

Would someone please recommend a virtualization platform to run 32 bit Windows on 64 bit Linux?  I would appreciate it.

By the way, I know about wine but can't run everything I need on it.


Thank you.  :)

---

### Post by mrsteveman1 on 2009-03-17
In my experience VMware has the best tools and probably the fastest hypervisor, parallels is pretty good too (they do have a Linux version). 

Virtualbox may be good, i have never used it on linux, i have used it on OS X though and it wasn't ready for real world use yet then (month or 2 ago).

---

### Post by cariboo on 2009-03-17
I installed Virtualbox from [here]("http://www.virtualbox.org/wiki/Linux_Downloads"), as the open source has some problems with proper nic drivers for 64-bit os's. You can run almost any OS in virtualbox, at various times I have had Win95, Win98, WinMe, XP, Vista and Windows 7 running in it. I currently have XP 32-bit, Vista 64-bit and Windows 7 64-bit setup.

Jim

---

### Post by linux4life88 on 2009-03-17
I run Virtual Box OSE on a 64 bit version on Ubuntu and have never ran into any problems running operating systems through it either. You should be fine.

---

### Post by inphektion on 2009-03-18
on my 64bit ubuntu i run 64bit virutal box with a 32bit vista and a 64bit windows 7 inside.  zero issues.  Virtual box is starting to get better than vmware on the desktop side.

---

### Post by euxneks on 2009-03-19
I highly recommend Virtual Box. It's easy to use, extremely free, there's an open source version, and you can get packages for ubuntu from the repos.
```

sudo apt-get install virtualbox-ose
```
:)

---

### Post by 3Miro on 2009-03-19
I use Virtual Box to run 32-bit XP under 64-bit Kubuntu 8.10. Never had any problems. I don't know if VM ware would have more features (such as directx support), but for that you are probably better off with wine.

You can use the OSE from the repositories, however, the OSE doesn't have USB support. IF you want to connect UBS devices to your virtual machine, go to the Virtual Box web-page and download the version from there (free but not open source).

---

