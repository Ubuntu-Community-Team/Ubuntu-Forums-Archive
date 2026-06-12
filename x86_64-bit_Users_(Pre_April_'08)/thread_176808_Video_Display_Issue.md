---
title: "Video Display Issue"
date: 2006-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by VoiceOvGod on 2006-05-15
Having trouble with my display:

Using standard VESA drivers (Will be installing nVidia depending on the outcome of any advice I get).

When using the system, everything works fine, until (apparently) randomly, the screen becomes distorted and garbled. The only way that I can resolve it is to log out, then log back in, even then, it has the chance of occuring again.

I am thinking my X is not completely configured. 

In any case, any advice on what to look for or do would be greatly appreciated. Thanks!

---

### Post by Strangerdave on 2006-05-15
I know that you can type 

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask a series of questions, but it could be refresh rate?

-SD-

---

### Post by skylark on 2006-05-16
It is probably worth trying to install the binary nVidia drivers since they should provide faster 2D graphics and will support hardware 3D. As you suspect it also has a fair chance of resolving your issues too, and if it doesn't it at least eliminates one possible cause.

---

