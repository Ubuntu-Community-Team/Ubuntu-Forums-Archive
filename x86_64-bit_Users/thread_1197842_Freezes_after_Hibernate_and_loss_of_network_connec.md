---
title: "Freezes after Hibernate and loss of network connectivity after Suspend"
date: 2009-06-26
forum: x86 64-bit Users
---

### Post by Th3_uN1Qu3 on 2009-06-26
When waking up from hibernate, after i get the password prompt, i get to type two characters at most then my keyboard stops responding. I can move the mouse around but i can't click anything, and the only solution is a hard reboot.

Also after waking up from Suspend my wired network will not work anymore. Unplugging/replugging the cable doesn't help, and the system needs a restart. So basically both Suspend and Hibernate are unusable. Any ideas?

---

### Post by siryuhan on 2009-06-26
After suspending, try doing a rmmod and then a modprobe on your ethernet card. I remember running into a similar problem in the past, reloading the device can sometimes help.

---

### Post by AClark on 2009-06-29
Sounds a bit like a problem many people have had related to various WiFi drivers and suspend.

Check out these two threads for a possible fix.
Specifically the SUSPEND_MODULES solution seems like the simplest and there is no real down side to trying it.
 
[http://ubuntuforums.org/showthread.php?t=1190881](http://ubuntuforums.org/showthread.php?t=1190881)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780)

I have used this on a couple of different Jaunty boxes with different WiFi drivers and significantly different symptoms with complete success in both cases.

Good Luck

---

### Post by Th3_uN1Qu3 on 2009-07-08
I have tried: /etc/init.d/networking restart and it didn't work. Killing and restarting Network Manager didn't work either. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780/comments/2](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780/comments/2)

^^^

That worked for me. :D Just replaced rt61pci with r8169 and everything is fine. Thanks!

---

