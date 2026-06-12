---
title: "Newly installed system fails to boot."
date: 2005-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by nxsty on 2005-01-25
I have a problem with Ubuntu Linux 5.04 Array 3.

The installations seems to work perfectly but after the reboot GRUB never appears. It just prints out a message "operating-system not found" and nothing more happens. I choosed to install GRUB to the MBR and the windows bootloader gets removed so at least it does something.

I have tried to set the disks på LBA in the BIOS but it didn't work. I have also tried creating a small /boot partition but it didn't work either.

The system is an AMD65 3500+ on an Asus A8N-SLI (nforce4 based). The hardrive is an ordinary PATA device, not SATA.

Maybe it's related to this, from the release-notes:

> 
  * On my amd64 system, grub enters an infinite loop trying to load
    stage 1.5. I've never seen this before, and suspect hardware
    problems, but if it affects other people too I'd like to know about
    it.


---

### Post by valadil on 2005-01-25
I've had some problems with grub too.  Try booting off the cd, but changing to a shell as soon as possible.  Mount our hdd then chroot in and install grub from there.  Or try lilo.

---

### Post by nxsty on 2005-01-25
Thanks, but it didn't work. I tried to boot from the installer cd, start a shell and then run grub-install manually but I just got the same error. I then tried with different options to grub-install but nothing helped.

But I found a workaround; instead of using a shell from the ubuntu cd I booted with a gentoo live-cd and did the same thing. Then grub-install would work!

---

### Post by quackking on 2005-01-25
What options did you use with the Gentoo grub-installer? I have a SATA drive and everything seems to be there correctly - the images, the system maps, the menu.lst file - everything is there. But when I boot, all I get are some generic Grub instructions and a grub> prompt. Obviously the grub binary is running, but it does not see the menu.lst file, which is definitely there (I can see it if I boot with Knoppix).

The only thing that seems like it may be odd is that for all the boot images, root is defined as root (hd0,0). Is that correct given that the actual device is sda1?

Any ideas?

---

### Post by scaltro on 2005-01-26
> when I boot, all I get are some generic Grub instructions and a grub> prompt. Obviously the grub binary is running, but it does not see the menu.lst file, which is definitely there (I can see it if I boot with Knoppix).
I've the same problem...  my grub is installed on the root partition (not MBR) , 
what can i do for permit grub to reload the menu.lst file (that is in the same partition) ???

---

### Post by Mumbly Joe on 2005-01-26
I am having a similar problem.  The pressed Warty AMD64 release works fine, but when I install Hoary Array 3, I receive a Grub error the states there is a hard disk error upon reboot.  The installation appears to go perfectly.  Upgrading to Hoary from Warty works fine though.  Grub is loaded to the MBR.

Here are my system specs:

AMD 64 3200+
Asus A8V Deluxe
1 GB DDR400 Memory
IBM ServeRAID 4H Adapter
Root Partition:  9.0GB SCSI set to Raid 0 on Channel 1
Home Partition:  70GB SCSI set to Raid 1E on Channel 2
Ugly Stickers on Case

---

### Post by quackking on 2005-01-26
Well, I tried both the pressed Warty-64 release and the Hoary-64 release, and  also a network install of Hoary-mini-iso. None of them work. My comment before (only seeing the grub>  prompt) is from the Warty pressed disk install.

I can install the Warty-i386 system with no problem (as long as I use "linux acpi=off" at the very beginning)

---

### Post by nxsty on 2005-01-26
[QUOTE=quackking]What options did you use with the Gentoo grub-installer? I have a SATA drive and everything seems to be there correctly - the images, the system maps, the menu.lst file - everything is there. But when I boot, all I get are some generic Grub instructions and a grub> prompt. Obviously the grub binary is running, but it does not see the menu.lst file, which is definitely there (I can see it if I boot with Knoppix).

The only thing that seems like it may be odd is that for all the boot images, root is defined as root (hd0,0). Is that correct given that the actual device is sda1?

Any ideas?[/QUOTE]

I used grub-install --recheck --no-floppy when it worked.

I'm not sure because I don't have any SATA drives myself but I think that woud be correct if the SATA has the highest boot priority in the BIOS.

---

### Post by Scay on 2005-01-27
This is exactly what stops me from getting inside my brand new Array 3-install.  :mad: 

Does anyone have any suggestions for a fix? Tried most of the previous mentioned... 

The endless-"GRUB Loading stage1.5"-loop-problem...argh  :neutral:

---

### Post by broch on 2005-01-29
Had the same problem, Ubuntu for AMD64 installs fine (?) however hangs after first reboot. In my case no grub (hangs after DMI poll)
Tried at first install on SATA, then on PATA with the same result. Downloaded SuSe 9.2 for AMD64 and SuSe works fine.

---

### Post by Scay on 2005-01-31
Really frustrating...have spent a couple of hours tweaking the hardware without luck. I suppose that's what computers are all about.....frustration  ;)

---

### Post by Lubrei on 2005-02-26
I have problems with GRUB too.It screen a message that says "Booting GRUB, please wait..." and I wait, and wait, and... But the system not boot.Because this I have to format the system other time to WIndows

---

### Post by callahan on 2005-02-26
I posted how to fix this a while back.

[http://www.ubuntuforums.org/showthread.php?t=13112](http://www.ubuntuforums.org/showthread.php?t=13112)

grub has been updated a couple of times in Hoary since then.  You might want to just give the latest Array a try and see if it's been fixed.  I think the next one comes out on Monday.

  Michael

---

