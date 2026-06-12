---
title: "Wrong colours rendering in PDF XChange Editor 5.5"
date: 2015-08-10
forum: Wine
---

### Post by andrea75 on 2015-08-10
Hello, I've installed PDF XChange Editor v.5.5.313.1 x86 on Wine v. 1.7.44. I have a book which looks like this on windows
[IMG]http://i.imgur.com/hnZDadO.png[/IMG]

And now on Wine looks like this
[IMG]http://i.imgur.com/LVq0dWq.png[/IMG]

I can't figure out why the colours are so off. The colours settings in PDFXC editor can't be changed (well, they can but there's only one entry for each menu), anyway, they're the same as on Windows.
At first I installed the 64bit version from .msi and imported the preferences from Windows, then uninstalled, tried the .exe installation, which looked the same, so I uninstalled and finally installed the 32bit .msi. Note that after the first installation the preferences were always retained (I don't know how to completely wipe the program).

The console output from the last installation was
```
~$ msiexec /i PDFXVE5.x86.msi
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ver:GetCurrentPackageId (0x32eff8 (nil)): stub
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:richedit:ReadColorTbl malformed entry
err:richedit:ReadColorTbl malformed entry
err:richedit:ReadColorTbl malformed entry
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
fixme:msi:event_spawn_wait_dialog doing nothing
fixme:propsys:PSUnregisterPropertySchema L"PDFProperties.propdesc" stub
~$ 
```

[EDIT] If I highlight the text again it gets the right colour, but then if I close the pdf and re-open it it's messed up again.

[EDIT 2] The first time opened Configure Wine it said I had to install Gecko, but I didn't. Is it needed?

Thanks for any help!

---

### Post by TheLazza on 2015-08-10
May I ask you how did you manage to install it under Wine? :o I tried different Wine versions (1.4, 1.5.31, 1.7.31, 1.7.49) under PlayOnLinux and none of those worked. I tried the 32bits MSI and the EXE installer, with no luck. My OS is Ubuntu 15.04 64-bits.

---

### Post by andrea75 on 2015-08-11
For me it only works with Wine1.7 (actually tested on 1.7.44). Try installing the 32bit msi with "msiexec /i ". [Appdb]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=30820&iTestingId=85847") gives it a platinum rating, but for me both the 32 and 64bit versions worked, and the exe too.

[EDIT] I've been given the solution to the problem here: [https://www.tracker-software.com/forum3/viewtopic.php?f=35&t=24038&p=93702](https://www.tracker-software.com/forum3/viewtopic.php?f=35&t=24038&p=93702)
I had to go to Edit > Preferences > Page display > Rendering > Default transparency blending color space and change it to Working RGB.

---

