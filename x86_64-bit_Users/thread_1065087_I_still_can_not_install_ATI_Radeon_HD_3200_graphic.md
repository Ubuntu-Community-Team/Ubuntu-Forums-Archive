---
title: "I still can not install ATI Radeon HD 3200 graphic driver"
date: 2009-02-09
forum: x86 64-bit Users
---

### Post by canh_nguyen on 2009-02-09
I have ATI Radeon HD 3200 card intergrated in mobo.

I tried many way to install driver for this graphic card but it still not work.
I tried install fglrx, envyng or driver(9.1) from AMD website.

But when I reboot after install my screen is blank with black color :( and I have to restore the xorg.conf to default.

Anybody have solution for me ?

---

### Post by Yashiro on 2009-02-10
[http://ubuntuforums.org/showthread.php?p=6709120#post6709120](http://ubuntuforums.org/showthread.php?p=6709120#post6709120)

---

### Post by soxs on 2009-02-11
I hav an 3300 onboard chip, and 9.1 works pretty fine.

Did you do ```
sudo aticonfig --initial --force
``` _after_ installing and _before_ rebooting?

Plx attach the output from ```
fglrxinfo
``` and```
 cat /var/log/Xorg.0.log | grep fglrx
```

---

