---
title: "Flip/flop Ubuntu kernels x86/X64?"
date: 2007-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by mcook2 on 2007-06-20
Well, this might be rather a silly question, but I want to run various virtualization tools like VirtualBox and Parallels workstation and I keep bumping into things not running on AMD64 with X64 kernel, so ...

If I am running a x64 kernel, can I compile myself an x86 kernel and boot and run it successfully off the same partition to get around the problem? I'd like to avoid having to install and boot Feisty x86 off another partition, and having to reload all the apps I have already installed and configured. 

If this is in fact a complete "non-starter", could some kind soul enumerate the technical reasons for me?  I suspect it's to do with all those "wrappers" and different versions of libs, but what about making a way to  flip/flop those folders and/or files during the boot process, say linking /usr/lib to either a /usr/libx86 or /usr/libx64 in order to fake it out?

---

### Post by incubus on 2007-06-20
mcook2,

I don't think there's a simple way of going from x86_64 to i386.  It's not just a matter of switching the /lib directories, the issue is that pretty much everything in your system is compiled in 64 bit.  Converting to 32 bit would be like having both a brain surgery and transplant of all organs at the same time, if you pardon the poor analogy.  Probably the few things that you can keep are the config files.  Other than that, you would be overwriting lots of files, which may simply make your system crash in the process.

It may not be impossible, but it's just that I don't recommend you try it at home.  Since you're practically reinstalling the whole system, it's better to backup the whole partition and fresh-install Ubuntu i386 on it.

incubus

PS: You can also tell us the issues you're having and we can try to help.  But it seems that you've made up your mind already.  I haven't tried VirtualBox, but I had VMware server and KVM working flawlessly a while ago in 64 bit.

---

### Post by Cappy on 2007-06-20
Tao help us clear up this thread before Kilz gets here =P

All i386 programs work on AMD64, don't be fooled.

Both programs you want:
[http://virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb](http://virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb)
[http://www.parallels.com/load/5](http://www.parallels.com/load/5)

Search in the AMD64 section next time (Change to the AMD64 section and then search in the top right corner).

Parallels is 32-bit only so you'll have to
```
sudo dpkg --force-architecture -i packagenamehere
```

---

### Post by mcook2 on 2007-06-20
incubus and Cappy,

Thankyou for your replies -  will check out what Cappy suggests - probably tonite as it's a sunny day here (finally!) and I have it off.

mcook2

---

### Post by mcook2 on 2007-06-21
Ya, so I reinstalled VirtualBox with that amd64 package - same results - it might be running 64-bit but it doesn't support 64-bit VMs yet - NP -  I'm just ahead of the wave for a change - it feels weird but i'll get over it.

Parallels failed to compile - problem I was having earlier, also with Parallels-2-2.2164-lin-en.deb.bin referenced elsewhere -  maybe I'll futz some more with that later, but it's also not a big deal for me if I don't get it running - "virtual schmertual" - I get quite enough excitement running natively.

I love my Festy AMD64 system, 

TY, MC

---

