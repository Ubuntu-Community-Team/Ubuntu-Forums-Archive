---
title: "WoW shuts off my pc"
date: 2007-12-16
forum: Wine
---

### Post by skroops on 2007-12-16
When I play WoW, everything works great but after 2-8 minutes my PC just shuts off.

Specs: HP zd8000 laptop, 3Ghz P4 CPU, 1 Gig of RAM, ATI mobility x600 256MB with restricted drivers.
Version: wine0.9.51, gutsy amd64

I have the increased FPS registry hack, and lighting and shadows turned off through the config file.

I've tried running with and without my battery installed, and it didn't make a difference.  I checked the syslog and the only thing around the time of the crash is a "-- mark --".  The wine terminal shows no big problems, but here is the output:
```
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f40c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f55c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34f124,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x721444a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34d1a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34d200,0x00000000), stub!
```

Regards.

---

### Post by skroops on 2007-12-18
bump

---

### Post by angryfirelord on 2007-12-18
Could be a couple issues. First, make sure all the latest patches are applied. Next, check for ventilation. A common fault of PCs shutting down randomly is due to overheating. Play another 3D intensive game such as Nexuiz and see if you get similar results. If that still doesn't work, then try turning down some of the graphics. (although it looks like you already did that) Finally, test it on 32-bit Ubuntu. I've found 64-bit wine to be more finicky than 32-bit wine.

---

