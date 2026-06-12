---
title: "Automatic HFS+ Partition Mounting on Startup?"
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by AlphaMack on 2006-03-24
I tried searching this to no avail, but what I did was edit my /etc/fstab to include my HFS+ partition in the list of devices to enable (from what I did search about making HFS+ appear in Ubuntu):

/dev/hdaX /mnt/hdname hfsplus user,noauto 0 0

I have to manually mount it via System->Admin->Disks, which is fine by me, but there has to be an easier way. ](*,)

I just want to have it already up and running by the time I login...

---

### Post by tidris on 2006-03-24
I belive the problem is that you specified the "noauto" option, which means not to mount automatically at boot time? On my fstab I use "defaults" for the options and the HFS partitions show up on the desktop when I log in.

---

### Post by AlphaMack on 2006-03-25
Doh...I'm such an idiot.  Thanks.  It mounts now. :)

---

### Post by CSMatt on 2006-04-21
I have a question that I would like to add.  How do I get the HFS+ partition to appear as a disk drive in the Computer window now that it mounts at startup?

---

### Post by AlphaMack on 2006-04-21
I'd like to know this too, since I already have my partition bookmarked in Nautilus.

---

### Post by CSMatt on 2006-04-23
Never mind.  I think I found out the solution.  You have to add "rw" to the options so that it reads "rw,user,auto" instead of just "user,auto."

---

### Post by Rxke on 2006-04-24
noob question: how can I, from Linux, scan my peripherals to see which partitions there are (I mean, I know I have a partition on another disk I want to mount, but I'm not sure about its name...

---

