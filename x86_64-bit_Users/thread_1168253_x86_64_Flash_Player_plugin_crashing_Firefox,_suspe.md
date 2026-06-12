---
title: "x86_64 Flash Player plugin crashing Firefox, suspect proprietary NVIDIA video card d"
date: 2009-05-23
forum: x86 64-bit Users
---

### Post by davisch on 2009-05-23
I see this bug is documented on the Adobe bug tracking site -

[http://bugs.adobe.com/jira/browse/FP-1069](http://bugs.adobe.com/jira/browse/FP-1069)

There has been no action since early April.  The driver causing the problems seems to be the "legacy" card driver 173.xxx.  Since this appears to be only causing problems for us poor folks with legacy cards can I assume that my only solution is to buy a new video card so I can use the non legacy driver (180.xx)?

---

### Post by Kareeser on 2009-05-23
No dice with the updated driver. I have 180.51 and I can't use 64-bit flash. I've reverted to the 32-bit driver with npwrapper.

---

### Post by Anubis on 2009-05-24
I have no such issues with 64bit flash AT ALL. I wonder how people in these forums have their systems configured, because I just don't understand how you guys stuff stays broken , while I keep on humming along?

---

### Post by fooman on 2009-05-24
have you tried this guide for flash on x86_64:

[http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964)

---

### Post by davisch on 2009-05-24
I have upgraded my system to Ubuntu 9.04 Jaunty Jackalope and installed the Adobe native 64 bit driver (ver 173) just as described in the post below.  Flash does work properly on many sites - including youtube.com - but fails on many others like hulu.com and the huffingtonpost.com.  Firefox just closes - I have not trapped the error but it exhibits the exact behavior as described on the Adobe Bug Tracking page.  Many people with newer nvidia cards do not seem to have the same problem.  I feel certain that my only solution is to upgrade my video card - or just skip most flash content.

---

### Post by Clancy_s on 2009-05-25
> **Anubis said:**
> I have no such issues with 64bit flash AT ALL. I wonder how people in these forums have their systems configured, because I just don't understand how you guys stuff stays broken , while I keep on humming along?

Some of the problems are specific to certain graphics cards...

---

