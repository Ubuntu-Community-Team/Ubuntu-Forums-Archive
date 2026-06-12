---
title: "Problem with WoW on 8.04 with Wine 0.9.60"
date: 2008-04-24
forum: Wine
---

### Post by BombeNissen on 2008-04-24
I've just installed ubuntu 8.04 on my laptop that Used to run Kubuntu 7.10. I've also installed Wine 0.9.60 and World of Warcraft, downloaded the *.dll files thats mentioned in the howto for 7.10 with older versions of wine, added the Regedit value and also added the "OpenGL" line to the config.wtf file in the wow folder.

It all used to work just perfectly, ran wow in Windowed mode, and could Maximize the window without any trouble at all, also the game ran smooth.

Now, 8.04 and the latest version of Wine, Now I cant maximize the window and still play the game due to the window turn black and freezes. And the gamewindow flashes every 1-2 sec.

I dont have a clue of what to do anymore :confused:

Wine output from the Terminal:
> 
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
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
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecac,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3462
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f57c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402b24) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB


fglrxinfo:
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release


System Specs: Lenovo T60
> 
T5600(1.83GHz), 1GB RAM, 80GB 5400rpm HD, 14.1in 1400x1050 LCD, 128MB ATI Radeon X1400, CDRW/DVDRW, Intel 802.11abg wireless, Bluetooth/Modem, 1Gb Ethernet, UltraNav, Secure chip, Fingerprint reader, 9c Li-Ion batt


---

### Post by peppage on 2008-04-25
I have the exact same problem, I even tried to update to the newest wine.

---

### Post by Jaxilian on 2008-04-26
same problem here

---

### Post by McLeod Brennaman on 2008-04-26
This existed under the 8.04 beta as well, even using 0.9.58 and 0.9.59. Hardy broke it, Wine's still fine; I've got a little partition still running Gutsy and 0.9.60 pretty much dedicated to WoW, and not having issues. You may just want to gparted yourself a 10G Gutsy partition, throw Wine on it, and run WoW there. Not exactly sure what Hardy did to it, but it's broken, and considering the volume of little other issues with Hardy, it may be a while till that's figured out.

Irritating yes, but it's not Wine, and Hardy will end up getting polished out anyways, so with a Gutsy partition and a little patience, you should be fine.

---

### Post by Rody on 2008-04-27
I used to use wine all the time, but one day i got lazy and purchased crosoveroffice. I know that it is just wine with some tweaks and stuff but hot damn wow works no problem even on the ubuntu 8.4

I am not doging wine it self at all, but some times it is just nice to install a program and have it work.

rody

---

### Post by Mr_Congeniality on 2008-04-27
If you are a gamer, use wireless, or have a laptop, I strongly urge you to stay with Gutsy.  Hardy is turning out to be a major disaster.

---

