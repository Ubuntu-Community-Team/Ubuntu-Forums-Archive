---
title: "[SOLVED] Dual boot 8.10 with XP - Guided or manual"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by alt3rn1ty on 2008-10-31
Hi all I think I have a problem installing 8.10 on desktop.

I have prepared the HD with partition magic, its 160gb ata

C: partition for windows XP 25gb
D: partition for everyones documents/games 80gb
Free space around 50gb intended for Ubuntu 8.10

Downloaded the final 8.10 x64 distro and burned onto CD.

Distro verified and really slow burn

Boot from CD is fine, and did Ubuntu's own disc verification - No errors.

Problem = I now get to installing, stage 4, and only have the options to either use guided use entire disk 160gb, or manual.

No guided use only free space option. And dont want to trash XP and all users setup. Seems at this stage without going any further it is not recognising windows XP partitions. Any ideas?

---

### Post by Stunts on 2008-10-31
Hi there.
If you enter the manual setup, do you get to see all your partitions?
The manual partitioner is fairly simple. You just need to divide your free space into a swap partition (I advise the same as your RAM memory in case you want to use hibernation, otherwise 1-2Gb is more than enough in most cases) and a root partition ("/"). Just declare how much of your free space you want each of these to take, and you're ready to go.
Hope this helps.

---

### Post by alt3rn1ty on 2008-10-31
No if I choose manual and go forward it lists one partition of 160gb /dev/sda with the 'new partition table' and 'undo changes buttons', other buttons are ghosted out.

If I now reset windows will still boot (this is my third time round without applying any changes).

---

### Post by alt3rn1ty on 2008-10-31
More information - If I quit the install and just boot from the 8.10 CD, then look at Computer, the XP NTFS partitions are recognised. (Listed as NTFS 3.1 under properties volume).

Also I have previously had 8.04 on there, same configuration. Knowing 8.10 was coming out and XP was getting a bit slow, I decided to completely reformat/partition the HD with Partition Magic (from CD), then re-installed windows, updated to SP3, recovered all documents from backup to the second ntfs partition, then formatted the third partition, then deleted the third partition to free space for new 8.10 installation.

Since then I have this problem 8.10 not recognising the two NTFS and free space after during installation.

---

### Post by AteZ on 2008-10-31
Hi,

it seems the partioning tool did not create the partitions, following al the rules properly, so it looks like ubuntu does not recognise them.

if they are still Fat32 partitions, try to convert them into NTFS under XP. then retry the installation procure.( do not use partion magic tooling)

then there should be a good chance ubuntu can see them

---

### Post by alt3rn1ty on 2008-10-31
Could this have anything to do with Primary/logical partitions?, I think I may have made two primary ntfs, going to convert the second D: partition to logical and update the master boot record and see if that makes any difference.

I also just had a check with the old 8.04 and that has the same problem so I am assuming its something I have done with redoing the hd setup.

---

### Post by alt3rn1ty on 2008-11-01
Making progress - I think the problem was using an old version of Partition Magic which has NTFS bugs. I installed it on the HD instead then patched up to date.
Had to remap my second partition and redo all users file/device sharing, but the end result is the mbr has been updated properly and Ubuntu now recognises the two NTFS partitions.

So last question, I just want to be sure I do this the right way.

Back to stage 4 of the install of 8.10, I have...

c: /dev/sda1 16%
d: /dev/sda5 58%
free space 24%

The first guided option wants to use d:, resize it and use free space after. Which would leave my current free space untouched.

The second option is guided use entire disk, also not good

Third option Guided, use largest contiguous free space - correct me if I am wrong but I think this is what I need to use, the thing thats putting me off is the graphical representation of this shows the 'after' bar as using the entire disk aswell!

---

### Post by alt3rn1ty on 2008-11-01
Or if I use Stunts suggestion going through manual install instead does that still setup dual booting?. I am unsure of myself at this stage. I have installed before using a guided option but ended up with more partitions and a delete/resize problem. Also a strange sequence of hard drive labels. And I cant remember which one I chose last time for 8.04. This time with 8.10 I want to get it right first time utilising the free space.

---

### Post by Yellow Pasque on 2008-11-01
I hope you have your important data backed up.

You're on the right track. Do the manual partitioning. I take it you have about 35 GB free? 
Create a 10GB root partiton, mountpoint /
Create a 2GB swap partiton
Use the rest of the free space for /home

---

### Post by alt3rn1ty on 2008-11-01
Hi Temujin and thanks for giving the confidence to go ahead.

I have seen making a separate /home partition mentioned before and wondered why this is considered a good practise. Previously with 8.04 my home went into the same root partition (using whatever guided option I chose). I understand the need for a separate swap partition (going to use 2048mb). But I was hoping to keep everything linux apart from the swap partition confined to the one, so as not to present the family with a confusing array of partitions (should they be forced to use it, its intended to be a backup OS for everyone else and a learning curve for the kids (my eldest already recognises the security advantages, and prefers using GIMP in linux to windows).

But willing to defer to advice, is the setup of a separate /home partition better because you will never then run out of space in /root and endanger the OS in some way?

---

### Post by alt3rn1ty on 2008-11-02
Success - And 8.10 x64 working beautifully with my athlon 64 3400. I have multiple users setup, nvidia drivers for geforce 7300 gt, all external devices recognised and windows set as default OS boot.

Thank you all for the help, Atez got me sniffing out partitioning problems and the manual install was the best way ahead after all, I didnt doubt Stunts but at that time more serious issues needed sorting first. Hope this helps others who may be unsure with the installers presentation and what it will actually do with their setup. 

For a noob the graphical representation particularly the 'after' bar does not instill much confidence in some circumstances for instance choosing guided use only contiguous free space shows the after bar as using the whole HD, if it highlighted just the free space portion for ubuntu as what will be used, and the rest as XP untouched... oh well doesn't matter, now I am used to manual install and know it will not forget XP is installed I think this is the better way to go for finer control now.

---

### Post by alt3rn1ty on 2008-11-02
And bump .... edited content, more thanks and suggestion for installer. :)

---

### Post by Stunts on 2008-11-04
Hi! Sorry I didn't show up for so long!
I'm glad you got it all sorted out. Hope it's all working fine on your end, and I'm glad you felt like you have learned something.
Anyway, enjoy your new system! =-)

---

