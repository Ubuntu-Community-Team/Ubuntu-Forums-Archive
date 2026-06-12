---
title: "Yet another WoW thread, yes again."
date: 2008-02-24
forum: Wine
---

### Post by str3ck on 2008-02-24
alright i've spent 3 days lurking and looking at the forums trying to figure out where i went wrong.  i've read pretty much ever single WoW forum post i could find here and from what i can tell no one seemed to have the specific issue i am having.  first let me tell everyone what the problem is, then i will continue with what i think you are going to ask me.  

when i launch WoW, the screen fades to black for about 3 seconds then fades back to my desktop.  during this time i can hear the WoW music playing in the back ground the entire time.  also if i move the mouse around i have the WoW cursor.  but while on that desktop i can't click anything or move to a different desktop using the mouse.  if i use the keyboard commands to move to a different desktop that works fine and i can do pretty much anything i would normally be able to do.  if i go back to the desktop which i launched WoW from, it's still pretty much locked up.  and through all of this i can still hear the WoW music in the background taunting me.

Specs: Ubuntu 7.10, newest version of WINE. 3.0Ghz HT 1.25 GiGs of ram , 82915G/P/GV/GL/PL/910GL Intel Graphics controller.

i followed the most recent How-to on this forum to install and set up WINE, and WoW.  everything seemed to go fine with no error messages or anything.  looked at all the Trouble-shooting pages i could and none seemed to work for me.  i think i've installed the most recent drivers for the video but i may be wrong there.  (i'm not a Linux guru or anything, but this is not my fist Linux box either). tired OpenGL and d3d, same result.  tired the DLL's.  and last but not least, tried launching with the launcher, a direct icon, as well as the terminal.  the terminal spits this out to me.

> fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4f8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f124,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STU

i'm at my wits end here, please someone have the answer. i also know that my intel graphics chipset is probably the culprit but there have been a few people who have gotten them to work, and as far as i can see, no one with this chipset has posted if they have had problems or not.

---

### Post by str3ck on 2008-02-25
i got it to work finally.  for those of you that may have this issue in the future the fix is very simple.  during the WINE install there is a section that tells you to go in and tell WINE to mimic XP so that the apps you are running think they are in XP.  well after the install i went back in and told WoW specifically to be XP instead of using the global settings.  fired right up.  now i just got to do the framerate tweaks to be able to play.

---

