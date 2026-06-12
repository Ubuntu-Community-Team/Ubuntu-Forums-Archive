---
title: "Cedega hideously slow on amd64 hoary"
date: 2005-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by mkavanagh on 2005-04-14
I've been trying to install [EVE online](http://www.eve-online.com) using cedega; the installer ran at literally less than one percent of the speed it ran on a less powerful windows machine, and the game never got past the loading screen when I'd got it installed. -debugmsg +warn reveals this:
```
matthew@monolith:~ $ cedega -debugmsg +warn TransGaming_Drive/Program\ Files/CCP/EVE/eve.exe
fixme:cdrom:CDROM_GetIdeInterface cdrom not a block device!!!
fixme:console:SetConsoleCtrlHandler (0x1012c578,1) - no error checking or testing yet
fixme:thread:GetThreadTimes (0xfffffffe): stub
err:file:CreateFileA Couldn't open device 'CON'!
err:file:CreateFileA Couldn't open device 'CON'!
err:bitmap:X11DRV_DIB_CreateShmPixmap pitch mismatch in ShmPixmap creation
fixme:thread:GetThreadTimes (0xfffffffe): stub
fixme:file:FindFirstChangeNotificationA this is not supported yet (non-trivial).fixme:file:FindFirstChangeNotificationA this is not supported yet (non-trivial).fixme:console:SetConsoleCtrlHandler (0x100eee70,1) - no error checking or testing yet
fixme:thread:GetThreadTimes (0xfffffffe): stub
fixme:thread:GetThreadTimes (0xfffffffe): stub
```

The only bit that strikes me is "fixme:file:FindFirstChangeNotificationA this is not supported yet (non-trivial)"; however, I can verify that EVE Online works at a decent speed under the same version of cedega, as another guy runs it fine on his 32-bit box.

Some of my relevant hardware:
Athlon64 3000+
ATi Radeon 9800 PRO 128MB
160GiB SATA drive, 8MB cache
Abit KV8-PRO motherboard
1GB PC3200 RAM

Everything else on my system runs blazing fast, including the linux version of Enemy Territory (stable at 90FPS, at which I have the FPS capped). I get 3000FPS+ in glxgears with about 15 other GUI programs and countless background processes running,

---

### Post by mkavanagh on 2005-04-16
Another note: I've tried this both in 32-bit chroot and in a 64-bit environment. No dice.

---

### Post by Amon80 on 2005-10-02
I don't know if it can be useful, but i had the same problem. Even if i am not using a 64bit machine (i have an AthlonXP 2400+).
The solution?

For me worked this one:
1. Install the game using regular wine
2. Play using cedega 4.4.1

Hope it helps. :)

---

