---
title: "Unique Problem with WoW."
date: 2008-03-01
forum: Wine
---

### Post by djfuze on 2008-03-01
So I bought a new laptop the other day (Dell Inspiron 1420. The Vista version, so I had fun installing ndiswrapper). All in all though, everything was running fine.

Yesterday though, I decided I wanted to play World of Warcraft on this laptop. I installed wine, got all the install files onto my desktop, and proceeded to install. The install ran smoothly, but when I started wow (by graphical shortcut) the gecko install failed, but i just bypassed it, and clicked "Play." About two seconds later, my screen switches to 1024x768 resolution (from 1280x800), so I thought it was going to start up, but after about 2 minutes, nothing happened. I switched my resolution back, and tried again. Same problem.

I knew something was wrong, so I started wow from the terminal.
```
fizzums@Squiggles:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe
err:wineboot:pendingRename couldn't get file attributes (2)
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c870000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c870000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34edd8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed38,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f31c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f050,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f744,0x00000000), stub!
Segmentation fault (core dumped)

```

Is what I got.

I uninstalled Wine (--purge) and deleted my .wine folder. Reinstalled it all, and still the same problem.

What's the deal here?

I'm using wine 0.9.55, but have also tried other versions with the same luck.
I've tried various windows OS in the winecfg.
Everything at this point is at their defaults in wine, and no other program is installed along side wow.
Using Ubuntu 7.04 Feisty.

Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
Intel Core 2 Duo, 1.66GHz
2GB Ram
250GB HDD

---

