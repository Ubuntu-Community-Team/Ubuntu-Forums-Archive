---
title: "Wireless on HP dv6355us Laptop"
date: 2007-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Elliot.strumlauf on 2007-05-20
Hey, I have posted several questions on threads, none of which have been answered...
I just bought a new HP dv6355us laptop with a broadcom wireless card. I cannot simply add my network (WPA-personal and TKIP) for some bizarre reason, Ubuntu has always been pretty lousy as far as internet. My concern is that I hate Vista, love Ubuntu, but NEED wireless for college. Can anyone please help me set this up (I have no experience with any sorts of wireless). Thanks a lot!!!!

---

### Post by John Jason Jordan on 2007-05-20
> **Elliot.strumlauf said:**
> Hey, I have posted several questions on threads, none of which have been answered...
I just bought a new HP dv6355us laptop with a broadcom wireless card. I cannot simply add my network (WPA-personal and TKIP) for some bizarre reason, Ubuntu has always been pretty lousy as far as internet. My concern is that I hate Vista, love Ubuntu, but NEED wireless for college. Can anyone please help me set this up (I have no experience with any sorts of wireless). Thanks a lot!!!!
1) Which specific Broadcom chip is it? (Try "lspci" at a command line if you don't already know.)
2) Search this forum for "Broadcom" and it should turn up a long thread starting with a how-to for getting ndiswrappeer working with Broadcom chips. That is what I used to get my Broadcom 4306 working. I never could get the bcm43xx driver working. Sorry I don't have the thread bookmarked. :(

---

### Post by shad0w_walker on 2007-05-20
Are you using the broadcom drivers included with ubuntu? If your using fiesty the new version of them seem to be very good (Cant speak for 64bit ones as my laptop is only 32bit)

If you havent tried it yet i would recommend trying to this tutorial:

[http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx+easy](http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx+easy)

After i installed my drivers everything works nicely and i have WPA support. Good luck.

---

### Post by Elliot.strumlauf on 2007-05-20
Thanks for your reponses. I do not know which Broadcom I have, and I cannot run lscpi or whatever since I am in windows!!!! Thanks for the tutorial, I will try it out and let you know how it works out for me!

---

