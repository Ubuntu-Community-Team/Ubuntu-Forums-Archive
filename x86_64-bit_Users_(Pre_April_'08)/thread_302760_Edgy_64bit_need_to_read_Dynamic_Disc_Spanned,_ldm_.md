---
title: "Edgy 64bit need to read Dynamic Disc Spanned, ldm - ntfs-3g"
date: 2006-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by anixon on 2006-11-19
Hi guys, I'm a totally newb with ubuntu. But i finally ditch the windows last week for good to try my luck with 64bit Edgy. I've spent almost every waking hour over the last weak getting everything set up and scouring forums.

I seemed to have hit a roadblock here. The problem is i have 2 hard drives in my comp formatted and spanned using windows Dynamic Disk format. Documentation on how to mount this is scarce but i think i need to have ntfs-3g and ldm in the kernal.

I used synaptic to install ntfs-3g but I don't know where to go from here. I couldn't find much info on the ldm driver. I don't know how to get this driver into my kernel. I downloaded a driver bin from [http://www.linux-ntfs.org/content/view/19/37/](http://www.linux-ntfs.org/content/view/19/37/) and i took a peek inside, there seems to be a patch but it's for 2.4 kernel so i don't know if it would work or how i would apply it.

I found this link that outlines... "the process" [http://forum.linux-ntfs.org/viewtopic.php?p=1572&sid=7e2ba87c68c9e2416cf6cc27aa2bca75](http://forum.linux-ntfs.org/viewtopic.php?p=1572&sid=7e2ba87c68c9e2416cf6cc27aa2bca75) but the guy totally stonewalls on the HOWTO, which doesn't help a newb like me.

Is there anyone with some time who could walk me through how to access my spanned disks? I'd be SOOO grateful, i've spend soo much time on this.

Thank You.

---

### Post by RAOF on 2006-11-19
I'm pretty sure that the current NTFS drivers don't support that, sadly
[quote=lunux-ntfs.org]LDM - Tools
Tool 	Status 	Description
ldminfo 	Stable 	Display the database contents in a simple form
simple 	Beta 	Mount a single volume from a single partition
multi-volumes 	**Not started** 	Support NTFS volumes that span several partitions, e.g. Spanned, Stripes, Mirrors and RAID
dbtools 	Not started 	Read/write information from/to the database
ldmlib 	Not started 	Move all the common code into a shared library[/quote]

---

### Post by anixon on 2006-11-19
> **RAOF said:**
> I'm pretty sure that the current NTFS drivers don't support that, sadly

Hmm, that update may be a little outdated. In the linux-ntfs forums somebody asked about spanned disks and an admin posted this response (i have this linked to above, but i'll quote here so more people can see).

"Just compile the Linux kernel with the LDM partitioning driver enabled
then boot your system and your dynamic partitions will be recognized.

Then simply glue them together using software raid or the device mapper
in the Linux kernel as described in the ntfs kernel driver
documentation. It is in the kernel sources in
Documentation/filesystems/ntfs.txt."

It 'sounds' simple enough, unfortunately, I don't know how to implement the above said procedure... If anyone could walk me through how to accomplish this i'd be much grateful.

---

### Post by Azakus on 2006-11-19
Do you need to use NTFS for some reason? Linux doesn't like NTFS very much, and although it has some decent driver support, it still is very beta. I'd suggest that you just delete those partitions and try any other filesystem. Ext3, ReiserFS, XFS, they're all good. Then you can create a RAID array and use it from there.

---

