---
title: "DVD player"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by albertoramirez on 2006-01-20
Hello:

I've installed the xine player, but tried to play a DVD and it gets stuck, doesn't play smoothly, fluid.  Any advice?  :confused: 

Thanks in advance.

---

### Post by FluffyElmo on 2006-01-20
First, try enabling DMA for your DVD drive:
```
sudo hdparm -d1 /dev/hdc
```

Note that if you have more than one drive the location of your drive (/dev/hdc) may vary. If that doesn't improve things, you can try different video display methods. In Xine and Mplayer right click on the video, click settings and try changing methods (xv, opengl, etc). 

I haven't had to do that since I got a recent video card though, so I think it's DMA:)

---

