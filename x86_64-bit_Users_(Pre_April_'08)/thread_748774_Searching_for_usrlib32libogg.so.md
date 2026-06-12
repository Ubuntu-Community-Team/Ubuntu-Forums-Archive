---
title: "Searching for /usr/lib32/libogg.so"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicholim on 2008-04-07
I've been told that in order to run a video game, I need to have the ogg libraries in /usr/lib32/.  Can anyone shed any light on this?  Whenever I link from /usr/lib32 to /usr/lib I get an error about the libraries being the wrong ELF class.

---

### Post by gsmanners on 2008-04-07
If you use a 64-bit system, you can't link the normal 64-bit libs to a 32-bit folder. If you want to use 32-bit libs, you'll need to install "ia32-libs" (or whatever package contains the lib you need).

---

### Post by Cappy on 2008-04-08
Use getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

After installing you should change to the directory where the game executable is and use sudo getlibs executable's_name

---

