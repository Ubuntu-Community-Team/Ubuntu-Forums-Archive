---
title: "GTA San Andreas installs but will not start with wine"
date: 2007-08-31
forum: Wine
---

### Post by djrobthaman on 2007-08-31
Hi,

I got gta to install perfectly.  But for some reason it is not listed in the gnome menu drop down for wine programs even though the files are in the "program files" folder in the hidden wine folder and when I try to run the game it doesn't run 

And when I try to run it through the terminal I get the output I pasted below.

Anybody know how I can get it working?

Thanks

```

douglas@douglas-desktop:~$ wine '/home/douglas/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas/gta_sa.exe' 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
wine: Unhandled page fault on read access to 0x00000000 at address 0x746929 (thread 003a), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00746929).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00746929 ESP:0178f3fc EBP:0178f5ac EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:c0000034 EDX:00000000
 ESI:00000000 EDI:7b864fe0
Stack dump:
0x0178f3fc:  00748732 7b8b0888 01000002 00000000
0x0178f40c:  00828cb3 00856c80 008a5a08 7b8b0888
0x0178f41c:  ffffffff 0178f408 00400000 7b8b0888
0x0178f42c:  00000002 0178f47c 0178f454 7b864f9f
0x0178f43c:  00000002 00000000 0178f47c 7b8b0888
0x0178f44c:  00000000 7b864fe0 0178f484 7b86500c
Backtrace:
=>1 0x00746929 in gta_sa (+0x346929) (0x0178f5ac)
  2 0x7b874cce in kernel32 (+0x54cce) (0x0178f5f8)
  3 0x00cbe38b in gta_sa (+0x8be38b) (0x0178fe2c)
  4 0x0115c3af in gta_sa (+0xd5c3af) (0x0178ff08)
  5 0x7b874cce in kernel32 (+0x54cce) (0x0178ffe8)
  6 0xb7de59a7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00746929: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (78 modules)
PE        230000-  239000       Deferred        ogg
PE        240000-  348000       Deferred        vorbis
PE        350000-  380000       Deferred        eax
PE        400000- 1577000       Export          gta_sa
PE      10000000-10011000       Deferred        vorbisfile
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e260000-7e292000       Deferred        uxtheme<elf>
  \-PE  7e270000-7e292000       \               uxtheme
ELF     7e292000-7e350000       Deferred        comctl32<elf>
  \-PE  7e2a0000-7e350000       \               comctl32
ELF     7e350000-7e453000       Deferred        shell32<elf>
  \-PE  7e360000-7e453000       \               shell32
ELF     7e453000-7e4ac000       Deferred        shlwapi<elf>
  \-PE  7e460000-7e4ac000       \               shlwapi
ELF     7e4ac000-7e4c1000       Deferred        midimap<elf>
  \-PE  7e4b0000-7e4c1000       \               midimap
ELF     7e4c1000-7e4e7000       Deferred        msacm32<elf>
  \-PE  7e4d0000-7e4e7000       \               msacm32
ELF     7e4e7000-7e4ff000       Deferred        msacm32<elf>
  \-PE  7e4f0000-7e4ff000       \               msacm32
ELF     7e4ff000-7e539000       Deferred        wineoss<elf>
  \-PE  7e510000-7e539000       \               wineoss
ELF     7e539000-7e53e000       Deferred        libxfixes.so.3
ELF     7e53e000-7e55b000       Deferred        imm32<elf>
  \-PE  7e550000-7e55b000       \               imm32
ELF     7e55b000-7e563000       Deferred        libxrender.so.1
ELF     7e572000-7e612000       Deferred        libgl.so.1
ELF     7e612000-7e617000       Deferred        libxdmcp.so.6
ELF     7e617000-7e61a000       Deferred        libxau.so.6
ELF     7e61a000-7e70b000       Deferred        libx11.so.6
ELF     7e70b000-7e719000       Deferred        libxext.so.6
ELF     7e719000-7e71e000       Deferred        libxxf86vm.so.1
ELF     7e71e000-7e736000       Deferred        libice.so.6
ELF     7e736000-7e73f000       Deferred        libsm.so.6
ELF     7e73f000-7e748000       Deferred        libxcursor.so.1
ELF     7e748000-7e74e000       Deferred        libxrandr.so.2
ELF     7e74e000-7e7d8000       Deferred        winex11<elf>
  \-PE  7e760000-7e7d8000       \               winex11
ELF     7e860000-7e880000       Deferred        libexpat.so.1
ELF     7e880000-7e8ab000       Deferred        libfontconfig.so.1
ELF     7e8ab000-7e8bf000       Deferred        libz.so.1
ELF     7e8bf000-7e92f000       Deferred        libfreetype.so.6
ELF     7e92f000-7e943000       Deferred        lz32<elf>
  \-PE  7e940000-7e943000       \               lz32
ELF     7e943000-7e95d000       Deferred        version<elf>
  \-PE  7e950000-7e95d000       \               version
ELF     7e95d000-7e9b6000       Deferred        rpcrt4<elf>
  \-PE  7e970000-7e9b6000       \               rpcrt4
ELF     7e9b6000-7ea55000       Deferred        ole32<elf>
  \-PE  7e9d0000-7ea55000       \               ole32
ELF     7ea55000-7ea68000       Deferred        libresolv.so.2
ELF     7ea68000-7ea86000       Deferred        iphlpapi<elf>
  \-PE  7ea70000-7ea86000       \               iphlpapi
ELF     7ea86000-7eab3000       Deferred        ws2_32<elf>
  \-PE  7ea90000-7eab3000       \               ws2_32
ELF     7eab3000-7eafb000       Deferred        advapi32<elf>
  \-PE  7eac0000-7eafb000       \               advapi32
ELF     7eafb000-7eb07000       Deferred        libgcc_s.so.1
ELF     7ec00000-7ecc0000       Deferred        gdi32<elf>
  \-PE  7ec20000-7ecc0000       \               gdi32
ELF     7ecc0000-7edfe000       Deferred        user32<elf>
  \-PE  7ece0000-7edfe000       \               user32
ELF     7edfe000-7ee8c000       Deferred        winmm<elf>
  \-PE  7ee10000-7ee8c000       \               winmm
ELF     7ef9e000-7efa9000       Deferred        libnss_files.so.2
ELF     7efa9000-7efb3000       Deferred        libnss_nis.so.2
ELF     7efb3000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff1000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c72000-b7c76000       Deferred        libdl.so.2
ELF     b7c76000-b7db7000       Deferred        libc.so.6
ELF     b7db8000-b7dcf000       Deferred        libpthread.so.0
ELF     b7dde000-b7ef2000       Export          libwine.so.1
ELF     b7ef4000-b7f0f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000039 (D) C:\Program Files\Rockstar Games\GTA San Andreas\gta_sa.exe
        0000003a    0 <==
00000013 
        00000014    0
0000000d 
        00000011    0
        0000000e    0

```

---

### Post by splintercellguy on 2007-09-01
What Wine version are you using? Are you using Wine's BudgetDedicated repo? [http://appdb.winehq.org/appview.php?iVersionId=3780](http://appdb.winehq.org/appview.php?iVersionId=3780)

---

### Post by DoktorSeven on 2007-09-01
1) "Xlib:  extension "XFree86-DRI" missing on display ":1.0"." sounds like missing 3d drivers.  Make sure you have 3d enabled with **glxinfo | grep direct** (should return "direct rendering: Yes").

2) Always best to run from the directory it's installed in: 
[b]cd /home/douglas/.wine/drive_c/Program\ Files/Rockstar\ Games/GTA\ San\ Andreas/
wine gta_sa.exe[/b]

(Also, I've found it best to create a symbolic link to .wine/drive_c to make it easy to get to:
[b]cd ~
ln -s ~/.wine/drive_c winedrive[/b]
)

---

### Post by djrobthaman on 2007-09-02
@splintercellguy: Yes, I'm using that repo, and according to synaptic I'm using 0.9.44~winehq0~ubuntu~7.04-1

@doktorseven: I have 3d enabled.  I'm using compiz fusion as we speak actually.  After reading your post, though, I logged in to the regular gnome session without the xgl server running and still had the same problems (except of course the first line of output about 3d rendering didn't show up).  I will try launching it from within the folder though and see what happens.

---

