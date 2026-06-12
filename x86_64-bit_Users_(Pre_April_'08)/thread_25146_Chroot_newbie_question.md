---
title: "Chroot newbie question"
date: 2005-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by deppingh on 2005-04-09
Hi All,
   I created a separate /home disk partition during install (/dev/hda2) while everything else was installed to /dev/hda1.  I've followed the instructions for setting up the chroot from this thread:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Everything is working, but I have a question.  Unless I'm mistaken the "/home" entry added to /etc/fstab in step 4 of the chroot howto points my /home into the new /chroot/home.  My /chroot resides on /dev/hda1.  Does this mean that I am effectively no longer using my initial /home partition I created on /dev/hda2?  This is an issue for me because if this is true I need to rethink how I partition my disk.

Any help would be appreciated.
Dan

---

### Post by edubarr on 2005-04-09
It should be ok if you are using the 'bind' option when mounting.

---

### Post by deppingh on 2005-04-09
Thanks.

---

### Post by gratefulfrog on 2005-04-10
i'm not getting this... do you have to create each users' home directory, under /chroot/home?  

and then when I run under chroot, I don't find my envt, in particular my X envt... any ideas?

---

### Post by deppingh on 2005-04-11
From what I've seen you do not need to create users in /chroot/home.  I can't comment on your environment question.  I followed the howto I mentioned above and I've setup 32-bit Synaptic/Firefox/flash with no problems.

---

