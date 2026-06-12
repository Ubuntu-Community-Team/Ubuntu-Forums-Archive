---
title: "Widescreen Laptop, External Flat Panel NVidia support"
date: 2005-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by KrazyArrow250 on 2005-10-22
I have a widescreen HP zv5000 laptop with an nVidia 440Go in it and an HP1955 external flat panel monitor that I would like to get working dual head. Basically I just want to turn off my laptop's screen and use only my external flat panel.  I've searched online endlessly but can't find anything that will work for me.  Right now my monitor only shows a small chunk of my desktop that's all scrambled.  Any help would be greatly appreciated.

---

### Post by gandalf72704 on 2005-10-23
I got an external samsung 710n working on a hp zd7000 (native 1440 x 900), after install on laptop, I went in and edited the xorg.conf, and changed 1440 x 900 to 1280 x 1024 (native res of lcd) this worked, as the laptop boots, you have to switch displays (FN+F4 on zd7000), we are working this way now. I tried setting up 2 displays in xorg.conf, and setting both resolutions (1440 x 900 and 1280 x 1024), neither of these worked.

---

### Post by KrazyArrow250 on 2005-11-03
I guess I didn't autosuscribe to this, oops.  Anyway, since I use my laptop both with and not with my moniter that would mean constant switching.  Is there  another way anyone knows about?

---

### Post by KrazyArrow250 on 2005-11-08
Any help at all?  Being able to switch between them isn't too important right now, I'd just really like to be able to see more than the garbled crap on my DFP.

---

