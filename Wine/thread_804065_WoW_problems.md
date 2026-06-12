---
title: "WoW problems"
date: 2008-05-22
forum: Wine
---

### Post by siterock on 2008-05-22
I read and followed a guide to install and update World of Warcraft on my laptop.  This went without a hitch, but when I try to play the game it plays the opening video with no problems, but that's as far as it goes.  Just to throw this out there, I am a linux newb.  I'm running Ubuntu 8.04.  My graphics card is an Intel.  Thanks in advance for your time.

---

### Post by Redmumba on 2008-05-22
For one, are you sure you're running it in OpenGL mode?  Also, does the video freeze mess it up, or does the Login menu?  Check the WoWwiki wine page for information on disabling the video if this is the case, and also for enabling OpenGL.

---

### Post by siterock on 2008-05-22
I'm pretty sure it's set to use opengl.  I added the SET gxApi "opengl"
line to the config.wtf file like the guide mentioned.  As I mentioned before, the opening video works great and the sound is great.  After that, the screen goes black and the music from the login screen plays, but no visual.  Here's the output of my terminal window:


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
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f298,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub

---

