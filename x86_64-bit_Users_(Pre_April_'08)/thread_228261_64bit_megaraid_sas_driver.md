---
title: "64bit megaraid_sas driver?"
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Grizzly_Adams on 2006-08-02
G'day all,

Still trying to get my Dell 2950 to play properly with Ubuntu.

Now trying 64bit in order to get access to my full 4Gb of RAM.

Problem I am having with the 64bit install is that it is seeing all of my HDD's + the RAID device, where is should only be seeing the RAID device.

It's driving me nuts.  I can install 32-bit Ubuntu but can only see 3.2Gb of my 4Gb of RAM, or I can install 64-bit Ubuntu and fight with the megaraid_sas driver.

Basically I am presented with 3 HDD's to choose from:

sda (hard disk 1)
sdb (hard disk 2)
sdc (raid device)

Where I should only be presented with the raid device.  If I install on any but the raid device it screws up grub and the system won't boot.

So far out of the x amount of re-installs I've tried, the only one which appeared to come close to working was when I installed Ubuntu on sda, then on the next reinstall I only saw the RAID controller device (I had to reinstall because ubuntu wouldn't boot if I installed straight to sda).

However shortly after getting the system up and going I ended up with some file system corruption (buggered if I know how that happened), and that ended up in another re-install.  I've now removed the RAID logical volume and tried installing directly to the HDD's thinking I could use software mirroring except the Bios now doesn't see the physical HDD's as something you can boot off and goes off in it's little world of trying to PXE boot off the network card *sigh*

I dunno what if any help I'm asking of anyone, I can't think of any questions to ask.  I just thought I'd vent my frustration here and maybe someone else could sympathise. ](*,) ](*,)

---

### Post by TripleE on 2006-08-03
I use a raid0 array with 2 SATA drives.  I had to use 1 of my IDE drive to put the boot dir on.  I tried my best to document it.  It is still a work in progress.  Check out what I did [here]("http://geocities.com/eric1548/").

---

### Post by furrfu on 2006-08-09
> **Grizzly_Adams said:**
> 
Problem I am having with the 64bit install is that it is seeing all of my HDD's + the RAID device, where is should only be seeing the RAID device.


I have exactly the same problems - on PowerEdge 1950s and 2950s.

---

