---
title: "New to Linux"
date: 2008-06-04
forum: x86 64-bit Users
---

### Post by Sao Paulo on 2008-06-04
Hi, I'm going to be installing Ubuntu in a day or two and just need to know if I can have a smiliar setup to XP in regards to my network bridge.  I have three eithernet cards including the one I use for net access and the other two are shared by the 360 and my sons computer.  Also if it can be done is it easy or one of those long winded linux things you hear about ?

---

### Post by Melk79 on 2008-06-04
I would say the simple answer is "Yes."  How much work it would take to get it setup is hard to say.  I've had much better luck at networking with Linux/Ubuntu than I've ever had with Windows, but I haven't done bridging.  I found what seems to be a good [link]("http://www.linuxfoundation.org/en/Net:Bridge") for reading about it however.

For me, the "long winded" aspect of Ubuntu has simply been learning a new OS.  That does take some time and effort, but it has definitely paid off.  I would say you should research your ethernet cards some for compatability, etc. and see if the indicators give you a good feeling.

---

### Post by Sao Paulo on 2008-06-06
Thanks Melk79, I did try Linux out yesterday but after having my first problem I thought no way.  Sound worked but while playing flash it was silent.  Now I did look into fixing this but it involved so much and this remember was my first problem so it's a no no to Linux from me.

---

### Post by Yellow Pasque on 2008-06-06
Fixing sound in Flash should be easy if you're using ALSA w/PulseAudio. Just:
```
sudo apt-get install libflashsupport
```

---

