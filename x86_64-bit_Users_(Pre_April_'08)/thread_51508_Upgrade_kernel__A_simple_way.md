---
title: "Upgrade kernel?  A simple way?"
date: 2005-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mortoray on 2005-07-24
What is the easiest way to upgrade a kernel in Ubuntu?  I have found the instructions on how to build a new kernel, but that seems like extra work (and prone to disaster) as I don't need to set any custom options.

I need a newer kernel since I have an SATA driver on the ATI RS480 chipset, which of course had its support only introduced in the 2.6.11 kernel (Hoary is of course using 2.6.10 at the moment).

So, how can I go about quickly upgrading the kernel?  Or since I just want the SATA support, is there another way to get this enabled without upgrading the kernel?

---

### Post by PeP on 2005-07-24
[QUOTE=mortoray]What is the easiest way to upgrade a kernel in Ubuntu?  I have found the instructions on how to build a new kernel, but that seems like extra work (and prone to disaster) as I don't need to set any custom options.

I need a newer kernel since I have an SATA driver on the ATI RS480 chipset, which of course had its support only introduced in the 2.6.11 kernel (Hoary is of course using 2.6.10 at the moment).

So, how can I go about quickly upgrading the kernel?  Or since I just want the SATA support, is there another way to get this enabled without upgrading the kernel?[/QUOTE]
kernel 2.6.11 & 12 are in breezy, 
but according to the breezy forums, it is a bad Idea to upgrade now unless:
-you can manage the troubles you're going to get in
-you can do without the restricted modules (including ati and nvidia graphic drivers)
-you're not in kubuntu (In the forum kubuntu users seems to have worst problems)

you might also try this:
add the breezy repository in /etc/apt/sources.list
update,
install _only_ the 2.6.11 kernel-image, headers, tree and sources and whatever you need related to the kernel version.
remove the breezy reps,
update

once again you won't have support for ati and nvidia chips and will have to use the free 2d only drivers.
once again you might have some troubles with your system.

---

### Post by Tamir on 2005-07-24
Better don't do that, I am building packages of the newsest kernels for amd64.

---

### Post by ricardo06 on 2005-07-27
I might be wrong but i had the same kind of problem with 2.6.10 not supporting dma disks acces with my ati chipset. 
I upgraded to 2.6.11-1 that is in ubuntu hoary (and not breezy) universe repository (do a search of 2.6.11 from synaptic and you should find it)  and i now have dma acces to my ide disks. 

It probably causes problems elsewhere as my PC freezes very often and i have to re-boot like 30 times a day, but at least I can use it.

I am not a kernel specialist so that solution might not be good for you but as i said it makes my PC usable. 

Now, this kernel image is present in the hoary repository so it is probably safe tu use it. 

I would anyway like to go deeper in the process of analyzinfg my cpu freezes problems. The machine did pass the  mem86 tests. so i am looking for some kind of log file that would be preserved over a reset and that would help me diagnose.

Has  anybody an idea of how i could do progress ?

cheers 

Richard

---

