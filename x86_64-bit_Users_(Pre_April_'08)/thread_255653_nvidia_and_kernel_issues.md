---
title: "nvidia and kernel issues"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by blackrim on 2006-09-11
just clean installed AMD64 kubuntu on a machine that use to run AMD64 ubuntu but am having problems with nvidia. 
when i use method 1 from [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
everything seems to go ok, but when i reboot or restart the x server it hangs on the kubuntu startup (not login, before that) screen. so i boot into safe mode and it appears that even though i am running kernel 2.6.15-24-amd64-k8, nvidia-glx is being configured for kernel version 2.6.15-23-amd64-k8 and not the latest version.
so it works perfectly if i boot into the old version. 
any ideas?
i would prefer to use the nvidia from the repos not from nvidia (jst easier).

---

### Post by kuja on 2006-09-11
What's wrong with the version in the repos? Probably a lot easier to just use it, unless it's giving you trouble.

Edit: after re-reading things, I realize I had overlooked something. The proprietary nvidia drivers are tied directly to a specific kernel version, whichever you had it build against. In other words, it will only work with that kernel.

---

### Post by blackrim on 2006-09-11
yeah, i am trying to use the one in the repo. it is just configured (it would seem) for the older kernel. or mine apt is downloading the wrong one.

---

### Post by kuja on 2006-09-11
Check what version of linux-restricted-modules is installed, perhaps that's the reason it's installing the nvidia-glx for the slightly older kernel?

---

### Post by blackrim on 2006-09-12
that was it. the restricted is .23 and the kernel is .25 so i will stick with the .23 kernel for now.
thanks

---

