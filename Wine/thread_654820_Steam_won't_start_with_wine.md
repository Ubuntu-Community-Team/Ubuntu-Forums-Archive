---
title: "Steam won't start with wine"
date: 2007-12-31
forum: Wine
---

### Post by swedishlf on 2007-12-31
Well I've had steam running under ubuntu before, but I believe a wine upgrade may have killed it.

SteamInstall.msi runs fine and completes, but when I try to run steam I get:

```
$ wine steam
fixme:seh:check_no_exec No-exec fault triggered at 0x47d2d0, enabling work-around
wine: Unhandled page fault on execute access to 0x0047d2d0 at address 0x47d2d0 (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x0047d2d0 in 32-bit code (0x0047d2d0).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0047d2d0 ESP:0034ff0c EBP:0034ffe8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7b8b0888 ECX:00000000 EDX:00000000
 ESI:0047d2d0 EDI:7ffdf000
Stack dump:
0x0034ff0c:  7b87547e 7ffdf000 00000000 00000000
0x0034ff1c:  00000000 00000000 00000000 00000000
0x0034ff2c:  ffffffff 7b82f030 7b844150 7b8b0888
0x0034ff3c:  7ffdc000 00001000 0034ffe8 a82d01ca
0x0034ff4c:  cf74c13d 00000001 10012a03 00000000
0x0034ff5c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x0047d2d0 EntryPoint() in steam (0x0034ffe8)
  2 0xf7eb8a17 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0047d2d0 EntryPoint in steam: pushl   $0x60
Modules:
Module  Address                 Debug info      Name (73 modules)
PE        400000-  53a000       Export          steam
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d72f000-7d761000       Deferred        uxtheme<elf>
  \-PE  7d740000-7d761000       \               uxtheme
ELF     7d761000-7d766000       Deferred        libxfixes.so.3
ELF     7d766000-7d76f000       Deferred        libxcursor.so.1
ELF     7d76f000-7d78c000       Deferred        imm32<elf>
  \-PE  7d780000-7d78c000       \               imm32
ELF     7d78c000-7d792000       Deferred        libxrandr.so.2
ELF     7d792000-7d79a000       Deferred        libxrender.so.1
ELF     7d79a000-7d79d000       Deferred        libxinerama.so.1
ELF     7d835000-7d837000       Deferred        libnvidia-tls.so.1
ELF     7d837000-7e2ea000       Deferred        libglcore.so.1
ELF     7e2ea000-7e38e000       Deferred        libgl.so.1
ELF     7e38e000-7e393000       Deferred        libxdmcp.so.6
ELF     7e393000-7e484000       Deferred        libx11.so.6
ELF     7e484000-7e492000       Deferred        libxext.so.6
ELF     7e4ad000-7e53c000       Deferred        winex11<elf>
  \-PE  7e4c0000-7e53c000       \               winex11
ELF     7e621000-7e641000       Deferred        libexpat.so.1
ELF     7e641000-7e66c000       Deferred        libfontconfig.so.1
ELF     7e66d000-7e670000       Deferred        libxau.so.6
ELF     7e687000-7e69c000       Deferred        libz.so.1
ELF     7e69c000-7e70c000       Deferred        libfreetype.so.6
ELF     7e727000-7e73b000       Deferred        oleacc<elf>
  \-PE  7e730000-7e73b000       \               oleacc
ELF     7e73b000-7e74f000       Deferred        lz32<elf>
  \-PE  7e740000-7e74f000       \               lz32
ELF     7e74f000-7e769000       Deferred        version<elf>
  \-PE  7e760000-7e769000       \               version
ELF     7e769000-7e78b000       Deferred        oledlg<elf>
  \-PE  7e770000-7e78b000       \               oledlg
ELF     7e78b000-7e828000       Deferred        oleaut32<elf>
  \-PE  7e7a0000-7e828000       \               oleaut32
ELF     7e828000-7e881000       Deferred        rpcrt4<elf>
  \-PE  7e830000-7e881000       \               rpcrt4
ELF     7e881000-7e922000       Deferred        ole32<elf>
  \-PE  7e890000-7e922000       \               ole32
ELF     7e922000-7e9e0000       Deferred        comctl32<elf>
  \-PE  7e930000-7e9e0000       \               comctl32
ELF     7e9e0000-7ea39000       Deferred        shlwapi<elf>
  \-PE  7e9f0000-7ea39000       \               shlwapi
ELF     7ea39000-7eb3c000       Deferred        shell32<elf>
  \-PE  7ea50000-7eb3c000       \               shell32
ELF     7eb3c000-7ebdd000       Deferred        comdlg32<elf>
  \-PE  7eb40000-7ebdd000       \               comdlg32
ELF     7ebdd000-7ec11000       Deferred        winspool<elf>
  \-PE  7ebf0000-7ec11000       \               winspool
ELF     7ec11000-7ecac000       Deferred        gdi32<elf>
  \-PE  7ec20000-7ecac000       \               gdi32
ELF     7ecac000-7edea000       Deferred        user32<elf>
  \-PE  7ecd0000-7edea000       \               user32
ELF     7edea000-7ee33000       Deferred        advapi32<elf>
  \-PE  7ee00000-7ee33000       \               advapi32
ELF     7ee33000-7ee51000       Deferred        iphlpapi<elf>
  \-PE  7ee40000-7ee51000       \               iphlpapi
ELF     7ee51000-7ee7e000       Deferred        ws2_32<elf>
  \-PE  7ee60000-7ee7e000       \               ws2_32
ELF     7ef9d000-7efa8000       Deferred        libnss_files.so.2
ELF     7efa8000-7efc0000       Deferred        libnsl.so.1
ELF     7efc0000-7efe5000       Deferred        libm.so.6
ELF     7efe9000-7effc000       Deferred        libresolv.so.2
ELF     f7d24000-f7d2e000       Deferred        libnss_nis.so.2
ELF     f7d2f000-f7d33000       Deferred        libdl.so.2
ELF     f7d33000-f7e7d000       Deferred        libc.so.6
ELF     f7e7e000-f7e96000       Deferred        libpthread.so.0
ELF     f7e97000-f7ea0000       Deferred        libnss_compat.so.2
ELF     f7eb1000-f7fc5000       Dwarf           libwine.so.1
ELF     f7fc7000-f7fe5000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) F:\media\winedrive\Program Files\Steam\steam.exe
        00000009    0 <==
fixme:seh:check_no_exec No-exec fault triggered at 0x47d2d0, enabling work-around

```$

very similar error messages happen with some other programs.  Some programs (seam to be apps with no 3d acceleration) run just fine though.

Using Gutsy AMD64, wine 0.9.46 installed from apt-get, and NVIDIA 169.07 drivers.

As a side note, some of the programs will crash X when first run, but subsequent attempts give similar error messages to the above.  Winecfg will also occaisionally crash X.  I've attempted reinstalling wine from scratch as well, same problems.

Any hints?

---

### Post by swedishlf on 2008-01-01
Updated to wine 0.9.52 with no results.  I've also considered attempting to build wine from source, but I get these errors:

```
configure: WARNING: No OpenGL library found on this system.
Wine will be built without OpenGL or Direct3D support.

configure: WARNING: FreeType development files not found.
Fonts will not be built. Dialog text may be invisible or unaligned.

```

not too worried about the fonts, but glxgears runs just fine so I assume OpenGL is  working.

Any hints there?

***Edit***

Using the instructions found [here]("http://wiki.winehq.org/WineOn64bit") I managed to compile wine from source with no problems.  However I still am unable to run any of the more serious applications.  It seems that I can run anything that doesn't require opengl or d3d.  What's odd is the programs won't run regardless of weather they use 3d on initialization.  Still looking for hints.

---

### Post by kwiksand on 2008-10-02
Any updates on this, did you manage to get Steam working?

---

### Post by Dark9204 on 2008-10-03
Steam and steam games runs just fine.

Upgrade to Ubuntu 8.04 and wine 1.1.5!

I don't get why people post these threads when they are using outdated software!

---

### Post by Dark9204 on 2008-10-04
To install steam, move it to your home directory and run in terminal: wine start SteamInstall.msi

---

