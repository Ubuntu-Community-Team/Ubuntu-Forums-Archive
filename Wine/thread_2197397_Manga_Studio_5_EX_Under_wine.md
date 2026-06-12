---
title: "Manga Studio 5 EX Under wine"
date: 2014-01-03
forum: Wine
---

### Post by ancyllaqc on 2014-01-03
Hello, I am using a 64 bit PC with the latest release of Ubuntu and Wine 1.7.7.

The only other program i have installed under wine is Steam.

I am trying to run Manga Studio 5 EX and all i get is the cursor to show that the computer is trying something, then nothing. Here is the terminal output. 

err:module:load_builtin_dll failed to load .so lib for builtin L"mscms.dll": liblcms2.so.2: cannot open shared object file: No such file or directory
err:module:import_dll Loading library mscms.dll (which is needed by L"C:\\Program Files\\Smith Micro\\Manga Studio 5E\\Manga Studio\\Manga Studio.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Smith Micro\\Manga Studio 5E\\Manga Studio\\Manga Studio.exe" failed, status c0000135


Thank you in advance for the help.

---

### Post by ukbeast on 2014-02-04
Might run better in 32bit prefix.
[COLOR=#333333][FONT=UbuntuRegular]delete  .wine (hidden in home folder)
Run in terminal - WINEARCH=win32 WINEPREFIX=~/.wine winecfg
This will create a 32bit environment for wine 
[/FONT][/COLOR]
If that still does not work. try [COLOR=#000000][FONT=monospace]winetricks msxml6 gdiplus gecko vcrun2005sp1 vcrun2008 msxml3 atmlib[/FONT][/COLOR]

---

