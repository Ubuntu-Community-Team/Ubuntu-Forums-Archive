---
title: "grub boot not working"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tank Biggun on 2005-10-16
Hey people. I just installed 5.10 64-bit on my comp and for some reason once it gets to the reboot stage it just goes straight to windows. I tried reinstalling incase grub wasnt installed properly, but it still doesnt work. Any ideas of a windows based boot manager i might be able to use??

---

### Post by LittleReinhart on 2005-10-30
Hey,

Do you have one harddisk with multiple partitions on? Or multiple harddisks with multiple partitions?

I don't have windows anymore, but I had a look-alike problem ones:

I have 3 harddisks:
[hda1: reiserfs(data)]
[sda1: swap] [sda2: reiserfs(ubuntu 5.10)] [sda3: reiserfs(data)]
[sdb1: swap] [sdb2: reiserfs(ubuntu 5.04)] [sdb3: reiserfs(data)]

I have installed grub into my master boot record (mbr). Now, because I did something wrong when I started using linux (long story :-p), I have two different grubs installed on sda and sdb. And my computer booted the wrong grub.
Solution: I had to go into my bios, and change the "boot-order"

In your case, I think the problem is that the mbr of your first harddrive is pointing to the windows startup script (boot.ini), and that grub or is installed on an other mbr (other disk) or isn't installed in the mbr at all.

So, I would say, change the boot-order in your bios (but remember how it is now, in case it isn't working).
And/or to reinstall grub in your mbr.

Greetings,
Reinhart

---

