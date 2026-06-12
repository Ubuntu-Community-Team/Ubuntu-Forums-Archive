---
title: "[HELP] Dungeon Runners in WINE"
date: 2008-04-02
forum: Wine
---

### Post by blaise69 on 2008-04-02
Howdy,

I've been hearing  a lot recently about Dungeon Runners, it's a relatively new MMORPG made by the creators of Guild Wars, and allegedly it uses the same graphics engine as Guild Wars.

I'd love to get this running on my Ubuntu 7.10 installation, but I've had little success with WINE in the past, and I wondered if anyone out there has managed to get Dungeon Runners already up and running without any trouble?

I am aware that Guild Wars is currently a Platinum app in the Wine DB, so I will follow any instructions there if I have trouble first, but I'm really looking for some first hand experience.

Finally failing any first hand experience, can anyone recommend some simple steps that they follow in getting a program working in Wine, the only thing I manage to do is change the Windows OS emulation for the exe, I'm not really sure what else to change in order to help.

I've had Diablo 2, Steam and TF2 successfully running, I've failed with Armada Online, Oblivion and Hellgate London.

Cheers,

Blaise.

---

### Post by blaise69 on 2008-04-02
Ok I've found it's not as easy as Guild Wars, and I still haven't got it running, when I went for my first run after installation, that seemed to go fine I came across a Mono error.

Wine outup told me that I needed to install the Windows version of Mono, so I went ahead and did that, once this was complete Dungeon Runners complained about not being able to find a config/defautl folder in Mono, so I created it, then it told me I was missing a NCLauncher.config file.

I managed to copy one from a friends installation on his XP machine and this managed to load up the NCLauncher, however this just got stuck on the updating progress bar.

I haven't even got into Dungeon Runners yet, I'm still stuck with this NCLauncher thing, I get no errors from Wine, it just seems to stick without progress being made on the update. I can click cancel however (although this doesn't completely cancel out).

Any ideas?

---

### Post by ajackson on 2008-04-03
To run a fully patched version use
```
wine DungeonRunners.exe ran_from_launcher
```
The "ran_from_launcher" is how NC's launcher fires it off.

As I said in my PM, patching is identical to Tabula Rasa but the problem I have hit is that the current version number is part of DungeonRunners.exe so I'm looking at how to access that.

Once I have information I should be able to create a version of my TRLinux for this game pretty easily.

---

### Post by blaise69 on 2008-04-03
Thanks for the info ajackson,

I'll give this a whirl tonight and we'll see what happens.  Have you asked any questions over at the Dungeon Runners Forum?  If you like I can start something off over there to help out.

Cheers,

Blaise.

---

### Post by blaise69 on 2008-04-03
Ok, using the ran_from_launcher argument seemed to load Dungeon Runners, but a problem instantly arose.

Here's what Wine output.

```
$ wine DungeonRunners.exe ran_from_launcher
fixme:win:EnumDisplayDevicesW ((null),0,0x34ece4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x34ece4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ece4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x34ece4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34eaf8,0x00000000), stub!
wine: Call from 0x9142ad to unimplemented function GDI32.dll.GdiEntry1, aborting
fixme:dbghelp_msc:codeview_fetch_type Cannot locate type 42
fixme:dbghelp_msc:codeview_fetch_type Cannot locate type 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42

```

Then there is this.

```
wine: Unimplemented function GDI32.dll.GdiEntry1 called at address 0x9142ad (thread 0009), starting debugger...
Unhandled exception: unimplemented function GDI32.dll.GdiEntry1 called in 32-bit code (0x7bc43003).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc43003 ESP:0034e3cc EBP:0034e430 EFLAGS:00200202(   - 00      - - I1)
 EAX:00a6abbe EBX:7bc86afc ECX:02653da8 EDX:02653de4
 ESI:0034e3d8 EDI:00000000
Stack dump:
0x0034e3cc:  7e20654e b7e66170 b7e66140 80000100
0x0034e3dc:  00000001 00000000 009142ad 00000002
0x0034e3ec:  00a6abf4 00a6abbe b7e66140 00010000
0x0034e3fc:  7e26db10 7c085880 00000002 0034e478
0x0034e40c:  7e206e64 00010000 0034ea38 0034e438
0x0034e41c:  7e1ff694 7c085880 7bc42fc4 02653ddc
Backtrace:
=>1 0x7bc43003 call_dll_entry_point+0x67() in ntdll (0x0034e430)
  2 0x009142ad in d3d9 (+0x342ad) (0x0034ec88)
  3 0x0090ae42 in d3d9 (+0x2ae42) (0x0034f03c)
  4 0x0090c445 in d3d9 (+0x2c445) (0x0034f064)
  5 0x00909f35 in d3d9 (+0x29f35) (0x0034f268)
  6 0x0090a5dd in d3d9 (+0x2a5dd) (0x0034f380)
fixme:dbghelp_msc:codeview_fetch_type Cannot locate type 42
fixme:dbghelp_msc:codeview_fetch_type Cannot locate type 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
fixme:dbghelp_msc:codeview_get_type Returning NULL symt for type-id 42
  7 0x00654182 in dungeonrunners (+0x254182) (0x0034f50c)
  8 0x00650119 in dungeonrunners (+0x250119) (0x0034f550)
  9 0x00651d5d in dungeonrunners (+0x251d5d) (0x0034f588)
  10 0x00405d51 in dungeonrunners (+0x5d51) (0x0034f964)
  11 0x0066fb60 in dungeonrunners (+0x26fb60) (0x0034fdb0)
  12 0x0066a96c in dungeonrunners (+0x26a96c) (0x0034fde0)
  13 0x006a462f WinMainCRTStartup+0x184() [f:\vs70builds\3077\vc\crtbld\crt\src\crt0.c:251] in dungeonrunners (0x0034ff08)
  14 0x7b86f7f9 in kernel32 (+0x4f7f9) (0x0034ffe8)
  15 0xb7e991cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc43003 call_dll_entry_point+0x67 in ntdll: subl     $4,%esp
Modules:
Module  Address                 Debug info      Name (98 modules)
PE        350000-  355000       Deferred        d3d8thk
PE        400000-  8da000       CodeView        dungeonrunners
PE        8e0000-  a89000       Export          d3d9
PE        a90000-  ce0000       Deferred        d3dx9_28
PE        df0000-  e92000       Deferred        dfengine
PE      10000000-1013d000       Deferred        fmodex
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Export          ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dfbd000-7dfc8000       Deferred        libgcc_s.so.1
ELF     7dfd8000-7dff5000       Deferred        imm32<elf>
  \-PE  7dfe0000-7dff5000       \               imm32
ELF     7e14e000-7e180000       Deferred        uxtheme<elf>
  \-PE  7e150000-7e180000       \               uxtheme
ELF     7e180000-7e194000       Deferred        midimap<elf>
  \-PE  7e190000-7e194000       \               midimap
ELF     7e194000-7e1ab000       Deferred        msacm32<elf>
  \-PE  7e1a0000-7e1ab000       \               msacm32
ELF     7e1ab000-7e271000       Deferred        libasound.so.2
ELF     7e271000-7e2a6000       Deferred        winealsa<elf>
  \-PE  7e280000-7e2a6000       \               winealsa
ELF     7e2a6000-7e2af000       Deferred        libxcursor.so.1
ELF     7e2af000-7e2b4000       Deferred        libxfixes.so.3
ELF     7e2b4000-7e2b7000       Deferred        libxcomposite.so.1
ELF     7e2b7000-7e2bd000       Deferred        libxrandr.so.2
ELF     7e2bd000-7e2c5000       Deferred        libxrender.so.1
ELF     7e2c5000-7e2ca000       Deferred        libxdmcp.so.6
ELF     7e2ca000-7e2cd000       Deferred        libxau.so.6
ELF     7e2cd000-7e3be000       Deferred        libx11.so.6
ELF     7e3be000-7e3cc000       Deferred        libxext.so.6
ELF     7e3cc000-7e3d1000       Deferred        libxxf86vm.so.1
ELF     7e3d1000-7e3e9000       Deferred        libice.so.6
ELF     7e3e9000-7e3f1000       Deferred        libsm.so.6
ELF     7e401000-7e48f000       Deferred        winex11<elf>
  \-PE  7e410000-7e48f000       \               winex11
ELF     7e4ed000-7e50d000       Deferred        libexpat.so.1
ELF     7e50d000-7e538000       Deferred        libfontconfig.so.1
ELF     7e538000-7e54d000       Deferred        libz.so.1
ELF     7e54d000-7e5bd000       Deferred        libfreetype.so.6
ELF     7e5bd000-7e67c000       Deferred        comctl32<elf>
  \-PE  7e5d0000-7e67c000       \               comctl32
ELF     7e67c000-7e6d2000       Deferred        shlwapi<elf>
  \-PE  7e690000-7e6d2000       \               shlwapi
ELF     7e6d2000-7e7d8000       Deferred        shell32<elf>
  \-PE  7e6e0000-7e7d8000       \               shell32
ELF     7e7d8000-7e879000       Deferred        oleaut32<elf>
  \-PE  7e7f0000-7e879000       \               oleaut32
ELF     7e879000-7e892000       Deferred        wsock32<elf>
  \-PE  7e880000-7e892000       \               wsock32
ELF     7e892000-7e8b8000       Deferred        msacm32<elf>
  \-PE  7e8a0000-7e8b8000       \               msacm32
ELF     7e8b8000-7e902000       Deferred        dsound<elf>
  \-PE  7e8c0000-7e902000       \               dsound
ELF     7e902000-7e92d000       Deferred        ws2_32<elf>
  \-PE  7e910000-7e92d000       \               ws2_32
ELF     7e92d000-7e940000       Deferred        libresolv.so.2
ELF     7e950000-7e96e000       Deferred        iphlpapi<elf>
  \-PE  7e960000-7e96e000       \               iphlpapi
ELF     7e96e000-7e9cc000       Deferred        rpcrt4<elf>
  \-PE  7e980000-7e9cc000       \               rpcrt4
ELF     7e9cc000-7ea6c000       Deferred        ole32<elf>
  \-PE  7e9e0000-7ea6c000       \               ole32
ELF     7ea6c000-7eaa2000       Deferred        dinput<elf>
  \-PE  7ea70000-7eaa2000       \               dinput
ELF     7eaa2000-7eaba000       Deferred        dinput8<elf>
  \-PE  7eab0000-7eaba000       \               dinput8
ELF     7eaba000-7eacf000       Deferred        psapi<elf>
  \-PE  7eac0000-7eacf000       \               psapi
ELF     7eacf000-7eb17000       Deferred        dbghelp<elf>
  \-PE  7eae0000-7eb17000       \               dbghelp
ELF     7eb17000-7eb2e000       Deferred        imagehlp<elf>
  \-PE  7eb20000-7eb2e000       \               imagehlp
ELF     7eb2e000-7ebba000       Deferred        winmm<elf>
  \-PE  7eb40000-7ebba000       \               winmm
ELF     7ebba000-7ebce000       Deferred        lz32<elf>
  \-PE  7ebc0000-7ebce000       \               lz32
ELF     7ebce000-7ebe7000       Deferred        version<elf>
  \-PE  7ebd0000-7ebe7000       \               version
ELF     7ebe7000-7ec31000       Deferred        advapi32<elf>
  \-PE  7ebf0000-7ec31000       \               advapi32
ELF     7ec31000-7ecc9000       Deferred        gdi32<elf>
  \-PE  7ec40000-7ecc9000       \               gdi32
ELF     7ecc9000-7ee05000       Deferred        user32<elf>
  \-PE  7ece0000-7ee05000       \               user32
ELF     7ee05000-7ee6a000       Deferred        msvcrt<elf>
  \-PE  7ee10000-7ee6a000       \               msvcrt
ELF     7efa8000-7efb3000       Deferred        libnss_files.so.2
ELF     7efb3000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff0000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d11000-b7d1a000       Deferred        libnss_compat.so.2
ELF     b7d1b000-b7d1f000       Deferred        libdl.so.2
ELF     b7d1f000-b7e69000       Deferred        libc.so.6
ELF     b7e6a000-b7e82000       Deferred        libpthread.so.0
ELF     b7e92000-b7fa6000       Export          libwine.so.1
ELF     b7fa8000-b7fc4000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\NCSoft\Dungeon Runners\DungeonRunners.exe
        00000019    0
        00000018    1
        00000017   15
        00000016   15
        00000015   15
        00000009    0 <==
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000011 
        00000013    0
        00000012    0
0000001c 
        0000001d    0
Backtrace:
=>1 0x7bc43003 call_dll_entry_point+0x67() in ntdll (0x0034e430)
  2 0x009142ad in d3d9 (+0x342ad) (0x0034ec88)
  3 0x0090ae42 in d3d9 (+0x2ae42) (0x0034f03c)
  4 0x0090c445 in d3d9 (+0x2c445) (0x0034f064)
  5 0x00909f35 in d3d9 (+0x29f35) (0x0034f268)
  6 0x0090a5dd in d3d9 (+0x2a5dd) (0x0034f380)
  7 0x00654182 in dungeonrunners (+0x254182) (0x0034f50c)
  8 0x00650119 in dungeonrunners (+0x250119) (0x0034f550)
  9 0x00651d5d in dungeonrunners (+0x251d5d) (0x0034f588)
  10 0x00405d51 in dungeonrunners (+0x5d51) (0x0034f964)
  11 0x0066fb60 in dungeonrunners (+0x26fb60) (0x0034fdb0)
  12 0x0066a96c in dungeonrunners (+0x26a96c) (0x0034fde0)
  13 0x006a462f WinMainCRTStartup+0x184() [f:\vs70builds\3077\vc\crtbld\crt\src\crt0.c:251] in dungeonrunners (0x0034ff08)
  14 0x7b86f7f9 in kernel32 (+0x4f7f9) (0x0034ffe8)
  15 0xb7e991cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
wine: Call from 0x9142ad to unimplemented function GDI32.dll.GdiEntry1, aborting

```

---

### Post by ajackson on 2008-04-03
**DRLinux-0.1**
It's got one almight bodge to extract the current game version (a little dos program that spews out the header info) but it will do until something better is found.

Using this I patched the game from it's downloaded state to the current server version and launched the game.

Logged in on a free account and set the screen resolution to something less horrible (it seemed to default to 640x480). Didn't play it though.

[http://www.lotrolinux.com/DR]("http://www.lotrolinux.com/DR") houses the launcher source tarball.

I don't play the game and I have no intentions of playing so while I can help where the launcher is concerned I can't for the game itself.

---

### Post by blaise69 on 2008-04-04
Understood,

Thankyou anyway, I know there are people out there that will be very greatful for your efforts.

---

### Post by blaise69 on 2008-04-08
Ok, I managed to get this working successfully with your Launcher, I did need to make sure I had a couple of DLL's however, but the output that Wine gave me revealed which ones so it was straight forward, it's quite possible that if you've used Wine for other applications you'll have these DLL's already.

Required DLL's were GDI32.dll and GdiPlus.dll, these were found easily using a google search

It runs very well, better than expected.

---

### Post by arrakis31 on 2008-04-08
This game looks really good. I am a big Diablo fan, this should keeps use busy waiting for the next one.

Anyway, could you post a quick howto for installing and running the game, i am still a newbie sorry....

Thanks a lot !!!!!

---

### Post by blaise69 on 2008-04-10
Hi Arrakis31, I saw your post over at [Wine - Dungeron Runners]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8765"), so I take it you got it working?

If that's the case the post you made would probably be perfect for a HowTo, can I ask, did you have to install any extra dlls also?  I had to make sure I had GDI32.dll and GDIPlus.dll

Cheers,

Blaise.

---

### Post by arrakis31 on 2008-04-10
I am posting the HowTo right now.
I hope you don't mind me doing it, you guys did all the works...

But the game is fun, its working nice with the launcher so I had to change the statut of Garbage on the wineDB...

And you're right I forgot about the dll
I did override gdi32.dll and gdiplus.dll, I will detail it in the howto.

Thanks to you guys and cheers.

---

### Post by blaise69 on 2008-04-11
I checked out your HowTo and it's excellent.

I did try and change the status in of the existing reports in there but it hasn't been approved yet, so it's good that you went ahead and created a new one.

---

### Post by beemer on 2008-04-11
Well - I tried this and it all went smooth as silk until the game actually launched...I get a black square in the upper left of the screen with a white area around the remainder.  I also tried the reg fix from the wine appdb instructions.

Any ideas?

---

### Post by blaise69 on 2008-04-12
Hi beemer, when you DRLinux through the the command line do you receive any warnings from Wine when this happens?

---

### Post by beemer on 2008-04-12
Here's what I get from the command line:

err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F

The above err is repeated *many* times...then the following:

err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to ch
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to ch
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to ch
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to ch
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to ch
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to ch
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to ch
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to ch
err:ntdll:RtlpWaitForCriticalSection section 0x7e34ffa0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 001d, blocked by 0009, retrying (60 sec)
wine: Unhandled page fault on read access to 0x00221000 at address 0x7d634200 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00221000 in 32-bit code (0x7d634200).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d634200 ESP:0033be30 EBP:00000200 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000008 EBX:7cdd0500 ECX:00000008 EDX:00221000
 ESI:00221000 EDI:7cdd0500
Stack dump:
0x0033be30:  00000200 00221000 0033c15c 00000080
0x0033be40:  00000000 00000000 00000000 00000000
0x0033be50:  7d4553ca 7cdd0500 00221000 00000200
0x0033be60:  00000000 005e1f00 7d6309c0 7cb81000
0x0033be70:  1f95c300 7c037170 00000200 00019d81
0x0033be80:  00001000 00000004 00000080 00000080
Backtrace:
=>1 0x7d634200 in libglcore.so.1 (+0x65c200) (0x00000200)
  2 0x00000000 (0x00000000)
0x7d634200:
Modules:
Module  Address                 Debug info      Name (105 modules)
PE        340000-  3e6000       Deferred        dfengine
PE        400000-  8f5000       Deferred        dungeonrunners
PE        900000-  ca9000       Deferred        d3dx9_36
PE       2f10000- 3177000       Deferred        d3dx9_31
PE      10000000-1013d000       Deferred        fmodex
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cae3000-7cb41000       Deferred        winedos<elf>
  \-PE  7caf0000-7cb41000       \               winedos
ELF     7cfd8000-7d94a000       Export          libglcore.so.1
ELF     7d94a000-7d9de000       Deferred        libgl.so.1
ELF     7dd11000-7dd1d000       Deferred        libgcc_s.so.1
ELF     7df54000-7df73000       Deferred        imm32<elf>
  \-PE  7df60000-7df73000       \               imm32
ELF     7e0a8000-7e0da000       Deferred        uxtheme<elf>
  \-PE  7e0b0000-7e0da000       \               uxtheme
ELF     7e0da000-7e0ee000       Deferred        midimap<elf>
  \-PE  7e0e0000-7e0ee000       \               midimap
ELF     7e0ee000-7e105000       Deferred        msacm32<elf>
  \-PE  7e0f0000-7e105000       \               msacm32
ELF     7e105000-7e140000       Deferred        wineoss<elf>
  \-PE  7e110000-7e140000       \               wineoss
ELF     7e165000-7e16e000       Deferred        libxcursor.so.1
ELF     7e16e000-7e173000       Deferred        libxfixes.so.3
ELF     7e173000-7e176000       Deferred        libxcomposite.so.1
ELF     7e176000-7e17c000       Deferred        libxrandr.so.2
ELF     7e17c000-7e184000       Deferred        libxrender.so.1
ELF     7e184000-7e189000       Deferred        libxdmcp.so.6
ELF     7e189000-7e18c000       Deferred        libxau.so.6
ELF     7e18c000-7e27d000       Deferred        libx11.so.6
ELF     7e27d000-7e28b000       Deferred        libxext.so.6
ELF     7e28b000-7e290000       Deferred        libxxf86vm.so.1
ELF     7e290000-7e2a8000       Deferred        libice.so.6
ELF     7e2a8000-7e2b1000       Deferred        libsm.so.6
ELF     7e2c2000-7e2c4000       Deferred        libnvidia-tls.so.1
ELF     7e2c6000-7e354000       Deferred        winex11<elf>
  \-PE  7e2d0000-7e354000       \               winex11
ELF     7e3e1000-7e401000       Deferred        libexpat.so.1
ELF     7e401000-7e42c000       Deferred        libfontconfig.so.1
ELF     7e42c000-7e440000       Deferred        libz.so.1
ELF     7e440000-7e4ab000       Deferred        libfreetype.so.6
ELF     7e4c0000-7e57f000       Deferred        comctl32<elf>
  \-PE  7e4d0000-7e57f000       \               comctl32
ELF     7e57f000-7e5d6000       Deferred        shlwapi<elf>
  \-PE  7e590000-7e5d6000       \               shlwapi
ELF     7e5d6000-7e6de000       Deferred        shell32<elf>
  \-PE  7e5f0000-7e6de000       \               shell32
ELF     7e6de000-7e6f7000       Deferred        version<elf>
  \-PE  7e6e0000-7e6f7000       \               version
ELF     7e6f7000-7e798000       Deferred        oleaut32<elf>
  \-PE  7e710000-7e798000       \               oleaut32
ELF     7e798000-7e7b1000       Deferred        wsock32<elf>
  \-PE  7e7a0000-7e7b1000       \               wsock32
ELF     7e7b1000-7e7d7000       Deferred        msacm32<elf>
  \-PE  7e7c0000-7e7d7000       \               msacm32
ELF     7e7d7000-7e821000       Deferred        dsound<elf>
  \-PE  7e7e0000-7e821000       \               dsound
ELF     7e821000-7e84c000       Deferred        ws2_32<elf>
  \-PE  7e830000-7e84c000       \               ws2_32
ELF     7e84c000-7e85f000       Deferred        libresolv.so.2
ELF     7e860000-7e874000       Deferred        lz32<elf>
  \-PE  7e870000-7e874000       \               lz32
ELF     7e874000-7e892000       Deferred        iphlpapi<elf>
  \-PE  7e880000-7e892000       \               iphlpapi
ELF     7e892000-7e8f0000       Deferred        rpcrt4<elf>
  \-PE  7e8a0000-7e8f0000       \               rpcrt4
ELF     7e8f0000-7e990000       Deferred        ole32<elf>
  \-PE  7e900000-7e990000       \               ole32
ELF     7e990000-7e9c7000       Deferred        dinput<elf>
  \-PE  7e9a0000-7e9c7000       \               dinput
ELF     7e9c7000-7e9df000       Deferred        dinput8<elf>
  \-PE  7e9d0000-7e9df000       \               dinput8
ELF     7e9df000-7ea6b000       Deferred        winmm<elf>
  \-PE  7e9f0000-7ea6b000       \               winmm
ELF     7ea6b000-7ea80000       Deferred        psapi<elf>
  \-PE  7ea70000-7ea80000       \               psapi
ELF     7ea80000-7eac8000       Deferred        dbghelp<elf>
  \-PE  7ea90000-7eac8000       \               dbghelp
ELF     7eac8000-7eadf000       Deferred        imagehlp<elf>
  \-PE  7ead0000-7eadf000       \               imagehlp
ELF     7eadf000-7eb44000       Deferred        msvcrt<elf>
  \-PE  7eaf0000-7eb44000       \               msvcrt
ELF     7eb44000-7eb93000       Deferred        advapi32<elf>
  \-PE  7eb50000-7eb93000       \               advapi32
ELF     7eb93000-7ec2b000       Deferred        gdi32<elf>
  \-PE  7eba0000-7ec2b000       \               gdi32
ELF     7ec2b000-7ed6b000       Deferred        user32<elf>
  \-PE  7ec40000-7ed6b000       \               user32
ELF     7ed6b000-7ee6b000       Deferred        wined3d<elf>
  \-PE  7ed80000-7ee6b000       \               wined3d
ELF     7ee6b000-7ee9b000       Deferred        d3d9<elf>
  \-PE  7ee70000-7ee9b000       \               d3d9
ELF     7efad000-7efc4000       Deferred        libnsl.so.1
ELF     7efc4000-7efeb000       Deferred        libm.so.6
ELF     7efeb000-7eff6000       Deferred        libnss_files.so.2
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c62000-b7c6b000       Deferred        libnss_compat.so.2
ELF     b7c6c000-b7c70000       Deferred        libdl.so.2
ELF     b7c70000-b7db1000       Deferred        libc.so.6
ELF     b7db2000-b7dc9000       Deferred        libpthread.so.0
ELF     b7dde000-b7ef2000       Deferred        libwine.so.1
ELF     b7ef4000-b7f0f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\NCSoft\Dungeon Runners\DungeonRunners.exe
        00000028    0
        00000027    1
        00000026   15
        00000025   15
        00000023   15
        00000009    0 <==
0000000c
        0000001c    0
        00000015    0
        0000000e    0
        0000000d    0
00000011
        00000014    0
        00000013    0
        00000012    0
00000018
        0000001b    0
        0000001a    0
        00000019    0
0000001e
        00000020    0
        0000001f    0
Backtrace:
=>1 0x7d634200 in libglcore.so.1 (+0x65c200) (0x00000200)
  2 0x00000000 (0x00000000)

Thanks

Beemer

---

### Post by nixgeek on 2008-04-20
I have the same issue Beemer, I run DRLinux (It patched properly) but it simply goes to a black screen and nothing else happens.

---

### Post by arrakis31 on 2008-04-21
What version of wine are using ?

Did you try to change the windows version for the program to win98 ?
To do that start wine config with :
# winecfg

On the first page add application 
and look for DungeonRunners.exe
DungeonNCLauncher.exe
NClauncher.exe
in the game folders

Put all of them in win 98 version
and retry the game

---

### Post by beemer on 2008-04-22
Ok - Before I saw the post about trying win98 settings, I wiped my system and installed Hardy on it, thus needing to recompile.  I got ./configure all happy but make spits out:
make
/usr/bin/gmcs Main.cs MainWindow.cs Config.cs Patch.cs PatchWindow.cs RepairWindow.cs Settings.cs SettingsWindow.cs StartGame.cs -noconfig -codepage:utf8 -warn:3 -out:DRLinux.run -target:exe -resource:DRLinux.ico -resource:DRLinux.png -resource:MainWindow.glade -resource:PatchWindow.glade -resource:RepairWindow.glade -resource:SettingsWindow.glade -r:System -r:System.Xml -r:System.Web -pkg:gtk-sharp-2.0 -pkg:glade-sharp-2.0
error CS0006: cannot find metadata file `System.Web'
Compilation failed: 1 error(s), 0 warnings
make: *** [DRLinux.run] Error 1

What is System.Web?  When I did this under Feisty, once I had the ./configure happy all was well for the make.

FOUND IT: had to 'sudo apt-get install libmono-system-web2.0-cil'

20:07 - Ok - awesome! got it working with the win98 setting and the regfix from the Wine AppDB entry.

To recap the compile for other folks:
In Kubuntu (and I would think Ubuntu as well), you will need to apt-get the following in order to compile:
libmono-system-web2.0-cil
mono-gmcs
unrar
xdelta
libglade2-dev
libglade2.0-cil

And I think that's it.  After the compile/install follow the AppDB instructions.  Thanks arrakis and blaise!

Beemer

---

### Post by blaise69 on 2008-04-23
Well done Beemer, I think I had to install some extra dependencies when I ran make, naturally this is a problem with your setup and make, not the DRLinux launcher or Dungeon Runners, so it's good you didn't come across any other issues there.

Glad to have you on board!

Can you confirm the version of Wine you are using, and just to check you are running this on Hardy Heron now?  That's great!

---

### Post by ajackson on 2008-04-23
> **beemer said:**
> What is System.Web?  When I did this under Feisty, once I had the ./configure happy all was well for the make.

FOUND IT: had to 'sudo apt-get install libmono-system-web2.0-cil'

System.Web does cause problems (getting it installed that is), under Dapper it is not in it's own package (Feisty onwards it is) so I couldn't include a check for that package. Up until Hardy it was grabbed as one of the dependencies for the other required packages so again I could get away with not specifying it separately.

I'll see if I can amend the config script to check for the library without upsetting any Dapper users (thankfully in around a month I can consider dropping support for Dapper).

Nice spot though.

---

### Post by blaise69 on 2008-04-23
ajackson, with all the NCLauncher games coming out, how feasible would it be to put together a universal launcher?  Or at least a multi-launcher?

From what you said about finding version numbers from the DR exe this may not be straight forward, but it seems that NCSoft will be using this launcher for all future games, and it's possible a standard will come form this, some sort of extensible launcher would be ideal.

I was considering revealing the launcher on the DR forum, but was concerned that it may considered to be tampering with the code, as I understand similar things were banned for WoW users as it's a common way for hacks to be applied, I wonder though how things could be different if NCSoft used your code to make Linux compatible launchers of all their games with wine support.

---

### Post by ajackson on 2008-04-23
> **blaise69 said:**
> ajackson, with all the NCLauncher games coming out, how feasible would it be to put together a universal launcher?  Or at least a multi-launcher?
The way my config file is setup make adding extra games fairly easy. If you look at LotROLinux it handles LOTRO and DDO as they are virtually identical in how the start the game.

Dungeon Runners & Tabula Rasa are identical in terms of patching, it is just the name of the patch server (and the path on that server) that changes.

> From what you said about finding version numbers from the DR exe this may not be straight forward
I've got my inelegant little hack program that does the job, it should work with any program that stores the version number within the executable rather than a separate file.

> I was considering revealing the launcher on the DR forum
Considering the game is free I doubt they would be too concerned, TRLinux is mentioned on one of unofficial TR sites and one of the TR devs has said in the thread about getting TR working with wine that he admires the communities dedication to getting it working. Also to look back at LOTRO, the dev team exposed the patch function purely so that those people who aren't using the official launcher could patch the game.

So I think in general the worse that would happen is the thread gets deleted. Just make sure you mention that NCSoft do not support running the game on any platform other than Windows, if they start getting support requests from linux users they may complain.

I have thought about creating a unified launcher, all the information I need to start games is handily included in an xml file that gets installed when NCSofts's launcher is installed.

I do know that some games still include their own patching systems (City of Heroes/Villians is one).

I certainly don't mind giving it a shot, could do with a new project to work on now that the bulk of testing Hardy is finished.

---

### Post by ajackson on 2008-04-26
Well version 0.1 of ULL (Universal Linux Launcher for NCSoft Games) should be ready for release tomorrow. The games my version of the NCSoft launcher seems to handle are:

Auto Assault, Dungeon Runners (incl PTS), Tabula Rasa, Lineage 1 & 2 (incl test), Guild Wars, City of Heroes/Villains (inc EU & test) and Exteel.

I've tested DR & TR as they don't have stand alone patching, CoH works (though there seems to be a problem with the EU version), GW & Lineage 1 launch OK. The rest I don't know, Exteel seems to use the launcher to patch itself so I'm trying to get a demo version to check it.

Any suggestions, such as a decent name, appreciated or if your version of the NCSoft launcher handles other games can you paste Games.xml files (there maybe more than one) from the Prog Files/NCSoft/Launcher directories.

Thanks.

---

### Post by torgo on 2008-04-27
I downloaded the game. I compiled the loader program. I successfully patched the game. When I launch the game from the DRLinux program, I get a black full screen, then it flickers, and then locks up my desktop. When I run WINE in a window, the same thing happens. Blank Window, locked up. No progress.

What steps should I take to get this program working from this point. I don't really know my way around WINE or Linux that well, so any help would be appreciated.:)

---

### Post by ajackson on 2008-04-27
**ULL 0.1**
I've released my universal launcher ([http://ubuntuforums.org/showthread.php?t=770438]("http://ubuntuforums.org/showthread.php?t=770438")), TR & DR work fine though I have found that DR sometimes installs files as read-only so updates may fail unless you turn them back to read-write (mainly the stuff in the DR directory, the dlls, etc).

The other games I haven't really checked so if you happen to have one of them please give it a go.

---

### Post by olskar on 2008-05-08
I am using the ULL program and trying to run Dungeon Runners, I get to the screen where I can create a character and click play. After that I go to some other screen (with a drawing or something) and then it crashes with "encountered an unhandled exception" 

Got any tips?

---

### Post by darkice_ita on 2008-05-18
downloaded ULL-0.5.tar.bz2, then configured correctly, make and make install succeded

but when i start ULL that's what i see:

```
 $ ULL
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IO.DirectoryNotFoundException: Directory '/home/.wine/dosdevices/c:/Program Files/NCSoft/Launcher' not found.
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String pattern, FileAttributes mask, FileAttributes attrs) [0x00000]
  at System.IO.Directory.GetFiles (System.String path, System.String pattern) [0x00000]
  at System.IO.DirectoryInfo.GetFiles (System.String pattern) [0x00000]
  at System.IO.DirectoryInfo.GetFiles () [0x00000]
  at (wrapper remoting-invoke-with-check) System.IO.DirectoryInfo:GetFiles ()
  at ULL.MainWindow.InitialSetup () [0x00000]
  at ULL.MainWindow.OnSelectionChanged (System.Object o, System.EventArgs args) [0x00000]
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000]
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr gch)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.TreeView.gtk_tree_view_set_cursor(IntPtr , IntPtr , IntPtr , Boolean )
   at Gtk.TreeView.gtk_tree_view_set_cursor(IntPtr , IntPtr , IntPtr , Boolean )
   at Gtk.TreeView.SetCursor(Gtk.TreePath path, Gtk.TreeViewColumn focus_column, Boolean start_editing)
   at ULL.MainWindow.FillGameList()
   at ULL.MainWindow.Run()
   at ULL.GladeApp..ctor(Boolean args)
   at ULL.GladeApp.Main(System.String[] args)

```

all dependencies are satisfied
don't know what to try

i've to say also that this is the second time i compile and install ULL.Previously i've installed the program in the same way, and when started from console it worked..but always failed to find the game version in the Launcher folder..so i've uninstalled...now i'm trying again but that's what happened...

please help

(i'm on gentoo amd64)

ps: please forgive my grammar errors....my english isn't good as i desire

---

### Post by ajackson on 2008-05-19
> **darkice_ita said:**
> downloaded ULL-0.5.tar.bz2, then configured correctly, make and make install succeded

but when i start ULL that's what i see:

```
 $ ULL
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IO.DirectoryNotFoundException: Directory '/home/.wine/dosdevices/c:/Program Files/NCSoft/Launcher' not found.
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String pattern, FileAttributes mask, FileAttributes attrs) [0x00000]
  at System.IO.Directory.GetFiles (System.String path, System.String pattern) [0x00000]
  at System.IO.DirectoryInfo.GetFiles (System.String pattern) [0x00000]
  at System.IO.DirectoryInfo.GetFiles () [0x00000]
  at (wrapper remoting-invoke-with-check) System.IO.DirectoryInfo:GetFiles ()
  at ULL.MainWindow.InitialSetup () [0x00000]
  at ULL.MainWindow.OnSelectionChanged (System.Object o, System.EventArgs args) [0x00000]
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000]
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr gch)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.TreeView.gtk_tree_view_set_cursor(IntPtr , IntPtr , IntPtr , Boolean )
   at Gtk.TreeView.gtk_tree_view_set_cursor(IntPtr , IntPtr , IntPtr , Boolean )
   at Gtk.TreeView.SetCursor(Gtk.TreePath path, Gtk.TreeViewColumn focus_column, Boolean start_editing)
   at ULL.MainWindow.FillGameList()
   at ULL.MainWindow.Run()
   at ULL.GladeApp..ctor(Boolean args)
   at ULL.GladeApp.Main(System.String[] args)

```

all dependencies are satisfied
don't know what to try

i've to say also that this is the second time i compile and install ULL.Previously i've installed the program in the same way, and when started from console it worked..but always failed to find the game version in the Launcher folder..so i've uninstalled...now i'm trying again but that's what happened...
Your best bet is to delete everything inside the ~/.ULL folder (ie wipe the configuration).

When you add a game the game directory you need to enter is that of the game, not NCSoft's launcher (which is what you seem to have done this time).

---

### Post by darkice_ita on 2008-05-19
> **ajackson said:**
> Your best bet is to delete everything inside the ~/.ULL folder (ie wipe the configuration).

When you add a game the game directory you need to enter is that of the game, not NCSoft's launcher (which is what you seem to have done this time).

ok that worked

so my real problem is PlatNCLauncherSetup.exe that doesn't complete  the installation of the game...i've setted wine to win2k otherwise it hangs and i have to force the closure
the output is attached in the txt i've provided

---

### Post by ajackson on 2008-05-19
> **darkice_ita said:**
> so my real problem is PlatNCLauncherSetup.exe that doesn't complete  the installation of the game...i've setted wine to win2k otherwise it hangs and i have to force the closure
the output is attached in the txt i've provided
I'm not sure why you are running that. The last time I looked at DR the installation exe was DungeonRunnersSetup.exe (or something like that), is that what you have ran and it's done the PlayNCLauncherSetup itself or what?

Maybe one of the people who actually plays the game can give you more help.

---

### Post by darkice_ita on 2008-05-19
> **ajackson said:**
> I'm not sure why you are running that. The last time I looked at DR the installation exe was DungeonRunnersSetup.exe (or something like that), is that what you have ran and it's done the PlayNCLauncherSetup itself or what?

Maybe one of the people who actually plays the game can give you more help.


DungeonRunnersSetup.exe works, but as i can see it downloads and starts that PlayNCLauncherSetup.exe that i was talking about.After DungeonRunnersSetup.exe downloads and starts the launcher, every time i try to execute again it stops, and that's because it finds the launcher exe already downloaded in ~/%MYDOCS%/
So i start PlayNCLauncherSetup.exe directly...and there's the problem, because it seems to install something but actually i can't see any game folder

sorry if i'm not much clear

---

### Post by ajackson on 2008-05-19
> **darkice_ita said:**
> DungeonRunnersSetup.exe works, but as i can see it downloads and starts that PlayNCLauncherSetup.exe that i was talking about.After DungeonRunnersSetup.exe downloads and starts the launcher, every time i try to execute again it stops, and that's because it finds the launcher exe already downloaded in ~/%MYDOCS%/
So i start PlayNCLauncherSetup.exe directly...and there's the problem, because it seems to install something but actually i can't see any game folder

sorry if i'm not much clear
Any help I could give would be guesses as I don't play the game so I don't know how it's install works.

If you don't get any answers here the next best place is the appdb page for DR over at [http://www.winehq.org](http://www.winehq.org)

---

### Post by darkice_ita on 2008-05-19
ok, maybe it's the best way...anyway thank'you very much for the .ULL hint

and thanks for your work in developing that loader

---

### Post by kiepmad on 2008-06-05
Hi.

I guess NCsoft has started to distribute Dungeon Runners install files by the same client, they are using for updating... I've been looking on their ftp server and found some "setup files". I'll try out if these executables are the actual game.

[ftp://ftp.dungeonrunners.com/setup_data_files/](ftp://ftp.dungeonrunners.com/setup_data_files/)

What one could do would be to change ULL to be able to download the install as well...

Freaky bureaucratization over at NCsoft...


Edith says:

ok, it was the right file. I'm updating from 0.100 to 0.127 with ULL. Thanks alot for the patcher. :)

---

### Post by ajackson on 2008-06-06
> **kiepmad said:**
> What one could do would be to change ULL to be able to download the install as well...
With the latest version of ULL (well 0.6.1 onwards) if you create a directory for Dungeon Runners and add that as a game (ignoring it complaining about finding the local version file) you can use the repair option to install the game. I'd love to claim I implemented it that way by design but it would be a lie :)

---

### Post by kiepmad on 2008-06-07
Very nice, thank you for your effort! :)

The same is probably true for exteel( [ftp://ftp.exteel.com/client/](ftp://ftp.exteel.com/client/) ), but apparently it does not run with wine anyway.

---

### Post by brie on 2008-06-26
I'm having trouble getting dungeon runners going. I've gotten past the launcher issue, ULL works fine for me.
The game starts, then pops up an error about my graphics card not meeting the minimum specs (which it does, DR ran fine when I was running XP) and then hangs until I force quit.
It seems almost like the problem others in this thread were having (black screen) except that the game cursor does work.
I tried running with win98 compatibility mode, but that didn't fix it. 
Oh, and I'm running this on a Dell Inspiron E1405.

Here are some error logs:

DungeonRunners.log
```
06/26 20:13:32.304	9:	ResourceManager::initResources: BEGIN INIT

06/26 20:13:33.984	9:	ResourceManager::initResources Initializing sound...

06/26 20:13:33.984	9:	fmodSampleManager::Init Initializing sound in pkg mode...

06/26 20:13:33.984	9:	fmodSampleManager::Init ...done.

06/26 20:13:33.984	9:	ResourceManager::initResources ...done.

06/26 20:13:33.984	9:	ResourceManager::initResources: INIT COMPLETE

06/26 20:13:34.548	9:	D3D using VSPF pipeline: Vertex shader 1.1 detected, pixel shader 2.0 not detected

06/26 20:13:35.206	9:	Max: Simultaneous textures 8,  texture blend stages 8

06/26 20:13:35.206	9:	Max: Coordinate Sets 8

06/26 20:13:35.206	9:	Warning: Graphic device does not support UBYTE4, disabling hardware skinning.

06/26 20:13:35.206	9:	*** Compiling shader game/effects/2.0/SilhouetteBlit.fx

06/26 20:13:35.261	9:	dxCursorManager::create Loading Cursors...

06/26 20:13:35.265	9:	dxCursorManager::create Failed to find cursor holding.

06/26 20:13:35.265	9:	dxCursorManager::create Failed to find cursor invite.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir00.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir01.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir02.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir03.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir04.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir05.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir06.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir07.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir08.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir10.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir11.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir12.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir13.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir14.

06/26 20:13:35.266	9:	dxCursorManager::create Failed to find cursor dir15.

06/26 20:13:35.267	9:	dxCursorManager::create Failed to find cursor zone.

06/26 20:13:48.735	9:	FatalError: Your video card does not meet the minimum specification requirements to run the game. Please go to www.dungeonrunners.com for more information on the minimum specifications required to run the game.

06/26 20:13:48.735	15:	Created CrashLog: C:\logs\DungeonRunnersCrash-06262008-20-13-48-735-00.log.
```

DungeonRunnersCrash.log
```
[Application]

EXE=DungeonRunners.exe

Version=0.131

Process Id=8

Crashing Thread Id=9

World='NULL'

Time=06/26/2008-18:55:57:184

LogFileName=C:\logs\DungeonRunners.log



[Memory]

MemoryLoad=59

TotalPhysical=518492160

AvailablePhysical=209874944

TotalVirtual=2147352575

AvailableVirtual=2147287039



[Exception]

Code=C0000005



[Registers]

EAX=00111F50

EBX=00000000

ECX=00000000

EDX=00002E65

ESI=022381A8

EDI=0032F574

EIP=006A662F

ESP=0032F168

EBP=0032F58C



[Stack]

006A662F

006A654F

00000000



[CodeBytes]

006A65EF FF FF FF FF 8D 95 E8 FB FF FF 52 68 A0 11 80 00 

006A65FF E8 AC 01 00 00 83 C4 08 64 A1 2C 00 00 00 8B 00 

006A660F 8D 80 10 00 00 00 80 38 00 75 15 68 00 04 00 00 

006A661F 8D 8D E8 FB FF FF 51 50 E8 E4 7B 03 00 83 C4 0C 

006A662F C6 05 00 00 00 00 00 8B 4D F0 64 89 0D 00 00 00 

006A663F 00 5F 5E 5B 8B E5 5D C3 CC CC CC CC CC CC CC CC 

006A664F CC 55 8B EC 83 E4 F8 81 EC 18 05 00 00 56 57 33 

006A665F C0 C6 84 24 20 01 00 00 00 B9 FF 00 00 00 8D BC 

006A666F 24 21 01 00 00 F3 AB 8B 4D 08 66 AB AA 8D 45 0C 

006A667F 50 51 8D 94 24 28 01 00 00 68 00 04 00 00 52 E8 

006A668F E9 9A 03 00 83 C4 10 8D 44 24 08 50 FF 15 9C D1 

006A669F 77 00 8D 4C 24 08 51 8B D1 52 68 00 AF 84 00 FF 

006A66AF 15 A0 D1 77 00 33 C0 C6 44 24 18 00 B9 40 00 00 

006A66BF 00 8D 7C 24 19 F3 AB 66 AB AA 8D 44 24 18 68 04 

006A66CF 01 00 00 50 8D 44 24 10 E8 B4 01 00 00 8B F0 83 

006A66DF C4 08 85 F6 74 63 8D 4C 24 18 51 68 88 11 80 00 

006A66EF E8 BC 00 00 00 83 C4 08 8D 7C 24 08 E8 50 02 00 

006A66FF 00 68 54 11 80 00 56 E8 F0 8F 03 00 8D 84 24 28 

006A670F 01 00 00 50 68 50 11 80 00 56 E8 DD 8F 03 00 56 

006A671F E8 FA 8B 03 00 56 E8 43 8A 03 00 83 C4 1C 8D 8C 



[FatalErrorMessage]

Your video card does not meet the minimum specification requirements to run the game. Please go to www.dungeonrunners.com for more information on the minimum specifications required to run the game.

```

Just let me know if there's any more info that could be of use in figuring out my problem. :)

Edit: Wine version is 1.0

---

### Post by ardathwest on 2008-08-24
could someone please explain to me, step by step, what i need to do in order to install and run the game? and in simple terms, please.

i just installed wine, am downloading the dungeon runners data files, downloaded the ULL launcher, and have the gdi.dll's.

now i see that i need mono to compile the launcher using ./configure, make, make install. i also read that i need to add "deb [http://ppa.launchpad.net/ajackson-bcs/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ubuntu) hardy main" to my repository list (i use hardy). i don't understand this at all. i don't have any experience with wine and have little knowledge with ubuntu.

i guess what im trying to say is that i need complete, easy to understand instructions. thanks

---

### Post by Xfcn on 2008-09-23
Howdy. I just installed Dungeon Runners tonight, since it looked like a lot of fun and might be something I'd enjoy playing. I've gotten it to install and run just fine (as near as I can tell), but I have a really hard time with the graphics, because... well... take a look at the included screen shot.

That's my issue. I've got a Dell Inspiron E1505 running an ATI Radeon X1400 with 256 MB of GPU RAM and 1GB of RAM with 1.83 GHZ Core Duo processors. I have the ATI drivers installed and in use and ULL is installed. As near as I can tell I'm doing it right. My WINE is version 1.0 incidentally. Any ideas?

Any help is appreciated.

---

### Post by Xfcn on 2008-09-24
Ah. It's a feature called "X-Ray Vision" that's under some settings (not under graphics, under like controls or something). Once I turn that off, bingo-bango woot woot. It runs awesomely!

---

### Post by munch3 on 2009-03-03
Guys, I posted this like a year ago, and I totally forgot about it xD I got Xp and played DR there, and then I stopped cuz it got boring D:

but u guys rly made some effort, thanks :3
and I'm sure others will be grateful too :D
you made quite a discovery :P

---

### Post by munch3 on 2009-10-21
theyre cancelling DR, theres a big bomb in townston that will explode on january 1st 2010 and all servers will go down :(

---

