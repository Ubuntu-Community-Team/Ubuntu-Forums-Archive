---
title: "World of Warcraft Crashes after intro movies"
date: 2007-12-03
forum: Wine
---

### Post by tabithaboof on 2007-12-03
I am trying to install WoW under wine and have a bit of a problem, I installed the game using the Free Trial (which worked fine as far as I can tell)

[https://signup.worldofwarcraft.com/trial/index.htm](https://signup.worldofwarcraft.com/trial/index.htm)

I havent played WoW or used wine before for that matter. It seemed to go well, when starting WoW.exe in wine I can watch the two introduction movies perfectly but as soon as the second one finished (or if I skip them) the game returns to the desktop without locking or giving any error message

This is the output from terminal

```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cad0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cad0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed18,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f724,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x13ac70) call to IWineD3DDevice_Cr             eateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x13bf80) Event query: Unimplemented,              but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000):              STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not suppor             ted on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Mesa 7.0.1 implementation error: i915_program_error: Exceeded max nr indirect te             xture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

```

I have a rather wimpy Mobile Intel® 945GM Express Chipset but it is apparently capable of running wow. I also have checked to see it I have direct rendering enabled which I apparently do.

Im running Ubuntu 7.10 on a Thinkpad X60 with a 2.0 core 2 duo with 1 GB of ram.

Help much appreciated!

---

### Post by Sammi on 2007-12-03
Only the last three lines are indeed crash info. The other lines that start with "fixme" are standard Wine debug messages, which you should just ignore.

To me it looks graphics card related. i915 is a Intel chipset.

---

### Post by tabithaboof on 2007-12-03
> **Sammi said:**
> Only the last three lines are indeed crash info. The other lines that start with "fixme" are standard Wine debug messages, which you should just ignore.

To me it looks graphics card related. i915 is a Intel chipset.

Thanks so much Sammi, that narrowed things down to a point where I could start looking and I found a post here

[http://ubuntuforums.org/showthread.php?t=377139&page=2](http://ubuntuforums.org/showthread.php?t=377139&page=2)

Which indicated I should turn off pixel shading thus solving the problem!

---

### Post by Sammi on 2007-12-04
Glad to hear it :D

---

### Post by Orkun Sensebat on 2008-01-08
pal, i love people who report back after having solved a problem.

wow seems to work now(its really nice fps-wise), but after accepting the Scanning EULA I get a hard-lock.

at least my notebook is very capable of playing wow.

---

### Post by M!K3_$ on 2008-01-08
> **Sammi said:**
>  i915 is a Intel chipset.

*shudder*
...intel graphics
if so

/breakcomputer

*shudder*

btw i got it to work by installing direcX under wine... they dont recomend this... but it workd


bonne chance
mike

---

### Post by f33nom on 2008-03-06
I love you guys, Had the same problem for so long, was getting frustrated and was on the verge of going back to windows, this thread saved my ubuntu's life!!!!! thanks again.

---

