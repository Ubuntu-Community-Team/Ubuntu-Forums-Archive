---
title: "No Display (Scolling squares + random colours)"
date: 2006-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by sayash on 2006-10-20
I just installed kubuntu 64 bit version on this system

AMD Athlon 64 3200+
ASUS M2N-MX - nForce 430 chipset with onboard geForce 6100

Just after install, my computer locked up with random scrolling coloured squares going around. Also, the results of 'lspci' show that none of the nforce hardware have been detected, including the ethernet interface.

I tried changing the X driver from nv to vesa and vga and also changing the resolution. Didn't help.

any ideas?

thanks,
sayash

---

### Post by kuja on 2006-10-20
Most of that hardware probably is detected, and just marked unknown, that's how it usually acts anyhow. Maybe the proprietary nvidia driver will work better for you?

```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

---

