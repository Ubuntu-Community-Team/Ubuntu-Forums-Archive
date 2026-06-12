---
title: "amd64 NForce Audio Drivers"
date: 2007-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by driectly3d on 2007-09-23
i cant seem to get this nforce install working for the life of me, have been trying to follow this guide:

[http://ubuntuforums.org/showthread.php?t=96370&highlight=surround+sound+fix](http://ubuntuforums.org/showthread.php?t=96370&highlight=surround+sound+fix)

with absolutely no success

It seems to me like i dont have the right version of the linux source, Im running 2.6.20-16-generic  and the source folder is named 2.6.20

anyway when i run

sh NFORCE-Linux-x86_64-1.0-0310-pkg1.run --kernel-source-path=/usr/src/linux-source-2.6.20

The error log comes out like this

ERROR: 
       If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the appropriate nvidia-installer command line option.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
 
And when i run this:

sudo sh NFORCE-Linux-x86_64-1.0-0310-pkg1.run --kernel-source-path=/usr/src/linux-headers-2.6.20-16-generic
or this 

sudo sh NFORCE-Linux-x86_64-1.0-0310-pkg1.run --kernel-source-path=/usr/src/linux-headers-2.6.20-16

i receive this error

echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it

which I have  no idea how to do as ive only been using linux for about a week now, its probably something very simple, but i have yet to come accross a thread that explains how to do this. Any help at all is greatly appreciated ^^  These forums rock, Ive gotten more working on linux64 in a week, than either xp64 or vista64

---

### Post by jocko on 2007-09-24
The nforce sound drivers (nvsound) will only help you if you have an old nforce 2 motherboard with a soundstorm chipset (this was a sound chipset that could do real-time dolby digital encoding. Nvidia decided to stop making it a long time ago).
The drivers will probably work for nforce 3 and nforce 4 as well (not sure about amd64), it's just that there is no benefit of using these fancy, but discontinued, drivers for simple ac97 codecs.

Also, the nforce drivers were dropped by nvidia almost two years ago, which mean it does not support newer kernels (unless you patch the drivers to reflect the changes in the kernel).

I think you would be better off if you found a way to get sound working with alsa drivers. They should already be included in the kernel and be running by default, but sometimes you may need to change some settings somewhere and tweak some file somewhere else to get them working properly...

For reference, in case someone else is interested in getting better sound out of an old [COLOR=Red]nforce2/soundstorm[/COLOR]: the guide you linked to is quite old and incomplete (will not work with kernels newer than 2.6.15). I have a [more up to date guide here]("http://ubuntuforums.org/showthread.php?t=253725") (works fine with all Ubuntu releases from breezy to gutsy).

For those that does not have a soundstorm chip, there is a "[Comprehensive Sound Problems Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide")" that may help you in the right direction.

Good luck.

---

