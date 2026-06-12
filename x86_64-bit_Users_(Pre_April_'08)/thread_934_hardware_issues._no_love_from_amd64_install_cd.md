---
title: "hardware issues. no love from amd64 install cd"
date: 2004-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by chewy on 2004-10-16
having some significant failures bootstrapping.

the hardware:
asus k8v-sedx
athlon 64 2800+
ATI X800 pro (i know it's as of yet unsupported everywhere)

linux-image-amd64-k8 

attempting to run with the A64 iso, i bumped into several surprising problems. 
- X fails most likely because of the unsupported chipset. 
- the help from [http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html) fails since binaries and patches apply only to i386 (i think)
- my meager attempt to resolve the situation led me to discover agpgart was missing. (? what happened to agpgart? in the kernel?) 
- i'm either in way over my head or there are significant differences in architecture that i'm just not getting
- i'm pretty sure the video issue will continue to be a thorn in my side without recompiling a custom kernel (but i so love pre-built optimised kernel images)

i threw the install away and am running with a sub-optimal i386 iso install and am hoping some kind contributor will direct my aimless forum post. 

it looks like the convergence of amd64 + bleeding edge ati = headache. any direction would be greatly appreciated

---

### Post by killerfish on 2005-01-11
[QUOTE=chewy]having some significant failures bootstrapping.

the hardware:
asus k8v-sedx
athlon 64 2800+
ATI X800 pro (i know it's as of yet unsupported everywhere)

linux-image-amd64-k8 

attempting to run with the A64 iso, i bumped into several surprising problems. 
- X fails most likely because of the unsupported chipset. 
- the help from [http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html) fails since binaries and patches apply only to i386 (i think)
- my meager attempt to resolve the situation led me to discover agpgart was missing. (? what happened to agpgart? in the kernel?) 
- i'm either in way over my head or there are significant differences in architecture that i'm just not getting
- i'm pretty sure the video issue will continue to be a thorn in my side without recompiling a custom kernel (but i so love pre-built optimised kernel images)

i threw the install away and am running with a sub-optimal i386 iso install and am hoping some kind contributor will direct my aimless forum post. 

it looks like the convergence of amd64 + bleeding edge ati = headache. any direction would be greatly appreciated[/QUOTE]
 Well, no one can say I didn't search! :)  Reviving this thread.   I just did an AMD64 install and I also do not have the agpgart driver and related modules build (ie, amd64_agp)...  These modules are built in the i386 install.  

I figured "no problem" I'll compile my own kernel.  So I download the linux-source package and  run make menuconfig.  Strangely, I can't select AGP support under Device Drivers->Character Devices.  It just looks like this and doesn't accept choosing Y,M, or N:

--- /dev/agpgart (AGP Support)

Any ideas?

---

### Post by killerfish on 2005-01-11
[QUOTE=killerfish]Well, no one can say I didn't search! :)  Reviving this thread.   I just did an AMD64 install and I also do not have the agpgart driver and related modules build (ie, amd64_agp)...  These modules are built in the i386 install.  

I figured "no problem" I'll compile my own kernel.  So I download the linux-source package and  run make menuconfig.  Strangely, I can't select AGP support under Device Drivers->Character Devices.  It just looks like this and doesn't accept choosing Y,M, or N:

--- /dev/agpgart (AGP Support)

Any ideas?[/QUOTE]
 Well, now I know why... agpgart & amd64-agp are compiled automatically into the kernel/not as modules..  Problem is, for my chipset, ULi m1689, I need to patch the amd64-agp module to get it to work. 

I've done this patch without issue in the i386 install, but how do I override this 'feature' of the AMD64 Ubuntu kernels?  

BTW< this doesn't just affect me with an M1689 chipset, it looks like it affects any chipset that uses agpgart/but not the stock amd64-agp module...

KF

---

### Post by killerfish on 2005-01-13
[QUOTE=killerfish]Well, now I know why... agpgart & amd64-agp are compiled automatically into the kernel/not as modules..  Problem is, for my chipset, ULi m1689, I need to patch the amd64-agp module to get it to work. 

I've done this patch without issue in the i386 install, but how do I override this 'feature' of the AMD64 Ubuntu kernels?  

BTW< this doesn't just affect me with an M1689 chipset, it looks like it affects any chipset that uses agpgart/but not the stock amd64-agp module...

KF[/QUOTE]
 Well, looks like kernel 2.6.11 will have drivers for all the ULi M1689 chipset components right in the kernel.  Net, I suppose I can wait a little longer to get it going in AMD64.  I have it all in i386, but it was painful! :)

---

### Post by bigtim.north on 2005-04-12
Does the ULI M1689 motherboard you have work directly under Warty and will it work with 2.6.10 under Hoary.

---

