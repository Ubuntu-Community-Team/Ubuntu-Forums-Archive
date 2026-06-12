---
title: "NVIDIA 7900 driver install"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-08-28
Someone must have been through this before. I've downloaded the latest driver for NVIDIA but need help installing. I managed to get through the x-terminal problem by exiting with ctr-alt-F1 and ran the .run package I downloaded. I got through the several prompts and was stopped by not having "cc" in the path. GCC is installed. Any suggestions???

---

### Post by kuja on 2006-08-28
Sounds like you're trying to do it the hard way to me.
Try installing the nvidia-glx package, which is in Ubuntu's restricted repository, I believe.

```
sudo apt-get install nvidia-glx
```

---

### Post by mrw on 2006-08-28
I understood that the Ubuntu driver was not up to date and that I needed a later version for the NVIDIA 7900

---

### Post by kuja on 2006-08-28
The Nvidia driver in the repositories isn't the latest out, however, according to [this](http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-a.html), the 7900 should be supported by the older 1.0-8762 driver.

---

