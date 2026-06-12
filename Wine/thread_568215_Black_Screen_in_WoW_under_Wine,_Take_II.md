---
title: "Black Screen in WoW under Wine, Take II"
date: 2007-10-05
forum: Wine
---

### Post by denali on 2007-10-05
Good Evening, 

I'm currently using version 0.9.46 of Wine. My system setup is as follows: 

```
cpu: AMD Athlon(tm) XP 2000+ 
cpu_ghz: 1.66 
memory: 884 
videocard_manufacturer: NVIDIA Corporation 
videocard_type: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW! 
videocard_ram: 128 
agp_aperture_size: 92 
videocard_driver_version: 1.5.8 NVIDIA 96.39 
soundcard: NVidia nForce2 with ALC650E at 0xec080000, irq 1 
soundcard_driver: ALSA Version 1.0.13 
machine_bitness: 32 
kernel: 2.6.20-16-generic 
x_version: Xorg Version 7.2.0
```

My config.wtf can be seen at [http://pastebin.com/f7521582f](http://pastebin.com/f7521582f) 

Regardless of mode, when I start WoW, I get a black screen with the gauntlet cursor. Back when I had sound turned on, I'd also get the login screen music/sound effects. 

In Direct3D mode, Wine gives the following: 

```
denali@mountain:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -d3d 
fixme:advapi:SetSecurityInfo stub 
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED) 
fixme:powrprof:DllMain (0x7c3e0000, 1, (nil)) not fully implemented 
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11 
fixme:powrprof:DllMain (0x7c3e0000, 0, (nil)) not fully implemented 
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda8,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecd0,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2cc,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ac,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a4,0x00000000), stub! 
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED) 
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible 
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x1302a0) call to IWineD3DDevice_CreateQuery failed 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f004,0x00000000), stub! 
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED) 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4 
fixme:reg:GetNativeSystemInfo (0x374026c4) using GetSystemInfo() 
fixme:process:IsWow64Process (0xffffffff 0x7a23e494) stub! 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc() 
@ utils.c / 1346 
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc() 
@ utils.c / 1346 
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc() 
@ utils.c / 1346 
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc() 
@ utils.c / 1346 
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc() 
@ utils.c / 1346 
fixme:d3d:set_tex_op_nvrc >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from set_tex_op_nvrc() 
@ utils.c / 1346 
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_OUT_OF_MEMORY (0x505) from glDrawElements @ drawprim.c / 266 
fixme:d3d_draw:drawStridedFast >>>>>>>>>>>>>>>>> GL_OUT_OF_MEMORY (0x505) from glDrawElements @ drawprim.c / 266
```

The last couple of lines repeat ad infinitum until the wineserver is terminated. The only thing that changes is the function after the draw:. 

In OpenGL mode, I get the following: 

```
denali@mountain:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl 
fixme:advapi:SetSecurityInfo stub 
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED) 
fixme:powrprof:DllMain (0x7c3e0000, 1, (nil)) not fully implemented 
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11 
fixme:powrprof:DllMain (0x7c3e0000, 0, (nil)) not fully implemented 
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda8,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecd0,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2cc,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ac,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a4,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f52c,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f51c,0x00000000), stub! 
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED) 
fixme:win:EnumDisplayDevicesW ((null),0,0x33f004,0x00000000), stub! 
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED) 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4 
fixme:reg:GetNativeSystemInfo (0x374026c4) using GetSystemInfo() 
fixme:process:IsWow64Process (0xffffffff 0x7ad1e494) stub! 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED) 
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED) 
fixme:win:EnumDisplayDevicesW ((null),0,0x33de84,0x00000000), stub!
```

Am I doing something wrong? If so, what?

---

### Post by Darkblizz on 2007-10-05
did you install the latest video drivers for ur card?

---

### Post by denali on 2007-10-05
> **Darkblizz said:**
> did you install the latest video drivers for ur card?

It appears nVidia has recently updated their website to post new drivers (96.43.01) for my card.  I will try them tonight and report back if there is any change.

This is a bit odd, considering I was just on their site last night to check for this very thing.  :confused:

---

### Post by denali on 2007-10-05
Ok, no joy.  The latest drivers cause the same problem.

---

### Post by indiechixor on 2007-10-05
Hey nice I came on here to talk about this exsact issue.

This is what my screen looks at when trying to load WoW
[Screenshot]("http://img.photobucket.com/albums/v247/indie_chixor2/Screenshot.png")

the most annoying thing that happens is once I enter this windowed mode, I can still move my mouse, but I can't click anything...i can't even hit my power button and do a soft-restart..only thing i can do is a hard restart.

total newB... any help is appreciated.

---

### Post by indiechixor on 2007-10-05
Also, I don't know how to get into the game via terminal, so i've been using my wine Installer.exe, since it essentially does the same thing.

heres what i get: ```
fixme:powrprof:DllMain (0x7c630000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c630000, 0, (nil)) not fully implemented
fixme:font:CreateScalableFontResourceW (1,0x84f7b0,0x84f708,(nil)): stub
failed to play a WAVindie@Hikaru:~/BurningCrusade$ err:systray:delete_icon invalid tray icon ID specified: 0
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:shdocvw:WebBrowser_QueryInterface (0x12e0e8)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x34e780) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x12e0e8)->(0x34e74c)
fixme:shdocvw:OleControl_FreezeEvents (0x12e0e8)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x12e0e8)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x12e498): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12e478): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12e478): WIN32_FIND_DATA is not yet filled.
err:wininet:INTERNET_ReadFile not all data received 0/41220
fixme:iphlpapi:NotifyAddrChange (Handle 0x78fad9e8, overlapped 0x78fad9cc): stub
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12e17c)->((null) 1 0x34df04 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 25 2 0x34df18 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 26 2 0x34df18 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12e17c)->(0x34df54)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34e010 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x143140)->(L"" L"" 0 0x34e044)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x143140)->(0x34e048 0x34e058)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 29 2 0x34ecc0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12e17c)
fixme:shdocvw:ClientSite_GetContainer (0x12e17c)->(0x34ece0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12e17c)->(0xb7e5f109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 25 2 0x34ec14 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 26 2 0x34ec14 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 28 2 0x34ec6c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 26 2 0x34eca0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 29 2 0x34ecb0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12e17c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12e17c)->(0x7bc9e546)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x12e0e8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x143440)->((nil))
fixme:shdocvw:OleObject_Close (0x12e0e8)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c550000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c550000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed18,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f34c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f724,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x12da98) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x130700) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x34f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

```

---

### Post by denali on 2007-10-05
> **indiechixor said:**
> Hey nice I came on here to talk about this exsact issue.

This is what my screen looks at when trying to load WoW
[Screenshot]("http://img.photobucket.com/albums/v247/indie_chixor2/Screenshot.png")

the most annoying thing that happens is once I enter this windowed mode, I can still move my mouse, but I can't click anything...i can't even hit my power button and do a soft-restart..only thing i can do is a hard restart.

total newB... any help is appreciated.

Luckily enough for me, locking up is not part of my problem.

---

### Post by Nyxess on 2007-10-06
i had a similar problem, but instead of a black screen, my desktop just stayed the same. i still couldn't click anything, and had to do a hard restart. Strating WoW from the terminal seemed to fix that

command:

wine "C:\Program Files\World of Warcraft\Launcher.exe"

or go straight into WoW:

wine "C:\Program Files\World of Warcraft\WoW.exe"



hope that helps =/

---

### Post by denali on 2007-10-06
In the original post, I'm starting it in a terminal.  Thanks for the reply, tho. :)

---

### Post by denali on 2007-10-08
I'm still looking for assistance with this problem?  Any advice?

---

### Post by denali on 2007-10-09
Problem solved: Video card built into nVidia NForce 2 IGP chipset is incompatible.

---

### Post by tyrion2323 on 2007-10-10
Hey Denali - I'm having this issue!  Responsive, but a black screen with the gauntlet hand.  :(

Here's what I've got:

Athlon X2 4200+
Asus A8N32-SLI Motherboard
1GB DDR400 RAM
Seagate 160GB HDD
Western Digital 160GB HDD
GeForce 7600GT Graphics

---

### Post by tyrion2323 on 2007-10-10
I updated my graphics drivers, and things seem to be working :)

---

### Post by denali on 2007-10-11
Yeah, for the later (Non-Legacy) nVidia cards, that is generally the solution.  For the old Legacy cards (the ones that MUST use the 96.xx.xx and 71.xx.xx drivers), you're pretty much boned.

---

### Post by tyrion2323 on 2007-10-11
Well, I've got WoW fully installed and updated.  It has all the latest patches, and I can login, select my character and hit PLAY.

It loads up as if it's going to play, but the becomes non-responsive :(  I am sure I can fix this, but at the moment, I'm not sure how.

My drivers are up to date from nVidia, so I'm sure it's something else I'm doing.

Any ideas?

---

### Post by denali on 2007-10-11
Well, if you can get that far, it's fixable.

First off, lets start with the basics.  Lets see your Config.WTF (minus ANY reference to your login account name!  Be SURE to remove it!), your list of addons and what options you have checked in the graphics/audio section of winecfg.

---

### Post by tyrion2323 on 2007-10-11
Denali, thanks for the help!

How do I get that info?  Also, to let you know - when WoW becomes unresponsive, the audio continues to play and my Gauntlet cursor continues to react, and I can get back to the desktop and to the kernel.

I'm a total linux noobie.  Don't worry, I'm buying books to remedy my lack of knowledge.  I want to be able to come these forums and help people!

---

### Post by denali on 2007-10-12
Locate your WoW directory on the hard drive.

In that directory, you will find another directory called "WTF".  In that directory is config.WTF.  It's a text file, so you can open it in a text editor, then cut and paste it here.  Like I said previously, MAKE SURE to look for and remove your log in name from the post.  You don't want someone to get that!

Go back to the main WoW directory and locate another directory called Interface.  Go into it and you should have an Addons directory.  I'm betting it's empty, but look in there and give me a list of what's there.

Next, open a terminal and type winecfg and hit enter.  Click on the Audio tab.  Tell me what all the settings say.  Next click on Graphics and do the same.

---

### Post by tyrion2323 on 2007-10-12
Will do as soon as I get out of work today

---

### Post by vacolten on 2007-10-15
I have been having a similar issue.  I haven't played WoW in 2 months (gasp!) and when I ran it under wine 0.9.45 (I think) it was fine.  After patching WoW with the latest patches and updating wine it freezes at authentication.  Brings up the opening screen but wont get past handshaking.  Sometimes it's even dropped my wireless connection.  I'm going to try the new NVidia drivers and see how that goes.

Also in the past and now when I quit the game, the sound from the game continues.  It basically loops the last sound that was playing when I quit (like the breeze over Barrens).

My config.WTF:
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1440x900"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "48"
SET farclip "777"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET realmList "us.logon.worldofwarcraft.com"
SET soundMaxHardwareChannels "12"
SET locale "enUS"
SET realmName "XXXXXXXX"
SET gameTip "88"
SET mouseSpeed "1.5"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET anisotropic "16"
SET Gamma "1.000000"
SET uiScale "1"
SET DesktopGamma "1"
SET expansionMovie "0"
SET spamFilter "0"
SET profanityFilter "0"
SET minimapInsideZoom "0"
SET guildMemberNotify "1"
SET MusicVolume "1"
SET SoundVolume "1"
SET MasterVolume "1"
SET AmbienceVolume "1"
SET EnableSoundWhenGameIsInBG "1"
SET patchlist "us.version.worldofwarcraft.com"
SET showToolsUI "1"
SET rotateMinimap "1"
SET autoSelfCast "1"
SET checkAddonVersion "0"
SET useUiScale "1"
SET minimapZoom "0"
SET gxTripleBuffer "1"
SET shadowLevel "0"
SET weatherDensity "3"
SET lod "1"
SET M2UsePixelShaders "1"
SET shadowLOD "0"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET cameraView "3"
SET UnitNameNPC "1"
SET SoundNumChannels "128"
SET ShowTargetCastbar "1"
SET readTerminationWithoutNotice "-1"
SET coresDetected "1"
SET Sound_OutputDriverName "dmix:0"

---

### Post by vacolten on 2007-10-15
Well scratch that.  I do have the most current Nvidia driver already, at least thats what Synaptic says (1.0.9755, right?  I installed the nvidia-glx-new and it's been working wonders for me).  Is this the most recent driver from Nvidia, or just the most recent to hit the repository?

My winecfg:

[IMG]http://the434.com/img/graphics.png[/IMG]

[IMG]http://the434.com/img/audio.png[/IMG]

---

### Post by Faud on 2007-10-15
In my wine set up on .946 I actually do not have the window manager to control window checked. I have the emulate a desktop checked and then if Im playing wow full screen I have the resoultion of wine and WoW set up to the same resoultion as my desktop

---

### Post by tyrion2323 on 2007-10-17
Sorry - I had to take my brother to the hospital (he's fine)

I'm back and want to fix my WoW :)

---

### Post by pissedoffdude on 2007-10-21
> **denali said:**
> Problem solved: Video card built into nVidia NForce 2 IGP chipset is incompatible.

That's odd, I have the same video card and WoW is able to work under Windows but gives me a black screen in linux.  I also get a black screen in other 3d games under linux.

---

### Post by denali on 2007-10-22
> **vacolten said:**
> Well scratch that.  I do have the most current Nvidia driver already, at least thats what Synaptic says (1.0.9755, right?  I installed the nvidia-glx-new and it's been working wonders for me).  Is this the most recent driver from Nvidia, or just the most recent to hit the repository?

No, 1.0.9755 is not the latest from nVidia. Before I take you down that path, do you feel comfortable working outside of X Windows in command line?  If you don't, then I feel I should draw you a map rather than just saying "do this and write back when it's done."

Let me know.

---

### Post by denali on 2007-10-22
> **tyrion2323 said:**
> Sorry - I had to take my brother to the hospital (he's fine)

I'm back and want to fix my WoW :)

Scroll back up to my last reply to you and provide me with the requested info so we can continue. :)

P.S.- Glad to hear your bro is ok!

---

### Post by denali on 2007-10-22
> **pissedoffdude said:**
> That's odd, I have the same video card and WoW is able to work under Windows but gives me a black screen in linux.  I also get a black screen in other 3d games under linux.

Taken in context with the thread topic, how is it odd? :confused:  While I understand it worked in Windows (as it did for me), it does not work under Wine in Linux.  Maybe I'm not understanding your question?

Either way, it took me upgrading to a later video card to fix the problem.  Newer nVidia cards with 256M of ram can be had for under $40, so it is worth it.  I know I'm glad I did.

---

### Post by thepiratefish on 2011-05-19
I'd like to reopen this issue...I just installed 11.04 and have WoW completely up to date and I'm running it through the latest version of wine.

I can get to the login screen and the character selection screen and I can even click "enter world" but as soon as that loading screen is finished, I get some random colors and then it eventually goes black. All I can see after that is the gauntlet cursor and I can hear everything happening around my character. Hot keys seem to work since i can hear "I can't cast that" when I hit them but I can't see anything.

Anyone experience this same problem???

---

### Post by cwwilson721 on 2011-05-19
Don't necro threads.

Search for a MUCH newer one (There are TONS in this forum)

---

