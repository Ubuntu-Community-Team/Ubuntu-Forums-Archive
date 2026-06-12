---
title: "How do i get Opera browser on Kubuntu 64bit"
date: 2005-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zepticon on 2005-10-05
Is it possible, and how is it done?

---

### Post by mlomker on 2005-10-05
[QUOTE=Zepticon]Is it possible, and how is it done?[/QUOTE]

It isn't available in 64-bit, so it'd have to be run in a 32-bit chroot environment.  Chroot seems like a hassle to me, but there are [instructions on the wiki]("https://wiki.ubuntu.com/DebootstrapChroot?highlight=%28chroot%29").

---

### Post by gorod on 2005-10-07
Just download a binary installer with static qt library from opera's site. You might try to get a deb file with static qt and install it with dpkg -i --force-architecture opera*.deb so you can uninstall it later if you want.

---

