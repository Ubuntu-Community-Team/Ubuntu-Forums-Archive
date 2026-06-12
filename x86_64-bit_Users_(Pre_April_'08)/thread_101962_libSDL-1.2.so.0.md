---
title: "libSDL-1.2.so.0"
date: 2005-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by EPOX123 on 2005-12-11
Err i just got done installing quake 4  and i get stupid message any one know a fix?

./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

i dont want to go back to windows... and i dont want to go to another distro ;/ help!!!

---

### Post by tokyovigilante on 2005-12-11
Don't stress this is an easy fix. The compatibility libraries haven't been updated  for ALSA. Check out [http://skuld.bmsc.washington.edu/~yi/?p=6]("http://skuld.bmsc.washington.edu/~yi/?p=6").

His method requires some mucking about with configs and such, so I found a better way was after extracting the archives to just copy libasound.0 and libsdl1.2.0 (these are symlinks) plus the linked libraries to /usr/lib32, and run sudo ldconfig. 

Quake 4 worked fine with this, I'd assume Doom 3 would as well (although I haven't installed to check).

---

### Post by SRu on 2006-01-31
That wasn't a very heplful reply.

For anyone landing here to solve this problem install libsdl1.2debian-alsa like this:

*sudo apt-get install libsdl1.2debian-alsa*

This will end the 'get stupid message' situation without going to another distro or worse.

---

### Post by PandabeaR on 2006-02-02
SRu I did this and I STILL get the same message! :(

---

### Post by PandabeaR on 2006-02-02
Nevermind, I have this problem fixed, It just didnt copy to the usr/lib dir.... but now I have a NEW problem... The menu text is wierd, such as this "#str_20000" and so on. I checked to see if I have english.zpack and I do... what could be the problem?

---

