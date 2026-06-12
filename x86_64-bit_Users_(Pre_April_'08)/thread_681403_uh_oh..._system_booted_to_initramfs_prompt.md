---
title: "uh oh... system booted to initramfs prompt"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by inphektion on 2008-01-28
I booted up computer today after a clean shutdown yesterday and it came up and said couldn't mount /sys or /proc or /something/init... so I reboot and it came up in initramfs.   I had no clue what to do so I typed help and saw a sync command.  I typed that and rebooted again and it came up fine.

Now I'm worried is there something going wrong?  These are brand new seagate drives in a linux md raid1 using 64 bit and  XFS for all parititions.  Is there something I can check?

---

### Post by inphektion on 2008-01-29
I'm thinking, from my current research, it could always be that uuid in fstab.  how do I convert that to a /dev/sda or /dev/md0 to find out what mine is and I'll change it to that instead of the UUID thing...

---

### Post by Yellow Pasque on 2008-01-29
See this thread:
[http://ubuntuforums.org/showthread.php?t=675528](http://ubuntuforums.org/showthread.php?t=675528)

---

### Post by Yellow Pasque on 2008-01-29
> **inphektion said:**
> I'm thinking, from my current research, it could always be that uuid in fstab.  how do I convert that to a /dev/sda or /dev/md0 to find out what mine is and I'll change it to that instead of the UUID thing...
I just realized that I didn't read that correctly. Why would you want to mount by the path to the device instead of the UUID? In general, the UUID should be less susceptible to change. Nevertheless, the commands in the thread I linked to above will still help you convert if you wish.

---

### Post by inphektion on 2008-01-29
its seems from what I've read, even with kernel upgrades, its the UUID that is susceptible to change while I'm always going to boot from /dev/md0 on my system regardless of the UUID.

However this may or may not have been the cause of my problem.  In fact, I'm doubting it is cause then why would it have booted the second (actually third) time around.  I can't image me typing the sync command fixed it.

---

### Post by inphektion on 2008-01-29
hmm... I see what you are saying.  I see posts where people say their /dev/disk is changing and I see posts where people say their UUID is changing...

---

