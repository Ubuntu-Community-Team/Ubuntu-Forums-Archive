---
title: "Getting Red Screen on install of 5.10 to HD"
date: 2006-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Theo-Ubu on 2006-05-03
Hello,

I put in a fresh 10Gig drive (it was used, but I think wiped by the store...) in this iMac G3 Rev-A with aprox 100Mb of RAM and tried to install from CD.  Somewhere along the way, all seems to be going fine, then I hit a red-screen saying something to the effect of:

"unable to install initrd-tools"

"check /target/var/log/bootstrap.log"

I try to continue on past that point through the blue-screen menus, but then I come to:

[!!] failed to install base system

Anybody have some clues for me as to what's happening or going wrong?  Perhaps there's not enough memory to unpack the base system packages?  It told me on a couple of occasions that old verions of the files existed, and did I want to overwrite them...?

Thanks!

---

### Post by bugme on 2006-05-03
Are you dual-booting or just installing ubuntu?
I think I know what your problem is just answer me the question first.
Thanks

---

### Post by bugme on 2006-05-03
Go here: [http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted](http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted)
It tells you what partitions to make and how to install every thing. 
Just ignore the partitions that are already there on the partition since the harddrive you are using is wiped. Just resond in this thread if you have any questions/problems related to the guide I gave you.

---

### Post by Theo-Ubu on 2006-05-03
No, I'm just installing straight from a CD, from the tray-load CD drive.

I hold the "C" key and then it boots up and begins install from that.

Thanks!

---

### Post by bugme on 2006-05-03
No problem!
Like I said, if you have any problems just respond in this thread.
Good luck : )
Also, sorry for my English at times it can be bad because I'm in a hurry to do my homework.

---

### Post by Theo-Ubu on 2006-05-03
Actually... it is a problem.  I am trying to install a version to the HD.  I have tried Live-CD and it runs too slowly to be of any use.

While I'm trying to install to HD from CD is when I encounter the red-screens.  I have just rebooted the installation and now I have tried bumping up the main partition size to 7.2 GB.  I'll see what happens now.

---

### Post by Ptero-4 on 2006-05-03
Try cutting the root partition to 8GB or less. It's a known bug in earlier iMac G3's in which they don't support having an OS in a partition bigger than the first 8GB of the internal HD.

---

### Post by Theo-Ubu on 2006-05-03
OK, how do I know which is the root partition?  Is it "hda".   Sorry, but I'm not very familiar with the linux file system yet.  I'm excited to try this all out though and hopefully transition away from "windows".

Thanks!

---

### Post by bugme on 2006-05-03
Please read through the whole guide, I know it sais use the Live CD but the live cd is only for making the partitions.
Please take the time to explore the whole guide, it sais exactly how to mount a partition as root ( / ). You mount the partitions you make in the actual installation.

---

### Post by Theo-Ubu on 2006-05-03
Live CD will not work on this machine.   It's so slow as to be unusable.  So... I can't do any partitioning through live CD.

I guess Ubuntu has failed this user.  It's dissapointing.  I doubt linux will ever gain headway with the masses with this kind of install failure stuff.  I'm a fairly advanced computer user but the linux stuff is all so non-standardized and VERY seldom just plug-and-play.   I've never failed with a windows install as bad as this, even as much as I loath that company.

So very too bad.

---

### Post by bugme on 2006-05-04
I'm sorry, it works a lot better on standard hardware like AMD and i386/x86.
But honestly, how could you call yourself an advanced computer user if you are used to plug and play?

---

