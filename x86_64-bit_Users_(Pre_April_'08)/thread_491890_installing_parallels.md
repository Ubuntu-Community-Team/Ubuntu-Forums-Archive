---
title: "installing parallels"
date: 2007-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by carniolus on 2007-07-04
I'm trying to install parallels on my feisty machine., but I always get an error when running parallels-config:

```
    
 Compiling Parallels Workstation 2.2 drivers...

Can not compile and/or link drivers. Read /usr/lib/parallels/doc/INSTALL
and follow instructions specified in this document.

Compilation log is available at /usr/lib/parallels/comp.log.7718.error

```

Compilation log is in attachment.

Please help....

---

### Post by dionysian_mind on 2007-07-04
I have been having the exact same problem. Has anyone found a solution?

---

### Post by gjtoth on 2007-07-04
> **dionysian_mind said:**
> I have been having the exact same problem. Has anyone found a solution?

Good luck!  I purchased Parallels about a 1 1/2 ago.  It ran fine for a time and then, after a kernel update, died.  As you have undoubtedly found out by now, tech support  (or any other support) from Parallels is non-existent.  I cut my losses, chalked it up to experience, vowed never to do business with Parallels again, and run either VM or Virtualbox.

---

### Post by scxtt on 2007-07-04
@gjtoth: if you make kernel changes, anything that built kernel drivers (for your current, running kernel) will be "broken" when you update your kernel ... it's like saying "i got a bigger engine for my car, why should i have to hook it up any differently?" ...

@carniolus: i've not used parallels, nor will i be anytime soon, but i'd venture to guess you either don't have "build-essentials" installed and/or don't have the kernel source/headers installed as well ...

---

### Post by Frak on 2007-07-11
I've the exact same error

```
frak@frak-desktop:~$ sudo parallels-config
Password:


[: 141: ==: unexpected operator
     Compiling Parallels Workstation 2.2 drivers...

Can not compile and/or link drivers. Read /usr/lib/parallels/doc/INSTALL
and follow instructions specified in this document.

Compilation log is available at /usr/lib/parallels/comp.log.15056.error
```

I checked, and I have all the kernel source/headers along with build-essential.

---

### Post by SirBob1701 on 2007-07-19
its an easy one.  if you have the linux kernel headers you they install with a longer folder name in /usr/src/  you have to ln -s  a linux folder (which is what parallels is looking for) to your kernel version headers.

---

### Post by michwill on 2007-07-22
> **SirBob1701 said:**
> its an easy one.  if you have the linux kernel headers you they install with a longer folder name in /usr/src/  you have to ln -s  a linux folder (which is what parallels is looking for) to your kernel version headers.



Where are we linking TO and FROM?  Please post example.

---

### Post by scxtt on 2007-07-22
ln -s linux-headers-2.6.20-15-generic linux

this will make a symbolic link so the linux --> linux-headers-2.6.20-15-generic, which is a pretty standard way of doing things, not sure why ubuntu doesn't seem to do it ...

---

