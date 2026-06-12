---
title: "[SOLVED] Morrowind, ATI BAD, Nvidia GOOD, and Lots of Errors"
date: 2008-07-27
forum: Wine
---

### Post by Sugi on 2008-07-27
I have been trying to install Morrowind on Wine 1.0 within 8.04 Hardy for the last 24 hours.  It's not going too well.

I get two errors,
"Unknown frame buffer Mode"
and
"Unknown stencil mode format"
and
Now, when the game starts up, it throws me to desktop without any erros.

Specs:
P4 1.8 Ghz
Gb of DDR PC 3200
ATI 9600 SE
ATI drivers from "Hardware Drivers"
Direct Rendering: Yes

```
wine /home/USR/.wine/drive_c/Program\ Files/Bethesda\ Softworks/Morrowind/Morrowind\ Launcher.exe 
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
USR@USR:~$ err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7cfb283 (thread 0019), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7cfb283).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7cfb283 ESP:0033ef7c EBP:0033ef98 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7dd3ff4 ECX:00000000 EDX:00000000
 ESI:00000033 EDI:00000000
Stack dump:
0x0033ef7c:  b7cfafc5 00000000 00000087 00000087
0x0033ef8c:  7e63079c 00000033 00000000 0033f018
0x0033ef9c:  7e5f3002 00000000 00000087 7c338eb0
0x0033efac:  00000001 00000000 00110000 00000002
0x0033efbc:  7bc88444 7c338eb0 7c089170 00000087
0x0033efcc:  7ed17cf0 00000001 00152a78 0033f008
Backtrace:
=>1 0xb7cfb283 strlen+0x33() in libc.so.6 (0x0033ef98)
  2 0x7e5f3002 in winex11 (+0x43002) (0x0033f018)
  3 0x7e5f5027 X11DRV_wglGetProcAddress+0x27() in winex11 (0x0033f058)
  4 0x7ecf948d wglGetProcAddress+0x6d() in gdi32 (0x0033f088)
  5 0x7e8e6bb5 InitAdapters+0x155() in wined3d (0x0033f518)
  6 0x7e958f52 WineDirect3DCreate+0x22() in wined3d (0x0033f548)
  7 0x7e99e144 Direct3DCreate8+0x84() in d3d8 (0x0033f578)
  8 0x006b1014 in morrowind (+0x2b1014) (0x001535d8)
  9 0x001588c0 (0x0074665c)
  10 0x004f52a0 in morrowind (+0xf52a0) (0x004174a0)
0xb7cfb283 strlen+0x33 in libc.so.6: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (89 modules)
PE	  400000-  7e4000	Export          morrowind
PE	30000000-3006e000	Deferred        binkw32
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d1de000-7e1e9000	Deferred        fglrx_dri.so
ELF	7e1e9000-7e1f4000	Deferred        libgcc_s.so.1
ELF	7e1f4000-7e26e000	Deferred        libgl.so.1
ELF	7e26e000-7e2a1000	Deferred        uxtheme<elf>
  \-PE	7e270000-7e2a1000	\               uxtheme
ELF	7e2c9000-7e2dd000	Deferred        midimap<elf>
  \-PE	7e2d0000-7e2dd000	\               midimap
ELF	7e2dd000-7e303000	Deferred        msacm32<elf>
  \-PE	7e2e0000-7e303000	\               msacm32
ELF	7e303000-7e31a000	Deferred        msacm32<elf>
  \-PE	7e310000-7e31a000	\               msacm32
ELF	7e31a000-7e3dd000	Deferred        libasound.so.2
ELF	7e3e9000-7e41f000	Deferred        winealsa<elf>
  \-PE	7e3f0000-7e41f000	\               winealsa
ELF	7e41f000-7e428000	Deferred        libxcursor.so.1
ELF	7e428000-7e42d000	Deferred        libxfixes.so.3
ELF	7e42d000-7e430000	Deferred        libxcomposite.so.1
ELF	7e430000-7e436000	Deferred        libxrandr.so.2
ELF	7e436000-7e43e000	Deferred        libxrender.so.1
ELF	7e43e000-7e45e000	Deferred        imm32<elf>
  \-PE	7e440000-7e45e000	\               imm32
ELF	7e45e000-7e463000	Deferred        libxdmcp.so.6
ELF	7e463000-7e47b000	Deferred        libxcb.so.1
ELF	7e47b000-7e562000	Deferred        libx11.so.6
ELF	7e562000-7e570000	Deferred        libxext.so.6
ELF	7e570000-7e575000	Deferred        libxxf86vm.so.1
ELF	7e575000-7e58d000	Deferred        libice.so.6
ELF	7e58d000-7e595000	Deferred        libsm.so.6
ELF	7e596000-7e59f000	Deferred        librt.so.1
ELF	7e5a1000-7e638000	Export          winex11<elf>
  \-PE	7e5b0000-7e638000	\               winex11
ELF	7e676000-7e697000	Deferred        libexpat.so.1
ELF	7e697000-7e6c1000	Deferred        libfontconfig.so.1
ELF	7e6c2000-7e6c5000	Deferred        libxinerama.so.1
ELF	7e6cd000-7e6e2000	Deferred        libz.so.1
ELF	7e6e2000-7e752000	Deferred        libfreetype.so.6
ELF	7e753000-7e756000	Deferred        libxau.so.6
ELF	7e75e000-7e81d000	Deferred        comctl32<elf>
  \-PE	7e770000-7e81d000	\               comctl32
ELF	7e81d000-7e887000	Deferred        msvcrt<elf>
  \-PE	7e830000-7e887000	\               msvcrt
ELF	7e887000-7e98a000	Export          wined3d<elf>
  \-PE	7e8a0000-7e98a000	\               wined3d
ELF	7e98a000-7e9b5000	Export          d3d8<elf>
  \-PE	7e990000-7e9b5000	\               d3d8
ELF	7e9b5000-7e9ff000	Deferred        dsound<elf>
  \-PE	7e9c0000-7e9ff000	\               dsound
ELF	7e9ff000-7ea36000	Deferred        dinput<elf>
  \-PE	7ea10000-7ea36000	\               dinput
ELF	7ea36000-7ea4e000	Deferred        dinput8<elf>
  \-PE	7ea40000-7ea4e000	\               dinput8
ELF	7ea4e000-7ea62000	Deferred        lz32<elf>
  \-PE	7ea50000-7ea62000	\               lz32
ELF	7ea62000-7ea7b000	Deferred        version<elf>
  \-PE	7ea70000-7ea7b000	\               version
ELF	7ea7b000-7eb0d000	Deferred        winmm<elf>
  \-PE	7ea90000-7eb0d000	\               winmm
ELF	7eb0d000-7eb20000	Deferred        libresolv.so.2
ELF	7eb20000-7eb3e000	Deferred        iphlpapi<elf>
  \-PE	7eb30000-7eb3e000	\               iphlpapi
ELF	7eb3e000-7eb9f000	Deferred        rpcrt4<elf>
  \-PE	7eb50000-7eb9f000	\               rpcrt4
ELF	7eb9f000-7ec43000	Deferred        ole32<elf>
  \-PE	7ebb0000-7ec43000	\               ole32
ELF	7ec43000-7ec95000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec95000	\               advapi32
ELF	7ec95000-7ed30000	Export          gdi32<elf>
  \-PE	7ecb0000-7ed30000	\               gdi32
ELF	7ed30000-7ee77000	Deferred        user32<elf>
  \-PE	7ed50000-7ee77000	\               user32
ELF	7ee77000-7ee82000	Deferred        libnss_files.so.2
ELF	7ee82000-7ee9a000	Deferred        libnsl.so.1
ELF	7ee9a000-7eea3000	Deferred        libnss_compat.so.2
ELF	7eea3000-7eea5000	Deferred        libxcb-xlib.so.0
ELF	7efcf000-7eff4000	Deferred        libm.so.6
ELF	7eff5000-7efff000	Deferred        libnss_nis.so.2
ELF	b7c85000-b7c89000	Deferred        libdl.so.2
ELF	b7c89000-b7dd8000	Export          libc.so.6
ELF	b7dd9000-b7df1000	Deferred        libpthread.so.0
ELF	b7dfd000-b7f33000	Deferred        libwine.so.1
ELF	b7f35000-b7f51000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
00000018 (D) C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe
	00000019    0 <==
Backtrace:
=>1 0xb7cfb283 strlen+0x33() in libc.so.6 (0x0033ef98)
  2 0x7e5f3002 in winex11 (+0x43002) (0x0033f018)
  3 0x7e5f5027 X11DRV_wglGetProcAddress+0x27() in winex11 (0x0033f058)
  4 0x7ecf948d wglGetProcAddress+0x6d() in gdi32 (0x0033f088)
  5 0x7e8e6bb5 InitAdapters+0x155() in wined3d (0x0033f518)
  6 0x7e958f52 WineDirect3DCreate+0x22() in wined3d (0x0033f548)
  7 0x7e99e144 Direct3DCreate8+0x84() in d3d8 (0x0033f578)
  8 0x006b1014 in morrowind (+0x2b1014) (0x001535d8)
  9 0x001588c0 (0x0074665c)
  10 0x004f52a0 in morrowind (+0xf52a0) (0x004174a0)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb7cfb283
```

Pastebin: [http://pastebin.com/m5fe4156f](http://pastebin.com/m5fe4156f)
Winehq: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3383&iTestingId=29197](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3383&iTestingId=29197)
UESP: [http://www.uesp.net/wiki/Morrowind:Linux](http://www.uesp.net/wiki/Morrowind:Linux)

Thanks,
Sugi


THE FIX:

 - Unable ATI Driver within "Hardware Drivers"
 - Removed ATI CARD
 - Install Nvidia Card
 - Instal Nvidia Driver
 - Error: Problem with Morrowind.ini file
FIX: [http://yacoby.silgrad.com/MW/Tuts/IniTut/IniPopup/StockGOTYini.htm](http://yacoby.silgrad.com/MW/Tuts/IniTut/IniPopup/StockGOTYini.htm)
ONLY USE if you have Morrowind GOTY with Tribunal and Bloodmoon installed
 - Error: FILE NOT FOUND /Data/Fonts/magic_cards_regular.fnt
FIX: 
Terminal > ```
wine /home/USR/.wine/PATH/TO/DIRECTORY/OF/MORROWIND/
```
```
wine Morrowind\ Launcher.exe
```
Reason:  You have to CD to the directory of Morrowind before wine(ing) the .exe to startup the Game correctly.
 - Then, the Game should be fix.  

ENJOY

Sugi

---

### Post by aoanla on 2008-07-27
The appdb entries for Morrowind suggest that unpatched Morrowind is much harder to get working than something patched to 1.4 or higher.
Have you patched your copy?

---

### Post by Sugi on 2008-07-27
In order this is how I installed Morrowind...

Morrowind GOTY
Tribunal
Bloodmoon
Bloodmoon_v1.6.1820.exe

Then I tried to startup Morrowind in Wine and I got those erros.

Sugi

---

### Post by aoanla on 2008-07-28
Hrm. I'm tempted to blame your graphics card, simply because there are a couple of bugs on the appdb page referencing issues with the fglrx driver...

This bug [http://bugs.winehq.org/show_bug.cgi?id=12929](http://bugs.winehq.org/show_bug.cgi?id=12929) seems relevant...

---

### Post by Sugi on 2008-07-28
Thanks, I am going to try an extra nvidia video card laying around here (it's pci, hopefully that won't change anything.)

Sugi

---

### Post by Sugi on 2008-07-28
Oh kay, I removed my ATI card for a Nvidia card.

Then, I had some problem with my Morrowind.in, but I found a website with the correct Morrowind.ini and used that.  But now, I got an error with my Data>Fonts>"Magic_Cards_Regular.fnt".  The problem is, I have that font file in my Data>Fonts directory, but I went online to find a correct file for it and replace it.  But that still didn't fix it.

> wine /home/USR/.wine/drive_c/Program\ Files/Bethesda\ Softworks/Morrowind/Morrowind\ Launcher.exe 
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f720,0x00000000), stub!
USR@USR:~$ err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f118,0x00000000), stub!


What should I do now?

Sugi

---

