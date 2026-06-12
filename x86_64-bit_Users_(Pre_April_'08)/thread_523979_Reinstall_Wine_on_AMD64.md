---
title: "Reinstall Wine on AMD64"
date: 2007-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by framebuffer on 2007-08-12
Hello!

REF: AMD5200+ , Ubuntu 7.x updated to latest updates as you read

A few weeks ago, I installed wine on Ubuntu. Yesterday I formatted my installation (cause I messed up my display) and i tried to install wine again using synaptic but it said that wine is not for AMD64.

Now, I can install the 32 bit version of wine, but I am surprised why I am not able to reinstall it when I had did so before using synaptic.

Earlier it was not giving any problems.:confused: I also remember that it use to get updated automatically with weakly updates. So i believe its for sure i used synaptic.

Has it always been like this or am i dreaming? As far as I remember i installed wine using synaptic earlier. Also, no hardware modifications have been made. And I definitely didn't use the chroot method.

Please help to restore my memory.

---

### Post by DarkBring on 2007-08-12
Hello there!

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) has it that "packages for the 64 bit version of Ubuntu Feisty (7.04) are now available", but you need to use a hack to " install the 32-bit package into the 64-bit distribution and have it function normally". (the hack howto is at [http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64))

Perhaps you confused installing Wine64 with Synaptic and Wine32 through some other method? :confused:

---

### Post by Kilz on 2007-08-12
You can add the wine hq repository and install it with syanptic if you have Feisty. The 32bit version can be installed to, but I wouldn't call forcing in a package a hack.

---

