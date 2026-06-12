---
title: "nvidia driver makes system dead slow"
date: 2006-09-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravikm on 2006-09-16
hi,

i have nvidia Geforce 6100 on asus A8N-VM, with AMD Athlon 64 FX (3200+). the default ubuntu install has linux-amd64-generic with vesa driver for the video.

the nvidia drivers are getting installed. after restarting xserver, "glxgears -printfps" gives me about 10000, but i don't see any gears - only the RGB colours flashing randomly. system becomes unusable (dead slow/freezes) after few minutes.

any solution to this problem?

thanks,
ravi.

---

### Post by kuja on 2006-09-16
Does this happen with all opengl things? Also, can you show me what your /etc/X11/xorg.conf file looks like?

---

### Post by ravikm on 2006-09-17
> **kuja said:**
> Does this happen with all opengl things? Also, can you show me what your /etc/X11/xorg.conf file looks like?

glxgears -printfps slows down the system, firefox hangs the system, but mouse pointer moves. i don't know abt all opengl things. thanks to kilz i've installed wine, but no application other than notepad runs properly with the default video driver (vesa). following kilz's suggestion, i installed nvidia-glx, linux-restricted-modules & i have this freezing problem now.

i have attached the generic xorg.conf & xorg.conf after installing nvidia.

thanks,
ravi.

---

### Post by kuja on 2006-09-17
I'll keep looking around to see if I can find anything about it, but in the meantime, see if this will stop the freezing: ```
sudo nvidia-xconfig --no-render-accel
```

---

### Post by ravikm on 2006-09-17
> **kuja said:**
> I'll keep looking around to see if I can find anything about it, but in the meantime, see if this will stop the freezing: ```
sudo nvidia-xconfig --no-render-accel
```

thanks kuja,

no freezing now.

---

