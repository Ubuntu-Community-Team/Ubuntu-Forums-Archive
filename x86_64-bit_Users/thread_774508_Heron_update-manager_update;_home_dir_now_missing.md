---
title: "Heron update-manager update; home dir now missing"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by figgles on 2008-04-29
HELP!

I have performed an upgrade to heron from gutsy using update-manager. My home directory is on its own partition. After running the updater from u-m, my system is now not "seeing" or finding my home directory/partition. In other words, I'm DOA. What can I do to restore this? Why is it missing after the upgrade?

Thanks in advance!

---

### Post by macaholic on 2008-04-29
I'm not positive, but I'm pretty sure you mount your separate home directory as /home on your current partition. Such a feat would be accomplished by editing your /etc/fstab (gksudo gedit /etc/fstab) and adding a line akin to this:```
/dev/sda2      /home            ext3         defaults       0          0

```
NOTE: the /dev/sda2 will vary depending on where the partition your home directory is located in. Hope that helps.

---

### Post by figgles on 2008-04-29
> **macaholic said:**
> /home            ext3         defaults       0          0
[/CODE]
NOTE: the /dev/sda2 will vary depending on where the partition your home directory is located in. Hope that helps.I saw that on-line but I was unable to mount /dev/sda2, despite it passing a gparted check. I went ahead and performed a fresh install of heron. The good news is that my home directory was unscathed; I just wish I knew why it broke during the update. Thanks!

---

