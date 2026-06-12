---
title: "Any way to reinstall an earlier ver. of OpenOffice without reinstalling everything?"
date: 2008-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubersoft on 2008-03-05
This is making me CRAZY.

I've been playing around with the 64 bit Hardy Heron Alpha 5 release. During the course of this playing around I accidentally uninstalled OpenOffice... and now I can't re-install it, because some of the packages are 2.4 pre and some are 2.3.1.

I can't use the debian packages on openoffice.org because apparently they're intended for 32 versions of the OS. same with the RPMs, I suppose.

I can't install from the CD, because the install CD doesn't actually seem to have the deb packages.  I can't use the debs from my Gutsy DVD because dpkg claims they "aren't real deb packages."

It really seems like my only options are find the damn source and compile it myself, wait for the rest of the packages to update, or re-install Hardy.

I'd really like to find a fourth option. Is there one?

---

### Post by kuja on 2008-03-05
Option 4, grab  the packages that you need from archives.ubuntu.org (ouch), and sudo dpkg -i --force-downgrade open*.deb

Or similar might work.

---

