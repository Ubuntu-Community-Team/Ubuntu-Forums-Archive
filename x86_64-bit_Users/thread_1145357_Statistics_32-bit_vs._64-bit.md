---
title: "Statistics 32-bit vs. 64-bit"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by froling on 2009-05-01
I wonder if there is any official (or unofficial) statistics telling the trends of 32-bits vs. 64-bits Ubuntu downloads? Even better if there is statistics from the sources servers telling the ratio of 32-bit vs. 64-bits applications usages?

---

### Post by bford16 on 2009-05-01
I would be curious, too.  I know that many computers made these days are 64-bit, but they usually have a 32-bit OS installed.  All of my home computers are 64-bit, and I run 64-bit Ubuntu 9.04 on them.

---

### Post by jespdj on 2009-05-02
I have no idea about the download statistics, but I recently found a number in [this article](http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks) (from tuxradar.com about 32-bit vs. 64-bit benchmarks), and it says:
> Most Linux users run a 32-bit distro, and many of them run a 32-bit distro on a 64-bit computer. The question is, why? We put 32-bit Ubuntu 9.04 head-to-head with its 64-bit counterpart to see what difference it really makes, and whether old compatibility worries are justified.

Using TuxRadar as an example, we know that **77% of our visitors run a 32-bit Linux distro**, which is astonishing given that 64-bit Linux has been around for so long. All modern Intel chips support 64-bit out of the box - that's all Core 2 chips and all Core i7 chips, plus most Xeons and many Celerons. On AMD's side, all Athlon 64, Turion 64, Phenom and Phenom II chips also support 64-bit. But although Linux was first out of the door with support for these chips, early implementations were plagued with problems and extensive use of compatibility layers was needed to make things work.

No longer. Thanks to extensive testing and feedback from the community, 64-bit Linux is as stable as 32-bit Linux, so there's little reason not to use it unless you have a need for a specific, 32-bit only app. Even Wine happily supports 32-bit Windows apps such as Microsoft Office or Half-Life 2 running on a 64-bit Linux installation, and cross-platform mainstays such as VMware, VirtualBox and Java have already been ported.

---

