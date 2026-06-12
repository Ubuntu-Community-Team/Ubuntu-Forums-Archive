---
title: "Wine no fonts display"
date: 2008-11-11
forum: Wine
---

### Post by g0ldenchild562 on 2008-11-11
I just installed Wine and try to config wine, but no fonts showed up. I already installed the windows font into the correct folder. Help!
thanks

---

### Post by Dizzle7677 on 2008-11-11
Building from source? It's easier just to d/l the deb from the budgetdedicated repo. I have the same headache with the funky missing fonts , mainly for Steam. If you install the .deb it creates /usr/share/wine/fonts with .fon files but if I do the build from source I don't have it. So easy hack is to copy the fonts directory to ~/Documents, purge wine , build from source , copy over the fonts directory back over. Haven't tried it yet but let me know if it works. You dig daddy-o?

Intrepid 64-bit Compile...

CC="gcc-4.3 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v  --prefix=/usr  --exec-prefix=/usr --without-capi --without-cups --without-jack --without-sane --without-gphoto --with-x --with-wine-tools=./tools

...anyone see any probelms with it?

---

