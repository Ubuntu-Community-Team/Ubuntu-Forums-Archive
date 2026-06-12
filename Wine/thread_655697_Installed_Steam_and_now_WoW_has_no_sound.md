---
title: "Installed Steam and now WoW has no sound"
date: 2008-01-01
forum: Wine
---

### Post by notaphish on 2008-01-01
I recently (as of one week ago) installed wine and WoW.  After following the guide in the community docs section of Ubuntu site the game was working great (had lower framerates than I would have liked, but it worked well enough).  Then just yesterday I decided I would take on installing steam and counterstrike-source.  I got everything installed and the game opens up (still have some framerate issues I can't figure out) but now neither game has sound.  These are both updated games (WoW was working fine yesterday before I installed steam) and updated wine.  I have tried setting the sound to alsa and then back to OSS but it doesn't change anything.  I do get this message from clicking the audio tab under winecfg:> 
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
and I get this from running "~/.wine/drive_c/Program Files/World of Warcraft$ env WINEPREFIX="/home/brian/.wine" wine "C:\Program Files\World of Warcraft\WoW.exe""
> fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f40c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4f8,0x00000000), stub!
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f124,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7bbfe4a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x150046, (nil), 16): stub
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?

Just looking for a little help on what I might be able to change to at least get the sound working in WoW again.

---

