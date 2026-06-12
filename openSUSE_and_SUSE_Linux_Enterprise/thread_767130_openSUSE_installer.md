---
title: "openSUSE installer"
date: 2008-04-25
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Northsider on 2008-04-25
How does openSUSE's install process compare to ubuntu, particularly when it comes to partitioning and such?  I always thought that ubuntu's was really easy to follow: erase entire disk, erase partition, use free space on parition, manual, etc.  Does openSUSE's have an easy walkthrough like this?

I have a new HP desktop, AMD, NVidia, etc.  It came with an HP C:/ drive with the programs and such on it.  It also has an HP E:/ drive that is mostly empty with only MSO_Cache on it.  If I were to select that partition to format and install suse on, would that be safe to do?  Thanks/.

---

### Post by Growbag on 2008-04-26
I also have a HP laptop that has a "D:" drive on it.

I deleted it once to get rid of space, Vista threw a fit and refused to boot.  I had to do a total system restore!!!!

Luckily I made a copy before I deleted anything.

It is part of the system restore function, and if you delete it you will have to either buy a restore disk from HP, or pay MS money for a new copy of Vista (if you actually want Vista that is!).

You can safely resize the recovery partition, but unless you want to dump Windows completely, leave it on the drive!

I shrank mine to leave only about 300 megs free, it doesn't need any free space anyway.

---

### Post by Northsider on 2008-04-26
> **Growbag said:**
> I also have a HP laptop that has a "D:" drive on it.

I deleted it once to get rid of space, Vista threw a fit and refused to boot.  I had to do a total system restore!!!!

Luckily I made a copy before I deleted anything.

It is part of the system restore function, and if you delete it you will have to either buy a restore disk from HP, or pay MS money for a new copy of Vista (if you actually want Vista that is!).

You can safely resize the recovery partition, but unless you want to dump Windows completely, leave it on the drive!

I shrank mine to leave only about 300 megs free, it doesn't need any free space anyway.
WOW,  Thanks for the heads up.  My first question I guess would be why does Vista/HP need a 250GB "recovery" partition?  So resizing it and then using the new partition would be good?  Thanks for the reply


EDIT: Just opened up the resizer, I have 9GB D: as well as 250GB E:.  I'll just resize the E: drive.

---

### Post by overdrank on 2008-04-27
> **Northsider said:**
> How does openSUSE's install process compare to ubuntu, particularly when it comes to partitioning and such?  I always thought that ubuntu's was really easy to follow: erase entire disk, erase partition, use free space on parition, manual, etc.  Does openSUSE's have an easy walkthrough like this?

I have a new HP desktop, AMD, NVidia, etc.  It came with an HP C:/ drive with the programs and such on it.  It also has an HP E:/ drive that is mostly empty with only MSO_Cache on it.  If I were to select that partition to format and install suse on, would that be safe to do?  Thanks/.

Hi and I just installed Suse 10.3 today on a VM and on a spare system and I was not dual booting but I thought the installation was very smooth. :)

---

### Post by quickshade on 2008-04-27
10.3 is good.
11 is great, maybe even amazing.

---

### Post by Northsider on 2008-04-28
Suse ended up really messing vista boot up and I could not boot for the life of me.  Reinstalled Kubuntu and it worked like a charm!  Also, openSUSE seemed really sluggish compared to kubuntu 8.04

---

### Post by quickshade on 2008-04-28
Yea you have to edit grub from text and insert the correct Grub command.

EDIT: I'm not sure why but the Grub thing is really weird. It deletes My PClinuxOS option from the menu and screws around with my vista chainloader making it not work. I've asked the developers why but no answer yet. I might reinstall grub from another distro and use that to boot SUSE.

---

