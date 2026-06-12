---
title: "Problems with World of Warcraft.."
date: 2008-08-17
forum: Wine
---

### Post by Dfizzle on 2008-08-17
Hello.
Lately I installed a clean install of Kubuntu 8.04.
Installed nvidia-glx-new drivers, and newest wine currently available (though I tried to 1.0 too).

My problem is that WoW flickers every 10sec, some models look _really_ weird, and I get WoWerrors after ~5minutes even if I don't even move.

My setup is AMD athlon 3000+, 1.5gb ddr1 ram, geforce 7600GS.

Here's a console output during play:
```
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
fixme:powrprof:DllMain (0x7cf10000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cf10000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f57c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d200,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eff0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f444,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x20026, (nil), 16): stub

```

ps. running in OpenGL mode (tried DirectX too) with glow and death effect disabled.
I tried to search first, but didn't find anything similar ;|

---

### Post by werries on 2008-08-17
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
Have you seen this?
The registry part is really important, me thinks, in fact, the whole "configuration" part.

---

### Post by Dfizzle on 2008-08-17
I've checked that link like 10 times. + I've had WoW working fine on different computer, but with this I am having that weird problem. Registry tweak - yeah I have it.

---

### Post by werries on 2008-08-17
Are you sure nvidia-glx-new is the correct driver for your computer?
Have you tried installing with envyng?

---

### Post by Dfizzle on 2008-08-18
its Geforce 7600GS, it should be the correct drivers. 

I just tried envyng - same problem.

---

