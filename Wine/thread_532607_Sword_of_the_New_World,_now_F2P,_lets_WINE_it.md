---
title: "Sword of the New World, now F2P, lets WINE it"
date: 2007-08-22
forum: Wine
---

### Post by quadomatic on 2007-08-22
[http://www.swordofthenewworld.com/](http://www.swordofthenewworld.com/)

This is supposed to be a very good MMO. My friend is in love with him. Last this thread left off, they were making very good progress running this game in WINE. It was an old thread, so it could be that WINE is better running it now.

[http://forum.swordofthenewworld.com/index.php?showtopic=3567&mode=threaded&pid=36629](http://forum.swordofthenewworld.com/index.php?showtopic=3567&mode=threaded&pid=36629)

Does anyone here have any suggestions to get the game running. Here's what I know you used to have to do:

> You can get past the problem with the patcher/starter by installing IEs4Linux: [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
(Make sure to install the Flash Player during installation as well)

And then launching the app with:
WINEPREFIX="/install/path/to/.ies4linux/ie6" wine ge.exe
Except '/install/path/to' should be where you've installed IEs4Linux (defaults to the home directory).

Note though that under these conditions Wine will be using the configuration set up by IEs4Linux, my advice would be to use it purely for the patcher, and then once it's patched up and you've configured, close the app and launch the actual game manually as followed:

Move into the 'release' directory in the main SNW directory, then use wine to launch the game with:
wine ge.exe -SERVICE -WINDOWMODE

You can of course drop -WINDOWMODE if you want to try it in fullscreen.
This will allow you to use your regular Wine configuration for the actual game.

This solution only solves the issues with the patcher however, for me even with the latest Wine the game still crashes as soon as I try to make a character.
Hence, for now, the only real solution seems to be to play the game on Windows.

Then, it came to this:

> It is actually a common problem, you get around that by installing the mozctrl mods of wine, you can details on that by googling or asking on your ditro's IRC.

that mod i think from memory contains the mozilla browser window, and its extensions, which include flash.

Also yes it Does work, I had it working on wine(0.95, since i my stupid repos wont connect.. i coundlt update, was using SuSE). I did try VMWare as well... but it didnt really work, came up with the error the game could not start audio driver or something along that line... I think its probably just me stuffing things up lol

EDIT:
Hmm the person above mentioned it crashed on character creation.. I managed to get to the quaters screen, but it was like.. cut off, as in only 1/4 of the screen was actually rendering, so yeah..

Then this:

> Well the 1/4 screen problem is you're forcing Anti-Aliasing through the video card options. You can either deactivate AA or open the config window in the patcher and deactivate Spreading Effect.

Finally this:

> I"ve tested it with the latest version of wine, install was ok thanks to Vividd's help and character creation went with no problems but I can't see the character models when playing, just the world, UI and character's shadows =/

That last quote was from June 28th, 2007, so it could be that WINE is now better suited to running it. Also, there could be patches applied to get this to work, however I'm still a novice with WINE now.

Any help for this?

---

### Post by hikaricore on 2007-08-22
Not sure if this is useful to you, but a recent rating on the AppDB still shows garbage level.

[http://appdb.winehq.org/appview.php?iVersionId=8718](http://appdb.winehq.org/appview.php?iVersionId=8718)

---

### Post by quadomatic on 2007-08-22
> **hikaricore said:**
> Not sure if this is useful to you, but a recent rating on the AppDB still shows garbage level.

[http://appdb.winehq.org/appview.php?iVersionId=8718](http://appdb.winehq.org/appview.php?iVersionId=8718)

That person wasn't able to get past the problem with launching flash player, but there's a fix for that in this thread. That page isn't being updated properly.

---

### Post by quadomatic on 2007-08-22
Apparently someone got it working under Cedega...there's got to be a way to run it under WINE

[http://forum.iahgames.com/ge/showthread.php?t=5339&highlight=linux](http://forum.iahgames.com/ge/showthread.php?t=5339&highlight=linux)

I suppose it's possible it may work under this newest version of WINE. I haven't seen any records of people saying it hasn't worked with the newest version of WINE. I'll be trying it tomorrow once the game finishes downloading (3.6 GB, yikes!)

---

### Post by hikaricore on 2007-08-23
> **quadomatic said:**
> That person wasn't able to get past the problem with launching flash player, but there's a fix for that in this thread. That page isn't being updated properly.

It's only updated by users like yourself.  Pitch in if you find it lacking.

---

### Post by quadomatic on 2007-08-23
I've successfully installed the game. I followed the fix in the OP. The game is now updating. Once it's finished, I'll try running it!

---

### Post by quadomatic on 2007-08-23
Okay, when I start it I get the error:

```
Client closing due to the sound driver error. Install or reinstall the sound driver. [errorCode: 3]
```

Can someone help with this? I think this means that WINE isn't using my sound hardware...

My audio device for ALSA is a NVidia CK804. My motherboard also has a realtek audio device that uses AC97.

Here's the output from the terminal after running the game:

```
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x199c48) : stub, simulating 64MB for now, returning 64MB left
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
```

---

### Post by jkeyes0 on 2007-08-24
> **quadomatic said:**
> Okay, when I start it I get the error:

```
Client closing due to the sound driver error. Install or reinstall the sound driver. [errorCode: 3]
```

Can someone help with this? I think this means that WINE isn't using my sound hardware...

My audio device for ALSA is a NVidia CK804. My motherboard also has a realtek audio device that uses AC97.

Here's the output from the terminal after running the game:

```
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x199c48) : stub, simulating 64MB for now, returning 64MB left
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
```

From reading the error messages there, it sounds like you need to open a terminal, and type "winecfg" then hit enter. That will open a wine configuration panel. From there, click the "Audio" tab, and where it says "Hardware Acceleration" down at the bottom, select "Emulation" from this list, then hit "OK"

---

### Post by cogadh on 2007-08-24
> **quadomatic said:**
> That person wasn't able to get past the problem with launching flash player, but there's a fix for that in this thread. That page isn't being updated properly.
If you do manage to get this game running, please take the time to record what you did and add it to the AppDB. The only way that page will get updated is if users like yourself add your experiences to it. It's great that you are sharing this experience here on the forums, but it would be better to share what you learn from this with the entire Wine community.

---

### Post by quadomatic on 2007-08-24
> **cogadh said:**
> If you do manage to get this game running, please take the time to record what you did and add it to the AppDB. The only way that page will get updated is if users like yourself add your experiences to it. It's great that you are sharing this experience here on the forums, but it would be better to share what you learn from this with the entire Wine community.

Thanks for the suggestion. I hadn't done it already because I couldn't figure out the current version number.

BTW: I did try and change the sound driver to ALSA and to emulation, but it didn't work. I'm not sure what's causing that. It could be that my sound card isn't properly configured in WINE. How would I go about doing that?

My motherboard has a Realtek ALC655 (AC97) and some Nvidia sound

ALSO, when I run winecfg, it says this in the terminal output (winecfg still runs of course):

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
```

---

### Post by cogadh on 2007-08-24
You can ignore the "fixme" messages from Wine, they are just developer messages and notes.

When you say you say you turned on emulation, did you check the driver emulation box or did you change the hardware acceleration setting to emulation?

---

### Post by quadomatic on 2007-08-24
> **cogadh said:**
> You can ignore the "fixme" messages from Wine, they are just developer messages and notes.

When you say you say you turned on emulation, did you check the driver emulation box or did you change the hardware acceleration setting to emulation?

I've tried both. Here's a list of settings I've tried, none of which have gotten around that error:

OSS+ALSA+Emulation+Driver Emulation
OSS+ALSA+Full+Driver Emulation
OSS+ALSA+Emulation
OSS+ALSA+Full

ALSA+Emulation+Driver Emulation
ALSA+Full+Driver Emulation
ALSA+Emulation
ALSA+Full

OSS+Emulation+Driver Emulation
OSS+Full+Driver Emulation
OSS+Emulation
OSS+Full

Is there any other ideas people have? I checked Sword of the New World forums, and they said that could mean your sound card is broken/not detected (in windows). This may mean my sound card isn't properly configured, but I had sounds in CS: Source.

BTW: I got Super Maintainer Status on AppDB, and added the new version, my data, and a guide on how to get the game running:

[http://appdb.winehq.org/appview.php?iVersionId=8996](http://appdb.winehq.org/appview.php?iVersionId=8996)

---

### Post by quadomatic on 2007-08-24
Any help please?

I'm going to try the newest version of WINE that was released today once Ubuntu package for it is released.

---

### Post by quadomatic on 2007-08-25
Bump for help!

---

### Post by cogadh on 2007-08-25
Try adding the registry key for direct hardware access to your sound hardware. Using that has fixed many sound problems for me, but they were mostly stuttering sound and buffer underrun problems. See Wine's [Useful Registry Keys]("http://wiki.winehq.org/UsefulRegistryKeys") page for details.

---

### Post by quadomatic on 2007-08-25
I just installed the newest version of WINE (0.9.44).

I no longer get the sound card error, and now X-Trap anti-cheat software appears to start up and load as it should. Afterwards, The game crashes, and I get the following in the terminal

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:hook:IsWinEventHookInstalled (32773)-stub!
aneesh@aneesh-desktop:~/.wine/drive_c/Program Files/Sword of The New World$ fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x34f20c,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x134e50) : stub, simulating 64MB for now, returning 64MB left
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x34f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x8090809, 0x34f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x4070407, 0x34f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x4070407, 0x34f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x4070407, 0x34f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x4070407, 0x34f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x8070807, 0x34f63c, 260): stub
fixme:imm:ImmGetOpenStatus (0x124358): semi-stub
fixme:imm:ImmReleaseContext (0x20036, 0x124358): stub
fixme:vxd:VXD_Open Unknown/unsupported VxD L"sice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"ntice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"siwvid.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"sice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"ntice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"siwvid.vxd". Try setting Windows version to 'nt40' or 'win31'.
wine: Unhandled page fault on read access to 0x44ce7769 at address 0x40412f6e (thread 0013), starting debugger...
WineDbg starting on pid 0012
Unhandled exception: page fault on read access to 0x44ce7769 in 32-bit code (0x40412f6e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:40412f6e ESP:0034dcc8 EBP:065e7768 EFLAGS:00010212(   - 00      - RIA1)
 EAX:069ed1b5 EBX:065e7768 ECX:00005a4d EDX:3e700000
 ESI:065e7768 EDI:065e7768
Stack dump:
0x0034dcc8:  ffffffff 40430a19 000000a0 00000001
0x0034dcd8:  00000002 00000000 00000060 000000a0
0x0034dce8:  4041800a 0034e0b0 0034dd7c 00000015
0x0034dcf8:  40430a08 00000010 0034dfac 0000000d
0x0034dd08:  40430a08 00000010 0034e0b0 0000000d
0x0034dd18:  40430a08 00000010 404345dc 007c1d28
Backtrace:
=>1 0x40412f6e in xtrapva (+0x12f6e) (0x065e7768)
  2 0x00000001 (0x00405a4d)
  3 0x8b000a9a (0x1ce80000)
  4 0x00000000 (0x00000000)
0x40412f6e: movl        0x1(%edx,%esi,1),%ecx
Wine-dbg>

```

I haven't a clue what this means...The last line lets me enter something in.

Any help?

Right now I've deleted my .wine folder, ran winecfg again, and am in the process of reinstalling the game. I'll see what happens. If I still get the same issue, I'll add it to AppDB.

I guess it could be that this version of WINE had something changed that would cause this...but whatever else they changed also fixed my sound error!

---

### Post by quadomatic on 2007-08-25
I've added the information to AppDB

[http://appdb.winehq.org/appview.php?iVersionId=8996](http://appdb.winehq.org/appview.php?iVersionId=8996)

---

### Post by quadomatic on 2007-08-25
I just submitted a bug to Bugzilla with the wine terminal output.

Hopefully it will get fixed in the next release, though I find that unlikely. Maybe it will be fixed indirectly.

---

### Post by Jorenko on 2007-08-25
I am also interested in getting this working now that's it's totally free to play. Using the ies4linux workaround for the patcher, I too have gotten to the point of running the game, but having it crash right away. It looks like a page fault is happening. Here's the output...

```

fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 300, std (d/m/y): 4/11/2007, dlt (d/m/y): 11/03/2007
fixme:win:EnumDisplayDevicesW ((null),0,0x33f20c,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x13b928) : stub, simulating 64MB for now, returning 64MB left
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x33f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x8090809, 0x33f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x4070407, 0x33f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x4070407, 0x33f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x4070407, 0x33f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x4070407, 0x33f63c, 260): stub
fixme:imm:ImmGetIMEFileNameA (0x8070807, 0x33f63c, 260): stub
fixme:imm:ImmGetOpenStatus (0x124380): semi-stub
fixme:imm:ImmReleaseContext (0x30026, 0x124380): stub
wine: Unhandled page fault on read access to 0x0de278ec at address 0x40412f6a (thread 0009), starting debugger...
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 300, std (d/m/y): 4/11/2007, dlt (d/m/y): 11/03/2007
Unhandled exception: page fault on read access to 0x0de278ec in 32-bit code (0x40412f6a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:40412f6a ESP:0033dcc8 EBP:0de10fb8 EFLAGS:00210216(   - 00      -RIAP1)
 EAX:0e216a05 EBX:0de10fb8 ECX:00005a4d EDX:00000060
 ESI:0de10fb8 EDI:0de10fb8
Stack dump:
0x0033dcc8:  ffffffff 40430a19 000000a0 00000006
0x0033dcd8:  00000002 00000000 00000060 000000a0
0x0033dce8:  4041800a 0033e0b0 0033dd7c 00000015
0x0033dcf8:  40430a08 00000010 0033dfac 0000000d
0x0033dd08:  40430a08 00000010 0033e0b0 0000000d
0x0033dd18:  40430a08 00000010 404345dc 007c1d28
Backtrace:
=>1 0x40412f6a in xtrapva (+0x12f6a) (0x0de10fb8)
  2 0x00000001 (0x00405a4d)
  3 0x8b000a9a (0x1ce80000)
  4 0x00000000 (0x00000000)
0x40412f6a: movl	0x0(%ebp,%ecx,4),%edx
Modules:
Module	Address			Debug info	Name (127 modules)
PE	  340000-  37d000	Deferred        speedtreert
PE	  3e0000-  3ff000	Deferred        gelanguage_eng.lng
PE	  400000-  c91000	Deferred        ge
PE	  ca0000-  eef000	Deferred        d3dx9_27
PE	 7760000- 7827000	Deferred        pathengine
PE	10000000-10096000	Deferred        fmod
PE	40400000-4083e000	Export          xtrapva
PE	75fd0000-76031000	Deferred        msvcp60
ELF	7938c000-793ea000	Deferred        setupapi<elf>
  \-PE	793a0000-793ea000	\               setupapi
ELF	793ea000-7940f000	Deferred        netapi32<elf>
  \-PE	793f0000-7940f000	\               netapi32
ELF	79731000-7978b000	Deferred        crypt32<elf>
  \-PE	79740000-7978b000	\               crypt32
ELF	79bcf000-79be7000	Deferred        usp10<elf>
  \-PE	79be0000-79be7000	\               usp10
ELF	7b800000-7b929000	Deferred        kernel32<elf>
  \-PE	7b820000-7b929000	\               kernel32
ELF	7bbb7000-7bc00000	Deferred        dsound<elf>
  \-PE	7bbc0000-7bc00000	\               dsound
ELF	7bc00000-7bca0000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca0000	\               ntdll
ELF	7bcb3000-7bcde000	Deferred        d3d8<elf>
  \-PE	7bcc0000-7bcde000	\               d3d8
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7bf06000-7bf3b000	Deferred        rsaenh<elf>
  \-PE	7bf10000-7bf3b000	\               rsaenh
ELF	7bf3b000-7c000000	Deferred        libasound.so.2
ELF	7c25b000-7c272000	Deferred        cfgmgr32<elf>
  \-PE	7c260000-7c272000	\               cfgmgr32
ELF	7c272000-7c278000	Deferred        libnss_dns.so.2
ELF	7c278000-7c28c000	Deferred        winhttp<elf>
  \-PE	7c280000-7c28c000	\               winhttp
ELF	7c297000-7c2ac000	Deferred        midimap<elf>
  \-PE	7c2a0000-7c2ac000	\               midimap
ELF	7c2ac000-7c2c4000	Deferred        msacm32<elf>
  \-PE	7c2b0000-7c2c4000	\               msacm32
ELF	7c2c4000-7c2f9000	Deferred        winealsa<elf>
  \-PE	7c2d0000-7c2f9000	\               winealsa
ELF	7d1c8000-7d1fa000	Deferred        uxtheme<elf>
  \-PE	7d1d0000-7d1fa000	\               uxtheme
ELF	7d1fa000-7d1ff000	Deferred        libxfixes.so.3
ELF	7d1ff000-7d208000	Deferred        libxcursor.so.1
ELF	7d208000-7d210000	Deferred        libxrender.so.1
ELF	7d84b000-7d84d000	Deferred        libnvidia-tls.so.1
ELF	7d84d000-7df9e000	Deferred        libglcore.so.1
ELF	7df9e000-7e017000	Deferred        libgl.so.1
ELF	7e017000-7e01c000	Deferred        libxdmcp.so.6
ELF	7e01c000-7e01f000	Deferred        libxau.so.6
ELF	7e01f000-7e110000	Deferred        libx11.so.6
ELF	7e110000-7e11e000	Deferred        libxext.so.6
ELF	7e11e000-7e123000	Deferred        libxxf86vm.so.1
ELF	7e123000-7e13b000	Deferred        libice.so.6
ELF	7e13b000-7e144000	Deferred        libsm.so.6
ELF	7e144000-7e14a000	Deferred        libxrandr.so.2
ELF	7e158000-7e1e2000	Deferred        winex11<elf>
  \-PE	7e170000-7e1e2000	\               winex11
ELF	7e269000-7e289000	Deferred        libexpat.so.1
ELF	7e289000-7e2b4000	Deferred        libfontconfig.so.1
ELF	7e2b4000-7e2c8000	Deferred        libz.so.1
ELF	7e2c8000-7e333000	Deferred        libfreetype.so.6
ELF	7e347000-7e364000	Deferred        imm32<elf>
  \-PE	7e350000-7e364000	\               imm32
ELF	7e364000-7e402000	Deferred        oleaut32<elf>
  \-PE	7e380000-7e402000	\               oleaut32
ELF	7e402000-7e417000	Deferred        psapi<elf>
  \-PE	7e410000-7e417000	\               psapi
ELF	7e417000-7e461000	Deferred        dbghelp<elf>
  \-PE	7e420000-7e461000	\               dbghelp
ELF	7e461000-7e536000	Deferred        wined3d<elf>
  \-PE	7e470000-7e536000	\               wined3d
ELF	7e536000-7e565000	Deferred        d3d9<elf>
  \-PE	7e540000-7e565000	\               d3d9
ELF	7e565000-7e57f000	Deferred        version<elf>
  \-PE	7e570000-7e57f000	\               version
ELF	7e57f000-7e5b5000	Deferred        dinput<elf>
  \-PE	7e590000-7e5b5000	\               dinput
ELF	7e5b5000-7e5ce000	Deferred        dinput8<elf>
  \-PE	7e5c0000-7e5ce000	\               dinput8
ELF	7e5ce000-7e5fb000	Deferred        ws2_32<elf>
  \-PE	7e5e0000-7e5fb000	\               ws2_32
ELF	7e5fb000-7e615000	Deferred        wsock32<elf>
  \-PE	7e600000-7e615000	\               wsock32
ELF	7e615000-7e67c000	Deferred        msvcrt<elf>
  \-PE	7e630000-7e67c000	\               msvcrt
ELF	7e67c000-7e70a000	Deferred        winmm<elf>
  \-PE	7e690000-7e70a000	\               winmm
ELF	7e70a000-7e730000	Deferred        msacm32<elf>
  \-PE	7e710000-7e730000	\               msacm32
ELF	7e730000-7e743000	Deferred        libresolv.so.2
ELF	7e743000-7e761000	Deferred        iphlpapi<elf>
  \-PE	7e750000-7e761000	\               iphlpapi
ELF	7e761000-7e7ba000	Deferred        rpcrt4<elf>
  \-PE	7e770000-7e7ba000	\               rpcrt4
ELF	7e7ba000-7e859000	Deferred        ole32<elf>
  \-PE	7e7d0000-7e859000	\               ole32
ELF	7e859000-7e894000	Deferred        urlmon<elf>
  \-PE	7e860000-7e894000	\               urlmon
ELF	7e894000-7e8b4000	Deferred        mpr<elf>
  \-PE	7e8a0000-7e8b4000	\               mpr
ELF	7e8b4000-7e8fe000	Deferred        wininet<elf>
  \-PE	7e8c0000-7e8fe000	\               wininet
ELF	7e8fe000-7e9bc000	Deferred        comctl32<elf>
  \-PE	7e910000-7e9bc000	\               comctl32
ELF	7e9bc000-7ea15000	Deferred        shlwapi<elf>
  \-PE	7e9d0000-7ea15000	\               shlwapi
ELF	7ea15000-7eb18000	Deferred        shell32<elf>
  \-PE	7ea30000-7eb18000	\               shell32
ELF	7eb18000-7eb60000	Deferred        advapi32<elf>
  \-PE	7eb20000-7eb60000	\               advapi32
ELF	7eb60000-7eb6c000	Deferred        libgcc_s.so.1
ELF	7ec56000-7ec6a000	Deferred        lz32<elf>
  \-PE	7ec60000-7ec6a000	\               lz32
ELF	7ec6a000-7ed2a000	Deferred        gdi32<elf>
  \-PE	7ec80000-7ed2a000	\               gdi32
ELF	7ed2a000-7ee68000	Deferred        user32<elf>
  \-PE	7ed50000-7ee68000	\               user32
ELF	7ef99000-7efa4000	Deferred        libnss_files.so.2
ELF	7efa4000-7efae000	Deferred        libnss_nis.so.2
ELF	7efae000-7efc5000	Deferred        libnsl.so.1
ELF	7efc5000-7efec000	Deferred        libm.so.6
ELF	b7c86000-b7c8f000	Deferred        libnss_compat.so.2
ELF	b7c90000-b7c94000	Deferred        libdl.so.2
ELF	b7c94000-b7dd5000	Deferred        libc.so.6
ELF	b7dd5000-b7dec000	Deferred        libpthread.so.0
ELF	b7e00000-b7f14000	Deferred        libwine.so.1
ELF	b7f16000-b7f31000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000016 
	00000017    0
0000000a 
	0000000c    0
	0000000b    0
00000008 (D) C:\Program Files\Sword of The New World\release\ge.exe
	00000019    0
	00000018    0
	00000015    0
	00000014    0
	00000013    0
	00000012    2
	00000011   15
	00000010    0
	0000000f   15
	0000000e    0
	0000000d    0
	00000009    0 <==

```

I suppose at this stage I should just submit a bug to wine and sit back and hope it gets fixed, eh?

Edit: Upon closer inspection, this is a very similar instruction exploding as quadomatic is having. Fun! Well, at least it's fairly consistent...

Further edit: I found your bug report, quadomatic. I've added my output there as well.

---

### Post by Karmal on 2007-08-25
[http://forum.swordofthenewworld.com/index.php?showtopic=7558](http://forum.swordofthenewworld.com/index.php?showtopic=7558)

> 
I went a little extreme here and copied over the entire windows/system32 folder from my housemate's computer into Wine's system32 folder. This solved the problem and allowed the game to advance as far as the login screen. (I will see about going back later and isolating which DLLs are actually needed)


though the person ran into an issue at the login screen later that crashed it. X-Trap, the anti-cheating software that comes packaged with SotNW, is apparently the culprit.

---

### Post by quadomatic on 2007-08-25
> **Karmal said:**
> [http://forum.swordofthenewworld.com/index.php?showtopic=7558](http://forum.swordofthenewworld.com/index.php?showtopic=7558)



though the person ran into an issue at the login screen later that crashed it. X-Trap, the anti-cheating software that comes packaged with SotNW, is apparently the culprit.

I'm not positive about that...Anyhow I hope a developer will look at this bug and fix it. I mentioned X-Trap. I'm assuming they'll probably download the game, run it, and see if they get the bug. If they do, they'll confirm it (I think). If they don't, they'll tell us what they did to get around the problem (I hope).

---

### Post by Ferrat on 2007-08-25
just fast read the thread and see you get a read error, have you tried emulating other win versions? NT? 98? ME? 

I know that was a problem sometimes when playing WoW, specially when updating ect. sometimes it helps to switch

---

### Post by quadomatic on 2007-08-25
WOAH

I got some crazy strange error. Check the bugzilla entry:

[http://bugs.winehq.org/show_bug.cgi?id=9455](http://bugs.winehq.org/show_bug.cgi?id=9455)

---

### Post by Jorenko on 2007-08-26
Well, the copying system32 contents hack got me the same results as that guy claimed; I get to the login scree, but then x-trap pops up the error about running in compatible mode. Selecting different windows versions in winecfg doesn't seem to have any effect.

Edit: AHA! As Jesse on Bugzilla predicted, it's the goddamned copy protection. I got the exact same 'fixme:vxd:VXD_Open Unknown/unsupported VxD L"sice.vxd".' messages that are indicative of the problem he described, now that I have the DLL to fix the crashing problem.

When will companies learn that this stuff only messes up legitimate usage? The pirates always have a way to get around it anyway. Oh well, it looks like there is a fix for this problem that is on its way to being included in wine soon...ish. Looking in that [bug report](http://bugs.winehq.org/show_bug.cgi?id=219), it's actually a six year old bug that's just now getting its fix included in releases. Sheesh!

Edit: Looks like the only possibility for a short term fix is probably a crack to get around xcopy... which is pointless for even normal crackers because there's no need for it on a free game. Why the hell would they even include copy protection on a free game anyway? Sigh.

---

### Post by quadomatic on 2007-08-26
> **Jorenko said:**
> Well, the copying system32 contents hack got me the same results as that guy claimed; I get to the login scree, but then x-trap pops up the error about running in compatible mode. Selecting different windows versions in winecfg doesn't seem to have any effect.

Edit: AHA! As Jesse on Bugzilla predicted, it's the goddamned copy protection. I got the exact same 'fixme:vxd:VXD_Open Unknown/unsupported VxD L"sice.vxd".' messages that are indicative of the problem he described, now that I have the DLL to fix the crashing problem.

When will companies learn that this stuff only messes up legitimate usage? The pirates always have a way to get around it anyway. Oh well, it looks like there is a fix for this problem that is on its way to being included in wine soon...ish. Looking in that [bug report](http://bugs.winehq.org/show_bug.cgi?id=219), it's actually a six year old bug that's just now getting its fix included in releases. Sheesh!

Edit: Looks like the only possibility for a short term fix is probably a crack to get around xcopy... which is pointless for even normal crackers because there's no need for it on a free game. Why the hell would they even include copy protection on a free game anyway? Sigh.

I guess the "crack" would get rid of X-Copy anti-cheat software...which proly would get u banned

I'm starting to wonder why I even bother with this game...or any WINE game for that matter. ATI driver support doesn't have GLSlang support. Hopefully this would run anyways.

I'm hoping to get an nVidia Video Card in 2 weeks.

---

### Post by Joedude on 2007-11-11
So, does it work or not?

---

### Post by Ferrat on 2007-11-11
> **Joedude said:**
> So, does it work or not?

As I understand it no but latest post in this thread was August 25th, wine has jumped leaps from that so I accutally got curious myself and decided to download it and give it a try.

---

### Post by MasterXXL on 2007-12-14
So, works or not?
I'm asking, because the last post is 4 weeks old

---

### Post by quadomatic on 2007-12-15
No it doesn't work. From what I can tell, the issue that has to be resolved for this game to work, and for a lot of MMORPGs to work, as they all use anti-cheat software like Sword of the New World does, may take a very long time to fix.

---

### Post by Person_1873 on 2008-01-14
far out, those pplz over at wineHQ really need to work on all these anit-hacking type programs, its the main thing thats been stopping me from playing nie on all MMORPG's, Swords looks awsm but if wine don't support it, there's no point

---

### Post by kazuya on 2008-03-19
hello, i was in your predicament sometime back, the issue is the rootkit that is attached with those things such as gameguard.

---

### Post by rhanex on 2008-08-01
I have this games in my external HD so i just copy all files and put in one location in my hardy. However right after i x2-click the ge.exe an error window will appear telling me that "Fail to create Flash Player. Please restart program (62)".

So i follow this
> You can get past the problem with the patcher/starter by installing IEs4Linux: [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
(Make sure to install the Flash Player during installation as well)

And then launching the app with:
WINEPREFIX="/install/path/to/.ies4linux/ie6" wine ge.exe
Except '/install/path/to' should be where you've installed IEs4Linux (defaults to the home directory).

Note though that under these conditions Wine will be using the configuration set up by IEs4Linux, my advice would be to use it purely for the patcher, and then once it's patched up and you've configured, close the app and launch the actual game manually as followed:

Move into the 'release' directory in the main SNW directory, then use wine to launch the game with:
wine ge.exe -SERVICE -WINDOWMODE

You can of course drop -WINDOWMODE if you want to try it in fullscreen.
This will allow you to use your regular Wine configuration for the actual game.

This solution only solves the issues with the patcher however, for me even with the latest Wine the game still crashes as soon as I try to make a character.
Hence, for now, the only real solution seems to be to play the game on Windows. 

but every time i put this code
WINEPREFIX="/install/path/to/.ies4linux/ie6" wine ge.exe
im getting something like this 
```
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
wine: could not load L"C:\\windows\\system32\\ge.exe": Module not found
```

so im stock on this part.
hehe noob here :-P:-P

---

### Post by captaincrackers on 2010-07-09
So, has this thing been resolved at all? I have the most recent version of wine, I just got Ubuntu about a month ago, and wine about 2 weeks ago.

---

### Post by Forma on 2010-11-28
I am sorry to bump this thread thats over a year old, but im curious about how things are going, is there a way to get sotnw to actually work on linux yet?

---

### Post by cogadh on 2010-11-29
As long as the game still uses anti-cheat software, it most likely will never work in Wine. Most anti-cheat programs operate as a Windows device driver or in a similar fashion to a rootkit. Neither of those types of programs are ever going to work in Wine because of the kernel mode access they require (Wine only runs in user mode). So, until the publisher stops using that software or creates a Linux-native client, you won't be able to play it on your Linux machine.

---

### Post by Forma on 2010-11-29
Oh i see... that clears things up.
hopefully theyll create a client for linux, since its highly unlikely that they will change the anti-cheat program.
i guess a bypass would work but wouldnt want to risk that!

Thanks for the fast reply.

---

