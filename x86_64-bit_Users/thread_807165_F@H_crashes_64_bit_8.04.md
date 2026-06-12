---
title: "F@H crashes 64 bit 8.04"
date: 2008-05-25
forum: x86 64-bit Users
---

### Post by Amshu on 2008-05-25
Hello. Just started folding on my quad core with 64-bit 8.04 installed. F@H 6.10 smp 64-bit beta2 starts up runs then in about 15 to 20 minutes locks up the OS. It's not leaving any error messages. Or if it is I don't know where to find them. Any help would be greatly appreciated. Would really like to put this machines extra power to good use.

---

### Post by soxs on 2008-05-25
In case you own an ATI card, you might upgrade to the latest catalyst driver 8.5, they fixed any crashes I had so far. (Using an 3870 RadeonHD factory OC by Club3D, running hardy x86_63)

In case the cause lies somewhere else, you should have a look at all .log files in /var/log ; especially /var/log/Xorg.0.log (logging from the xserver init aswell video-driver init)

---

### Post by Amshu on 2008-05-25
I'm using the nvidia beta driver. This version of F@H is console only so I doubt that it is graphics related. Just to rule it out though I'll try running it with x stopped and see what happens. I'm also going to check those log files and post if I find anything. Thank you for the help.

---

### Post by Amshu on 2008-05-25
well running it with X stopped allowed me to see the errors. I get cpu machine check exception. on multiple cpu's. I also get kernel panic. it seems to happen when it completes a percent and writes to disk.

---

### Post by dicecca112 on 2008-05-25
if your overclocked drop the oc a bit.  Could be overclock unstableness

---

### Post by Amshu on 2008-05-25
I'm not overclocked. But this gigabyte mobo has some auto options that might overclock on its own I will turn them off and see. When it lockedup it said to look in mce.log but I can't find that file. Thank you

---

### Post by Jouke74 on 2008-05-26
F@H 6.10 smp 64-bit **beta2** starts up: It probably isn't a beta client for nothing. Does the non-beta client 6.09 run stable? I suggest you report this also to the people who make the F@H client. 

Best wishes, Jouke.

---

