---
title: "nvidia kernel modules"
date: 2006-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by lacerado on 2006-11-27
when I install the current nvidia drivers (1.0-9629), I can restart gdm and everything is fine until I reboot.  Then X crashes on start with an API Mismatch error and reports a different version of the nvidia kernel module.

Why is the nvidia kernel module changing every time I reboot?  It works fine if I reinstall the driver and fire up gdm without restarting.

---

### Post by kleeman on 2006-11-27
Something must have gone wrong in the driver install. How did you install? I have exactly that version and the stock edgy kernel and mine works fine. I installed manually not from a repository.

---

### Post by lacerado on 2006-11-27
I downloaded the installer from nvidia's website.  I think the install is going fine, as it works just after install.  The problem seems to happen when I reboot... then I have to install again to load gdm.

---

### Post by kleeman on 2006-11-27
Did you follow the wiki howto about deinstalling the standard ubuntu drivers? 

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)


Sometimes unless you get rid of ALL the old stuff issues can arise. See the conflicting software removal section.

---

### Post by xopher on 2006-11-27
> **lacerado said:**
> I downloaded the installer from nvidia's website.  I think the install is going fine, as it works just after install.  The problem seems to happen when I reboot... then I have to install again to load gdm.

Make a ```
sudo depmod -a
``` after the install, to make sure the module sticks..

---

### Post by pla7ma on 2006-11-28
did you try to run this envy-scripts of tselliot? I had the same error message after the kernel update,and this script then downloaded the latest driver from nvidia and took care of this mess with kernel-modules version mismatch and all the blabla that you don't want to think of. under 32bit it worked immediately,under 64bit i must have made a mess before, I had to reinstall xorg and gdm.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

dpkg -i envy??.deb and so on...

---

