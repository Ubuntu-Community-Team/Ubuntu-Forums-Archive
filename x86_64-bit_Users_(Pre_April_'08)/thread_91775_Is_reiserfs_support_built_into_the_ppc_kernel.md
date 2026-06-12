---
title: "Is reiserfs support built into the ppc kernel?"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by lazloman on 2005-11-18
Well is it? I just finished an install and can't boot because of a kernel panic caused by its inability to mount the root fs. I'm going to start over again and format to ext3 and see what happens. I'm installing on an old world beige g3 box.

---

### Post by slux on 2005-11-18
Yes, reiserfs has been working well for me on at least a couple of iBooks.

---

### Post by lazloman on 2005-11-18
Is it in the default kernel? I just finished the install, but can't boot into Linux. I double checked the boot partition/dev/hdb8 and set that up in BootX. But I get a kernel panic.

---

### Post by DJ_Max on 2005-11-18
If while installing you chose ReiserFS, than it was built with the kernel as a module.

---

### Post by lazloman on 2005-11-18
How does the module get loaded if the boot volume can't be mounted?

---

