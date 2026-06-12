---
title: "Reinstall nvidia drivers with each boot"
date: 2006-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by rugmonster on 2006-10-13
Every time I reboot my system running Dapper and the stock AMD64-K8 kernel, I have to reinstall the nvidia drivers. It's like the system is losing the kernel module. I am installing the standard drivers from Nvidia's site and I do not have the nvidia-glx package install. nvidia-kernel-common is installed as part of the restricted modules package. It's not a huge problem, but I know my wife will freak out if she turns on the computer in the morning and sees that.

---

### Post by krylko on 2006-10-13
try removing nvidia-kernel-common and then installing it again, but kdm should be stopped.

1) Ctrl+Alt+F1
2) sudo /etc/init.d/kdm stop
3) sudo apt-get remove nvidia-kernel-common
4) sudo apt-get install nvidia-kernel-common

It fixed it in my case, and I keep having the same problem each time I upgrade kernel.

---

