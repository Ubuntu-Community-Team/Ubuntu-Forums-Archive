---
title: "Program running in Maverick, not in Natty. Both wine 1.2.2"
date: 2011-09-19
forum: Wine
---

### Post by JC Cheloven on 2011-09-19
Hi, this is about a freely distributable program for windows (3.11) I've been running fine under wine until now. Maverick included, wine version = 1.2.2. 

Now under Natty it doesn't run, even though the wine version is the same (1.2.2). First it complains the .exe not being marked as executable. Ok, I make it executable (and later made executable also all dll_s just in case). Then, when I open it with wine, it says something like
> Program winevdm.exe has encountered a serious problem and must close. We apologize for the inconvenience (...) 

The window of my target program gets open, but with only the external frame/border visible, and in an urresponsive state. I have to close the debug wine window from the panel to close also that window.

Note: the program didn't need installation. It consists on an .exe main file with some .dll_s which are in the same directory.
Note2: The output of ls -al of the directory, just in case it matters. The file to run is CalcEstr.exe

```
drwx------ 3 jc jc   4096 2009-01-30 22:40 .
drwxr-xr-x 3 jc jc   4096 2011-09-08 02:18 ..
-rwxrwx--x 1 jc jc 158720 2008-05-04 02:28 Appdll.dll
-rwxrwx--x 1 jc jc 143802 2008-05-04 02:28 BC30RTL.DLL
-rwxrwx--x 1 jc jc  12276 2008-05-04 02:28 Borte.fon
-rwxrwx--x 1 jc jc 130144 2008-05-04 02:28 Bwcc.dll
-rwxrwx--x 1 jc jc 443392 2008-05-04 02:28 CalcEstr.exe
-rwxrwx--x 1 jc jc 112559 2008-05-04 02:28 CalcEstr.hlp
-rwxrwx--x 1 jc jc     67 2009-04-01 12:39 CALCESTR.INI
-rwxrwx--x 1 jc jc  78848 2008-05-04 02:28 Calculos.dll
-rwxrwx--x 1 jc jc  72704 2008-05-04 02:28 Cntrls.dll
-rwxrwx--x 1 jc jc 154240 2008-05-04 02:28 OWL31.DLL
drwx------ 2 jc jc   4096 2009-01-30 22:40 Proyecto
-rwxrwx--x 1 jc jc  68444 2008-05-04 02:28 TCLASS31.DLL

```

Thanks in advance for any help.

---

### Post by ergo-proxy on 2011-09-20
Try other wine versions... but if it's for win 3.11 try running it in dosbox?

---

### Post by JC Cheloven on 2011-09-20
> **ergo-proxy said:**
> Try other wine versions... but if it's for win 3.11 try running it in dosbox?
Thanks for answering. The program ***requires*** windows 3.1 at least. It runs also fine on XP. In a dos-only environment reports an error (tried dosbox nevertheless, didn't had before).

Thing is, it works in wine 1.2.2 but only under maverick, not in natty. So I presume it should be something related to the ubuntu version rather than the wine version. 

Anyone?

---

### Post by willmsbrt1 on 2011-09-20
maybe try installing play on linux as I  have also had a few issues with wine and play on linux loaded all the required dlls and such for me auto , , need to urge wine prior to install of play on linux as it loads and installs wine too

---

### Post by JC Cheloven on 2011-09-24
One last attempt. Bump.
Anyone has experinced something similar and found a solution?

---

### Post by ergo-proxy on 2011-09-24
You can always install virtualbox with win3.11

---

