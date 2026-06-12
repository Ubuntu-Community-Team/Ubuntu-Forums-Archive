---
title: "AMD64 ndiswrapper issues"
date: 2006-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by UnseenMenace on 2006-02-04
After trying ubuntu / kubuntu 32 without any issues I decided to attempt to move onto Kubuntu 64 for my AMD64 3000+ Acer laptop.
I have since been attempting to get ndiswrapper to work and failed using the ndiswrapper-utils included with the distro.
I have since attempted to resovle this by following the information on 
[This Thread]("http://ubuntuforums.org/showthread.php?t=110749") without any joy.
Eveything appears to go ok and in the manner described in the thread however I still end up with the following error message.

> 
(Reading database ... 78237 files and directories currently installed.)
Unpacking ndiswrapper-1.9 (from .../ndiswrapper-1.9_1.9-1_amd64.deb) ...
dpkg: error processing /home/Desktop/ndiswrapper-1.9/ndiswrapper-1.9_1.9-1_amd64.de
b (--install):
 trying to overwrite `/lib/modules/2.6.12-10-amd64-k8/modules.alias', which is also in p
ackage linux-image-2.6.12-10-amd64-k8
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/Desktop/ndiswrapper-1.9/ndiswrapper-1.9_1.9-1_amd64.deb


Can anyone advise me of the problem please

---

