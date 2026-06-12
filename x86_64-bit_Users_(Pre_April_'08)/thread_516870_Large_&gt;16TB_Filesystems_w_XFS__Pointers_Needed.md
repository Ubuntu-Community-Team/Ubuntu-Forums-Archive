---
title: "Large &gt;16TB Filesystems w/ XFS?  Pointers Needed"
date: 2007-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by stevecs on 2007-08-03
I am looking for some insight here from others who may also have some very large filesystems.   I am running Ubuntu 6.10 on a core2duo (x86_64) platform with a areca hardware raid card which has 24 500GB drives (11.5TB raid-5) presented to the OS.  Currently this is being run under JFS which I plan on changing to XFS for the next rebuild (want the dump/restore filesystem backup options)


This is fine, my question is mainly about scalability/best practices et al. for ease of management.   I double my filesystem size about every 18months.  I'm looking to replace this current array here w/ 24 1TB drives probably in November at the current rate of growth.   This upcoming replacement is not going to last long (probably beginning of 2009 or so) in which case I'll need to at least double it again if 2TB drives are available then OR change to a SAS raid controller and use sas extenders to external SAS/SATA disk chassis.

Anyway, the questions I have are:

	- Filesystem layout/partitioning:
		There are basically two methods that I can think of for laying this out:
			- Use LVM2 and XFS
				- does LVM2 handle huge arrays?  (>100TB?)
				- This has more steps in growth (expand array on raid card, pvresize, lvresize, then grow the filesystem)

OR:
			- use XFS native (no partition table) on the raid volume
				- easier to expand as long as only one raid volume (expand array on card & grow filesystem)
				- ? faster/less overhead?  



	- Does XFS under x86_64 use 64bit inodes?
		- If yes, any tools/applications break w/ 64bit inodes (tar? samba?)


	- Performance considerations?
		- # of allocation groups?  How do you determine what is best?
		- how to calculate stripe alignment (assuming here that w/ 24-drive raid-5 (23 data drives) w/ chunk size of 128K that would mean stripe size of 2944k (=stripe width?) so would I do a sunit=256,swidth=5888  or am I all wet?



Or any other insights/pointers?    This is my first time into >10TB filesystems.

---

### Post by kuja on 2007-08-03
Suffaces to say that I'm quite jealous of that massive array =P~

---

### Post by praxis22 on 2007-08-03
somehow I doubt you'll get too many answers here that are of any use. You're probably better off looking at Sys Admin magazine or Linux Journal. This is is the sort of thing canonical get paid for, and most home users wont have that sort of setup or money.

---

### Post by stevecs on 2007-08-04
Tried linux Journal no luck and sysadmin no longer exists (they shut down due to lack of readership which sucks).   The large block device mailing list also is vacant.    There is a decided lack of venues to post such a question.   (I even work at an outsourcing company which has many large sans et al but none of my clients even have a single file namespace >2TB so I'm already 6x their size here at home.

---

### Post by praxis22 on 2007-08-04
Bugger! 

Sys Admin mag was good, oh well, I suppose they fell victim to too much competition from the internet and Linux magazines. Luckily I still have my archive CD :)

Anyway, I had a think today, have you thought of using zfs?

[http://www.opensolaris.org/os/community/zfs/docs/](http://www.opensolaris.org/os/community/zfs/docs/)

The pdf should tell you al you need to know.

It's available as part of part of freeBSD:

[http://wiki.freebsd.org/ZFS](http://wiki.freebsd.org/ZFS)

Or, of course OpenSolaris.

---

### Post by stevecs on 2007-08-05
I have a couple machines using ZFS at work (sun/solaris systems).   I don't want to switch from linux at home as I have way too many programs/scripts/customizations that I don't want to work my way through at this point to update.   If it was available under linux I may look at it but frankly would probably hold off due to the 'newness' of it and the less active support (sun supports issues on solaris 1st).    Which is why I'm looking at XFS or JFS both have been available on linux long enough to get some bugs worked out of them.  XFS seems to have more active support (and the dump/restore plus easy method for filesystem growth is real nice).

At this point I'm on the fence between XFS native and LVM&XFS.   Thinking that my current chassis has 24 drive bays in it which I'll fill.   Seeing how long it took the industry to go from 750GB ->1TB I highly doubt that we'll have 2TB drives in 2009 (probably 2010-2011 at the earliest) in which case I'll probably have to go to an external drive chassis at some point (probably w/ sas) in the next 18months.  LVM would help me do that with less hassle.

I'm still hoping that someone with some first-hand experience would chime in though.

---

### Post by RAOF on 2007-08-05
I've never dealt with arrays of that size, but I really like LVM.  It's fun to move your root filesystem around while it's still mounted :).

I'd be surprised if it didn't support what you wanted.

---

### Post by stevecs on 2007-08-06
I'm mainly concerned w/ the robustness of the solution and stability factors when dealing w/ very large arrays.  I've run into numerous problems pushing size limits (2TB, 8TB, 16TB, et al) with other solutions.   Now I'm going to 24-100TB+ and I frankly don't want to be the lone pioneer out in front drawing on the maps "there be dragons here".   ;)

---

