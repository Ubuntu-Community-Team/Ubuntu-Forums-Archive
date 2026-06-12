---
title: "Sound issue with wine and wow"
date: 2008-11-17
forum: Wine
---

### Post by kayas80 on 2008-11-17
Hi all
 
 I'm having a sound issue with wotlk running under wine. The sound works fine in game. But if I alt-tab to an application running in the background the sound in wotlk stops and when I alt-tab back to wotlk the sound doesn't start again. I have to log out of wotlk and restart it. One answer is not to switch between applications when playing wotlk, but it's really annoying as I often switch to other applications whilst running wotlk.
 
 I am using Ubuntu 8.04 and version 1.1.8 of wine. I've tried changing the audio from ALSA to OSS but it makes no difference. I'm afraid it doesn't  make much sense to me and I don't know if it helps, but I have included the output when I run wotlk from the terminal whilst I alt-tab and the sound stops:


```
kayas80@kayas80:~$ env WINEPREFIX="/home/kayas80/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe"  
 fixme:advapi:SetSecurityInfo stub 
 archive Data\enGB\patch-enGB.MPQ opened 
 archive Data\patch.MPQ opened 
 archive Data\expansion.MPQ opened 
 archive Data\lichking.MPQ opened 
 archive Data\common.MPQ opened 
 archive Data\common-2.MPQ opened 
 archive Data\enGB\locale-enGB.MPQ opened 
 archive Data\enGB\speech-enGB.MPQ opened 
 archive Data\enGB\expansion-locale-enGB.MPQ opened 
 archive Data\enGB\lichking-locale-enGB.MPQ opened 
 archive Data\enGB\expansion-speech-enGB.MPQ opened 
 archive Data\enGB\lichking-speech-enGB.MPQ opened 
 fixme:powrprof:DllMain (0x7d390000, 1, (nil)) not fully implemented 
 fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11 
 fixme:powrprof:DllMain (0x7d390000, 0, (nil)) not fully implemented 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub! 
 fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers 
 fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39ecac,0x00000000), stub! 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39f2d8,0x00000000), stub! 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub! 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub! 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub! 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub! 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39f520,0x00000000), stub! 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39f018,0x00000000), stub! 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub! 
 fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x146250,0x146150): stub 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub! 
 fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub! 
 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
 fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000 
 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
 fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000 
 fixme:reg:GetNativeSystemInfo (0x374025c4) using GetSystemInfo() 
 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
 
```                                  Any suggestions would be greatly appreciated. Many thanks

---

### Post by Ferrat on 2008-11-18
Don't know really how to fix it but if you go in to WoW options and change sounds settings the sound "server" restarts and you should get sound back (atleast that's what I do)

---

### Post by hikaricore on 2008-11-18
There's an option in the sound panel in game something along the lines of "play sound in background" check this box.
You may also want to run the game in windowed mode instead of fullscreen, one of these should solve your simple issue.

---

### Post by kayas80 on 2008-11-25
> **hikaricore said:**
> There's an option in the sound panel in game something along the lines of "play sound in background" check this box.

That was easily fixed, thanks.

---

