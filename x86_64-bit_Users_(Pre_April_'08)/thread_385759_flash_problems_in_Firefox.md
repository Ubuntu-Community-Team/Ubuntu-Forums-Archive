---
title: "flash problems in Firefox"
date: 2007-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by rootlinuxusr on 2007-03-16
A friend is running 6.10, trying to get flash working in Firefox. After spending hours trying to get a .deb installed I learned he had a AMD64-bit architecture, something I know nothing about. Is there a program that he can install to get flash sites to work on his system? We tried the i386 Trevino repository, but yeah, he has an AMD 64 bit. Thanks for the help ahead of time, you guys have saved me and my friends in the past a lot(mostly lurkers).

---

### Post by Kilz on 2007-03-16
> **rootlinuxusr said:**
> A friend is running 6.10, trying to get flash working in Firefox. After spending hours trying to get a .deb installed I learned he had a AMD64-bit architecture, something I know nothing about. Is there a program that he can install to get flash sites to work on his system? We tried the i386 Trevino repository, but yeah, he has an AMD 64 bit. Thanks for the help ahead of time, you guys have saved me and my friends in the past a lot(mostly lurkers).

The problem is that the 64bit browser in the 64bit version cant use the 32bit proprietary plugins like flash. The simple solution is to install a 32bit browser. Check out my signature for the link to my howto.

---

### Post by rajeev1204 on 2007-03-16
Hi

the simplest solution is nspluginwrapper !!

it lets u use 32 bit plugins in a 64 bit browser 

Follow these steps and u r good to go.


[http://www.ubuntuforums.org/showthread.php?t=324698](http://www.ubuntuforums.org/showthread.php?t=324698)

Dont forget to remove the old swf flash from repository and whatever file named libflash ....etc.. U need to download flash 9 and copy file libflashplayer.so to /usr/lib/mozilla/plugins . before running the above steps !

go to [www.youtube.com](www.youtube.com) to test install.

If u have any problems let me know .



regards

rajeev nair

---

### Post by Kilz on 2007-03-16
> **rajeev1204 said:**
> Hi

the simplest solution is nspluginwrapper !!

it lets u use 32 bit plugins in a 64 bit browser 

Follow these steps and u r good to go.


[http://www.ubuntuforums.org/showthread.php?t=324698](http://www.ubuntuforums.org/showthread.php?t=324698)

Dont forget to remove the old swf flash from repository and whatever file named libflash ....etc.. U need to download flash 9 and copy file libflashplayer.so to /usr/lib/mozilla/plugins . before running the above steps !

go to [www.youtube.com](www.youtube.com) to test install.

If u have any problems let me know .



regards

rajeev nair

I dont think its simpler than downloading a script and clicking on the script and choosing run in terminal. Even if it were, lets hope you dont also need a java plugin. Because nspluginwrapper doesnt support it.

---

### Post by rajeev1204 on 2007-03-16
hmm

---

