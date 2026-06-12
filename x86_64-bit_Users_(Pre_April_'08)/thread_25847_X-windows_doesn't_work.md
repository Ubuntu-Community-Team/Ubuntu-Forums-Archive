---
title: "X-windows doesn't work"
date: 2005-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by belgarath on 2005-04-11
Hello.

I have installed Kubuntu Amd 64 (5.04) on my system, but X doesn't work.
My system: 
mainboard: Asus A8n-sli
cpu: Athlon 64 3000
video: XFX geforce 6600GT (pci-x)
mem: 1024 mb
sound: soundblaster audigy.
The install went fine, but i cannot startup in graphical mode, my screen gets all garbled up, i also cannot bail out, (ctrl-alt-backspace).
I can startup in textmode tough.
I also mis 'mc' by the way.

Greetz, Ger.

---

### Post by erkki70 on 2005-04-11
Hi,
This is a good place to start:
[http://www.ubuntuforums.org/search.php?searchid=506544](http://www.ubuntuforums.org/search.php?searchid=506544)
So I guess you need Nvidia drivers and once installed if not yet
type this on console:
```
sudo dpkg-reconfigure xserver-xorg
```

Hope this helps.
Cheers,
Erkki

---

