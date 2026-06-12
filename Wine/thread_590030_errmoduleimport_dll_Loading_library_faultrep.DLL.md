---
title: "err:module:import_dll Loading library faultrep.DLL"
date: 2007-10-24
forum: Wine
---

### Post by Hexaphim on 2007-10-24
I originally posted this in the Football Manager 2008 thread, but I've gotten the same error when trying to install a different game as well.

When I try to run setup.exe (with wine), I get the following error message:

Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library faultrep.DLL (which is needed by L"H:\\setup.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"H:\\setup.exe" failed, status c0000135

I tried installing it in Windows Vista and then starting the game in Linux, but I got the same error when I attempted to run fm08.exe.

Any ideas? I'm a newbie, so you probably need to explain it to me like I'm a six year old. :)

---

### Post by Danzzzz on 2007-10-26
alright mate i had the same problem all you need to do is download the file - u can get it off google by searching for faultrep.dll download. once downloaded cut and paste it in well it may be differnet for u but i went to c:/program files/sports interactive/football manager 08 and pasted it in there and then it will work. hope this is useful :) ave fun !! 
Danny :D

---

### Post by cogadh on 2007-10-26
Just to clarify that a bit, search for and download the DLL file (or if you have an existing Windows installation, you may be able to copy it from that). Put the DLL file in /home/<username>/.wine/drive_c/windows/system32 (the .wine directory is a hidden directory, so hit CTRL+H to show it in the file browser). Then launch winecfg, go to the Libraries tab and add an override for that DLL. Faultrep is available in the drop-down list of libraries that can be overridden. Set the load order to native first or native only. Then try running the game, hopefully that will get it past the error.

---

### Post by lisa107b on 2011-12-05
> **cogadh said:**
> Just to clarify that a bit, search for and download the DLL file (or if you have an existing Windows installation, you may be able to copy it from that). Put the DLL file in /home/<username>/.wine/drive_c/windows/system32 (the .wine directory is a hidden directory, so hit CTRL+H to show it in the file browser). Then launch winecfg, go to the Libraries tab and add an override for that DLL. Faultrep is available in the drop-down list of libraries that can be overridden. Set the load order to native first or native only. Then try running the game, hopefully that will get it past the error.

I'm afraid I'm having a similar problem with mscoree.dll, its loaded into the ".wine/drive_c/windows/system32" directory and in the library override tab, can anyone help?

I'm running Xubuntu 11.04 with Wine v1.3.28, its all just newly installed - I'm new to the linux os and would love to have it replace windows!

Lisa

---

### Post by Perfect Storm on 2011-12-05
Necromancing, very old thread. Also belongs on wine forums.


Thread closed.

---

