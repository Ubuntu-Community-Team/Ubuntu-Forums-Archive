---
title: "Can't get BootX to start cd..."
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Eleaf on 2005-10-15
Hi!  I've been trying to get this to work for about a month and am very surprised at the lack of information on this... >.<

I have a Power Mac 8100/100.  I was able to get BootX to work and it loads fine at startup.  I however, cannot get the cd to start!  I've followed all the instructions at the ubuntu wiki and everywhere else I could find.  I select the kernel fine and the kernel seems to load up saying "Welcome to Linux Kernel...." and all that.  Then it loads about 4 lines of code with some hex numbers and just doesn't do anything...

So in essence, it just loads the kernel on my computer but DOES NOT load the cd.  Is there some argument I have to pass to the kernel for it to load the cd?  I 've been searching for months and have not found 1 answer anywhere!!!!!

What do I do for it to load the cd once the kernel is loaded????????? O.O

Thanks...

---

### Post by Rusty1 on 2005-10-15
You should have both the vmlinux and initrd.gz files copied from the cd to your linux kernels folder.  In bootx choose to use an initial ramdisk, browse to it (initrd.gz)  in the linux kernels folder, and click the linux button.

---

### Post by Eleaf on 2005-10-15
[QUOTE=Rusty1]You should have both the vmlinux and initrd.gz files copied from the cd to your linux kernels folder.  In bootx choose to use an initial ramdisk, browse to it (initrd.gz)  in the linux kernels folder, and click the linux button.[/QUOTE]

Thanks...  Yes, I have already done that though!!  However, it still doesn't work.

There is also no option to "browse" to the ramdisk.  That could be the problem.  I had to use an older BootX because the new one would never work saying there was a bad error in the extension and program on startup no matter how many times I tried to redownload it or anything.

Do you have any other suggestions, that may be the problem with the older version not having the ability to 'browse' to the ramdisk...

---

### Post by Rusty1 on 2005-10-15
Hmm, I don't have any experince with a non browsable ramdisk option.  Have you tried passing an initrd=/path/to/initrd.gz. On the command line? I'm not sure what the path would be.  Also you might be able to get help on the #debianppc irc channel.

---

### Post by Eleaf on 2005-10-15
Hmm...  That didn't work..  I don't know what could be wrong...  Is the ramdisk image supposed to link it to the cd or something?  I'm confused with how this should work..  But It certainly loads the kernel but the does nothing else.

---

### Post by Rusty1 on 2005-10-15
the initrd (initial ramdisk) loads a small os into memory which will launch the installer. The vmlinux kernel just bootstraps the system.  On the bootx i use on a beige g3, there is an options bottun, therein lies the use initrd option with browse.  I browse to it, and leave the kernel arguments box blank.

When i installed bootx, i had to make sure and drop the bootx extention into the extentions folder in my system folder.  I'm sure you did this but i'm trying to cover as many bases as i can. 

Getting a newer bootx to work would be a real help. I think the source is in the package if your so inclined :)

---

### Post by Eleaf on 2005-10-15
Ok, well with the newer BootX, I put everything in the correct folders.  However when the machine boots, it says there is a fatal error with the BootX extension and that I must start up holding shift to disable extensions.  Using 1.1.3 solves this and it boots up fine.  I don't know, is it a problem with the newer bootx for some odd reason.  I just don't know what to do...  Anyways, with this older bootx, I think you name the initrd.gz to ramdisk.image.gz and the option in bootx "Use Ramdisk" comes up that you can check.  I did that and it still doesn't work...  I'm really lost here, I hate it how the new bootx won't work!  I don't understand why it would work for everybody else but gives a fatal error for me... = S

---

### Post by Rusty1 on 2005-10-15
I have another g3 around for parts, i'll see if i can put together a box with 9.1 and bootx (old ) later tonight or tomorrow, and get the breezy cd to start.

---

### Post by Eleaf on 2005-10-15
[QUOTE=Rusty1]I have another g3 around for parts, i'll see if i can put together a box with 9.1 and bootx (old ) later tonight or tomorrow, and get the breezy cd to start.[/QUOTE]

Omg..  You are so awesome!!!  Thank you so much for your help! = ),

---

### Post by Eleaf on 2005-10-15
Hmm...  I tried 3 different BootX versions *after* 1.1.3.  Every one of them said the same error at boot.  "Bootx Extension address error" and I have to hold shift to disable extions then get rid of that extension.  It's so weird.  All of them show that same error except the old 1.1.3, this is odd.  = S

---

### Post by Rusty1 on 2005-10-16
Ok, i got it to work with bootx 1.1.3

copy the vmlinux file from the cd to liux kernels
 
copy the initrd.gz file from the cd to your bootx folder (not linux kernels), RENAME IT ramdisk.image.gz (trash any init.image.gz there first)

i also copied the initrd.lst file to the bootx folder.

start bootx, see that use ramdisk is checked, no root device , no kernel arguments.

Save prefs.

Click linux.   Let us know how you make out.

---

### Post by Eleaf on 2005-10-16
GRR...  It is still not working!!!!!!!!!!!  I don't understand..  I have everything exactly how it is supposed to...  And it still doesn't boot the cd...

It load the kernel and shows a black screen with this white text;

Welcome to Linux, Kernel 2.6.12-8-powerpc

Linked at            :xxxxxxxxxxxxxxxx
Frame buffer at  :xxxxxxxxxxxxxxx
Klimit                  :xxxxxxxxxxxxxxx
MSR                    :xxxxxxxxxxxxxxx

(The x's are justs some hex code..)
And it still won't do anything..  I am so confused.......  = S  Can my computer just not boot the cd?  I don't understand.  So far I've tried 5.04 and 5.10 and they both won't boot...  = /  They do boot fine on my iBook however.

---

### Post by jdp on 2005-10-16
The 8100 is NuBus based, not PCI.  Does Breezy have support for NuBus machines in the install kernel, or even the running kernel?  You may have to do the install on another machine, move the HDD and install the NuBus kernels from the NuBus PowerMac Kernel project on Source Forge.

---

### Post by Eleaf on 2005-10-16
[QUOTE=jdp]The 8100 is NuBus based, not PCI.  Does Breezy have support for NuBus machines in the install kernel, or even the running kernel?  You may have to do the install on another machine, move the HDD and install the NuBus kernels from the NuBus PowerMac Kernel project on Source Forge.[/QUOTE]

Oh.....  Well that could be it...  I don't have another computer that uses scsi hard drives...  hmm...  I don't know what to do... = /

---

