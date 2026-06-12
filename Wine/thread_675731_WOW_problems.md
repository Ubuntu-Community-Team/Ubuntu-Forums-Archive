---
title: "WOW problems"
date: 2008-01-23
forum: Wine
---

### Post by Kingfield on 2008-01-23
Okay, so basically I get this output when i run wow (and its really slow)

```
kingfield@kingfield-laptop:/$ env WINEPREFIX="/home/kingfield/.wine" wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f40c,0x00000000), stub!
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
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7d4324a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34d1a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34d200,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

```

So um. Anyone know why?

Thanks.}

OK, by the way I have an integrated intel graphics card, maybe that is the problem?

---

### Post by Kingfield on 2008-01-23
Oh, and it works perfectly on windows by the way.

---

### Post by FiatLux on 2008-01-23
Please post your specifications of your laptop. Laptops are generally not made for running graphic intensive games like WoW - so it could be the problem that causes the bad performance.

Btw, there's a special thread regarding WoW - it's long, but it helps out when all posts are kept within one thread.

---

### Post by Kingfield on 2008-01-23
Processor: Intel T2500 2.0GHz Core Duo
Memory/RAM: 1GB
Graphics Card: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

WoW works perfectly on windows though....

---

### Post by Kingfield on 2008-01-23
bump just before i sleep

---

### Post by person_99 on 2008-01-23
Go to your WoW folder (Defalt home/youruser/World of Warcraft), then the folder WTF. Open config.WTF with a text editor. Add the line: ```
SET gxApi "opengl"
```.
That is what killed the problems for me.

---

### Post by Kingfield on 2008-01-23
I got that I followed the instructions on the How to WOW with wine

---

### Post by Kingfield on 2008-01-24
additional info: the framerate is 2 Fps, and there is a bug where i stand beneath the ground and lots of other graphical glitches

---

### Post by scizzo on 2008-01-24
Sounds like the standard DirectX errors that is for DirectX 9 since wine has low support for that at the moment.

However shouldn't be that bad really. Are you starting the wow.exe from a install in the homefolder or are you starting it from a windows directory somewhere else? (a disk mounted as a fat32 or simular)

---

### Post by Ferrat on 2008-01-24
AFAIK Laptop integrated cards have some real problems in linux on the 3d front and Intel chips are no exception and sometimes even worse than others since the drivers are really lacking. 

are you sure that Direct Rendering ect is working as it should?

try " glxinfo|grep direct " in a terminal and see if you get the output " direct rendering: Yes "

---

### Post by Kingfield on 2008-01-24
Warcraft III works perfectly (except no widescreen resolution) on linux. and the output would be yes, I use a quite a lot of direct rendering required applications.

---

### Post by Kingfield on 2008-01-24
> **scizzo said:**
> Sounds like the standard DirectX errors that is for DirectX 9 since wine has low support for that at the moment.

However shouldn't be that bad really. Are you starting the wow.exe from a install in the homefolder or are you starting it from a windows directory somewhere else? (a disk mounted as a fat32 or simular)

I am running it from Program Files in wine directory
```

env WINEPREFIX="/home/kingfield/.wine" wine "C:\Program Files\World of Warcraft\WoW.exe"
```

---

### Post by Kingfield on 2008-01-25
liek bump homg

---

### Post by Resonance378 on 2008-01-25
Try this thread instead - much more likely to get what you need: [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

---

### Post by Kingfield on 2008-01-27
Sorry but i'm not online that often to be able to check a big thread like that so im asking for help here

---

### Post by Kingfield on 2008-01-27
BUMP can somebody Please tell me >_>

---

### Post by nyinge on 2008-01-28
It's strange that you're only getting 2fps.  Can you post your Config.wtf?

---

### Post by Kingfield on 2008-01-28
Config.wtf

```
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET doodadAnim "0"
SET SmallCull "0.010000"
SET DistCull "350.000000"
SET MaxLights "1"
SET frillDensity "8"
SET farclip "237"
SET particleDensity "0.400000"
SET baseMip "1"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET lastCharacterIndex "1"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName ""
SET Sound_VoiceChatOutputDriverName "Analog Devices AD1981"
SET Sound_OutputDriverName "Analog Devices AD1981"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET patchlist "us.version.worldofwarcraft.com"
SET spellEffectLevel "6"
SET groundEffectDist "70"
SET realmName "Frostmourne"
SET gameTip "18"
SET uiScale "1"
SET mouseSpeed "1"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET UIFaster "2"
SET Sound_OutputDriverIndex "1"
SET Sound_VoiceChatInputDriverIndex "1"
SET Sound_VoiceChatOutputDriverIndex "1"
```

---

### Post by toben7l on 2008-01-28
standard answer of course but i haven't seen it mentioned, so here it goes - is your graphics card driver up to date? Warcraft III takes a LOT less processing power to run than WoW btw. integrated graphics cards, especially on laptops (which usually max out ram at 2gb) tend to be bad for gaming

---

### Post by nyinge on 2008-01-28
Config.wtf seems fine to me.  Can you double check your wine registry settings?  This [gentoo-wiki]("http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine") page also has some other great tips as well.  Other than that, I think it's rather a hardware limitation at this point.

---

### Post by Kingfield on 2008-01-29
it works no problem on windows though...

---

### Post by hikaricore on 2008-01-29
> **Kingfield said:**
> it works no problem on windows though...

Please refrain from making pointless replies such as this one.
Also sticking to one thread my be more useful than jumping back and forth.

People have made suggestions here and you've ignored at least a few of them.

I'm going to make it known again that Linux is Not Windows.  Just because something works on your Intel integrated chip in ***ows does not mean it will work under Linux.  These types of cards depend heavily on DirectX to function properly, and there is no such thing as DirectX for linux.  WINE converts DX to OpenGL or runs OpenGL native.  Thus bringing us to the problem with the Intel hardware/drivers, in my experience little to no OpenGL support.  I'm tempted to compare Intel video to a WinModem where the hardware is slim relying on software to do all the work.  Perhaps I am wrong about this and Intel just released useless drivers for the the Linux community, but I doubt it.  I think the problem lies in both.

---

### Post by Kingfield on 2008-01-29
okay... And i have not ignored any suggestions mate.

---

### Post by nyinge on 2008-01-29
At this point, I would look around this forum and the rest of the web for a similar hardware and see their performance on games in general (i.e. if you couldn't find someone trying to play wow).  [Phronix.com]("http://www.phoronix.com/scan.php?page=phoronix_articles#Graphics") would be a start (linked to their video section).

After research, If you've come to a conclusion that your hardware is capable, you'd solely focus your effort in tweaking your software configurations.

Yes, it'd take some time and pain, but once you get it, it'd be no less joy than getting a full set of Vengeful Gladiator.  :)

---

### Post by Kingfield on 2008-02-01
> **nyinge said:**
> At this point, I would look around this forum and the rest of the web for a similar hardware and see their performance on games in general (i.e. if you couldn't find someone trying to play wow).  [Phronix.com]("http://www.phoronix.com/scan.php?page=phoronix_articles#Graphics") would be a start (linked to their video section).

After research, If you've come to a conclusion that your hardware is capable, you'd solely focus your effort in tweaking your software configurations.

Yes, it'd take some time and pain, but once you get it, it'd be no less joy than getting a full set of Vengeful Gladiator.  :)

thanks for your suggestion I will try it out.

---

### Post by jaytek13 on 2008-02-01
What is the guide that you used exactly? Did it include the registry edit tweak?

   1.  Open regedit (regedit)
   2. Navigate to HKEY_CURRENT_USER\Software\Wine\
   3. Right click on the wine folder and select [NEW] then [KEY].
   4. Replace the text New Key #1 with OpenGL (case sensitive).
   5. Right click in the right panel and select [NEW] then [String Value].
   6. Replace the text New Value #1 with DisabledExtensions (case sensitive).
   7. Now right click on DisabledExtensions and select Modify
   8. A dialog box should appear. In the value field type GL_ARB_vertex_buffer_object

---

### Post by Kingfield on 2008-02-04
jaytek, I have followed those instructions properly. By the way I want to clarify something, IS THERE A KNOWN PROBLEM OF INTEL INTEGRATED CARDS AND WoW?

Thanks, Kingfield

---

