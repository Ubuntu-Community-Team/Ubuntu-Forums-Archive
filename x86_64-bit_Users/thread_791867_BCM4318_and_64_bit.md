---
title: "BCM4318 and 64 bit"
date: 2008-05-12
forum: x86 64-bit Users
---

### Post by arfink on 2008-05-12
Hey all! I have been using Ubuntu for almost 2 years now, and this 8.04 release is really great- 64 bit support is really quite up to speed as far as I can tell, and performance on my machine is very nice. Only one problem- the wireless for my bcm4318 is messed up. I should be getting 54 Mb/s but with the fwcutter option I only get 1 Mb/s. Also the previous fix using NDISWrapper is not working at all; is this a problem with the new modules in Ubuntu or is it a problem with 64 bit edition? In the past I used the 32 bit edition to avoid this problem, but I would like to keep the 64 bit if at all possible because of how nice it is in 8.04.

---

### Post by alcatris on 2008-05-12
From what I remember NDISWrapper did not work at all on a 64bit kernel.
--Later edit.
check this out : http://bcm43xx.spugna.org/index.php?topic=131.msg450;topicseen#msg450
U can use iwconfig to try and set the right rate for your wireless card.
do a  "man iwconfig" and check the rate parameter.
I've done some testing on my own and managed to mess up my card. so please do a 
ifwconfig wlan0 (if wlan0 is your wireless adapter ) and save the output.
Also please not that setting the parameters requires root privileges.
But no matter.. thanks to you I've discovered that I have a problem. My wireless card works at 2Mb/s. I had never noticed that because my internet connection is at 2Mb/s and over the local lan I only transfered small files and for backups is use external drives or dvds.

---

### Post by Junichiromayo on 2008-05-12
Before kernel 2.6.24 I used ndiswrapper both with Ubuntu and Debian amd64.

---

### Post by arfink on 2008-05-12
Yes, I have found the answer. (for my machine anyway)

For AMD64 users of Hardy, see this wiki page:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c8cbba1734885284e4f79c2054461c863169f1bf)

Yes, this guide does work. For the BCM4318 follow step 2a, and so the Hardy fix listed below step 3. I used the version .3 of the "making it permanent" and everything is golden now! Full 54Mb/s!

---

