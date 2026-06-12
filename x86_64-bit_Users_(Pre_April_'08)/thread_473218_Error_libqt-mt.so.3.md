---
title: "Error libqt-mt.so.3"
date: 2007-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cam1223 on 2007-06-13
ok im trying to install VirtualBox and it installed ok but when i try to run it. the terminal says ```
/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```
other apps are giving me erros with the same libqt-mt.so.3 but idk what to do.....???

---

### Post by Kilz on 2007-06-13
> **Cam1223 said:**
> ok im trying to install VirtualBox and it installed ok but when i try to run it. the terminal says ```
/opt/VirtualBox-1.3.8/VirtualBox: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```
other apps are giving me erros with the same libqt-mt.so.3 but idk what to do.....???

You can find the package that contains t[hat file here.]("http://packages.ubuntu.com/feisty/libs/libqt3-mt") For future reference you may want to[ bookmark this page]("http://packages.ubuntu.com/") that lets you search for packages, and the files in them. Make sure to get AMD64 packages. Also as a side note, if you have by any chance force installed the Virtualbox package, never, ever ,ever force in libraries like the above.

---

### Post by Cam1223 on 2007-06-13
Apperantly its not that simple. i downloaded the package and it said i already had it installed (i reinstalled anyway) and still virtualbox tells me the same thing when i try and start it. oh and thx for the side note, i whould of tried to force a 386 version of the library heheh good thing u told me

---

### Post by Case_f on 2007-06-14
Di you install the AMD64 VirtualBox package? Or did you install the i386? You need the AMD64 one, available here (assuming you run Feisty):

[http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb](http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb)

---

### Post by Cam1223 on 2007-06-14
yup thx i installed the 64 version and it works beutifuly much better than vmware player. mayb even better than a real XP lol

---

