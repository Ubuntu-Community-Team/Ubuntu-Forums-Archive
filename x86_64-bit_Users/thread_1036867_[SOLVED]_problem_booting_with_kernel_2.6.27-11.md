---
title: "[SOLVED] problem booting with kernel 2.6.27-11"
date: 2009-01-11
forum: x86 64-bit Users
---

### Post by glennoph on 2009-01-11
I have recently have problems booting 2.6.27-11.  I am able to boot with -9.
The system is an older Compaq Presario laptop with amd64 processor.  

uname -a
Linux amd64 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

Are there logs to check?
Should I re-install -11?

Suggestions?

---

### Post by glennoph on 2009-01-11
I may have corrected the problem.  I noticed that the 2.6.27-10 kernel was not installed.  I installed it and was able to boot with 2.6.27-11.

---

### Post by Yellow Pasque on 2009-01-11
> **glennoph said:**
> I may have corrected the problem.  I noticed that the 2.6.27-10 kernel was not installed.  I installed it and was able to boot with 2.6.27-11.

You can mark the thread as solved then (under thread tools). Note that you don't need to install one kernel to get another to work. I suspect something went wrong with the dpkg/initramfs script when you installed the -11 kernel, and this coincidentally got fixed when you installed -10. You can remove the -10 packages if the -11 kernel works.

---

### Post by glennoph on 2009-01-11
I agree that installing one kernel may not have fixed the problem.  The problem recurred.  I then booted with the recover version of the kernel (sorry if my words are not accurate.  this is based on memory.)
I now believe that the problem was that X11 was not configured.  The system has Nvidia graphics adapter.  I ran 
nvidia-xconfig
and updated the /etc/X11/xorg.conf

It seems to be working now.  
Thanks for responding!

---

