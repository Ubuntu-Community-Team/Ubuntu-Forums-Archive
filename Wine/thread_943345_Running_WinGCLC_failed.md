---
title: "Running WinGCLC failed"
date: 2008-10-10
forum: Wine
---

### Post by avecchiato on 2008-10-10
Hi,
I'm trying to run a program named WinGCLC ([http://www.matf.bg.ac.yu/~janicic/gclc/](http://www.matf.bg.ac.yu/~janicic/gclc/)).
After having recovered two missing dlls from [www.dll-files.com](www.dll-files.com) (MSVCP60.dll and MFC42.dll) the program fails to start giving the error messages below about an unimplemented function of MFC42.dll. Does this mean that this program cannot run under wine?

Any help is appreciated, thanks.

Alberto Vecchiato

-------------------------------
fixme:system:SystemParametersInfoW Unimplemented action: 88 (SPI_SETICONS)
wine: Call from 0x4da411 to unimplemented function MFC42.DLL.6625, aborting
wine: Unimplemented function MFC42.DLL.6625 called at address 0x4da411 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6625 called in 32-bit code (0x7bc4569c).
Register dump:
[omitted]
wine: Call from 0x4da411 to unimplemented function MFC42.DLL.6625, aborting

---

### Post by pedroquaresma on 2009-06-08
You can load all the C++ related dll files with this procedure.

-------------
Or, better yet, get a fresh copy straight from Microsoft with the command 
wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) 
sh winetricks vcrun6 
-------------

I found that in the Wine foruns.

I have the WinGCLC program runing in two different (32bits and 64bits) Debian systems.
 
Bye

---

### Post by avecchiato on 2009-06-09
Now it works. :D
Thank you!

Alberto

---

