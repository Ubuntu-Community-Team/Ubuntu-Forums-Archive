---
title: "Save Settings"
date: 2009-05-25
forum: x86 64-bit Users
---

### Post by Bert_421 on 2009-05-25
I am new to Ubuntu.  I have been have problem with the video settings, when the Nvidia driver where installed the monitor would turn off am I would have a black screen, but I figured out the problem now. I have two monitors installed on the video card and Ubuntu would start with the small monitor (VGA) instead of the (DVI). I have been trying to save the setting but there is a problem (Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.) error keeps popping up. Needless to stay every time I start the computer the system starts with the smaller monitor.  
 

 _**What am I doing wrong?**_  
 

 My system
 Intel 6420 duo  
 Nvidia 7800 agp
 2 gb. Memory
 250 gb hd
 Gigabyte Motherboard   
 Ubuntu 9.04 64 bit dual boot Win XP 64bit

---

### Post by sisco311 on 2009-05-25
try to run nvidia-settings as root, press Alt+F2 and type:
```
gksu nvidia-settings
```

---

### Post by Bert_421 on 2009-05-25
Thanks that did the trick.

---

