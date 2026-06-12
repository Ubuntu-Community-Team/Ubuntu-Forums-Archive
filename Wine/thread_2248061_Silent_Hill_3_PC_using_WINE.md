---
title: "Silent Hill 3 PC using WINE"
date: 2014-10-12
forum: Wine
---

### Post by Rvdpeet on 2014-10-12
Hello everybody,

I wanted to install Silent Hill 3 for PC on my ubuntu 14.04 pc. So I downloaded it and clicked the setup.exe.
After about 10-20 seconds, the installer stops with the message "1608: Unabgle to create InstallDriver instance Return code: -2147221164".

I tried googling the message, but I found nothing useful for me.
Here are the specs of my pc:

CPU: AMD A8 6600-K Quad core
RAM: 8 GB DDR3 1866
GPU: AMD Radeon R7 250 1 GB
OS: Ubuntu 14.04 Trusty

I hope this is enough information for you, please tell me if you have a solution.

Regards and thanks,

Rvdpeet

---

### Post by Rvdpeet on 2014-10-13
In addition:

When I try to run the setup.exe from the terminal, these are the lines that show:

fixme:storage:create_storagefile Storage share mode not implemented.
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
err:ole:create_server class {8b1670c8-dc4a-4ed4-974b-81737a23826b} not registered
err:ole:CoGetClassObject no class object {8b1670c8-dc4a-4ed4-974b-81737a23826b} could be created for context 0x4

I hope this helps, please let me know if you have a suggestion or something I could try.

Thanks and regards,

rvdpeet

---

### Post by adec2 on 2014-10-13
From the winehq page ([https://appdb.winehq.org/objectManager.php?sClass=version&iId=7767](https://appdb.winehq.org/objectManager.php?sClass=version&iId=7767))


*"winetricks dsdmo directmusic" fixes the problem with the sound effects not working as mentioned here: [http://bugs.winehq.org/show_bug.cgi?id=35478](http://bugs.winehq.org/show_bug.cgi?id=35478). 
Also it seems like directmusic is now required, otherwise the game will just crash on start.

Quartz however is NOT required (winetricks directmusic already registers it).

Works flawlessly with some winetricks verbs.

---

