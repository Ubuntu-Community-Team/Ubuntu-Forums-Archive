---
title: "Ubuntu-9.04 64-bit raid or not to raid"
date: 2009-10-01
forum: x86 64-bit Users
---

### Post by Richard Carlson on 2009-10-01
Just wondering if it would be worth the effort to set up a raid 10 (striped and mirror raid) on two identical 500 gig drives with 64-bit Ubuntu 9.04. First of all:
 (1) Will it be worth the work and effort or be a big pain in the butt? 
(2) Will I see any performance enhancement ? 

If you've done it successfully let me know the in's and out's and what you're feelings
are. Any help and comments would be appreciated. 

I'm running an old 4200 dual-core 949 pin Amd processor, 4 gig of ram, nvidia  video card using an Asus A8N-SLI motherboard. 

Rich

---

### Post by Slim Odds on 2009-10-01
Well.... for starters..... RAID10 requires at least 4 drives.....

---

### Post by Richard Carlson on 2009-10-01
I stand corrected. . . . .raid 10 does require 4 drives. I guess then I meant  raid  0 and or 1 raid configuration (2 drives) without parity. Is either going to increase read/write performance? I suppose that even the smallest error on raid 0 will crash the system.  So is there anything to be gained with either type? And has anyone tried either with success with Ubuntu????


Rich

---

### Post by mattkoehn on 2009-10-01
This is one of those topics that is more in depth than seems from the start. In general yes, it is better running on a raid. However, there are server caveats. And all of this is just what I have gathered over the time I've researched the topic and could be incorrect.

Raid 0 of course isn't good if it is on your data partition, as you are increasing your likelyhood of a failure. But that is basic.

If you don't have a raid card, you aren't running a real raid and it will never be max performance. Like the on board nvidia raid cards aren't real raid cards as they require a software driver. For linux its the dmraid. But it works great under 64 or 32 bit.

Doing the disk tests for read/write performance there is a significant jump for every disk I've added up to 4 disks in a raid 0. However, there is much speculation how much that number matters to real world usage. Even disk copies don't really function the way read/write tests function I've heard.

In linux it is super easy to do. Google 'faidraid howto'.

---

### Post by fjgaude on 2009-10-01
I've found that using **mdadm** is a great way to get the benefits of raid. With two drives raid0 doubles your throughput, I/O speed, but cuts your reliability in half over that of one drive.

Now with raid1 your double your reliablity but without any speed increase or decrease.

I use raid5 with four drives and my speed is three times that of one drive alone. I love it! I use the array only for data.

---

### Post by Tanker Bob on 2009-10-01
I recommend mdadm and RAID1 for both flexibility, simplicity, and safety. I have tried NVidia fakeraid with dmraid as well as mdadm to set up RAID1 on my system under Ubuntu. The performance of both systems seemed the same, but mdadm proved more flexible. Either one is launch-and-leave as long as you don't mess with the setup.

When I changed motherboards, the NVidia fakeraid wanted to wipe both of the drives! That's when I switched over to mdadm, which had no problems picking up the drives once I straightened out the superblocks. That switch isn't for the faint of heart. Backup regularly and always before major changes!

---

### Post by Slim Odds on 2009-10-02
> **fjgaude said:**
> Now with raid1 your double your reliablity but without any speed increase or decrease.

Actually, RAID1 will double your read speeds (or, at least, it should if it's working properly).

I'm using mdadm for RAID0 and the speed is great. I know about the "reliability" issue and I'm not worried. It's a home desktop and I have a good backup strategy. I wanted the speed.

BTW, RAID1 is **NOT** a backup strategy. It is a strategy to provide maximum UP TIME. On hot swappable systems, there is no down time when replacing a failed drive. That is the real use for RAID1 (and many others). 

I'll say it again, redundancy is not backup!

---

### Post by dcstar on 2009-10-03
> **Richard Carlson said:**
> I stand corrected. . . . .raid 10 does require 4 drives. I guess then I meant  raid  0 and or 1 raid configuration (2 drives) without parity. Is either going to increase read/write performance? I suppose that even the smallest error on raid 0 will crash the system.  So is there anything to be gained with either type? And has anyone tried either with success with Ubuntu????


RAID 0 is **ANTI-RAID**!, there is no additional redundancy whatsoever with RAID 0 (striping) so it actually never (ever) be grouped with any other configuration that actually provides redundancy.

You halve your MTBF with RAID 0 and basically double the chances of losing your data because if **either** of the drives fail you lose **all** of your data.

---

### Post by Slim Odds on 2009-10-04
> **dcstar said:**
> You halve your MTBF with RAID 0 and basically double the chances of losing your data because if **either** of the drives fail you lose **all** of your data.

Yes, we understand this. That does NOT mean that it is not useful. If you lose **all** of your data, it means you didn't have a BACKUP.

As I've mentioned on many occasions, RAID is NOT a BACKUP SOLUTION.

MTBF's for hard drives is pretty long these days, so even halving it is quite acceptable to those of us who want better disk I/O performance.

For a home desktop system, RAID1 is just a wasted disk drive.

---

