---
title: "Transparency on Kubuntu 6.06.1"
date: 2006-08-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by kubuntu on 2006-08-19
Hi im sorta a newbie, not to much but yea. Im having problems trying to get my translucency to work in my kubuntu 6.06.1, i have a AMD 64 bit processor, and my video card is an Nvidia 6100 (on board) 256 video card. I enabled everything for translucency but nothing works. Idk if its my v-card ...but ok if sombody could help me that would be wonderful, my email is [email]matt__1@hotmail.com[/email]:frown:

---

### Post by kuja on 2006-08-19
To get translucency to work, you'll likely need to add the following lines to the file /etc/X11/xorg.conf:

Section "Extensions"
Option "Composite" "Enable"
EndSection

Granted, there are issues with this. I've experienced crashes with this enabled. With XGL it seems to be a bit more stable, yet, it breaks opengl altogether (despite their being clever workarounds, I think it's just not worth the trouble).

Also, if you're planning on doing this, you'll need to be using the propietary nvidia driver or your performance will be really, really sluggish. So:
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

---

