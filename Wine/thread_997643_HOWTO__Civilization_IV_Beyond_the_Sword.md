---
title: "HOWTO :: Civilization IV Beyond the Sword"
date: 2008-11-30
forum: Wine
---

### Post by digitalb0y on 2008-11-30
I have BTS working just about perfect (from trial and error) I'm making a quick how-to to help those who have had issues. Starting from a clean wine install.

First, download winetricks. This makes the process so much easier.
```
wget http://www.kegel.com/wine/winetricks
```

Then download cabextract if your system does not have it.
on ubuntu type ```
sudo apt-get install cabextract
```
otherwise download cabextract here [http://www.cabextract.org.uk/](http://www.cabextract.org.uk/)

This is needed for winetricks. Once cabextract is installed lets run winetricks.

```
sh winetricks corefonts vcrun6 dotnet11 msxml3 msxml4 directx9
```
This installs windows fonts needed some DLLS, the XML engine, DOT.NET and DirectX 9

Then type
```
sh winetrcisk winxp 
```
This changes the version on windows to XP

then

install Civ4 from the Setup.exe on the CD

once its installed
Start the program. Once at the Main Menu, Exit the program. (this step creates the CivilizationIV.ini file)
now edit 
```
nano ~/My\ Games/Sid\ Meier\'s\ Civilization\ 4/CivilizationIV.ini
```

Find the following and make sure it matches what is below

; Set to 1 for no tech splash screens
```
NoTechSplash = 1

```


; Set to 1 for no intro movie
```
NoIntroMovie = 1
```


; Disable voice over IP capture and playback
```
EnableVoice = 0
```


once done 
try to run the program.

It all works lets move onto Warlords.

run the warlords cdrom setup.exe
after the install run the program then exit
 edit 
```
nano ~/My\ Games/Warlords/CivizationIV.ini 
```
file ini to the same as the orginal civ4.

now try to run the program.

If it all works lets move onto Beyond the Sword.

Beyond the Sword tip ** Make sure your not connected to the Internet or it will try to download updates and freeze the system.

If the install freezes at updating directx then install directx updates manually by running setup.exe in the directx folder.

Once installed Run the program like before and exit.

Now edit the config file

```
nano ~/My\ Games/Beyond\ the\ Sword/CivizationIV.ini file
```

Find the following and make sure it matches what is below

; Set to 1 for no tech splash screens
```
NoTechSplash = 1

```

; Set to 1 for no intro movie
```
NoIntroMovie = 1
```

; Disable voice over IP capture and playback
```
EnableVoice = 0
```


now run BTS 

This is what worked for me I hope it helps you.


P.S. If your using early versions of civ4 it's recommended you download the patches directly from the website.
[http://www.firaxis.com/games/downloads.php ]("http://www.firaxis.com/games/downloads.php")here is the link for All Civ4 patches

**Audio TIP**

When upgrading to 9.0.4 Jaunty Jackalope I had sound issues with wine.

I opened up winecfg -> Audio Tab (unchecked all drivers but OSS)

Then added the pulseaudio oss wrapper "padsp" the the front of the wine command 

>  padsp wine Civilization4.exe

---

### Post by Orky on 2009-04-09
```
$ wine Civilization4.exe
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:service:QueryServiceObjectSecurity 0x140408 4 0x140ad8 0 0x32ef30 - semi-stub
fixme:service:QueryServiceObjectSecurity 0x140408 4 0x140ad8 28 0x32ef30 - semi-stub
fixme:advapi:SetEntriesInAclA 1 0x32eec0 0x140aec 0x32ef2c
fixme:service:SetServiceObjectSecurity 0x140408 4 0x32eeac
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:font:WineEngRemoveFontResourceEx :stub
```

I did the winetricks stuff, installed Civ IV from the CDs, and when I tried to run it (unpatched from CD version), I got the splash screen, and the messages above.

I run: Kubuntu 8.04, wine 1.1.18 (wine.budgetdedicated.com repository)
I have:
[LIST]
[*]Vanilla CD version from box
[*]Warlords CD version
[*]Beyond the Sword DVD version
[/LIST]

I haven't tried applying patches yet, because the unpatched version 1.0 won't even start, and your instructions did not mention patching.

I've read [http://appdb.winehq.org/objectManager.php?sClass=version&iId=8788&iTestingId=33466]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8788&iTestingId=33466"), but it doesn't seem to be very helpful.

Could you please offer some assistance?

---

### Post by digitalb0y on 2009-04-13
Orky,

When you got the splash screen where did it Crash. This helps determine where the issue can be? 
I'm currently using the gold Edition and worked right out of the box. No patches. I also have Civ4 ver 1.0 but disk 1 has scratches and no longer works. The disk did work on earlier versions of wine. 
Currently I'm using wine-1.0.1 direct from Ubuntu.

[http://www.firaxis.com/games/downloads.php ]("http://www.firaxis.com/games/downloads.php") here is the link for Civ4 patches. I didn't need it but if your using version 1.0 it's a recommended download.

---

### Post by Neo40 on 2009-04-18
Hi,

I was able to install and play civ iv and BTS with Intrepid 8.10. Today, I decided to install Ubuntu 9.04 RC Jaunty Jackalope. I did a fresh
install, so I had to reinstall civ IV and BTS. I had no problem to install the game. I can play Civ IV but if I try BTS, It crashes after  the load screen saying "Init MP/Voice". I use wine 1.1.19

Any idea?
Thanks

---

### Post by MindFlayer on 2009-04-19
Wine 1.1.19 broke Civilization IV for me. I had to downgrade it to 1.1.18 to make it work.

---

### Post by osarusan on 2009-05-13
In Jaunty and Wine 1.1.21 I have BTS working *almost* perfectly. The sound is perfect, the videos work, the game is FAST! The cities still dont have progress bars, but that is no problem if you enable extra city data in the options.

The one problem I'm having now is kind of major though... Every once in a while the game crashes. I've played up to the Renaissance in one game, and just a handful of turns in another game, so I'm not sure what is causing the crash.

---

### Post by moocher on 2009-05-26
Following directions from here: [http://www.rikertothebridge.com/2009/05/installing-civilization-iv-warlords-and-beyond-the-sword-on-ubuntu-linux/](http://www.rikertothebridge.com/2009/05/installing-civilization-iv-warlords-and-beyond-the-sword-on-ubuntu-linux/)
I have managed to install the game but can't play it. I start a game fine, but as soon as it finishes loading and should take me to the start, the game crashes.

The CivFanatics site reccomends this method: [http://forums.civfanatics.com/showthread.php?t=313577&highlight=linux](http://forums.civfanatics.com/showthread.php?t=313577&highlight=linux)
I'd rather not install another app and reinstall the games if I don't need to, but the method I'm following doesn't seem to work. Is there any hope for it, or should I give up and start over the CifFanatics way?

---

### Post by jacksaff on 2009-05-27
Run civ4 from the terminal. 
wine "path/to/civ4.exe"
Then, when it crashes the terminal should have some error messages.
Civ4 crashes consistently for me in jaunty as long as pulse audio is installed.

---

### Post by moocher on 2009-05-28
I'm not sure what here is due to the crash, and what isn't.
```
fixme:powrprof:DllMain (0x7e350000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000457,(nil),0x0001,0x00000000,0x7e5da254,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime Optimization Service (clr_optimization_v2.0.50727_32) - Service reached limit of transient errors. Will shut down. Last error returned from Service Manager: 0x80070005.\n"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000454,(nil),0x0001,0x00000000,0x7e5da2c8,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for E:\Firaxis Games\Civ4\Beyond the Sword\Logs.lnk
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for E:\Firaxis Games\Civ4\Beyond the Sword\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for E:\Firaxis Games\Civ4\Beyond the Sword\CivilizationIV.ini.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x2002a 0x00000000
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "<string>", line 2, in ?
IOError: [Errno 2] No such file or directory: 'C:\\windows\\profiles\x07lex\\My Documents\\My Games\\Beyond the Sword\\Logs\\PythonErr2.log'
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:win:EnumDisplayDevicesW ((null),0,0x32efb8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4f0,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1dd8d0) : stub
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 513
Mesa 7.0.3-rc2 implementation error: bad target in BindTexture
Please report at bugzilla.freedesktop.org
Mesa 7.0.3-rc2 implementation error: bad target in BindTexture
Please report at bugzilla.freedesktop.org
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexImage2D @ surface.c / 340
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCopyTexSubImage2D @ surface.c / 937
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1dd8d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1dd8d0) : stub
```

---

### Post by NightMKoder on 2009-05-28
Wow, there's some major bad mojo with your graphics card. What's your video card driver/version?

---

### Post by vuroth on 2009-06-05
For some reason, wine fails on reading /home/myname/.winetrickscache.  I'm having to run the installation by hand.  :(

---

### Post by Carolla on 2009-06-05
Hi, I am absolutely new to Ubuntu, just dual installed 8.10 and wine. I want to be able to run CIV IV BTW with a mod. I find I don't understand the Ubuntu language yet and that most of the instructions are pretty well meaningless. Does anyone have any help for me? I am computer literate in other areas - from way back in the DOS days through Windows (running XP pro atm). I'd love to break the Windows habit and am willing to learn the language, but I do need to run my multiplayer games on CIV IV. :)

Please send me to a starting point, or walk me through this? Thanks!!

---

### Post by Neo40 on 2009-08-22
Well, me again with the same problem. Installed game without problem. I can play vanilla civ iv. But if I start BTS, it crashes after the load screen saying "Init MP/Voice".
 Here is I get from command line:

```
[eric@myhost Beyond the Sword]$ wine Civ4BeyondSword.exe
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
err:menubuilder:Process_Link unable to load L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Beyond the Sword\\Saves.lnk"
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:Process_Link unable to load L"C:\\Program Files\\Firaxis Games\\Sid Meier's Civilization 4\\Beyond the Sword\\CivilizationIV.ini.lnk"
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\CivilizationIV.ini.lnk
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:wtsapi:WTSRegisterSessionNotification Stub 0xc0030 0x00000000
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
wine: Unhandled exception 0xc06d007f at address 0x7edfa8b2 (thread 0009), starting debugger...
Unhandled exception: 0xc06d007f in 32-bit code (0x7edfa8b2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7edfa8b2 ESP:0032f570 EBP:0032f5d4 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7ede4c2d EBX:7ee6b7fc ECX:00000000 EDX:c06d007f
 ESI:c06d007f EDI:00000000
Stack dump:
0x0032f570:  0032f600 00000004 00ba0386 c06d007f
0x0032f580:  00000000 00000000 7edfa8b2 00000001
0x0032f590:  0032f604 c000007a 7e006672 7ef9d86b
0x0032f5a0:  00bf5acc 7ef8d8f9 00bf5acc 0032f5dc
0x0032f5b0:  7ee1b9fd c000007a 0032f5c8 00000000
0x0032f5c0:  0032f5d0 7ee1b9bd 7edfa86a 00bf5acc
Backtrace:
=>0 0x7edfa8b2 RaiseException+0x52() in kernel32 (0x0032f5d4)
0x7edfa8b2 RaiseException+0x52 in kernel32: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (91 modules)
PE	  330000-  343000	Deferred        zlib1
PE	  350000-  35e000	Deferred        hapdbg
PE	  400000- 1038186	Deferred        civ4beyondsword
PE	 1040000- 13af000	Deferred        d3dx9_33
PE	 1ca0000- 2144000	Deferred        cvgamecoredll
PE	10000000-1002b000	Deferred        boost_python-vc71-mt-1_32
PE	18000000-18038000	Deferred        binkw32
PE	1e000000-1e1ca000	Deferred        python24
PE	21100000-2118c000	Deferred        mss32
PE	69b10000-69c14000	Deferred        msxml3
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7dd6e000-7dd82000	Deferred        midimap<elf>
  \-PE	7dd70000-7dd82000	\               midimap
ELF	7dd82000-7dda7000	Deferred        msacm32<elf>
  \-PE	7dd90000-7dda7000	\               msacm32
ELF	7dda7000-7ddbe000	Deferred        msacm32<elf>
  \-PE	7ddb0000-7ddbe000	\               msacm32
ELF	7ddbe000-7ddc7000	Deferred        librt.so.1
ELF	7ddc7000-7de8e000	Deferred        libasound.so.2
ELF	7de9f000-7ded5000	Deferred        winealsa<elf>
  \-PE	7deb0000-7ded5000	\               winealsa
ELF	7df23000-7df55000	Deferred        uxtheme<elf>
  \-PE	7df30000-7df55000	\               uxtheme
ELF	7df55000-7df5e000	Deferred        libxcursor.so.1
ELF	7df5e000-7df63000	Deferred        libxfixes.so.3
ELF	7df63000-7df66000	Deferred        libxcomposite.so.1
ELF	7df66000-7df6d000	Deferred        libxrandr.so.2
ELF	7df6d000-7df76000	Deferred        libxrender.so.1
ELF	7df76000-7df7b000	Deferred        libxxf86vm.so.1
ELF	7df7b000-7df7e000	Deferred        libxinerama.so.1
ELF	7df7e000-7df9e000	Deferred        imm32<elf>
  \-PE	7df80000-7df9e000	\               imm32
ELF	7df9e000-7dfa3000	Deferred        libxdmcp.so.6
ELF	7dfa3000-7dfbc000	Deferred        libxcb.so.1
ELF	7dfbc000-7dfbf000	Deferred        libxau.so.6
ELF	7dfbf000-7dfc3000	Deferred        libuuid.so.1
ELF	7dfc3000-7e0df000	Deferred        libx11.so.6
ELF	7e0df000-7e0ee000	Deferred        libxext.so.6
ELF	7e0ee000-7e106000	Deferred        libice.so.6
ELF	7e106000-7e10e000	Deferred        libsm.so.6
ELF	7e11f000-7e1ba000	Deferred        winex11<elf>
  \-PE	7e130000-7e1ba000	\               winex11
ELF	7e23a000-7e260000	Deferred        libexpat.so.1
ELF	7e260000-7e28b000	Deferred        libfontconfig.so.1
ELF	7e29c000-7e2b0000	Deferred        libz.so.1
ELF	7e2b0000-7e335000	Deferred        libfreetype.so.6
ELF	7e335000-7e380000	Deferred        dsound<elf>
  \-PE	7e340000-7e380000	\               dsound
ELF	7e380000-7e465000	Deferred        oleaut32<elf>
  \-PE	7e3a0000-7e465000	\               oleaut32
ELF	7e465000-7e4d0000	Deferred        rpcrt4<elf>
  \-PE	7e470000-7e4d0000	\               rpcrt4
ELF	7e4d0000-7e5c8000	Deferred        ole32<elf>
  \-PE	7e4f0000-7e5c8000	\               ole32
ELF	7e5c8000-7e5db000	Deferred        lz32<elf>
  \-PE	7e5d0000-7e5db000	\               lz32
ELF	7e5db000-7e5f4000	Deferred        version<elf>
  \-PE	7e5e0000-7e5f4000	\               version
ELF	7e5f4000-7e620000	Deferred        ws2_32<elf>
  \-PE	7e600000-7e620000	\               ws2_32
ELF	7e620000-7e6bb000	Deferred        winmm<elf>
  \-PE	7e630000-7e6bb000	\               winmm
ELF	7e6bb000-7e727000	Deferred        msvcrt<elf>
  \-PE	7e6d0000-7e727000	\               msvcrt
ELF	7e727000-7e7ec000	Deferred        comctl32<elf>
  \-PE	7e730000-7e7ec000	\               comctl32
ELF	7e7ec000-7e848000	Deferred        shlwapi<elf>
  \-PE	7e800000-7e848000	\               shlwapi
ELF	7e848000-7e9d4000	Deferred        shell32<elf>
  \-PE	7e860000-7e9d4000	\               shell32
ELF	7e9d4000-7ea29000	Deferred        advapi32<elf>
  \-PE	7e9e0000-7ea29000	\               advapi32
ELF	7ea29000-7eac9000	Deferred        gdi32<elf>
  \-PE	7ea40000-7eac9000	\               gdi32
ELF	7eac9000-7ec12000	Deferred        user32<elf>
  \-PE	7eae0000-7ec12000	\               user32
ELF	7edb6000-7ef20000	Export          kernel32<elf>
  \-PE	7edd0000-7ef20000	\               kernel32
ELF	7ef20000-7ef2c000	Deferred        libnss_files.so.2
ELF	7ef2c000-7ef52000	Deferred        libm.so.6
ELF	7ef52000-7f000000	Deferred        ntdll<elf>
  \-PE	7ef60000-7f000000	\               ntdll
ELF	b7c9d000-b7cb1000	Deferred        wtsapi32<elf>
  \-PE	b7ca0000-b7cb1000	\               wtsapi32
ELF	b7cb3000-b7cb7000	Deferred        libdl.so.2
ELF	b7cb7000-b7dfd000	Deferred        libc.so.6
ELF	b7dfd000-b7e16000	Deferred        libpthread.so.0
ELF	b7e27000-b7f62000	Deferred        libwine.so.1
ELF	b7f63000-b7f81000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Civ4BeyondSword.exe
	00000009    0 <==
0000000e 
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000018    0
	00000017    0
	00000013    0
	00000012    0
00000019 
	0000001a    0
Backtrace:
=>0 0x7edfa8b2 RaiseException+0x52() in kernel32 (0x0032f5d4)

```

I'm using wine 1.1.27

---

### Post by TheSqueak on 2009-08-25
... Never mind, installing the patch fixed it ...

---

### Post by yazmonium on 2010-05-02
I followed the instructions above and I managed to get BTS to run, but after playing for a while, the game causes a disk error and the partition that it is on becomes read only and I have to restart my computer and run fsck to fix it.  I thought it was an auto-save problem, but I turned changed the .ini file to auto-save every 10,000 turns and it still is happening.  Has anyone else had this problem?

-Yaz

---

### Post by yazmonium on 2010-05-04
bump

---

### Post by yazmonium on 2010-05-15
Is no one playing this game anymore???

---

### Post by vuroth on 2010-06-04
Trying to run Civ 4 (direct2drive), I get this:

```
err:module:find_forwarded_export function not found for forward 'msvcrt.__CppXcptFilter' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.__iob_func' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._strtoi64' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._strtoui64' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.__uncaught_exception' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.__pctype_func' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.___lc_codepage_func' used by L"C:\\windows\\system32\\msvcr71.dll". If you are using builtin L"msvcr71.dll", try using the native one instead.
```

If I use winetricks to update vcrun2003, civ4 just crashes hard.

---

