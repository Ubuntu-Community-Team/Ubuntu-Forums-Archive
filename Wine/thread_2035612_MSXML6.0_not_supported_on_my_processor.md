---
title: "MSXML6.0 not supported on my processor?"
date: 2012-07-31
forum: Wine
---

### Post by Stonecold1995 on 2012-07-31
I'm trying to install the MSXML6.0 package through Wine 1.5 on my Kubuntu 12.04 computer.  However, when I run "winetricks msxml6" or "wine msiexec /i /home/alex/.cache/winetricks/msxml6/msxml6_x86.msi", I get an error popup saying "This MSXML6.0 package is not supported on the current processor type".  I have an 8-core (4 physical) Intel Core i7-2760QM @ 2.4 GHz, btw.  I'd think it would be compatible. :/

Here's the output of "winetricks msxml6" through Terminal:
```
alex@kubuntu:~$ winetricks msxml6
Executing w_do_call msxml6
Executing load_msxml6
Executing mkdir -p /home/alex/.cache/winetricks/msxml6
Using native,builtin override for following DLLs: msxml6
Executing winetricks_early_wine regedit C:\windows\Temp\_msxml6\override-dll.reg
Executing wine msiexec /i /home/alex/.cache/winetricks/msxml6/msxml6_x86.msi
fixme:storage:create_storagefile Storage share mode not implemented.
err:msi:ITERATE_Actions Execution halted, action L"LaunchConditions" returned 1603
------------------------------------------------------
Note: command 'wine msiexec /i /home/alex/.cache/winetricks/msxml6/msxml6_x86.msi' returned status 67.  Aborting.
```

The output of "wine msiexec /i /home/alex/.cache/winetricks/msxml6/msxml6_x86.msi" is:
```
alex@kubuntu:~$ wine msiexec /i /home/alex/.cache/winetricks/msxml6/msxml6_x86.msi
err:menubuilder:init_xdg error looking up the desktop directory
fixme:storage:create_storagefile Storage share mode not implemented.
err:msi:ITERATE_Actions Execution halted, action L"LaunchConditions" returned 1603
```

I need MSXML6 to install Microsoft Office 64-bit on my computer (LibreOffice hates KDE), and it's one of the things I need installed for MS Office to run.

---

### Post by ergo-proxy on 2012-07-31
That's because use you have 64bit OS and you try to install 32bit xml addon on a 64bit default wine prefix, it won't work because most Microsoft addons are still 32bit.
 
First: create a NEW wineprefix
Seconds: choose 32bit architecture by running: export WINEARCH=win32 
Third: run winetricks again, it should work this time

---

### Post by KaisaUbun2 on 2012-08-04
> **ergo-proxy said:**
> That's because use you have 64bit OS and you try to install 32bit xml addon on a 64bit default wine prefix, it won't work because most Microsoft addons are still 32bit.
 
First: create a NEW wineprefix
Seconds: choose 32bit architecture by running: export WINEARCH=win32 
Third: run winetricks again, it should work this time

I'm quite the newbie, How do I run the win32?

---

### Post by TSniper on 2013-05-07
I have the same problem, how to solve it ?

---

