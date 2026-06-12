---
title: "Google Earth Performance"
date: 2007-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by mwacky on 2007-11-13
Google Earth performance with AMD64 edition of Gutsy is very poor, it is quite choppy.  I have the ATI driver enabled, why was my performance on par with Windows on 32bit Feisty but so bad with AMD64?

---

### Post by mwacky on 2007-12-05
Performance was much better from 32bit, one thing I notice is with the ATI driver in 64bit google earth wanted to run in OpenGL mode and would throw a warning, from 32bit that warning never appears and works flawlessly.

---

### Post by saru411 on 2007-12-05
im unsure of why you have issues but a simple search on the 64bit forum produced this thread([http://ubuntuforums.org/showthread.php?t=544064&highlight=google+earth](http://ubuntuforums.org/showthread.php?t=544064&highlight=google+earth)). another thing is if you do not know ati<nvidia when it comes to keeping up to date drivers for linux, although im not sure that would be your issue(however some have had the samem issue concerning ati cards acording to one person on this post [http://ubuntuforums.org/showthread.php?t=571930&highlight=google+earth](http://ubuntuforums.org/showthread.php?t=571930&highlight=google+earth)).

---

### Post by mwacky on 2007-12-05
> **saru411 said:**
> im unsure of why you have issues but a simple search on the 64bit forum produced this thread([http://ubuntuforums.org/showthread.php?t=544064&highlight=google+earth](http://ubuntuforums.org/showthread.php?t=544064&highlight=google+earth)). 

No problems installing the program on either architecture,


> **saru411 said:**
>  another thing is if you do not know ati<nvidia when it comes to keeping up to date drivers for linux, although im not sure that would be your issue(however some have had the samem issue concerning ati cards acording to one person on this post [http://ubuntuforums.org/showthread.php?t=571930&highlight=google+earth](http://ubuntuforums.org/showthread.php?t=571930&highlight=google+earth)).

The issue has nothing to do with installation, I think it's the graphics drivers difference, 32 v 64.  I have the latest driver directly from ATI on the 64bit setup, I used the driver from the restricted driver manager on 32bit, the issue is GoogleEarth runs flawlessly with 32bit and is choppy in 64bit.  Google Earth throws the OpenGL warning because it is not fully recognizing the graphics driver.  Linux Google Earth will not even launch without a graphics driver setup, it will hang on the splash screen.

---

### Post by RAOF on 2007-12-06
> **mwacky said:**
> ...
I have the latest driver directly from ATI on the 64bit setup, I used the driver from the restricted driver manager on 32bit, the issue is GoogleEarth runs flawlessly with 32bit and is choppy in 64bit.  Google Earth throws the OpenGL warning because it is not fully recognizing the graphics driver.  Linux Google Earth will not even launch without a graphics driver setup, it will hang on the splash screen.

You may not have got the IA32 OpenGL libraries installed if you've used the ATI installer.  If you don't have those you won't get 3D accel for the 32bit Google Earth binary.

Also, the very latest (7.11, aka 8.43.something and 7.10 aka 8.42.something) drivers seem to be rather poor, and have changed the way 3d accel is done by the drivers.  It's now done through the mesa library's architecture, so having an old ATI driver install, which will have broken mesa, will probably break the new drivers too.

I'd be guessing you have a badly installed driver problem.  It might be good to try to uninstall your manually installed driver & use the restricted manager.

---

### Post by mwacky on 2007-12-06
> 
I'd be guessing you have a badly installed driver problem. It might be good to try to uninstall your manually installed driver & use the restricted manager.

Thanks!  I have the 8.42 driver, probably better to roll back.

---

