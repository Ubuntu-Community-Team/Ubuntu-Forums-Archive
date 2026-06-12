---
title: "32-bit SDL in 64-bit environment"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by NFITC1 on 2008-01-22
Running 64-bit Gutsy (2.6.22-14-generic)
Trying to install some 32-bit apps that require SDL. I just installed from source the 64-bit SDL 1.2.13 (according to sdl-config --version) and the app isn't recognizing the installation because the 32-bit libs are version 1.2.11. That may not be the direct cause of error, but I keep getting the error
```
/usr/bin/ld: skipping incompatible /usr/local/lib/libSDL.so when searching for -lSDL
/usr/bin/ld: skipping incompatible /usr/local/lib/libSDL.a when searching for -lSDL
/usr/bin/ld: skipping incompatible /usr/lib/libSDL.so when searching for -lSDL
/usr/bin/ld: skipping incompatible /usr/lib/libSDL.a when searching for -lSDL
```
when it should be looking in /usr/lib32 and/or ./usr/local/lib32. I've tried ldconfig and depmod -a and that didn't help.
Any thoughts?

EDIT: Going to try ia32-libs-sdl. I just put it here to remind myself when I get back to my lappy.
Post EDIT: Tried it. ia32-libs-sdl was replaced by ia32-libs and was already installed. It didn't work.

---

