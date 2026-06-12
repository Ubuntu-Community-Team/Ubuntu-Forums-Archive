---
title: "Ubuntu / Windows 10 /  Wine"
date: 2018-08-14
forum: Wine
---

### Post by wmorgan12 on 2018-08-14
I installed Ubuntu. Have  a dual boot system Now. With Windows 10 and Ubuntu. I have Windows 10 installed on Primary SSD and Ubuntu installed on a secondary HD. My question is , does windows 10 and Ubuntu need too be installed on same Hard Drive for wine / PlayOnLinux too work? I have searched internet and forums, with no luck in search of this information. I didn't research or think of this , when installing Ubuntu.

---

### Post by kc1di on 2018-08-14
if you have windows 10 you should not need wine/pol but no they do not have to be installed on the same disk.  You can install wine in Ubuntu.  I would install Playonlinux myself as it make it much easier to work with wine.  If you want wine though and are using 18.04.1 you will need to install wine-stable and wine32. good luck.

---

### Post by Holger_Gehrke on 2018-08-14
Actually, you don't need to have windows at all to get wine and the wine-frontend Play On Linux to run.

'wine' is a translation layer that sits between a program written for Windows and a Linux OS. The program makes its calls to the OS as if it was running on Windows, wine intercepts these calls, makes the calls to Linux, translates the results into something the Windows program can understand and passes the results to the program. Since both Windows and Linux are still in active development, the wine developer are always busy playing catch up. Sometimes a program will work with only one very specific version of wine. 

That's were Play On Linux enters the situation. This program is not only a friendlier interface to the somewhat unwieldy wine, it also makes it possible to have multiple versions of wine installed and set specific programs to run with just the right wine version.

Holger

---

### Post by wildmanne39 on 2018-08-14
*Thread moved to **Wine for a more appropriate fit**.*

---

