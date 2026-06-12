---
title: "Intall Linux to my external firewire drive?"
date: 2005-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tipo on 2005-11-17
Hey guys, I'm a total newbie at this, so be gentle.

Is there a way I can install Linux to my External Firewire Drive? I am running OS X on the internal drive of my powerbook, and I don't want Linux to install over that, and I don't want to partition the internal drive either....

So can it be done? Or would it be best to invest in a cheap used PC to get more experience with linux without messing up my beautiful Powerbook?

---

### Post by X5-655 on 2005-11-17
[QUOTE=Tipo]Hey guys, I'm a total newbie at this, so be gentle.

Is there a way I can install Linux to my External Firewire Drive? I am running OS X on the internal drive of my powerbook, and I don't want Linux to install over that, and I don't want to partition the internal drive either....

So can it be done? Or would it be best to invest in a cheap used PC to get more experience with linux without messing up my beautiful Powerbook?[/QUOTE]
I know that Macs can boot off Firewire drives, and that that OS X can boot off a Firewire drive, so I think it should work (my Mac mini is booted off the Firewire HD).

---

### Post by bugrider on 2005-11-18
[QUOTE=Tipo]Hey guys, I'm a total newbie at this, so be gentle.

Is there a way I can install Linux to my External Firewire Drive? I am running OS X on the internal drive of my powerbook, and I don't want Linux to install over that, and I don't want to partition the internal drive either....

So can it be done? Or would it be best to invest in a cheap used PC to get more experience with linux without messing up my beautiful Powerbook?[/QUOTE]

yes Linux can be installed and run from an external  firewire disk.
I've been running Gentoo PPC for more than a year in this set-up. 
It was not that easy to install (YellowDog and MandrakePPC make it really easy to do it) but it works fine (but you have to use a ramdisk and have firewire support). 
I've decided to move to Ubuntu lately for various reasons  and I'm going to achieve an external firewire disk installation on an ibook in coming weeks ...
I will give feedback.
In the meantime have a look at : 
[http://ubuntuforums.org/archive/index.php/t-3952.html](http://ubuntuforums.org/archive/index.php/t-3952.html)

:)

---

### Post by Tipo on 2005-11-18
Thanks guys, I'll do some more homework and see how things go. Huge psychology paper due soon, so I can't waste all my time tinkering. Thanks for the link!:p

---

### Post by hardclip on 2005-11-18
I stumbled upon Ubuntu a few weeks back and totally fell in love with it..

Problem is I didn't really think that far ahead and installed it an old 40GB Hitachi Deskstar I had lying around. When I need to run Windows I am swapping the IDE Cables about, which is unacceptable...

What would happen if I put the Linux drive into an external USB casing?? Would the drive boot or would I need to do a fresh install??

---

### Post by deen on 2005-11-18
[QUOTE=hardclip]I stumbled upon Ubuntu a few weeks back and totally fell in love with it..

What would happen if I put the Linux drive into an external USB casing?? Would the drive boot or would I need to do a fresh install??[/QUOTE]

same question
is Ubuntu linux can be installed on USBDrive (sometime called USBStick) ???

already installed ubuntu detect this drive, ant mount point at /dev/sda2 (already partitioned using mac-fdisk)

Thanks, I need this information because my Powerbook Lombard dont have Firewire

---

### Post by brent.stephens on 2005-11-20
You will need to change some of the parameters of your yaboot.conf.  Basically, yaboot does not officially support external booting, but if you throw in the right arguments it will work.  Check out my post [here](http://www.ubuntuforums.org/showpost.php?p=498516&postcount=5) for help.

---

### Post by deen on 2005-11-20
thanks for the site, great info

but can ubuntu detect USB Harddisk for mount point root (/) in Instalation Mode ?

---

### Post by teaker1s on 2005-11-20
beware the deskstar-I had one search either ibm deathstar or hitachi deathstar -they have high fail rates

---

### Post by brent.stephens on 2005-11-20
[QUOTE=deen]thanks for the site, great info

but can ubuntu detect USB Harddisk for mount point root (/) in Instalation Mode ?[/QUOTE]

As far as I have experienced, the installer detects everything just fine.  The only thing it chokes on is installing the bootloader to an external drive.  After everything has been installed and such, you will need to chroot to the /target, roll your own kernel, and follow the instructions for yaboot.conf

---

### Post by deen on 2005-11-21
[QUOTE=brent.stephens]As far as I have experienced, the installer detects everything just fine.  The only thing it chokes on is installing the bootloader to an external drive.  After everything has been installed and such, you will need to chroot to the /target, roll your own kernel, and follow the instructions for yaboot.conf[/QUOTE]

Thanks for the reply Mr,
My Powerbook cannot boot from USB Stick/Harddisk. only From (HD IDE,CD, NetBoot and SCSI) so installing yaboot on USB Hardware is useless, even can be installed, openfirmware won't boot from there.

I install yaboot on own cd, but with 

root=/dev/sda2 

options
 (examples use USB Harddisk on second partition ), it wont boot,

 what is wrong ?

---

### Post by brent.stephens on 2005-11-21
[QUOTE=deen]Thanks for the reply Mr,
My Powerbook cannot boot from USB Stick/Harddisk. only From (HD IDE,CD, NetBoot and SCSI) so installing yaboot on USB Hardware is useless, even can be installed, openfirmware won't boot from there.

I install yaboot on own cd, but with 

root=/dev/sda2 

options
 (examples use USB Harddisk on second partition ), it wont boot,

 what is wrong ?[/QUOTE]

If you read the other page, you'll see that yaboot.conf needs more specific options.  Things like /dev/sda are too far abstracted from the actual hardware location for yaboot to actually know what they are, as far as I understand.  Really, the yaboot folks should get it in gear and program this in.  I know Macs aren't 'supposed' to boot from USB, but I think its possible.  Not sure tho.

---

