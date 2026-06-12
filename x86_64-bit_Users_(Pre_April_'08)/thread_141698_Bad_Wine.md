---
title: "Bad Wine"
date: 2006-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by llanitedave on 2006-03-08
I have a AMD64 system, nothing bleeding edge.  Kubuntu itself seems to be working fine.

I need to be able to use a couple of Windows utilities -- special-purpose programs for my other hobby, telescope making.  I've been assured by other telescope geeks that use Linux that they are accessing these programs using Crossover Office.

OK, I'm cheap.  I know Crossover Office is based on Wine, so I'll just install Wine and see if those programs will run on it.

I go into Adept and check the repositories.  Wine's not there.  I go to the winehq site -- turns out that to use it on an AMD64 device I have to compile it from source.  I follow all the instructions, but I'm getting errors every step of the way -- both activating universal repositories, and in the compile process itself.

Has any member of this group ever gotten Wine to work on an AMD64 system?  Is there any special trick I should know?

If I break down and buy Crossover Office, what assurances do I have that IT will install?

(I also tried the automatiks utility -- it hung befoe it started any downloads)

---

### Post by Terracotta on 2006-03-09
There are two ways you can install wine:
1) you use a 32-bit chroot
2) you install a 32bit version of wine you can find somewhere and do a force-install.

Since most windows programs are 32bit there is no use in compiling a 64bit version of wine. I must admit, I haven't been succesfull in getting wine to work, at all, not on my 64 bit mode nor in 32 bit. Buying Crossover Office, won't help this problem.

---

### Post by Jave27 on 2006-03-10
chroot is your best bet if you have any urge to hack at the wine sources at all.

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

Follow that, but make sure you install language-pack-en-base as well from inside the chroot environment before working with wine.

---

### Post by llanitedave on 2006-03-12
Thanks, guys.  I've at least got some direction to point now.

---

