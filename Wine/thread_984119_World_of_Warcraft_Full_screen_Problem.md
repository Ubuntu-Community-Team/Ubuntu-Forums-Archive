---
title: "World of Warcraft Full screen Problem"
date: 2008-11-16
forum: Wine
---

### Post by Samsinsane on 2008-11-16
Hi all,

Recently upgraded to Ubuntu 8.10, ever since I upgraded WoW no longer runs properly in wine when run full screen. While I had wine 1.1.7 I was able to get WoW to run properly using the window setting in winecfg although I really dislike playing like that. Since updating to wine 1.1.8 even using the window setting WoW will flick to full screen. That doesn't bother me, what bothers me is that WoW is completely distorted the only thing I can do is press esc. I can get a printscreen of this if it would help. I am using an AMD690G chipset for graphics, X1250 Radeon(according to the booklet, according to ATI Catalyst Control Center it's X1200 series) and using the flgrx driver(I read it does not support the X1250 though there is no other driver available). I have just gotten WoW membership again and would really love not having to log into windows to play.

I don't know a great deal about Linux and Wine but I am assuming the problem is either the driver or because I upgraded to 8.10 rather than do a fresh install. I have spent the past week or so searching for solutions but no-one else seems to have this problem or if they do, there is no response. I will include the terminal output below and I have configured WoW and wine the way the Ubuntu WoW page says to. 

```
wine "C:\Program Files\World of Warcraft\wow.exe"
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:powrprof:DllMain (0x7c030000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c030000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ecac,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3790
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f520,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374025c4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x20028, (nil), 16): stub

```

What really confuses me is that it mentions D3D in there but anyway if there is anything else that can help with finding the problem I will be more than happy to provide it, please also tell me how to do this, by this I mean if you require info from a file, a location would be very helpful, I do know how to use the terminal so running commands won't require too much help :p.

Oh I forgot to mention I am running 64-bit Ubuntu if that causes any problems.

Thanks in advanced,
Samsinsane

---

### Post by nzrock95 on 2008-11-16
Hmm...yea. Post a screenshot please. That'll help us know exactly what you mean by "WoW is completely distorted".
--Does this happen as soon as you switch to fullscreen mode? 
--Are you in a building (I know that sounds like it doesn't relate, but I've had trouble with WoW and buildings)? 
--Are you able to read the options when you press Esc?

---

### Post by Samsinsane on 2008-11-17
Ok I have attached the photo of the screen, sorry for the bad quality but you get the idea it's more blue than that but it was close enough. This happens when wow.exe is run, I'm assuming it stays the same if I blindly typed in my username and password too.

Does this appear to be a fixable problem or am I stuck using windows?

---

### Post by Samsinsane on 2008-11-21
Anyone have any ideas? I still have this problem.

---

### Post by nzrock95 on 2008-11-21
Post your Config.wtf inside WOWDIRECTORY/WTF.

P.S. Have you followed the configuration and registry hack [here]("https://help.ubuntu.com/community/WorldofWarcraft#Configuration")?

---

### Post by Samsinsane on 2008-11-22
> **Samsinsane said:**
> I have configured WoW and wine the way the Ubuntu WoW page says to. 

So that would be a yes, and my config.wtf file is as follows:
```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET farclip "507"
SET particleDensity "1.000000"
SET spellEffectLevel "6"
SET groundEffectDensity "24"
SET installType "Retail"
SET portal "us"
SET Gamma "1.000000"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET gxApi "OpenGL"
SET ffxDeath "0"
SET ffxGlow "0"
SET ffxSpecial "0"
SET M2UseShaders "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
```

---

### Post by desperado665 on 2008-11-22
I have had similar issues with the flgrx driver. I resolved it by removing the ati driver and using ubuntu's restricted driver.

---

### Post by Samsinsane on 2008-11-23
When I remove the driver through System-->Administration-->Hardware Drivers(I'm assuming this enables the Ubuntu restricted drivers) WoW won't even load. If there is more to enabling Ubuntu restricted drivers please tell me lol.

---

### Post by nzrock95 on 2008-11-23
Haha, sorry, did not read that part carefully.

Well, I have experienced similar problems (somewhat...), but using that registry key and editing config.wtf fixed it for me.

The only thing I can suggest is changing the line ```
SET gxApi "OpenGL"
``` to ```
SET gxApi "opengl"
``` I'm not sure if it is case sensitive or not, but it's worth a shot.

Good luck!

---

### Post by Samsinsane on 2008-11-24
Thanks for the tip, sadly it was originally in all lower case and on one of the sites used to create that wiki page, it had OpenGL so I changed it to that nothing changed though.

---

### Post by Zorthanis on 2008-11-24
I had to decrease the size of my window from fullscreen to even make it not do that.

---

### Post by Samsinsane on 2008-11-25
What do you mean? Change the resolution in Ubuntu? in WoW? or using a window in Wine?

---

### Post by Samsinsane on 2008-11-26
So any ideas anyone?

---

### Post by Samsinsane on 2008-11-30
anyone?

---

### Post by Samsinsane on 2008-12-06
Bump! Still experiencing the problem.

---

### Post by EnderEcho on 2009-01-02
What are your desktop settings? Make sure they are set to none. Sometimes that can be an issue. Try different configurations of Wine. Run it in a window instead.

Does it crash when you run it in Direct3D? I've heard thats a solution for ATI cards.

I'm running it on an Intel and im getting pretty jumbled graphics. Definitely clearer than what you're running though.

---

### Post by m0ibus on 2009-01-03
Hi Samsinsane

I had exactly the same problem in full screen mode.  What fixed it for me was going into Wine>Configure Wine;  select the Graphics tab; tick the "Emulate a Virtual Desktop" and set the resolution to 800x600.  You can use other resolutions too but that worked best for me.

Alternatively, running WoW in windowed mode also worked (but had a lower frame rate).  To run in windowed mode insert SET gxWindow "1" into your config.wtf file.

Regards
Gary

---

