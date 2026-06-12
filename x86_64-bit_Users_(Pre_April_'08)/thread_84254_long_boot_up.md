---
title: "long boot up"
date: 2005-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by summit on 2005-10-30
I am very new with Ubuntu or linux and was wondering why does it take so long to load up Ubuntu and is there anyway to bypass the login and password?

---

### Post by zox on 2005-10-30
You might have hardware problem, any failed services?

System/Administration/Login Screen Setup/ check Automatic login and make sure your user name is selected.

---

### Post by kmramki on 2005-10-30
Regarding the long bootup, check if the booting process stops at the msg "Synchronizing clock with ntp.ubuntulinux.org" or something similar to that. It might be that your computer is configured to sync with ntp server (which just gives u the current time) every time it boots. Then, if you are not connected to the internet when you boot, the process waits for quite some time, before it realizes that there is no network. :roll: 

If that is the problem, go System->Administration->Time and Date, and in the dialog, turn off the checkbox for "Periodically Synchronize clock with Internet Server"

As for ur second question, go System->Administration->Login Screen Setup. In the first tab, there is an option to automatically login a user at boot time.

HTH

Ramki

---

### Post by summit on 2005-10-31
I want to thank you Zox & Kmarmki. I tried several of your suggestion [automatic login & peridically synchronnize clock] and with doing these two I booted up again and what a difference in the boot time. 

Thanks again, Gary [summit]

---

