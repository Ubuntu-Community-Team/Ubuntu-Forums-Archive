---
title: "No common CD-ROM found"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by AlexTALL on 2008-06-12
**Issue:**
Unable to install Ubuntu Server 8.04.
After booting to the install disc, choosing keyboard layout and locale, the installer probes for my hardware and gives the message (paraphrased) no common CD-ROM device found.

**Troubleshooting:**
I have tried 'ls /dev' but could not find an appropriate device.
I have tried removing the 'quiet--' from the boot parameters (has worked with other issues).
I have been able to install FC9 with the same drive.

**Hardware:**
Mobo: ASUS P5E3 WS Pro
Proc: Intel Core 2 Quad Q9300 Yorkfield
Mem: 2x1GB DDR3
DVD-ROM: ASUS DVD-E616P3
CD-RW: NEC (no further model info available at the moment)

**NOTE:**
I will be able to provide more specific information later tonight after work. Also, thanks in advance for any help.

---

### Post by gwoodruff on 2008-06-12
You can check out this post " [http://ubuntuforums.org/showthread.php?t=777805](http://ubuntuforums.org/showthread.php?t=777805)  ". There are other problems that may make your drive unavailable, but if you see nothing that could be an optical drive in dev folder you probably have the same issue.

Gary

---

