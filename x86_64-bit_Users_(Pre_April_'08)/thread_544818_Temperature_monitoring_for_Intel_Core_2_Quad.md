---
title: "Temperature monitoring for Intel Core 2 Quad"
date: 2007-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Shadowtester on 2007-09-06
Is there any programs that will work with Kubuntu 7.04 64 bit to monitor the core temperatures on the intel core 2 quad I have tried ksensors but it will not monitor the core temperatures on the quad.

---

### Post by linuxwizard on 2007-09-07
Look at Super Karamba see if that will work for you, can be installed through repo. Go here to find & install widgets or some can be installed through Super Karamba.
[http://www.kde-look.org/index.php?xcontentmode=38&PHPSESSID=1df6e91dd8cab5bc5fadd312841f8260](http://www.kde-look.org/index.php?xcontentmode=38&PHPSESSID=1df6e91dd8cab5bc5fadd312841f8260)

Also do you have lm-sensors installed ?
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by Shadowtester on 2007-09-07
Yes lm-sensor is used by ksensor I will check out Super Karamba but if Super Karamba uses lm-sensor for its sensor source then it will also have the same problem as ksensor

---

### Post by Shadowtester on 2007-09-09
I installed Super Karamba and tried several of the themes but none of them seem to be able to monitor the Core 2 Quads core temperatures. Looks like they all use lm-sensors which does not seem to be able to monitor the Core 2 Quad. Any other ideas or possible solutions to monitor the core temps.

---

### Post by Shadowtester on 2007-09-09
Ok after doing a lot more research and reading about lm-sensors I found out I needed to configure them for my hardware. I used the instructions in the Quickstart documentation for 2.6 kernels. Here is a link that might help other core 2 dual and quad users.

[http://lm-sensors.org/browser/lm-sensors/trunk/QUICKSTART](http://lm-sensors.org/browser/lm-sensors/trunk/QUICKSTART)

Now if I knew someone who is good with Super Karamba and could create a widget to monitor the quads cpu usage and temperature for each core that would be great.

---

### Post by TheWizzard on 2007-10-26
> **Shadowtester said:**
> Now if I knew someone who is good with Super Karamba and could create a widget to monitor the quads cpu usage and temperature for each core that would be great.


[http://www.kde-look.org/content/show.php/Quad-Core-Monitor?content=61859&PHPSESSID=cae](http://www.kde-look.org/content/show.php/Quad-Core-Monitor?content=61859&PHPSESSID=cae)

---

