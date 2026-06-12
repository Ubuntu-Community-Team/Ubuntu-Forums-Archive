---
title: "Star Wars: Knights of the Old Republic WINE Help"
date: 2007-08-25
forum: Wine
---

### Post by quadomatic on 2007-08-25
Using WINE 0.9.44, I was able to install Star Wars: Knights of the Old Republic, and patch the game with the latest 1.03 patch. I had to use a no-cd exe after patching the game, because of a SecuROM error. 

I disabled movies and turned off hardware mouse, and am running it on the WINE virtual desktop.

I'm able to get through character creation, but once the actual gameplay finishes loading, the game crashes. Also, if I try to change graphics options, like turn on anisiotropic filtering, or soft shadows, the game crashes as well.

Here's the terminal output after starting the game exe and the game loading after character creation:

```
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
err:wgl:X11DRV_wglGetProcAddress (wglAllocateMemoryNV) - not found
err:wgl:X11DRV_wglGetProcAddress (wglFreeMemoryNV) - not found
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreateBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDeleteBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSaveBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglRestoreBufferRegionARB) - not found
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:X11DRV_wglCreatePbufferARB (0x1e4): unexpected iPixelFormat(2129148288) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:X11DRV_wglCreatePbufferARB (0x1e4): unexpected iPixelFormat(3399732) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:X11DRV_wglCreatePbufferARB (0x1e4): unexpected iPixelFormat(3399732) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:X11DRV_wglCreatePbufferARB (0x1e4): unexpected iPixelFormat(3399732) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:X11DRV_wglCreatePbufferARB (0x1e4): unexpected iPixelFormat(3399732) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:X11DRV_wglCreatePbufferARB (0x1e4): unexpected iPixelFormat(3399732) > nFormats(1), returns NULL
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:X11DRV_wglCreatePbufferARB (0x1e4): unexpected iPixelFormat(3399732) > nFormats(1), returns NULL
:: Server player list ::
ServerAdmins: 1
Bad StrRef [ServerAdmin]
Players: 1
Bad StrRef [Player]
Total: 2
:: Server mode: Module Loaded.
:: Server mode: Module Running.
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0033fb70 EBP:7ee6b2b0 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000000 EBX:7ee68230 ECX:00131b40 EDX:00131b40
 ESI:000001e4 EDI:7ee6aa20
Stack dump:
0x0033fb70:  0042c748 00000000 00000000 00131b40
0x0033fb80:  7ee6aca0 7ee6b1d0 7ee6b2b0 7ee68230
0x0033fb90:  7ee67027 00000de1 7ee68230 7ee6b1d0
0x0033fba0:  7ee6aca0 7ee66fd9 00131b40 00435e88
0x0033fbb0:  00000002 7ee6b1d0 0306c850 7ee67d90
0x0033fbc0:  012be23b 0045196d 0000001f 7ee6b2b0
Backtrace:
=>1 0x00000000 (0x7ee6b2b0)
  2 0x5d8928ec (0x83e58955)
  3 0x00000000 (0x00000000)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (86 modules)
PE        340000-  36c000       Deferred        msseax.m3d
PE        400000-  86d000       Deferred        swkotor
PE      21100000-21164000       Deferred        mss32
PE      22300000-2231b000       Deferred        mssds3d.m3d
PE      22400000-22419000       Deferred        msssoft.m3d
PE      24100000-24120000       Deferred        mssdsp.flt
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2c000       Deferred        mssmp3.asi
PE      30000000-30072000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c455000-7c49e000       Deferred        dsound<elf>
  \-PE  7c460000-7c49e000       \               dsound
ELF     7c74a000-7c75f000       Deferred        midimap<elf>
  \-PE  7c750000-7c75f000       \               midimap
ELF     7c75f000-7c785000       Deferred        msacm32<elf>
  \-PE  7c770000-7c785000       \               msacm32
ELF     7c785000-7c79d000       Deferred        msacm32<elf>
  \-PE  7c790000-7c79d000       \               msacm32
ELF     7c79d000-7c862000       Deferred        libasound.so.2
ELF     7c862000-7c897000       Deferred        winealsa<elf>
  \-PE  7c870000-7c897000       \               winealsa
ELF     7c897000-7c8a0000       Deferred        libxcursor.so.1
ELF     7d00c000-7d012000       Deferred        libxrandr.so.2
ELF     7d110000-7d115000       Deferred        libxfixes.so.3
ELF     7d9f5000-7d9fe000       Deferred        librt.so.1
ELF     7dab8000-7dac0000       Deferred        libxrender.so.1
ELF     7daca000-7e437000       Deferred        fglrx_dri.so
ELF     7e437000-7e4c1000       Deferred        winex11<elf>
  \-PE  7e450000-7e4c1000       \               winex11
ELF     7e548000-7e568000       Deferred        libexpat.so.1
ELF     7e568000-7e593000       Deferred        libfontconfig.so.1
ELF     7e593000-7e5a7000       Deferred        libz.so.1
ELF     7e5a7000-7e612000       Deferred        libfreetype.so.6
ELF     7e612000-7e62f000       Deferred        imm32<elf>
  \-PE  7e620000-7e62f000       \               imm32
ELF     7e62f000-7e643000       Deferred        lz32<elf>
  \-PE  7e640000-7e643000       \               lz32
ELF     7e643000-7e65d000       Deferred        version<elf>
  \-PE  7e650000-7e65d000       \               version
ELF     7e65d000-7e673000       Deferred        glu32<elf>
  \-PE  7e660000-7e673000       \               glu32
ELF     7e673000-7e6a9000       Deferred        dinput<elf>
  \-PE  7e680000-7e6a9000       \               dinput
ELF     7e6a9000-7e6c2000       Deferred        dinput8<elf>
  \-PE  7e6b0000-7e6c2000       \               dinput8
ELF     7e6c2000-7e750000       Deferred        winmm<elf>
  \-PE  7e6d0000-7e750000       \               winmm
ELF     7e750000-7e763000       Deferred        libresolv.so.2
ELF     7e763000-7e781000       Deferred        iphlpapi<elf>
  \-PE  7e770000-7e781000       \               iphlpapi
ELF     7e781000-7e7da000       Deferred        rpcrt4<elf>
  \-PE  7e790000-7e7da000       \               rpcrt4
ELF     7e7da000-7e879000       Deferred        ole32<elf>
  \-PE  7e7f0000-7e879000       \               ole32
ELF     7e879000-7e8c1000       Deferred        advapi32<elf>
  \-PE  7e890000-7e8c1000       \               advapi32
ELF     7e8c1000-7e981000       Deferred        gdi32<elf>
  \-PE  7e8e0000-7e981000       \               gdi32
ELF     7e981000-7eabf000       Deferred        user32<elf>
  \-PE  7e9a0000-7eabf000       \               user32
ELF     7eabf000-7eacb000       Deferred        libgcc_s.so.1
ELF     7ebb5000-7ebba000       Deferred        libxdmcp.so.6
ELF     7ebba000-7ec3a000       Deferred        libglu.so.1
ELF     7ec3a000-7ecda000       Deferred        libgl.so.1
ELF     7ecda000-7edcb000       Deferred        libx11.so.6
ELF     7edcb000-7edd9000       Deferred        libxext.so.6
ELF     7edd9000-7edde000       Deferred        libxxf86vm.so.1
ELF     7edde000-7edf6000       Deferred        libice.so.6
ELF     7ee08000-7ee89000       Deferred        opengl32<elf>
  \-PE  7ee20000-7ee89000       \               opengl32
ELF     7ef9b000-7efa6000       Deferred        libnss_files.so.2
ELF     7efa6000-7efb0000       Deferred        libnss_nis.so.2
ELF     7efb0000-7efc7000       Deferred        libnsl.so.1
ELF     7efc7000-7efee000       Deferred        libm.so.6
ELF     7efee000-7eff7000       Deferred        libsm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cd0000-b7cd3000       Deferred        libxau.so.6
ELF     b7cd4000-b7cd8000       Deferred        libdl.so.2
ELF     b7cd8000-b7e19000       Deferred        libc.so.6
ELF     b7e1a000-b7e31000       Deferred        libpthread.so.0
ELF     b7e43000-b7f57000       Deferred        libwine.so.1
ELF     b7f59000-b7f74000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\LucasArts\SWKotOR\swkotor.exe
        00000013    0
        00000012    0
        00000011    0
        00000010   15
        0000000f   15
        0000000e    0
        0000000d   -2
        00000009    0 <==
```

Any help?

---

### Post by cogadh on 2007-08-25
Now you're talking my language! KotOR is the first game I tried with Wine and got to run successfully. Here is my Wine setup:

*Applications tab-*
Windows version: XP

*Libraries tab*
d3dx9_24.dll through d3dx9_33.dll plus d3dX10_33.dll overridden with native libraries

*Graphics tab*
"Allow DirectX apps to stop the mouse..." checked
"Allow the window manager..." checked
"Emulate a virtual desktop" unchecked
Vertex shader set to Hardware
"Allow Pixel Shader..." checked

*Audio tab*
ALSA selected
Hardware Acceleration: Full
Default sample: 48000
Bits per sample: 16
Driver emulation: checked

*Registry edits*
ALSA - UseDirectHW
Direct3D - Direct draw renderer set to OpenGL, Use GLSL enabled, video memory size set to 256 (true memory for vid card)

*Game settings*
Disable hardware mouse
1024x768 resolution

I use a launch script to launch the game in a separate X Session, but it is not really necessary to do that, the game works fine without it. Certain advanced settings will not work (Frame buffer effects, soft shadows, antialiasing, anisotropic filtering), but I set the AA and Anisotropy at the video card using the Nvidia configuration tool. Since you have an ATI card, you may not be able to use those features at all. This game did already had problems with ATI hardware in Windows.

BTW - Do you already have the ATI binary driver installed?

---

### Post by quadomatic on 2007-08-25
> **cogadh said:**
> Now you're talking my language! KotOR is the first game I tried with Wine and got to run successfully. Here is my Wine setup:

*Applications tab-*
Windows version: XP

*Libraries tab*
d3dx9_24.dll through d3dx9_33.dll plus d3dX10_33.dll overridden with native libraries

*Graphics tab*
"Allow DirectX apps to stop the mouse..." checked
"Allow the window manager..." checked
"Emulate a virtual desktop" unchecked
Vertex shader set to Hardware
"Allow Pixel Shader..." checked

*Audio tab*
ALSA selected
Hardware Acceleration: Full
Default sample: 48000
Bits per sample: 16
Driver emulation: checked

*Registry edits*
ALSA - UseDirectHW
Direct3D - Direct draw renderer set to OpenGL, Use GLSL enabled, video memory size set to 256 (true memory for vid card)

*Game settings*
Disable hardware mouse
1024x768 resolution

I use a launch script to launch the game in a separate X Session, but it is not really necessary to do that, the game works fine without it. Certain advanced settings will not work (Frame buffer effects, soft shadows, antialiasing, anisotropic filtering), but I set the AA and Anisotropy at the video card using the Nvidia configuration tool. Since you have an ATI card, you may not be able to use those features at all. This game did already had problems with ATI hardware in Windows.

BTW - Do you already have the ATI binary driver installed?

Alright, I followed all of those settings EXCEPT the libraries tab settings and setting it to no virtual desktop. I don't have those items listed in the drop down menu under the libraries tab. I'm dual booting windows, but I wanted to run games in linux...should I look in my Windows's windows32 directories and grab dlls or something?

BTW: I had already submitted a bug to WINE Bugzilla about this before I saw this post.

---

### Post by cogadh on 2007-08-25
I don't think they are actually required for this game, I just made them part of my default Wine configuration a while back and they've never caused a problem, so I leave them be. They might help, they might not, I'm not really sure. According to the Wine documentation, they say those DLL files are the only DirectX files that might help with Wine, but they don't explain exactly how they help.

To add them, I manually created entries on the Library tab. Just copy them from your Windows partition to Wine's system32 directory, type in the names in the "New override..." field, then click Add. 

I don't know if you saw my last edit, asking if you have the ATI binary driver installed. I ask because a few of those errors appear to be saying that you don't have full hardware support or acceleration for 3D applications.

---

### Post by quadomatic on 2007-08-25
> **cogadh said:**
> I don't think they are actually required for this game, I just made them part of my default Wine configuration a while back and they've never caused a problem, so I leave them be. They might help, they might not, I'm not really sure. According to the Wine documentation, they say those DLL files are the only DirectX files that might help with Wine, but they don't explain exactly how they help.

To add them, I manually created entries on the Library tab. Just copy them from your Windows partition to Wine's system32 directory, type in the names in the "New override..." field, then click Add. 

I don't know if you saw my last edit, asking if you have the ATI binary driver installed. I ask because a few of those errors appear to be saying that you don't have full hardware support or acceleration for 3D applications.

I tried without adding those dlls, as I didn't know what to do, and had the same problem after character creation. I didn't try changing graphics settings.

I'll try adding those dlls and see what happens.

And, yes, I do have the ATI Binary Driver installed. It's definitely working properly, since I'm able to play Unreal Tournament 2004 with no problems, but that's running natively.

---

### Post by quadomatic on 2007-08-25
Alright, I've followed those settings as best as I can, and it STILL doesn't work.

Are you using the latest version of WINE?

I suppose it's possible that this could be a regression, though I've never tried KOTOR with any other version of WINE.

---

### Post by cogadh on 2007-08-25
Currently using Wine 0.9.44, but it has been working at least since 0.9.35. I just checked again and it still works. You might try using a launch script like I did to run the game, I do find that most games work better when run in a separate X session.

---

### Post by quadomatic on 2007-08-25
> **cogadh said:**
> Currently using Wine 0.9.44, but it has been working at least since 0.9.35. I just checked again and it still works. You might try using a launch script like I did to run the game, I do find that most games work better when run in a separate X session.

Could you give me a launch script?

I went ahead and submitted my application data to AppDB, since no one has since 0.9.41

---

### Post by cogadh on 2007-08-25
Here you go:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/LucasArts/SWKotOR/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all nice -15 wine "C:/Program Files/LucasArts/SWKotOR/launcher.exe"
```

It might be a while before your submitted data is added, I've had a pending submission for a while now, but it was a 0.9.41 test that contradicted the existing test data.

---

### Post by quadomatic on 2007-08-25
> **cogadh said:**
> 
It might be a while before your submitted data is added, I've had a pending submission for a while now, but it was a 0.9.41 test that contradicted the existing test data.

I guess that Super-Maintainer doesn't log in very often...

Are you Super-Maintainer for any applications?

---

### Post by quadomatic on 2007-08-25
I guess I probably set up the script wrong...Here's how it is right now. It's named kotor.sh

```
#!/bin/sh
#uncomment if launching from console session
sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac

# Goto game dir (modify as needed)
cd "/home/aneesh/.wine/drive_c/Program Files/LucasArts/SWKotOR/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all nice -15 wine "C:/Program Files/LucasArts/SWKotOR/launcher.exe"
```

I used "chmod +x kotor.sh", and then used "./kotor.sh". GDM stopped, or my X session stopped. All I know is I went to a text based screen, like if you watched your computer boot into linux under verbose mode.

Then it just stopped and didn't do anything for about a 30 seconds or a minute, so I restarted my computer. 

What should I have it set up to?

---

### Post by cogadh on 2007-08-25
> **quadomatic said:**
> I guess that Super-Maintainer doesn't log in very often...

Are you Super-Maintainer for any applications?
Nope, I just provide test data at the moment. I've currently got pending results for, KotOR, KotOR 2, Freelancer and Titanic: Adventure out of Time. I regularly test those games as well as Freedom Force, Star Trek: Armada 1 and 2, Vampire: Redemption, Vampire: Bloodlines, Hitman 2, Hitman: Contracts, Advent Rising, GTA 3, GTA Vice City, Tron 2.0, Call of Duty and Call of Duty: United Offensive. Of course I also test any new games as I get them.

EDIT -  Just saw your other post (must have been typing at the same time as me). Don't uncomment that first line unless you plan to do a CTRL-ALT-F1 to get to the console before launching the script.

---

### Post by quadomatic on 2007-08-25
> **cogadh said:**
> Nope, I just provide test data at the moment. I've currently got pending results for, KotOR, KotOR 2, Freelancer and Titanic: Adventure out of Time. I regularly test those games as well as Freedom Force, Star Trek: Armada 1 and 2, Vampire: Redemption, Vampire: Bloodlines, Hitman 2, Hitman: Contracts, Advent Rising, GTA 3, GTA Vice City, Tron 2.0, Call of Duty and Call of Duty: United Offensive. Of course I also test any new games as I get them.

EDIT -  Just saw your other post (must have been typing at the same time as me). Don't uncomment that first line unless you plan to do a CTRL-ALT-F1 to get to the console before launching the script.

By first line, do you mean the line that says "gdm stop"?

Right now, I'm trying to get KOTOR, Thief - Deadly Shadows, and Sword of the New World to work. I'll probably go ahead and try Painkiller, Far Cry, Tribes Vengeance, Deus Ex, and Deus Ex: Invisible War

---

### Post by cogadh on 2007-08-25
Yup, the "gdm stop" is only used if you plan on killing your current X session as well as Gnome before running the game. If that line is commented out, then you can run the script from within your normal Gnome session. To get back to Gnome, just do a CTRL-ALT-BACKSPACE after exiting the game (or it crashes, whichever happens).

Thief has a pretty dismal history with Wine, as does Deus Ex: Invisible War, but the rest should run great.

---

### Post by quadomatic on 2007-08-25
> **cogadh said:**
> Yup, the "gdm stop" is only used if you plan on killing your current X session as well as Gnome before running the game. If that line is commented out, then you can run the script from within your normal Gnome session. To get back to Gnome, just do a CTRL-ALT-BACKSPACE after exiting the game (or it crashes, whichever happens).

Thief has a pretty dismal history with Wine, as does Deus Ex: Invisible War, but the rest should run great.

I'll comment that line again then. Thanks.

Somehow, I think all these games would be a lot easier to get to work if I had a Nvidia video card...I think I'll get a new video card next month...then I'll need another 1GB of ram and a dual core processor.

A bit off topic, but I don't see the point in buying a GeForce 8x series right now. Shader Model 4 hardware isn't going to be necessary for at least a couple more years. Also, there will probably be an upgrade to Shader Model 5 by the time Direct X 10 hardware is necessary; similar to how almost no games REQUIRED Shader model 2 hardware, yet soon after Shader Model 3 became required.

Not to mention, GeForce 8x series probably doesn't handle Shader Model 4 well enough yet, just like GeForce 6x series didn't handle Shader Model 3 well.

---

### Post by cogadh on 2007-08-25
I am a hardcore NV fan myself, so take this with a little bit of bias. 

No video card out there, I don't care how good the manufacturer says it is, will work as well in Linux as any product produced by Nvidia. It has little to do with the actual capabilities of the hardware and everything to do with the fantastic drivers that Nvidia produces for Linux. I am now on my fourth Nvidia GPU with Linux and I have had little or no problems with any of them. I started with a GeForce2 MX400, then a TI4200 and then a FX5200. My current card is a 7600GS and I am extremely happy with it, I would not even consider upgrading to the 8xxx series (if my system could even support it, PCI Express is not in my future ATM). The Linux driver does have some reported problems with the 8800, but if history is any indication, Nvidia will have that fixed very soon.

If you have the means to get an Nvidia card, I highly recommend it. You will not regret changing brands and you will get excellent performance in Linux and Windows from any one of the 7xxx series cards at a very good price (now that the 8xxx cards are out).

---

### Post by quadomatic on 2007-08-25
> **cogadh said:**
> I am a hardcore NV fan myself, so take this with a little bit of bias. 

No video card out there, I don't care how good the manufacturer says it is, will work as well in Linux as any product produced by Nvidia. It has little to do with the actual capabilities of the hardware and everything to do with the fantastic drivers that Nvidia produces for Linux. I am now on my fourth Nvidia GPU with Linux and I have had little or no problems with any of them. I started with a GeForce2 MX400, then a TI4200 and then a FX5200. My current card is a 7600GS and I am extremely happy with it, I would not even consider upgrading to the 8xxx series (if my system could even support it, PCI Express is not in my future ATM). The Linux driver does have some reported problems with the 8800, but if history is any indication, Nvidia will have that fixed very soon.

If you have the means to get an Nvidia card, I highly recommend it. You will not regret changing brands and you will get excellent performance in Linux and Windows from any one of the 7xxx series cards at a very good price (now that the 8xxx cards are out).

I've figured for some time that NVidia's driver support was much better...for a few years now...which is why I wonder why I'm still using ATI. I was never using Linux this much until just recently.

For example, I couldn't use the last version of Ubuntu because my X850 PRO wasn't supported by the live cd (I know that has little to do with the driver, but ATI is so unsupported by linux). I was never able to get a Compositor outside of Beryl being automatically supported in SabayonLinux until just recently.

It appears as though ATI support has been getting better recently, but even still, I'd much rather switch to Nvidia. Everything, would be much better.

For example, I can only play CS: Source in DirectX 7 Mode in linux because ATI's GLSL shader support doesn't work in CS: Source.

Of course, I'd still use windows for gaming, but I'd like it if I didn't have to boot into Windows so often. I'd play games like Bioshock, which don't have WINE support, because they're so new. But older games for WINE, like the ones I'm trying to get working, and games like UT2007 and Enemy Territory: Quake Wars, should be very playable in Linux. I'll probably have a much better experience overall.

Maybe I'll try and get a used 7900 GT...or maybe an 8600 GTS. It has better Shader Model 3 support...I'll have to look around.

UPDATE: I ran the script, and then it said I didn't have permission to run the X Server, so I ran it as "sudo ./kotor.sh"

I got a gray blank screen, and nothing happened. I'm guessing there may be something else wrong for me...hopefully developers checking bugzilla will be able to tell me what's up.

---

### Post by Graelb on 2007-10-26
You know, i may just be completely missing something, but how did you get it to run with opengl? When i run the scan hardware program under wine, it says i have no vram, and that opengl was not detected...

---

### Post by cogadh on 2007-10-26
What video card do you have and do you have the 3D accelerated drivers for it installed?

---

### Post by Graelb on 2007-10-26
I have an nvidia 6200, and it's running the new glx drivers from the restricted driver manager =P

---

### Post by Graelb on 2007-10-27
Also, the hardware scan in kotor Kotor2 actually, but it should all be same same  on the hardware scan it says "video *failed* error []64MB
Graphics Required: 32 MB OpenGL 1.4 compatible PCI or AGP 3D Hardware Accelerator with Hardware Transform and Lighting (T&L) Capability required.

the game DOES run in windows btw

---

### Post by cogadh on 2007-10-27
You might need to make a couple of registry edits to make the detection work close to correctly. It will still fail because it won't find any Windows drivers, but it should detect your vrwam and OpenGL version correctly. Go to the Wine [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page and look for the Direct3D key section. Run regedit and add the "DirectDrawRenderer" string, set it to "opengl" then add the "VideoMemorySize" key, set it to your true vram.

---

### Post by Graelb on 2007-10-27
Sweet! that worked perfect! now the only problem i have is it yells at me saying that the nvidia drivers aren't up to date...

the error now says "Your current video card  drivers are out of date NVidia cards require Detonator 45.23 drivers or better." 


AND it's the only thing that's failed, which (i hope,) means that it will run if i can fix that part of it

edit: The game just crashes. the launcher runs, with sound, and when i try to run the game, the Wine desktop just dissapears after a second or two.

---

### Post by cogadh on 2007-10-27
It should fail to detect the video drivers, it is looking for Windows drivers, which obviously don't exist in Linux. You can ignore that, the game should run fine with that error.

Have you updated the game with the 1.03 patch and if so, are you using a cracked executable? The patch updated the game's copy protection and Wine doesn't fully support it (yet). Also, are there any errors output to the terminal when the game crashes?

---

### Post by Graelb on 2007-10-28
here's the output of the wine swkotor.exe 


[email]graelb@nirvana-X:~/.wine[/email]/drive_c/Program Files/LucasArts/SWKotOR2$ wine swkotor2.exe 
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
fixme:mixer:ALSA_MixerInit No master control found on Intel ICH6 Modem, disabling mixer
wine: Unhandled page fault on read access to 0x53e58955 at address 0xd9fcc8 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x53e58955 in 32-bit code (0x00d9fcc8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00d9fcc8 ESP:013ae0b0 EBP:013ae0b8 EFLAGS:00010297(   - 00     RISAP1C)
 EAX:53e58965 EBX:010e0244 ECX:00000004 EDX:00000000
 ESI:53e58955 EDI:01710b28
Stack dump:
0x013ae0b0:  0e02f828 010e02f8 013b5524 0092d2a9
0x013ae0c0:  01710b28 53e58955 00000010 00000000
0x013ae0d0:  00000000 00000000 00000000 013b091c
0x013ae0e0:  013b091c 013b1d20 013b1d20 013b3124
0x013ae0f0:  013b3124 00000000 00000000 00000000
0x013ae100:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x00d9fcc8 in swkotor2 (+0x99fcc8) (0x013ae0b8)
  2 0x0092d2a9 in swkotor2 (+0x52d2a9) (0x013b5524)
  3 0x010e0305 in swkotor2 (+0xce0305) (0x021c048a)
  4 0x00000000 (0x00000000)
0x00d9fcc8: movl        0xfffffff0(%esi,%ecx,4),%eax
Modules:
Module  Address                 Debug info      Name (86 modules)
PE        400000- 11bd000       Export          swkotor2
PE      21100000-21164000       Deferred        mss32
PE      30000000-3006d000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c78a000-7c7bc000       Deferred        uxtheme<elf>
  \-PE  7c790000-7c7bc000       \               uxtheme
ELF     7c7bc000-7c87a000       Deferred        comctl32<elf>
  \-PE  7c7d0000-7c87a000       \               comctl32
ELF     7c87a000-7c97d000       Deferred        shell32<elf>
  \-PE  7c890000-7c97d000       \               shell32
ELF     7c97d000-7c9d6000       Deferred        shlwapi<elf>
  \-PE  7c990000-7c9d6000       \               shlwapi
ELF     7c9d6000-7c9fd000       Deferred        msacm32<elf>
  \-PE  7c9e0000-7c9fd000       \               msacm32
ELF     7c9fd000-7cac3000       Deferred        libasound.so.2
ELF     7d689000-7d69e000       Deferred        midimap<elf>
  \-PE  7d690000-7d69e000       \               midimap
ELF     7d69e000-7d6b6000       Deferred        msacm32<elf>
  \-PE  7d6a0000-7d6b6000       \               msacm32
ELF     7d6b6000-7d6ec000       Deferred        winealsa<elf>
  \-PE  7d6c0000-7d6ec000       \               winealsa
ELF     7d6ec000-7d6f1000       Deferred        libxfixes.so.3
ELF     7d6f1000-7d6fa000       Deferred        libxcursor.so.1
ELF     7d6fa000-7d700000       Deferred        libxrandr.so.2
ELF     7d700000-7d708000       Deferred        libxrender.so.1
ELF     7da56000-7dae1000       Deferred        winex11<elf>
  \-PE  7da70000-7dae1000       \               winex11
ELF     7db5e000-7db7e000       Deferred        libexpat.so.1
ELF     7db7e000-7dba9000       Deferred        libfontconfig.so.1
ELF     7dba9000-7dbbe000       Deferred        libz.so.1
ELF     7dbbe000-7dc2e000       Deferred        libfreetype.so.6
ELF     7dc2e000-7dc4b000       Deferred        imm32<elf>
  \-PE  7dc40000-7dc4b000       \               imm32
ELF     7dc4b000-7dc5f000       Deferred        lz32<elf>
  \-PE  7dc50000-7dc5f000       \               lz32
ELF     7dc5f000-7dc79000       Deferred        version<elf>
  \-PE  7dc70000-7dc79000       \               version
ELF     7dc79000-7dc8f000       Deferred        glu32<elf>
  \-PE  7dc80000-7dc8f000       \               glu32
ELF     7dc8f000-7dcc5000       Deferred        dinput<elf>
  \-PE  7dca0000-7dcc5000       \               dinput
ELF     7dcc5000-7dcde000       Deferred        dinput8<elf>
  \-PE  7dcd0000-7dcde000       \               dinput8
ELF     7dcde000-7dd6c000       Deferred        winmm<elf>
  \-PE  7dcf0000-7dd6c000       \               winmm
ELF     7dd6c000-7dd7f000       Deferred        libresolv.so.2
ELF     7dd8c000-7ddaa000       Deferred        iphlpapi<elf>
  \-PE  7dd90000-7ddaa000       \               iphlpapi
ELF     7ddaa000-7de03000       Deferred        rpcrt4<elf>
  \-PE  7ddc0000-7de03000       \               rpcrt4
ELF     7de03000-7dea4000       Deferred        ole32<elf>
  \-PE  7de10000-7dea4000       \               ole32
ELF     7dea4000-7deed000       Deferred        advapi32<elf>
  \-PE  7deb0000-7deed000       \               advapi32
ELF     7deed000-7df88000       Deferred        gdi32<elf>
  \-PE  7df00000-7df88000       \               gdi32
ELF     7df88000-7e0c6000       Deferred        user32<elf>
  \-PE  7dfa0000-7e0c6000       \               user32
ELF     7e121000-7e12c000       Deferred        libgcc_s.so.1
ELF     7e21f000-7e221000       Deferred        libnvidia-tls.so.1
ELF     7e221000-7ebb9000       Deferred        libglcore.so.1
ELF     7ebb9000-7ebbe000       Deferred        libxdmcp.so.6
ELF     7ebbe000-7ebc1000       Deferred        libxau.so.6
ELF     7ebc1000-7ec44000       Deferred        libglu.so.1
ELF     7ec44000-7ecda000       Deferred        libgl.so.1
ELF     7ecda000-7edcb000       Deferred        libx11.so.6
ELF     7edcb000-7edd9000       Deferred        libxext.so.6
ELF     7edd9000-7edde000       Deferred        libxxf86vm.so.1
ELF     7edde000-7edf6000       Deferred        libice.so.6
ELF     7edf6000-7edfe000       Deferred        libsm.so.6
ELF     7ee0b000-7ee8c000       Deferred        opengl32<elf>
  \-PE  7ee20000-7ee8c000       \               opengl32
ELF     7efab000-7efb6000       Deferred        libnss_files.so.2
ELF     7efb6000-7efce000       Deferred        libnsl.so.1
ELF     7efce000-7eff3000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cd1000-b7cda000       Deferred        libnss_compat.so.2
ELF     b7cdb000-b7cdf000       Deferred        libdl.so.2
ELF     b7cdf000-b7e29000       Deferred        libc.so.6
ELF     b7e2a000-b7e42000       Deferred        libpthread.so.0
ELF     b7e4f000-b7f63000       Deferred        libwine.so.1
ELF     b7f65000-b7f81000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\LucasArts\SWKotOR2\swkotor2.exe
        00000009    0 <==

---

### Post by Graelb on 2007-10-28
Yes i updated it, do i need to reinstall it so it works right? i did indeed use a cracked patch *nods*

---

### Post by cogadh on 2007-10-28
If you reinstall and don't patch it, the game should work fine as long as the original CD is in the drive. If you patch it, then the updated copy protection will prevent it from working without a cracked exe. That dump you got is sometimes an indicator of a copy protection failure (but not always), so I would suggest you start with a reinstall and don't patch it.

---

### Post by Graelb on 2007-10-28
So, i'm using a patched exe because it's a burned CD, unless there's another way you know of to spoof the cd protection, but i'm not sure... The reinstall just asks for the CD

---

### Post by Graelb on 2007-10-28
OK! got it to work correctly. Now i just need to find a way to boost the speed of the game, it's very very choppy. *will try to diable compiz and other processes, * will running it in it's own X session help do you think?

---

### Post by Eddie002Fast on 2007-10-28
I am new too Linux and been checking out different Distro's for the last 5-7 days and i found that ubuntu and Linux XP to be my fav's.....anyways I can't get Star Wars-knights of the old republic 2 sith lords to install the game on ubuntu 7.10.......any suggestions would be appreciated!!! Thx!!! :D

---

### Post by Graelb on 2007-10-28
Just a note: i got it working, i had to get the right patch done... But it's working corectly now!

---

### Post by cogadh on 2007-10-28
> **Graelb said:**
> OK! got it to work correctly. Now i just need to find a way to boost the speed of the game, it's very very choppy. *will try to diable compiz and other processes, * will running it in it's own X session help do you think?
Yes, running in a separate X session is a huge help. That's how I run the game on my machine.

> **Eddie002Fast said:**
> I am new too Linux and been checking out different Distro's for the last 5-7 days and i found that ubuntu and Linux XP to be my fav's.....anyways I can't get Star Wars-knights of the old republic 2 sith lords to install the game on ubuntu 7.10.......any suggestions would be appreciated!!! Thx!!! :D
I only bring this up since you have said you are new to Linux... 
Windows applications cannot run in Linux normally. In order to use them, you need to install and configure Wine first. Wine is a open source replication of the Windows API; basically it allows Linux to understand Windows applications and Windows applications to understand Linux.

Have you installed and configured Wine yet?

---

### Post by Eddie002Fast on 2007-10-29
I just installed Wine from (add/remove programs repository)......:D

---

### Post by cogadh on 2007-10-29
In that case, installing the game is as simple as opening a terminal and typing:
```
wine /media/cdrom/setup.exe
```
Obviously change that to match your actual CD/DVD drive path and the correct install execuatable name (I don't have my disks handy right now, can't verify myself)

You might also want to click on the "Stuff I've learned about Wine" link in my sig to learn some of the basics of using Wine.

---

### Post by Eddie002Fast on 2007-10-29
OK! Game Installed!!!.......but there are 2 error's :(




[SWKotOR]

ReportDateTime=10/29/2007 5:17:28 PM

SysInfoVersion=v1.00.60

GameExists=1

GameVersion=v2.00.424

GameInstallLocation=C:\Program Files\LucasArts\SWKotOR2\



[OS]

Name=Win9x

Version=Windows 9X v6.0 build 6000  

Service Pack= 

Status=Fail



[SwapFiles]



[CPU]

CPUCount=1

CPUSpeed=2992

CPUFamily=15

CPUModel=4

CPUStepping=1

CPUVendor=Intel

CPUName= Intel(R) Pentium(R) 4 CPU 3.00GHz

Status=Pass



[Memory]

RAM=2032

Status=Pass



[Disk Free Space]

C: (NTFS)=127.86GB

Z: (NTFS)=127.86GB

Status=Pass



[CD-ROMs]

DriveLetters=D:\

Drives=



[Video]

Video Card Name=Error -- []

Video Memory=16

Desktop Resolution=1024x768x24

DirectX=DirectX 9.0c (4.09.00.0904)

OpenGL Version=2.0.6473 (8.37.6)

OpenGL Vendor=ATI Technologies Inc.

OpenGL Renderer=Radeon X300/X550/X1050 Series

Vid Card Status=Fail

Vid Card Driver Status=Pass

GL Status=Pass

DX Status=Pass



[Audio]

Sound Card Name=Analog Devices AD1980

Status=Pass





;Game Options from swkotor2.ini



[Display Options]

FullScreen=1

Disable Movies=0

Disable Intro Movies=0

Sort Modules=1

Width=640

Height=480

BitsPerPixels=32

RefreshRate=60



[Sound Options]

Disable Sound=0



[Graphics Options]

EnableHardwareMouse=1

FullScreen=0



[Game Options]



[config]

firstrun=0

---

### Post by Eddie002Fast on 2007-10-29
And I haven't updates the patches for this game yet i figured i ask you guys 1st !!! :D

---

### Post by Graelb on 2007-10-30
Atm i'm having issues with not being able to use my TTY's, they're black, well, i CAN use them, but i'm blind. I'm trying to figure out a way to fix that. I tried running that script you had on the 1st page, but it put me into a tty, and just didn't work, so... yeah. probably had something to do with it crashing, but we'll see.

---

### Post by cogadh on 2007-10-30
@Graelb:
You probably uncommented that line that kills the current X session (the "gdm stop" one). You only need to do that if you are going to launch the game from a console session (i.e. no GUI), not from a terminal. You might also need to edit the /etc/X11/Xwrapper.config file and change the allowed users entry from "console" to "anybody", otherwise the script might complain that you don't have permission to launch a new X session.

> **Eddie002Fast said:**
> OK! Game Installed!!!.......but there are 2 error's :(
You can ignore the vid card errors, that's just the hardware scan looking for Windows driver which are not present in Linux. The game still works despite that. However, you need to change your settings in Wine so that your default OS is Windows XP, I never had much luck running the game with Wine set for Win 98. As for the patches, you can apply them if you want, but that will mean that copy protection will prevent the game from launching without a cracked executable.

---

### Post by Crafty Kisses on 2007-10-30
I never got this game to run on my Computer. :(

---

### Post by reagentz on 2007-12-11
I know this is an older ongoing thread.

I wanted to dust off my copy of SWKotoR2 and check it out under WINE with Ubuntu.

I did get it load/run etc. everything works great in the game menus etc. when the game loads it's super choppy.

Other than running this bash script to launch the game is there any other way to get the game to work without it being choppy? I've disabled all special desktop effects, etc.

Thanks in advance.

---

### Post by cogadh on 2007-12-11
The problem is likely your sound card. Since the Audigy LS can't do hardware sound mixing, it creates a bit of latency since all the mixing work is being done with software by the processor. It usually doesn't make a difference in Windows, because the Creative drivers streamline the process a bit, but in Linux its a different story. I actually downgraded my LS to a SB Live! 5.1 to get away from that issue.

---

### Post by phildaman46 on 2007-12-30
I can't get the music or sound to work with both Kotor 1 and Kotor 2. They both run good though regardless of no sound.

---

