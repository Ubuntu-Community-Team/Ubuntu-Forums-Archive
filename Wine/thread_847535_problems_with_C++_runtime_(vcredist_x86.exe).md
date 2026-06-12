---
title: "problems with C++ runtime (vcredist_x86.exe)"
date: 2008-07-02
forum: Wine
---

### Post by kosmos on 2008-07-02
[Well, I found the solution almost immediately. Use "bash [_winetricks_](http://wiki.winehq.org/winetricks) vcrun2008". This installed the correct runtime and now the program works.]


Hi, I'm trying to install a small utility for the game Oblivion called _[FCOMhelper](http://www.tesnexus.com/downloads/file.php?id=16375)_. It uses the C++ runtime libraries MSVCP90.dll and MSVCR90.dll. So I tried installing _[vcredist_x86.exe](http://www.microsoft.com/downloads/details.aspx?FamilyID=9b2da534-3e03-4391-8a4d-074b9f2bc1bf&DisplayLang=en)_, but I still get these errors when I try to run FCOMhelper.exe:

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT"
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\oblivion\\Data\\FCOMhelper.exe") not found
err:module:import_dll Library MSVCR90.dll (which is needed by L"C:\\oblivion\\Data\\FCOMhelper.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\oblivion\\Data\\FCOMhelper.exe" failed, status c0000135
```

So, maybe the installation of vcredist_x86.exe didn't work right, but I'm lost and don't know how to fix it, or even if I'm really on the right track. Can anyone help me out? Thanks.

Wine - 1.1.0
Ubuntu - 8.04

---

### Post by brazemcee on 2008-07-03
Try grabbing the MSVCP90.dll file and put it on your system32 folder. That error is usual. It happenned to me once.
Try it.

[www.dll-files.com](www.dll-files.com) (Grab the dll here)

See you.

---

### Post by Tangbuntu on 2011-03-19
Thank-you, thank-you, thank-you!  I could not find a fix for this anywhere.  Much appreciated.

---

### Post by dino99 on 2011-03-20
> **Tangbuntu said:**
> Thank-you, thank-you, thank-you!  I could not find a fix for this anywhere.  Much appreciated.

only use packages from: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

