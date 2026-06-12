---
title: "Ububtu freezes after the login"
date: 2006-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by itaysp on 2006-03-03
Hey,
i just installed ubuntu for my first time.
i installed the 64 bit version (i have athlon 64).
everything was ok in the installation.
i started ubunto, typed the username and the pass, i logged in,
and then nothing happened. i see an empty brown screen.
i can move my mouse.

i tried to load it few times but it didn;t help.

what's wrong?

---

### Post by kuys on 2006-03-03
What video card do you have? You may have to reset to the vesa driver like I did. Here a fix that should work. 

Next time the GRUB loader screen comes up select recovery boot. This will load a text-only interface. Next type dpkg-reconfigure xserver-xorg. Select the vesa driver as your videcard driver and turn auto detect video card off.

---

### Post by itaysp on 2006-03-03
i have nvidia gf6800nu.
i did what u told me, but it was more compliated then ur desribe.
i have a lot of options there, the first one is autodeect.
and wat i need to choose form the list next?
and wen to choose after?

---

### Post by kuys on 2006-03-03
[QUOTE=itaysp]i have nvidia gf6800nu.
i did what u told me, but it was more compliated then ur desribe.
i have a lot of options there, the first one is autodeect.
and wat i need to choose form the list next?
and wen to choose after?[/QUOTE]


Defaults except when it comes to texture memory i used 250000 because it's roughly around 256megs the same as my 7800gt.

---

### Post by itaysp on 2006-03-03
working, thx :)

---

### Post by kuys on 2006-03-03
[QUOTE=itaysp]working, thx :)[/QUOTE]

No problem. 

You may want to look into this howto to install your nvidia drivers properly so you can make full use of your video card. 

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by itaysp on 2006-03-04
thx :)

---

