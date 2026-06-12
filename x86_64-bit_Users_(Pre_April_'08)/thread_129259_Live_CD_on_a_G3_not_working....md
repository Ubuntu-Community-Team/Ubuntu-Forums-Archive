---
title: "Live CD on a G3 not working..."
date: 2006-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by PFI_Optix on 2006-02-13
I'd like to demonstrate Ubuntu on a G3 running OS 8.6. I need to use a live CD, as it's not going to be my system. I just downloaded and burned the PPC live image this morning.

I can't get the Mac to boot off the CD. It will boot from an old Norton Utilities CD I had laying around, so I know it will at least boot from *that* disk. It can read the Ubuntu cd in MacOS.

Am I just mistaken in thinking that it should boot from the Live CD without any additional configuration? I can't find any documentation on the subject (which is a chronic problem with Linux, but that's a whole other rant :) )

---

### Post by linear on 2006-02-13
This is an Old World Mac, isn't it? I don't think you can boot the Live CD on it at all.

---

### Post by PFI_Optix on 2006-02-13
[QUOTE=linear]This is an Old World Mac, isn't it? I don't think you can boot the Live CD on it at all.[/QUOTE]

Looks that way.

Is that in the documentation anywhere? I couldn't find it if it is.

---

### Post by linear on 2006-02-13
I don't know if it's explicitly documented for the Live CD, but you could infer it from the gyrations needed to boot an installed Linux on an OldWorld Mac - for instance here:

[https://wiki.ubuntu.com/Installation/OldWorldMacs]("https://wiki.ubuntu.com/Installation/OldWorldMacs")

---

### Post by jdp on 2006-02-13
Yep, just install BootX as described, and copy the kernel and initrd.gz from the LiveCD and keep the Cd in the CD drive.  When you run BootX and choose Linux it should boot the LiveCD right up.  if you don't want the boot time dialog to show up, just don't install the BootX extension.  You should be able to still use the Control Panel to get Linux going, and the boot process shouldn't be changed at all for MacOS.

---

### Post by PFI_Optix on 2006-02-14
I installed BootX and copied it into the System Folder per the instructions. The boot dialog isn't a problem, I just want to avoid trashing the OS.

I copied vmlinux to "Linux Kernels" in the System Folder and initrd.gz to the System Folder.

On my first try, I got a kernel panic. I hadn't set a root device because I wasn't sure what it was. Before the system locked up, it announced that the CD-ROM was hda. Second try, I set the root device to /dev/hda. Same problem.

```
Kernel panic - not syncing: VFS: unable to mount root fs on unknown block (0,0)
  <0> Rebooting in 180 seconds.._
```

And that's it. It takes toggling the power supply to get it restarted.

I'm using BootX 1.1.3 because the newer versions won't fit on a floppy, and I'm out of CDs for the time being.

Any suggestions?

---

### Post by PFI_Optix on 2006-02-16
I spent some time today trying to find a solution to this, and I'm just stuck.

Anyone have any ideas?

---

### Post by PFI_Optix on 2006-02-20
I found this thread: 

[http://ubuntuforums.org/showthread.php?t=87267](http://ubuntuforums.org/showthread.php?t=87267)

and tried some of the ideas in it. Nothing seems to be working. Figured I'd bump this one more time before giving up on getting Linux into this organization.

---

### Post by jdp on 2006-02-22
If I can dig out and get one of my G3MTs hooked u I'll give it a try.  I dunno when I'll have time, but I've been meaning to investigate this.

---

### Post by erniewinner on 2006-03-18
hi,

i'm getting a similar error. i can't see to choose the ramdisk option. its greyed out. or boot with g3 cache whatever that is, also greyed out. i too am using 1.1.3 as it's the only version stuffit would unstuff. i could not copy the files from either of my usb sticks as they kept freezing the computer so i burnt the files to disk using nero.
it might be important to note i am using a non apple dvd drive and os 9.2.2 i shall try the proper drive tommorow. also i have what might be regarded as non apple ram. but it works with osx and os 9. any clues out there. 

desperately seeking ubuntu!

---

