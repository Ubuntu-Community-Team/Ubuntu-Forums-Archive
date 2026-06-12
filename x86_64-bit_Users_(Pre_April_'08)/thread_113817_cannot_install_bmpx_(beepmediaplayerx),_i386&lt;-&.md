---
title: "cannot install bmpx (beepmediaplayerx), i386&lt;-&gt;amd64"
date: 2006-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by hoffimar on 2006-01-07
Hi guys and girls,

I have trouble installing bmpx (the new beep media player x) on my ubuntu 5.10 x86_64 system. So far i cannot see any package in the repositories, but there is one for i386 mentioned at [http://www.ubuntuforums.org/showthread.php?t=76796&highlight=bmpx]("http://www.ubuntuforums.org/showthread.php?t=76796&highlight=bmpx")

However, i cannot install any of the packages via dpkg -i <packagename>, it tells me i have another package architecture (which i indeed have ;-) ). Is there a possibility to tell him to install it because i have a lib32 directory in my system?

I also tried to install the package via sourcecode, but i get an error while compiling:
```
*** Warning: Linking the shared library libcontainer_xspf.la against the
*** static library ../../xcs/libxcs.a is not portable!
gcc -shared  .libs/libcontainer_xspf.o .libs/libcontainer_xspf_main.o  -L/usr/lib /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libpangocairo-1.0.so -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so -lXrender -lX11 /usr/lib/libgobject-2.0.so /usr/lib/libgthread-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libglib-2.0.so /usr/lib/libcurl.so /usr/lib/libidn.so -lssl -lcrypto -ldl /usr/lib/libxml2.so -lz -lm ../../xcs/libxcs.a  -pthread -Wl,--export-dynamic -Wl,-soname -Wl,libcontainer_xspf.so.0 -o .libs/libcontainer_xspf.so.0.0.0
/usr/bin/ld: ../../xcs/libxcs.a(xml.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
../../xcs/libxcs.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libcontainer_xspf.la] Fehler 1
make[3]: Verlasse Verzeichnis »/home/martin/software/bmpx-0.12.9/plugins/container«
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis »/home/martin/software/bmpx-0.12.9/plugins«
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis »/home/martin/software/bmpx-0.12.9«
make: *** [all] Fehler 2
```

Can anyone help me?

Thanks, Martin

---

### Post by awi on 2006-01-29
[http://packages.ubuntu.com/breezy/sound/beep-media-player](http://packages.ubuntu.com/breezy/sound/beep-media-player)

If you would like gxmms applet for BMP, you must compile it, because the one in the repository is compiled for xmms, not for BMP.

---

