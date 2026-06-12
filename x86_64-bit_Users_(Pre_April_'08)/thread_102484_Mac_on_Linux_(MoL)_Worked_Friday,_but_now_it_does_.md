---
title: "Mac on Linux (MoL) Worked Friday, but now it does not"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by MonolithTMA on 2005-12-12
Greetings all,

Mac on Linux worked fine on Friday, but this morning when I tried to run it, I get the following:

```
monolith@ubuntu:~$ startmol --osx
Mac-on-Linux 0.9.70 [Jul 23 2005 19:20]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Loading Mac-on-Linux kernel module:
FATAL: Module mol not found.
====================================================================
  Failed to load the Mac-on-Linux kernel module -- please install
  mol-modules-source and build your own, or find a binary package
  providing mol-modules for your running kernel.
====================================================================

```

I followed the MaconLinuxHowto -Ubuntu wiki again, to no avail.

Any ideas?

Thanks in advance! :)

---

### Post by ssam on 2005-12-12
have you updated you kernel since it worked?

does it work if you run it with sudo?

---

### Post by MonolithTMA on 2005-12-12
I have not updated my kernel since I installed.

I get the same output if I run it with sudo.

The following is interessting and I'm not sure if it's correct. It looks to my newbie self that I have two kernels?

```
monolith@ubuntu:/lib/modules$ ls
2.6.12-10-powerpc  2.6.12-9-powerpc
```

Everything I did seemed to be for  2.6.12-9-powerpc.

---

### Post by MonolithTMA on 2005-12-14
Hmmmm...when I do a *uname -r* I get:
```
monolith@ubuntu:/usr/src$ uname -r
2.6.12-10-powerpc
```
But when I do *sudo debian/rules binary-mol-modules* I get:
```
monolith@ubuntu:/usr/src/modules/mol$ sudo debian/rules binary-mol-modules
dh_testdir
dh_testroot
dh_installdocs
dh_installmodules
dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_gencontrol
dh_md5sums
dh_builddeb --destdir=/usr/src/linux-headers-2.6.12-10-powerpc/..
dpkg-deb: building package `mol-modules-2.6.12-9-powerpc' in `/usr/src/linux-hea ders-2.6.12-10-powerpc/../mol-modules-2.6.12-9-powerpc_0.9.70+ubuntu0_powerpc.de b'.
```
Doing an *ls* gets me:
```
monolith@ubuntu:/usr/src$ ls
linux-headers-2.6.12-10          modules
linux-headers-2.6.12-10-powerpc  mol-modules-2.6.12-9-powerpc_0.9.70+ubuntu0_powerpc.deb
linux-headers-2.6.12-9           mol-modules.tar.gz
linux-headers-2.6.12-9-powerpc   rpm
```

It looks to me like it's building it for the wrong kernel, I'm afraid to try uninstalling the 2.6.12-9-powerpc in case that would hose my system even though *uname -r* reports 2.6.12-10-powerpc as the kernel I am using.

Any ideas? :confused:

---

### Post by ssam on 2005-12-14
its a good idea when you install a new kernel that you hang on to the old one until you no that the new one works (because its easy to build unbooting kernels). apt new removes old kernels, just set the new one to the default, and leaves the old one as a boot option.

if its booting 2.6.12-10 then you dont need to keep 2.6.12-9 installed.

if you can't get mol to build modules for 2.6.12-10, then maybe removing 2.6.12-9 and trying again will help.

you might want to do a backup first if you are scared of ubuntu not booting.

---

### Post by MonolithTMA on 2005-12-14
Thanks I will make an attempt to remove it and start again. I'll post here with the results. Aside from little quirks, like this one, and the sound and video card issues, I'm just loving Ubuntu. :)

---

### Post by trash on 2005-12-14
with mol from synaptic and os 10.3 i was able to get sound working with a few minor tweaks... in the molrc.sound file:
change alsa to oss, and
make sure startboing.enabled:     yes

everything else is commented out with #

the sound isn't perfect but it worked for me... there is a patch for sound but I couldn't find any info to help installing it so i'll wait for dapper and hope it's fixed.
good luck

---

### Post by MonolithTMA on 2005-12-15
Got it!

I totally removed all traces of MoL from my system. I removed the 2.6.12-9-powerpc kernel. i decided to ugrade the kernel to the 2.6.12-10-powerpc-smp so I can use both processors in my system. I followed the intructions to install [MoL]("https://wiki.ubuntu.com/MacOnLinuxHowto"), including this part:
> If you get mol module not found errors, try insmodding it manually

```
insmod /lib/modules/2.6.(your kernel version)-powerpc/misc/mol.ko
```

But I had to insmod in sudo. It worked like a charm! :) 

The only thing is that I can't see the Mac HD that I have mounted in Ubuntu, it's my main drive, it has Tiger on it, it's not the drive that MoL boots to though. I'll figure it out.

Thanks for everyone's input! :)

---

### Post by lusepuster on 2005-12-26
OS X run through MOL will not see any partition that's mounted in linux. Thats apita, but them again, just having a tool like MOl is sooooooooo kewl! :D

---

### Post by MonolithTMA on 2005-12-26
You just have to tell it to mount the drive. The only drive I can't see in MoL is the main Linux drive. I have all the ones with my files on them showing up.

---

