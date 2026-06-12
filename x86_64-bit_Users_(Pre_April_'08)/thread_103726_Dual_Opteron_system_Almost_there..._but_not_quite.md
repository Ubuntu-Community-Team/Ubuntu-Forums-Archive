---
title: "Dual Opteron system: Almost there... but not quite"
date: 2005-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by MagicNo14 on 2005-12-14
I have installed ubuntu 5.10 64 bit on my Java workstation W2100z. For those of you unfamiliar with the system, it is a dual AMD opteron system. Anyhow, like many others on the forum I have struggled to get Ubuntu to recognise the second CPU. 

I finally succeeded when I installed the latest stable Linux kernel with lvm enabled as suggested elsewhere on this forum. For those of you don't know how to do this, just follow [this excellent post]("http://ubuntuforums.org/showthread.php?t=85064&highlight=SMP")

However there is one (small?) issue that I would still like to sort out. During startup my system hangs for about a minute and then returns with the message:

FATAL: Module ext3 not found

In the post i mentioned it specifically states what to do to build ext3 into the kernel itself instead of using it as a module. (replace the 'M' in front of 'ext3 journalling filesystem support' by a '*'. However, I did this and it does not seem to have any effect. Am I missing something here?

All help appreciated!

---

### Post by MagicNo14 on 2005-12-19
Bump.... :p

---

