---
title: "ndiswrapper + AMD64 + vista"
date: 2007-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bastaard on 2007-04-16
Hey guys,

My problem is the following: I have a 64bit AMD processor and would like to install 64bit Ubuntu (7.04). However, my wireless networking adapter (Speedtouch 121g drivers are [here]("http://www.thomson.net/TMS/Minisites/BAP/Templates/SubCategory.aspx?NRMODE=Published&NRORIGINALURL=%2fEN%2fHome%2fMiniSites%2fBAP%2fTelecom%2fSubCategory%2ehtml%3fcategory%3dDSL%2520Modems&NRNODEGUID=%7b90224E22-AD3D-4EB5-97B7-5558F14F156D%7d&NRCACHEHINT=NoModifyGuest&category=DSL%20Modems")) does not have linux drivers available and so I will have to use ndiswrapper. Now, I think I won't be able to use 64bit Ubuntu because 64bit ndiswrapper doesn't support 32bit windows drivers.

Is there any way for me to get this wireless dongle working in 64bit Ubuntu? I've thought of two possible ways myself: trying to use a 32bit version of ndiswrapper on 64bit Ubuntu, or trying to use the (64bit?) Vista drivers with the regular 64bit ndiswrapper. I don't think those ideas would work though. Any other ideas? Or should I just use 32bit Ubuntu?

Thanks!

Ps. Cross-posted this on the Networking & Wireless forum - [click here]("http://ubuntuforums.org/showthread.php?p=2462146#post2462146")

---

### Post by prince_niceguy on 2007-04-18
yes 64 bit OS will require 64 bit driver. check out if your wireless card manufacturer has a 64bit dirver for xp. if yes, then it should work without any issues.

apart from that i do not think of any other option.

---

### Post by Jouke74 on 2007-04-18
Uhmm you need a 64bit windows XP wireless driver for your card, the latest ndiswrapper (build it from source), Feisty Fawn AMD 64 in two or three days or Edgy AMD 64, lots of reading about where to put which file and parameter and some luck to get it working.

---

### Post by Rondom on 2007-04-18
I'd like to emphasize that you _need_ a 64bit-XP-driver. Vista drivers don't work (yet), and 32-bit-drivers neither-.

---

### Post by Bastaard on 2007-04-20
Hey thanks for the responses guys. I'll just install 32-bit Ubuntu, as there are no 64-bit XP drivers available.

---

