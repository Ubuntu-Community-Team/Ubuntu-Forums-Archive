---
title: "WoW Black Screen w/ sound"
date: 2008-07-30
forum: Wine
---

### Post by servius09876 on 2008-07-30
Ok I have found a few post on this same issue.. I have followed the install instructions to a "T" I.E. emulation mode: win 98, update drivers with EnvyNG, Win Reg Edits, and WoW config.wtf edits.. and when i run the game i get no graphical output only sound.. i get the following in term. 

> wine "c:\Program Files\World of Warcraft\WoW.exe" -opengl

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
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f57c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

Any ideas I am currently running the most recent version of Ubuntu and running Fusion. 

Im also trying to get Sword of the Stars to work if anyone has any ideas.

---

### Post by Spydr4590 on 2008-07-30
Please post what video card you have, so I can better assist you.

---

### Post by servius09876 on 2008-07-30
Old Notebook... its a GeForce2 Go i believe it has 64mb or 128mb

---

### Post by flytripper on 2008-07-31
ty going to the wtf folder and either creating or adjusting a config.wtf file.... add SET GxApi= "OpenGl"

should fix

---

### Post by servius09876 on 2008-08-01
Ok sorry for the late reply, My Daughter just came into the World. 

Ok, so I checked the Config.WTF file and i have already made the following adjustments to no avail. 
> SET GxApi "OpenGl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET UIFaster "2"
SET M2UseShaders "0"

I have also set the color depths to 24 as I saw in another post and manually lowered the graphics settings to the lowest possible. I.E. Trilinear Filtering, draw distance, model details etc..

---

### Post by servius09876 on 2008-08-01
update. I managed to get the EULA screen up but the mouse doesnt show in this window... I am going to try somethings in wine... How i achieved this was setting the SET hwdetect "0" to "1".

---

### Post by servius09876 on 2008-08-01
Final Update.. After looking at my install notes I noticed i never tried D3D as the renderer and after removing the OpenGL line from the config.wtf it worked with no glitches.. I guess this version of Wine has much better D3D support than i believed.. Thanks to everyone for the suggestions.

---

