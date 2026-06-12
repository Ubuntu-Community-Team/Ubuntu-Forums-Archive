---
title: "this noob installed the wrong ver of ubuntu-tweak and i can not uninstall or install"
date: 2009-10-11
forum: x86 64-bit Users
---

### Post by ORVUEDGK360 on 2009-10-11
this noob installed the wrong ver of ubuntu-tweak and i can not uninstall or install other updates or programs and i can not even uninstall ubuntu-tweak


I think this is the one i installed ubuntu-tweak_0.4.9-1~karmic1_amd64.deb

but i think i was spose to install ubuntu-tweak_0.4.9.1-1~jaunty2_amd64.deb

which i just d/led please please please help me

---

### Post by Dejai on 2009-10-12
Pop a term:
sudo dpkg -r nameOfPackageHere.

---

### Post by bford16 on 2009-10-13
What happens when you open a terminal and type the following (and enter your password)?```
sudo apt-get remove --purge ubuntu-tweak
```

---

