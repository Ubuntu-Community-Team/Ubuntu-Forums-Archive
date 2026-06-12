---
title: "Google earth, beagle and flash"
date: 2006-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by meanmrmustard on 2006-09-28
I used automatix to install all three programs but they won't run.

Google Earth will begin to start - the splash screen appears-  but then disappears and nothing happens.

The beagle deskbar-applet seemed to install and the daemon is running but there's no applet. Sun's 64 bit jre seems to be installed: 

java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)


In Firefox, about":"plugins shows that the shockwave flash player is installed but at youtube, when I try to play a video, I get the black window for a second then it becomes a gray box - no video.

This is Dapper 6.06 64 bit.
I'm not sure where to start to find the problem.
Any pointers?

---

### Post by hajk on 2006-09-28
Do you have an nVidia graphics board? Then tough luck... a known problem with the driver that nVidia was trying to solve a couple of months ago. You can download/install the latest driver from nVidia, or hope that it is included in Edgy.

---

### Post by Kilz on 2006-09-28
> **meanmrmustard said:**
> I used automatix to install all three programs but they won't run.

Google Earth will begin to start - the splash screen appears-  but then disappears and nothing happens.

The beagle deskbar-applet seemed to install and the daemon is running but there's no applet. Sun's 64 bit jre seems to be installed: 

java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_06-b05, mixed mode)


In Firefox, about":"plugins shows that the shockwave flash player is installed but at youtube, when I try to play a video, I get the black window for a second then it becomes a gray box - no video.

This is Dapper 6.06 64 bit.
I'm not sure where to start to find the problem.
Any pointers?

It sounds like Automatrix installed 64bit versions of java. It also appears that you are using the 64bit version of Firefox that comes installed by default.
I suggest clicking on the firefox link in my signature and getting 32bit firefox and plugins.

---

### Post by jtbl on 2006-09-28
Automatix installs gnash in 64 bit firefox which currently doesnt work with flash video.  To get adobe flash working, you must use a 32 bit browser.  Selecting the swiftfox browser and swiftfox plugins options in amd64 automatix will install 32 bit swiftfox and adobe flash for 32 bit swiftfox which will work with flash video.

---

### Post by meanmrmustard on 2006-09-28
hajk - yup! it's nvidia
jtbl - thanks

Kilz - read you tutorial... thought when I found 64 bit Java-jre and flash that it wasn't necessary any longer... oh well
Thanks for the tutorial and advice.

---

### Post by BLTicklemonster on 2006-09-28
Okay, so I saw "google earth" and figured this would be as good a place as any to put this...
OMG GERMANY'S BEING OVER RUN!!!

[http://maps.google.com/maps?hl=en&t=k&q=Germany&ie=UTF8&z=18&ll=48.857699,10.205451&spn=0.002404,0.006738&om=1](http://maps.google.com/maps?hl=en&t=k&q=Germany&ie=UTF8&z=18&ll=48.857699,10.205451&spn=0.002404,0.006738&om=1)

---

### Post by kleeman on 2006-09-29
Nah just the famous Schwaebische beetle.

"Sagen sie! Im Amerika gibt es ein Insekt overlord für sechs Jahre!"

---

### Post by BLTicklemonster on 2006-09-29
Pardon me, did you say Sasquashed Beetle?

---

### Post by JGuru on 2006-09-30
**Google Earth**,**Flash**, **Win32 Codecs**, **Java** are 32-bit
applications!!. Even if you install **JRE 1.5.0_08(64-bit)**, **Java Applets**
won't run , since the Java plugin is 32-bit!!!

The drawbacks are that Ubuntu, with APT (the package manager for Ubuntu), currently does not support BiArch, which means you likely won't be able to install and run 32bit packages on your AMD64 install. This is a problem for users who wish to use Flash, w32 codecs, and WINE (for example), as they are only available for 32-bit. There are possible methods of getting it running, but they involve creating a chroot (see [**DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)**), for example. Hopefully things should be fixed when **Ubuntu 6.10 Edgy Eft**
is released.

---

### Post by Mongoose on 2007-04-03
Apt isn't really the problem -- you can use lib32 installed applications.  In fact this is how I run wine packages right now by using --force-architecture and installing the deps in ia32.  I guess I'm saying if packagers wanted they could have wine in as a ia32 package already.  I mostly run GIT and the x86_32 packages at the same time for testing purposes.

I also have a lot of other appliactions installed this way, or in a ia32 'branch'.  Chroot is nice however for compatibility testing, or making packages for a certain arch.

---

