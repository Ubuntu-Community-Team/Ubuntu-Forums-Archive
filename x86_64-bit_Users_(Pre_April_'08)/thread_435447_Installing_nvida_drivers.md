---
title: "Installing nvida drivers"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by colin59 on 2007-05-06
I followed the directions found at [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) . It seemed to be okay after restarting gdm. but after a reboot i get a blue screen that says "failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"  Then when i hit Yes it says that the error is "API mismatch: the NVIDIA kernel module has the version 1.0-7184, but this X module has the version 1.0-9755. Please make sure that the kernel module and all NVIDIA driver components have the same version. 

Now, i ran apt-install and it only updated it to the 7184 driver, i went to the vendor's site and got the 9755 release. I followed the directions on the faq, but i guess it didn't update the kernel module, how can i remedy this now?

---

### Post by colin59 on 2007-05-06
I found the problem. Now my system works fine, Thanks.

---

### Post by twistedneck on 2007-05-13
If you found the problem what was it?  I have the same problem and need a solution.. hence these forums exist.

Please post what you did to solve it.

---

### Post by LuisGMarine on 2007-05-13
Yes please post what the fix was, I'm about to install Ubuntu 64-bit and if I run into this problem I want to know what to fix!

---

### Post by twistedneck on 2007-05-13
> **LuisGMarine said:**
> Yes please post what the fix was, I'm about to install Ubuntu 64-bit and if I run into this problem I want to know what to fix!

Got it! :guitar: 

works great.. problem is its installing the glx driver first and then the legacy driver over the top of it.. it only looks at the last one.. hence it thinks 9755 driver is not installed, but it really is..

[https://bugs.launchpad.net/ubuntu/+bug/107646](https://bugs.launchpad.net/ubuntu/+bug/107646)

----
Yongsu Park  said:

I found the reason. When the script /sbin/lrm-manager (executed by upstart during boot on /etc/rcS.d/S07linux-restricted-modules-common) loads kernel modules, it loads all so nvidia, nvidia_legacy, nvidia_new will be loaded, respectively. So after loading nvidia, loading nvidia_legacy and nvidia_new has no effect. Essentially, loading them all is not appropriate. I found useful script /sbin/lrm-video but I cannot find what uses it. I think lrm-manager should behave differently to fix this problem.

Workaround: Modify /etc/default/linux-restricted-modules-common to skip unnecessary kernel modules. For new driver (9755) users, the content is

DISABLED_MODULES="nvidia nvidia_legacy"

---

