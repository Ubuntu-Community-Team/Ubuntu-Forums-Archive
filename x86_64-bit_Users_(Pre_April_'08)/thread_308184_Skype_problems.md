---
title: "Skype problems"
date: 2006-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by mesh2005 on 2006-11-27
I installed the skype using the .deb I have to force it but get the following error when trying to run it:
skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

---

### Post by xopher on 2006-11-27
```
sudo apt-get install ia32-libs-kde
```

Maybe this will do it.

---

### Post by RAOF on 2006-11-27
It will then likely fail with "error while loading shared libraries: libasound.so.2", and you should install the **ia32-libs-sdl** package to get those libraries.

---

### Post by mesh2005 on 2006-11-28
Thank you so much :)

---

