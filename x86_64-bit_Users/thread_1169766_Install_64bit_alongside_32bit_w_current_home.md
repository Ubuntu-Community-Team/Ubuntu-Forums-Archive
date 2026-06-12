---
title: "Install 64bit alongside 32bit w/ current /home?"
date: 2009-05-25
forum: x86 64-bit Users
---

### Post by ThePenguinKnight on 2009-05-25
Howdy all. I've got a Dell Inspiron 1520 laptop, which I have dual-booted with Ubuntu 8.04 Hardy alongside 32bit WinXP. When I set up Hardy, I created 3 partitions for it to use- one each for root, home, and swap (2gb)- as I was told this would enable me to upgrade/reinstall/etc without a complete wipe of the partition.

I'd like to play around with Ubuntu64. Is it possible for me to use part of my current home partition for Ubuntu64s root, and use the remaining home and swap without further alteration?

Thanks in advance :)

---

### Post by pixel :-) on 2009-05-25
First, and most importantly, backup your data, you are warned!!!!

Durring installation, choose the manual partitioning option (i don't remember the exact term)

you'll have to resize your old home, at this point something could go wrong and lose the entire partition. With the extra space format and create your root (/) partition(recommend ext3). Set /home and swap partitions, WITHOUT REFORMATTING.

---

