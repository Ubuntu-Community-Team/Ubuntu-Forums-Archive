---
title: "Radeon X1600 PRO Reset"
date: 2007-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by josefnpat on 2007-03-25
Oh dear god. I've really screwed up Ubuntu. I have no experience with Linux, so please go slow.

Well, I have a RADEON X1600 on a AMD64 running a partition of Ubuntu 6.10 fully updated (today). Well, I ran some thing that asked me a bunch of questions in the terminal about my graphic card and monitor and keyboard (something about x server). Now, when I boot, I get "Failed to start your X server."

ironically, it says:

"Fatal sever error:
no screens found."

now it says my X Server is disabled, and I get the terminal of the system. Can you help me 
a) Reset my graphic drivers to the default
b) install my card.

Thanks in advance,
-Seppi

---

### Post by xdarkxanarchyx on 2007-12-21
Have you tried opening the terminal and typing ```
 sudo dpkg--reconfigure -phigh xserver-xorg 
``` If that doesn't work try typing ```
 sudo nano /etc/X11/xorg.conf 
``` and change the driver to **vesa** or **flgrx**. What are you upgrading from? 
Here's a link that may help. 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
This one looks a bit old but may help
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

