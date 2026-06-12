---
title: "WOW Sound Problem"
date: 2007-08-03
forum: Wine
---

### Post by mokojin on 2007-08-03
Hi guys i had WOW running at some weeks now, but recenty i update wow with a patch and also ubuntu (i think wine ackages included) and now every time that switch from the game for the desktop i loose sound in the game.

Anyone has get similar experience?

The trace that when i run the game is this:

> 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
ricardo@ricardo:~$ fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x34f008,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374026c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7c645494) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34de64,0x00000000), stub!
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wave:wodPlayer_Reset shouldn't have headers left
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub



---

### Post by mokojin on 2007-08-11
no one has a similiar problem?

---

### Post by Zylar on 2007-08-11
I've heard wine .43 has caused some problems, especially with alt-tab.  Mine works fine in a 2nd X session though.

Check out Cogadh's awesome thread [here]("http://ubuntuforums.org/showthread.php?t=497332") to see how to run WoW in a 2nd session.

Good luck,

---

### Post by mokojin on 2007-08-12
Mne is wine-0.9.42, but i will follow your advice and read that thread. Thanks

---

### Post by WalmartSniperLX on 2007-08-13
I had the same thing. I think if you go into winecfg and go to the audio settings, make sure you have ALSA set and not OSS, and check "driver emulation" on the bottom. I think thats what fixed it for me.

---

### Post by mokojin on 2007-08-13
I have alsa option disabled, but i workaround setting enable background sound on wow options.

---

### Post by dublinfireman on 2007-10-19
Ok, none of that is working for me, now what do I do, I still have no sound

---

### Post by hikaricore on 2007-10-19
Thread closed, please post all WoW help questions in this thread: [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

Which I have stickied for the convenience of our World of Warcraft players.

---

