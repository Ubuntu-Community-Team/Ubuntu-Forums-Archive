---
title: "GTK and 32bit problems"
date: 2005-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by bannerboy on 2005-11-30
I use the gtk-engines-qt package so that firefox, gimp, and all of my other gtk2 apps look the same as my qt apps. and here's my problem. I have a amd64 processor, and openoffice2 is a 32bit executable, and it doesn't recognize my GTK theme, neither does audacity. how do I fix this?

---

### Post by bannerboy on 2005-11-30
I have discovered that if install ia32-libs-gtk, openoffice goes from ugly, to not quite so ugly, but how do I install a 32bit version of gtk2-engines-qt-gtk?

---

### Post by Navyblue on 2005-12-03
I observed the exact same thing as you, I also did installed the ia32-libs-gtk which helped a bit.

Btw, are you using very dark colour KDE theme? I notice that for shade of grey, if I use window background colour darker than rgb value of 40,40,40, ooffice2 would use a different set (very ugly) of icons for its tool bar. If I use button background colour darker than rgb value of 40,40,40, ooffice2 would use a different set (very ugly) of icons for its drop down menu. I have not experimented with other colour though. So by keeping window background and button background colour brigter than rgb value of 40,40,40 oofice2 looks preety indistinguishable from 32 bit Kubuntu.

---

