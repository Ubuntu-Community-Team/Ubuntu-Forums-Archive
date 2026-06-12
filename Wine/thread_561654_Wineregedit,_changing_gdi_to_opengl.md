---
title: "Wine/regedit, changing gdi to opengl"
date: 2007-09-27
forum: Wine
---

### Post by Tylerofl on 2007-09-27
I was told that this makes most games (starcraft, most importantly) run much better. I looked into regedit for the entry I was supposed to edit, but it isn't there. In HKEY_CURRENT_USER there isn't even a directory for Direct3D. Is there something I have to install, or some other setting I need to change?

Thanks.

---

### Post by cogadh on 2007-09-27
No, you need to create a "Direct3D" Key within the "Wine" Key found in HKEY_CURRENT_USER, then create a String Value named "DirectDrawRenderer" in the new Direct3D Key. After creating the string, change its value to "opengl". You can create Keys and String Values by either right-clicking in the right-hand pane or by right-clicking on the directory in the file tree in regedit.

EDIT - You might want to check out WineHQ's [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page for more info.

---

### Post by Tylerofl on 2007-09-28
Alright, done. That makes things faster for a second, but now after a few seconds, the mouse stops moving and Wine crashes, right at the game's main menu.

---

### Post by cogadh on 2007-09-28
What errors are output to the terminal when the game crashes?

---

### Post by Tylerofl on 2007-09-28
```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f4bc,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x130fa0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x125288)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ce70b45 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7ce70b45).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ce70b45 ESP:0033f5c4 EBP:0033fa4c EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000280 EBX:7cec93a0 ECX:02cd0020 EDX:02cd0020
 ESI:00000000 EDI:00000000
Stack dump:
0x0033f5c4:  00000000 00000000 00000000 00000000
0x0033f5d4:  0000000e 00000000 09818000 00000000
0x0033f5e4:  beef0201 00000a00 00000280 000001e0
0x0033f5f4:  00000000 00000009 00000008 00000000
0x0033f604:  00000003 00000000 00000000 00000000
0x0033f614:  00000000 00000000 02cd0020 00000000
Backtrace:
=>1 0x7ce70b45 d3dfmt_convert_surface+0x6b5() in wined3d (0x0033fa4c)
  2 0x7ce719e6 in wined3d (+0x719e6) (0x0033fadc)
  3 0x7ce78965 in wined3d (+0x78965) (0x0033fb3c)
  4 0x7cf02522 in ddraw (+0x32522) (0x0033fb6c)
  5 0x7cf0536a in ddraw (+0x3536a) (0x0033fb7c)
  6 0x1500d202 in storm (+0xd202) (0x7c24ca60)
  7 0x2a2a2a2a (0x2a2a2ac1)
  8 0x00000000 (0x00000000)
0x7ce70b45 d3dfmt_convert_surface+0x6b5 in wined3d: movzbl      0x0(%esi),%edx
Modules:
Module  Address                 Debug info      Name (100 modules)
PE        400000-  6be000       Deferred        starcraft
PE       2000000- 2011000       Deferred        local
PE      10000000-1001a000       Deferred        smackw32
PE      15000000-1503a000       Export          storm
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cb39000-7cb4e000       Deferred        midimap<elf>
  \-PE  7cb40000-7cb4e000       \               midimap
ELF     7cb4e000-7cb74000       Deferred        msacm32<elf>
  \-PE  7cb60000-7cb74000       \               msacm32
ELF     7cb74000-7cc39000       Deferred        libasound.so.2
ELF     7cc39000-7cc6f000       Deferred        winealsa<elf>
  \-PE  7cc40000-7cc6f000       \               winealsa
ELF     7cc6f000-7ccfd000       Deferred        winmm<elf>
  \-PE  7cc80000-7ccfd000       \               winmm
ELF     7ccfd000-7cd47000       Deferred        dsound<elf>
  \-PE  7cd10000-7cd47000       \               dsound
ELF     7cd51000-7cd8b000       Deferred        wineoss<elf>
  \-PE  7cd60000-7cd8b000       \               wineoss
ELF     7cdf0000-7cecb000       Export          wined3d<elf>
  \-PE  7ce00000-7cecb000       \               wined3d
ELF     7cecb000-7cf20000       Export          ddraw<elf>
  \-PE  7ced0000-7cf20000       \               ddraw
ELF     7d031000-7d082000       Deferred        libgcrypt.so.11
ELF     7d082000-7d097000       Deferred        libtasn1.so.3
ELF     7d097000-7d0c5000       Deferred        libcrypt.so.1
ELF     7d0c5000-7d135000       Deferred        libgnutls.so.13
ELF     7d135000-7d166000       Deferred        libcups.so.2
ELF     7d18a000-7d19d000       Deferred        libresolv.so.2
ELF     7d19d000-7d1bb000       Deferred        iphlpapi<elf>
  \-PE  7d1a0000-7d1bb000       \               iphlpapi
ELF     7d1bb000-7d214000       Deferred        rpcrt4<elf>
  \-PE  7d1d0000-7d214000       \               rpcrt4
ELF     7d214000-7d2b5000       Deferred        ole32<elf>
  \-PE  7d220000-7d2b5000       \               ole32
ELF     7d36a000-7d39c000       Deferred        uxtheme<elf>
  \-PE  7d370000-7d39c000       \               uxtheme
ELF     7d5e8000-7d600000       Deferred        msacm32<elf>
  \-PE  7d5f0000-7d600000       \               msacm32
ELF     7d600000-7d605000       Deferred        libxfixes.so.3
ELF     7d605000-7d60e000       Deferred        libxcursor.so.1
ELF     7d60e000-7d62b000       Deferred        imm32<elf>
  \-PE  7d620000-7d62b000       \               imm32
ELF     7d62b000-7d631000       Deferred        libxrandr.so.2
ELF     7d631000-7d639000       Deferred        libxrender.so.1
ELF     7d646000-7d64a000       Deferred        libgpg-error.so.0
ELF     7db70000-7db72000       Deferred        libnvidia-tls.so.1
ELF     7db72000-7e3f8000       Deferred        libglcore.so.1
ELF     7e3f8000-7e484000       Deferred        libgl.so.1
ELF     7e484000-7e489000       Deferred        libxdmcp.so.6
ELF     7e489000-7e48c000       Deferred        libxau.so.6
ELF     7e48c000-7e57d000       Deferred        libx11.so.6
ELF     7e57d000-7e58b000       Deferred        libxext.so.6
ELF     7e58b000-7e590000       Deferred        libxxf86vm.so.1
ELF     7e590000-7e5a8000       Deferred        libice.so.6
ELF     7e5a8000-7e5b1000       Deferred        libsm.so.6
ELF     7e5c2000-7e64c000       Deferred        winex11<elf>
  \-PE  7e5d0000-7e64c000       \               winex11
ELF     7e6dd000-7e6fd000       Deferred        libexpat.so.1
ELF     7e6fd000-7e728000       Deferred        libfontconfig.so.1
ELF     7e728000-7e73c000       Deferred        libz.so.1
ELF     7e73c000-7e7a7000       Deferred        libfreetype.so.6
ELF     7e7a7000-7e7bb000       Deferred        lz32<elf>
  \-PE  7e7b0000-7e7bb000       \               lz32
ELF     7e7bb000-7e7d5000       Deferred        version<elf>
  \-PE  7e7c0000-7e7d5000       \               version
ELF     7e7d5000-7e80a000       Deferred        winspool<elf>
  \-PE  7e7e0000-7e80a000       \               winspool
ELF     7e80a000-7e8c8000       Deferred        comctl32<elf>
  \-PE  7e810000-7e8c8000       \               comctl32
ELF     7e8c8000-7e921000       Deferred        shlwapi<elf>
  \-PE  7e8e0000-7e921000       \               shlwapi
ELF     7e921000-7ea24000       Deferred        shell32<elf>
  \-PE  7e930000-7ea24000       \               shell32
ELF     7ea24000-7eac5000       Deferred        comdlg32<elf>
  \-PE  7ea30000-7eac5000       \               comdlg32
ELF     7eac5000-7eb0d000       Deferred        advapi32<elf>
  \-PE  7ead0000-7eb0d000       \               advapi32
ELF     7eb0d000-7eb19000       Deferred        libgcc_s.so.1
ELF     7ec14000-7ecd5000       Deferred        gdi32<elf>
  \-PE  7ec30000-7ecd5000       \               gdi32
ELF     7ecd5000-7ee13000       Deferred        user32<elf>
  \-PE  7ecf0000-7ee13000       \               user32
ELF     7ee13000-7ee7a000       Deferred        msvcrt<elf>
  \-PE  7ee20000-7ee7a000       \               msvcrt
ELF     7ee7a000-7ee94000       Deferred        crtdll<elf>
  \-PE  7ee80000-7ee94000       \               crtdll
ELF     7efa6000-7efb1000       Deferred        libnss_files.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ca0000-b7ca9000       Deferred        libnss_compat.so.2
ELF     b7caa000-b7cae000       Deferred        libdl.so.2
ELF     b7cae000-b7def000       Deferred        libc.so.6
ELF     b7df0000-b7e07000       Deferred        libpthread.so.0
ELF     b7e18000-b7f2c000       Deferred        libwine.so.1
ELF     b7f2e000-b7f49000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000b 
        0000000d    0
        0000000c    0
00000008 (D) C:\Program Files\Starcraft\StarCraft.exe
        00000012    0
        00000011   15
        0000000f   15
        0000000a    1
        00000009    0 <==
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x125288)->((nil),00000008)
err:ntdll:RtlpWaitForCriticalSection section 0x7cd882dc "?" wait timed out in thread 0011, blocked by 0000, retrying (60 sec)

```

Phew, what a mouthful!

---

### Post by cogadh on 2007-09-28
Hmmm, should have asked this from the start; what version of Wine are you using?

---

### Post by Tylerofl on 2007-09-28
The latest version from Wine's repository, 0.9.45

---

### Post by cogadh on 2007-09-28
That's what I thought. There appears to be a bug or regression in 0.9.45 that is causing graphics-related crashes like this in some games. Try downgrading to 0.9.44 and run the game again. You will need to uninstall Wine, then download and install the archived .deb package from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Tylerofl on 2007-09-28
Hm, now it's giving me dsound errors. I think I'll just wait for them to fix the regression, I don't want to re-do everything, especially since I downloaded like three games in Steam. Thanks for the help, though!

---

### Post by wolfger on 2007-09-28
> **cogadh said:**
> There appears to be a bug or regression in 0.9.45 that is causing graphics-related crashes like this in some games.[/url]
Is there a launchpad or other bug filed for this, so we can track progress?

---

### Post by cogadh on 2007-09-28
There wouldn't be a Launchpad bug, Wine has it's own Bugzilla. I have not filed a bug report myself (still doing some testing), but if anyone else has, you would find it here:
[http://bugs.winehq.org/](http://bugs.winehq.org/)

EDIT - They just released a new Wine version (0.9.46) and so far, it appears to still have the same bug as 0.9.45.

---

