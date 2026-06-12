---
title: "Problem with Dual LCD monitor in Hardy"
date: 2008-09-27
forum: x86 64-bit Users
---

### Post by wangjiajun on 2008-09-27
Dear everyone,

I just installed Hardy on my Toshiba L355D-S7815. My laptop's screen resolution is 1440*900. I also have another external LCD monitor whose best resolution is 1680*1050. From time to time, I would like to use the external monitor, but not always. 

With a NVidia graphical card in my previous laptop, I installed NVidia management software that I can identify the external monitor and set resolution for each individual one separately, as in Windows Vista. Right now I am using ATI Raedon 3100 graphical card, I am thinking about whether we have a similar software which do the same thing as NVidia case in Hardy. 


Thanks!

---

### Post by wangjiajun on 2008-09-29
Let me make some clarifications. 

What am I trying to do is to dynamically adjust my display setting in Hardy based on my ATI 3100 graphical card. 

My laptop uses ATI 3100 graphical card. When use laptop in my lab, I use my laptop's screen, called "lvds" in aticonfig. At home, I have a larger LCD monitor, I would like to use the external LCD monitor, called "crt1" in aticonfig. 

So, I guess each time I get home I would have to change the screen settings, connect to the external monitor and set the best resolution. When in the lab, I will have to stay with my laptop's monitor with a lower resolution. 

Are there any program that allows me to change output monitor easily, just like what windows does, or how can I write my xorg.conf, in a way that I do not have to do any change each time I get home and connect to the external monitor.

Thanks for any suggestion or advice!

---

