---
title: "Memory problem"
date: 2008-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by j_dog on 2008-01-07
I have 2gb of dual channel OCZ ram that works fine. I decided to get another 2 gb of the same. The bios recognizes 4gb in dual channel 128 bit.  But I can not boot up. It just hangs on the boot splash.
 I remove it I'm fine. The modules are identical.  Any suggestions ?:confused:

---

### Post by ~LoKe on 2008-01-07
When the grub loader comes up, hit escape.  You should be able to edit your boot parameters.  Move down to the kernel line and hit "e", then at the end, remove "quiet splash", then hit esc again, then b to boot.  It should give some output.

---

### Post by ZootNerper on 2008-01-07
Hi,

Have you tried taking out the old memory and just using the new? Do you get the same problem?

-- Zoot

---

### Post by j_dog on 2008-01-07
Alright.......this new memory appears to be defective. Back to NewEgg it goes.    Thanks for your help .

---

