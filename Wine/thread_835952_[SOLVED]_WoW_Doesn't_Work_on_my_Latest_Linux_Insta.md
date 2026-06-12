---
title: "[SOLVED] WoW Doesn't Work on my Latest Linux Install"
date: 2008-06-21
forum: Wine
---

### Post by Pikestaff on 2008-06-21
Okay guys, I need some help.

Lil' background info: I started playing WoW about a year ago when I was already an exclusive Linux user.  So I installed it via Wine, it has always worked near flawlessly, and I have played basically exclusively on Linux.  Leveled to 70 on Linux, done instances, heroics and raids on Linux, never had any problems.

A couple days ago I reinstalled Kubuntu 6.06 (yes, it's old, I can't get my wireless card to run with anything newer... so I've been using 6.06 forever) and I tried to reinstall WoW, the same way I did last time... but I get errors and it won't start.  I even copied my entire folder over from my old Linux install and tried that, and it still gets me errors.  (That same folder seems to work flawlessly on my Windows XP partition.)  I am completely at a loss here and would love to get some input on what I can do to once again play WoW on my favorite operating system...

I am using Wine 0.9.9 and this is what happens in the terminal when I try to run a fresh WoW install:

```

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7c810000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c810000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f3fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f518,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f144,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=4824 < primary_done=4828)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=4824 < primary_done=4828)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=4824 < primary_done=4828)
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  385
  Current serial number in output stream:  386

```

And this is what happens when I run it from my old folder:

```

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7c810000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c810000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f3fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f57c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f144,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=7412 < primary_done=7416)
err:wave:wodPlayer_ProcessMessages pcm_pause failed: Input/output error
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd85648
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=15048 < primary_done=15052)
err:dsound:DSOUND_MixOne underrun on sound buffer 0x7fd85648
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  385
  Current serial number in output stream:  386

```


Any help would be very much appreciated... thank you all so much in advance.

---

### Post by Pikestaff on 2008-06-21
Okay never mind, I figured it out. :)  Basically for some reason it was refusing to work with OpenGL, which I was telling it to do, and obviously without OpenGL half the graphics don't show up.

But for some reason the fix suggested in [this post]("http://ubuntuforums.org/showpost.php?p=5189087&postcount=2") worked perfectly.  I just set the sound to ALSA + full hardware acceleration and everything is looking flawless like before.  :grin:  Happy questing all.

---

