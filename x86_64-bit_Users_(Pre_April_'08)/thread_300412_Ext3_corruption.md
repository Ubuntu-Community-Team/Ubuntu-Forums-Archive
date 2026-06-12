---
title: "Ext3 corruption"
date: 2006-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by jason_allen on 2006-11-15
Disclaimer: this is related to another post I did on the general forums.

Can anyone confirm that they either seeing or **not** seeing frequent ext3 corruption with dual core amd64 machines with high disk loads? 

Ever since upgrading to 6.06 (dapper) we are getting this really often (once every few weeks per machine) and I'm at a loss to understand what this is specific to (amd64? dual core? western digital drives?, etc...).

Thanks,

-jay

---

### Post by kuja on 2006-11-15
I've never experienced any trouble with corruption of partitions with either of my drives when using ext3 (or others for that matter). I don't think the problem is related to the processor, or the file system. I guess that leaves your drive, perhaps?

---

### Post by RFScheer on 2006-11-15
5 systems w/ ext3 on 6.06 or 6.10 (2 are dual-core).  Have never seen any problems like that, but then they only rarely reach high disk loading.

---

### Post by jason_allen on 2006-11-16
Thanks for the feedback!

> I guess that leaves your drive, perhaps?

I wish it was as simple as replacing a drive: I'm seeing this happen across single drive servers, software raid servers and even a hardware raided server.

Btw - regarding "heavy load", i'm talking 24/7 load average 4+ disk activity (not quite sure if that's **really** heavy or not).

---

### Post by kuja on 2006-11-16
Hmm, if you have the time, if ext3 is giving you so much trouble, why not try another filesystem? If the servers are fast XFS might be a good option.

---

### Post by John Jason Jordan on 2006-11-16
> **kuja said:**
> Hmm, if you have the time, if ext3 is giving you so much trouble, why not try another filesystem? If the servers are fast XFS might be a good option.
I have been having problems with ext3 on 64-bit Ubuntu off and on since I started using Linux a year and a half ago -- Hoary was my first Linux. My experience is only with my amd-64 laptop, single core. 

With Hoary I would get corruption about once a month. Luckily fsck would always fix things. still, it bothered me. I have used Windows NT/2000 computers since 1993 with ntfs and *never* had a filesystem problem. 

About six months ago I decided to speed up this laptop by replacing the original 60 GB 4200 rpm hard disk with a new 80 GB 7200 rpm drive. The computer is now a lot faster, but the filesystem errors continue. Currently I have been running for about a month without a problem. This is just a laptop that I use for school, so the load is not heavy. On the other hand, it is stopped and started an average of once a day.

I tried Reiserfs but could not get Ubuntu Dapper to run on it. It might be possible to install Ubuntu on a Reiserfs partition if the partition was already created before installing Ubuntu. But you can't create it with the installation utility.

---

### Post by kuja on 2006-11-16
One time I had trouble creating partitions in certain formats with the installer, only once. It had turned out the cd I tried to install with was in fact corrupt. The installer only gives you options of partition types it can actually create anyway & use anyway.

---

### Post by jason_allen on 2006-11-16
> I have been having problems with ext3 on 64-bit Ubuntu off and on

It's both comforting and yet disturbing to hear that someone else is seeing similar symptoms. Two cases doesn't indicate a wide-spread problem (yet?) -- but when it's happening to us so often and across multiple hardware...ugh.

We'll probably try XFS today and report back.

---

### Post by RAOF on 2006-11-17
> **John Jason Jordan said:**
> ...
I tried Reiserfs but could not get Ubuntu Dapper to run on it. It might be possible to install Ubuntu on a Reiserfs partition if the partition was already created before installing Ubuntu. But you can't create it with the installation utility.

Not the LiveCD, no.  The Alternate install CD allows you to format your partitions to ReiserFS.

---

### Post by Mongoose on 2006-11-17
I've been running on SATA with ext3 ( and eSATA ) on AMD64x2 for a long time now.  In fact this box has been running ubuntu 64 from day one on ext3 without problems.

---

### Post by jason_allen on 2006-11-17
Thanks mongoose,

Can i bug you for one more piece of data: how much stress does your computer have on its drive(s)?

---

### Post by Mongoose on 2006-11-17
I don't use it as a file server, but I often image disks and copy large vm disk images from SATA to eSATA.  I mainly use this box for development, so it's mostly gcc or apps that's doing the I/O.  I also rotate about 10GB of media files every week.  Hope that helps.  ;)

Edit:

Oops, it might help to tell you the controller..

nVidia Corporation CK804 Serial ATA Controller (rev f3)

---

### Post by Richard Sevenich on 2006-11-21
I've experienced ext3 corruption twice by repeating this sequence:
* install (or reinstall) edgy and use it for some days
* install a different distribution on a different partition
* next boot of edgy has fdisk bail out and boot stops with request that I perform repairs or else ctrl-D 

Kubuntu is on hda6.
The first time the 'different' distribution was debian etch rc1, installed to hda2. The second time the 'different' distribution was zenwalk 4.0, installed to hda2. 

Regards,
Richard

---

### Post by Richard Sevenich on 2006-11-21
Paying more attention, I see that fsck.ext3 is irritated because it cannot resolve UUID = string of numbers and dashes. Booting into another partition and doing a fsck.ext3 on edgy reports happiness.

This is an opteron chip, but running 32-bit edgy.

---

### Post by Richard Sevenich on 2006-11-21
and the log file grabs this portion of the boot monologue:

Log of fsck -C -R -A -a
Tue Nov 21 07:12:04 2006

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=fb023952-c816-4b82-b7b3-bb749b3b8d8a'
/dev/hda3: clean, 163148/2443200 files, 1516225/4885768 blocks
/dev/hda5: Superblock last mount time is in the future.  FIXED.
/dev/hda5: Superblock last write time is in the future.  FIXED.
/dev/hda5: clean, 104760/2443200 files, 1053472/4883752 blocks
fsck died with exit status 8

Tue Nov 21 07:12:04 2006
----------------

which is reported just after /dev/hda6 is found to be clean.

Richard

---

### Post by Richard Sevenich on 2006-11-21
Looks like this doesn't belong in this thread; not being a ext3 corruption issue. Manually edited the /etc/fstab to revert away from the UUID namings. System now completes boot happily, without intervention.

Regards,
Richard

---

### Post by Mongoose on 2006-11-21
I recently had to fix my UUID in fstab as well, but didn't post since I didn't think it was applicable.

---

### Post by jason_allen on 2006-12-05
Ugh!

This just happened again to another server. I'm at a loss to explain why our entire server farm is seeing this problem across different hardware. I can't think of anything else to blame than the OS (kernel/drivers). This is pretty maddening considering 6.06 is considered extremely reliable/stable. My options are:

1. Roll back to Ubuntu 5.x (6 months of no problems here).
2. Move forward to 6.10+
3. Different file system (xfs?)
4. Different OS (bsd?)

-jay

---

### Post by John Jason Jordan on 2006-12-05
> **jason_allen said:**
> Ugh!
This just happened again to another server. I'm at a loss to explain why our entire server farm is seeing this problem across different hardware. I can't think of anything else to blame than the OS (kernel/drivers). This is pretty maddening considering 6.06 is considered extremely reliable/stable.
I feel it important to update my earlier post in this thread. It may not help you resolve your problem, but perhaps it will help someone else.

The other day I tried to boot my laptop at the university. All that would come up was the Compaq BIOS splash screen. No Grub menu. After much gnashing of teeth (I had a presentation due in four hours and it was all on this computer), I thought things through and realized that if I wasn't getting past the BIOS, perhaps the problem was the hard disk.

It took some wandering about the university, but in the CompSci department help desk I was able to borrow a small phillips head screwdriver. I had previously upgraded the hard drive, so I knew how to get at it. I reseated it, after which the computer booted normally.

After this incident I started packing a small screwdriver with me. That turned out to be a good idea, as it happened several times again over the next several days.

Finally, after critical academic things were under control, I decided to take the drive out and inspect the situation. I discovered that the holes in the drive bay cover (which is what the drive is fitted into) are off by about 5 mm. In other words, the drive connector was not meshing fully into the connector in the drive bay.

I performed a bit of surgery on the holes in the drive bay cover so the drive would mesh firmly into the drive connector, and reseated the drive. That was several days ago. Ever since I have had no problems.

The long and the short of it is this: I think I was wrong to badmouth ext3. It is probable that the constant corruption I was experiencing was just due to a stupid hardware issue. Can't very well blame the filesystem software if the drive connection is erratic.

I have also had constant problems with the DVD drive not reading media properly. Sometimes whole folders on a disk are not visible. Again, when you insert media in the drive the hard disk light comes on as well. Perhaps the DVD drive problems are related to the hard drive problems.

So if you have servers that are experiencing problems, it may be a flaky drive or drive connection somewhere in the network. 

I just offer this as additional insight into the issue of ext3 filesystem corruption. Standard disclaimers apply. :)

---

