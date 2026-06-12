---
title: "Nvidia not install after kernel update"
date: 2007-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by kiev on 2007-05-29
I run:
sudo apt-get install nvidia-glx-new nvidia-kernel-common
sudo nvidia-glx-config enable

however:
sudo modprobe -r nvidia
FATAL: Module nvidia not found.

And:
cat /etc/X11/xorg.conf
 Driver          "nv" (!!!)
why did not change xorg.conf? must I change him hands?

how now to do?
Please Heeelp!!!!!

(kernel 2.6.20-16)

---

### Post by kuja on 2007-05-29
Not sure, but if you're running 6.10 or 7.04 try running ```
sudo nvidia-xconfig
```

---

