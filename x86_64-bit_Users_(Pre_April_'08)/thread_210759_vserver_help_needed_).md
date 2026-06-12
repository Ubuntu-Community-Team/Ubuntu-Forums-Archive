---
title: "vserver help needed :)"
date: 2006-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by vdvm on 2006-07-07
Hi,

I've installed vserver on a 64bit opteron server according to this tutorial:

[https://help.ubuntu.com/community/VServer](https://help.ubuntu.com/community/VServer)

I didn't use 'Build Yourself'.

The kernel i used: linux-image-2.6.15-26-amd64-k8

Everything seems to be working fine.
Currently i have 2 vservers running with Debian 3.1 32bit.


There are a few things that don't work as i thought.

vtop gives this error:
chcontext: tools were built without legacy API support; can not continue

How can i fix this?
Is it a problem if it doesn't get fixed?


DirectAdmin is running on one of my vservers.
It uses quotas to determine diskspace usage by users.
I can't get the quotas to work.
When i use: repquota /usr/sbin/repquota / i get these errors.

Mountpoint (or device) / not found.
repquota: Not all specified mountpoints are using quota.

Is there a way to fix this?
quota_partition=/


I hope that someone can help me with the 2 problems.
I would appreciate it.

Thank you in advance.

---

