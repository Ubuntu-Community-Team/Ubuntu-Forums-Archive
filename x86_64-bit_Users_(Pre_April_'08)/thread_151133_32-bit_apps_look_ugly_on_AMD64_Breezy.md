---
title: "32-bit apps look ugly on AMD64 Breezy"
date: 2006-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ehsan on 2006-03-27
Hi all,

I have an AMD64 laptop, on which I have installed the AMD64 version of Breezy.  I have also set up a 32-bit Breezy chroot so that I can run some applications that are not yet available in 64-bit world (like Firefox with Flash Player and Wine).  All looks good, except that all apps that run from the chroot look ugly.

I have selected the Glider theme in system preferences, and I've also set up the Industrial theme for gtk1 (using ~/.gtkrc.mine).  These settings work well in 64-bit apps, but neither work in 32-bit apps.  I have created a bind mount point for ~ and /usr/share/themes, but it doesn't seem to help.

How can I maintain a consistent look and feel for both 32-bit and 64-bit apps?

Thanks!
Ehsan

---

