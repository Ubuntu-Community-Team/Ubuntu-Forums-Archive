---
title: "x64 Server on Celeron D Problem"
date: 2007-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by zachsandberg on 2007-08-14
Hi all, I am trying to install Ubuntu Server 7.04 x64 on a Lenovo Thinkcentre A51.
I flashed the bios from off the website with the newest revision, and proceded to install Ubuntu, however, I get only two or three seconds past the "loading kernel" progress bar, before a message pops up and says my machine doesnt have 64 bit support.  IBM doesnt seem to know, and the bios is current.  The bios doesnt give me any options regarding 64 bit support either, so I dunno.  Anyone have some pointers?

Specs Below:
Intel Celeron 331
2GB PC2-4200
(1) 73.6GB WD Raptor

---

### Post by John.Michael.Kane on 2007-08-14
Looking up the spec's on the machine, and the processor it would seem 64bit support is there.

First I would try redownload/reburning the cd. Also making sure to check the md5sum on the iso.

checking mdsum
1) cd to download_directory

run the following command from within the download directory.
2)md5sum ubuntu-Version-Goes-Here.iso

md5sum will kick back a line similar to the one below.
3)b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-Version-Goes-Here.iso

I would also try doing using the alternate iso, and doing a regular desktop install or using the ubuntu live cd to see if the hardware can be read/seen, As "fully" supported in that environment first.

Barring the above not fixing the issue. You can try the commands below.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

To pass all the command in one go. At the boot/install prompt (make sure to hit F6 first),and add the command below to the boot parameter.
```
nosplash noapic nolapic pci=irqroute irqpoll framebuffer=false pci=acpi acpi=off pci=noacpi
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.


Hope this helps.

---

### Post by olmari on 2007-08-15
Now there is some diffirences especially with early Intel and Amd 64-bit implementations, so it might very well be just that. What to do about it I don't know. Lots of information [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by tgm4883 on 2007-08-15
> **olmari said:**
> Now there is some diffirences especially with early Intel and Amd 64-bit implementations, so it might very well be just that. What to do about it I don't know. Lots of information [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

The processor has EM64T so it is capable of a 64-bit OS.  I would grab the 32-bit CD (not to install) but just to run this and post the output.

cat /proc/cpuinfo

---

### Post by olmari on 2007-08-15
tgm4883:

I know his processor has EM64T, I said there are some diffirences with amd and intel implementations, especially early EM64T according to my link. If nothing seems to help, then it _can_ be that.

---

### Post by tgm4883 on 2007-08-15
> **olmari said:**
> tgm4883:

I know his processor has EM64T, I said there are some diffirences with amd and intel implementations, especially early EM64T according to my link. If nothing seems to help, then it _can_ be that.

Right and what I'm saying is that if you have a 64-bit processor and a 64-bit OS then there is your problem, either in the hardware or the software.  I'm trying to eliminate some factors here and narrow down the source of the problem.

---

### Post by tgm4883 on 2007-08-15
I should also point out, from .

[http://en.wikipedia.org/wiki/Celeron_D]("http://en.wikipedia.org/wiki/Celeron_D")
> In mid-2005, Intel refreshed the Celeron D with Intel 64 and XD Bit (eXecute Disable) enabled. Model numbers increase by 1 over the previous generation (e.g. 330 became 331). This only applied to LGA 775 Celeron Ds. There is no Socket 478 CPU with 64 bit and/or XD Bit capabilities.

---

