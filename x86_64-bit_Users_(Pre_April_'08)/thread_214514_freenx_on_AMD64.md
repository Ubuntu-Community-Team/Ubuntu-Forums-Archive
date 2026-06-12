---
title: "freenx on AMD64"
date: 2006-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by nacer on 2006-07-12
I have an Amd64 machine and 32 bit laptop. I installed ubuntu dapper 6.06 on both machines.

I want to be able to connect, from my laptop, to the 64 bit machine using freenx. After doing some research I found this website "[http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/freenx/) " which provides apparently all the packages needed to install freenx, with no reference to AMD64 though! I also found, from [www.nomachine.com](www.nomachine.com), that I had to install nxclient, nxnode prior to installing nxserver. Being fairly new to linux, the problem I am facing is that I cannot find clear instructions on what to install on each side (on the AMD64 machine? and on my laptop?) and how freenx works? does it use ssh or something else? and how do I know it is successfuly installed?:confused:

Is there anybody out there who has done this before. Thanks

---

### Post by amiga_os on 2006-07-12
Can't be of much assistance, but I hope this helps you get started:

If you can't find 64bit packages of freenx, then you can still install them!  There are 3 methods I've heard of to get 32 bit apps onto a 64 bit system:
1. use dpkg --force, since 64 bit systems are backwardly compat with 32 bit
2. install the ia32 libs from synaptic, and then use dpkg
3. set up a 32 bit chroot (a skeleton 'system within a system')

I would not recommend the first two.  Firstly I think they're (contrary to some) actually more complicated in the long run, and difficult to upgrade / clean up.  I would recommend the last option.  If anything goes wrong you can wipe and reinstall your chroot, leaving your system completely clean (though be wise about how you do this ;) ).

Instructions for setting up a 32bit chroot can be found here:
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)
with helpful stuff also here:
[http://www.ubuntuforums.org/showthread.php?t=24575](http://www.ubuntuforums.org/showthread.php?t=24575)

Though I would ask why you want to use freenx?  I don't know anything about it, but surely there must be other ways of connecting your ubuntu boxes together?

---

### Post by nacer on 2006-07-12
I mainly use Visualization applications which when run using ordinary ssh are very slow and I was told that freenx is incredibly fast (as if you run the application locally !) that is why I want to have a go at it.

I will try your third option and see what happens.


Cheers.

---

### Post by amiga_os on 2006-07-12
great, hope it helps... however, I have *just* (10mins ago) dpkg --force installed wine on my system, 'cos it didn't work in the chroot.

But it's worth having a chroot anyway, firstly can't harm your system, secondly easily removable, thirdly java and flash support with firefox... (and cinelerra, jahshaka, etc...)

---

