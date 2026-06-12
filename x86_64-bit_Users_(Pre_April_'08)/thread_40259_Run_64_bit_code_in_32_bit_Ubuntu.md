---
title: "Run 64 bit code in 32 bit Ubuntu"
date: 2005-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by randomjunk on 2005-06-08
I installed the 32 bit version of Hoary on my Athlon 64 3400 machine, and it works wonderfully. But now I want to run a couple of 64 bit applications, but I can't get it working.

I tried the 32 bit chroot thing, but specifying --arch amd64 instead so as to get a 64 bit environment, which is what it then seems to download correctly.
But when it gets to actually running something it fails with "cannot run command `mount': Exec format error". I'm presuming this is a 64 bit version of mount and that it doesn't know how to execute 64 bit binaries.

Is there a quick solution to fix this?

Thanks.

---

### Post by c_dog on 2005-06-08
You need to be running a 64-bit kernel to run 64-bit code. The 64-bit kernel can handle 32-bit calls, but not visa versa.

---

