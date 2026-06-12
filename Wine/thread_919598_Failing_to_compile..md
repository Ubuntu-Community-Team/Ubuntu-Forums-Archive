---
title: "Failing to compile."
date: 2008-09-14
forum: Wine
---

### Post by grjemo on 2008-09-14
I tried to install a patch to run spore on wine. ([http://bugs.winehq.org/attachment.cgi?id=15883](http://bugs.winehq.org/attachment.cgi?id=15883))

So I uninstalled my previous installation of Wine, made the patch into a .bz2, and used the command to add it to the Wine source.  When trying to install it, I came over many errors, mostly resulting from missing packages.  I would download, restart, and continue.  On my last try, everything seemed to work.  A humongous amount of text scrolled by in the terminal, so it seemed to be working.  After a VERY long time, it gave me this error:

```
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/grjemo/Desktop/wine-1.1.4/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/grjemo/Desktop/wine-1.1.4/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

```

Any ideas?

PS: Please speak in laymans terms, I'm a bit of a newbie.

---

### Post by McNils on 2008-09-14
You need to install a library, libxext6.

```
sudo apt-get install libxext6
```

---

### Post by grjemo on 2008-09-14
I have that.  I'll try libxext-dev.

EDIT:  Holy crap. Wine is taking a long time to compile.

---

### Post by grjemo on 2008-09-14
I got it working with instructions I got from another thread.  Thanks though.

---

