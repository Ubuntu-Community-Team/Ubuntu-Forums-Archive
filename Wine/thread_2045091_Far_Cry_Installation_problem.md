---
title: "Far Cry Installation problem"
date: 2012-08-20
forum: Wine
---

### Post by walkerna22 on 2012-08-20
Okay, so after recently starting to use Ubuntu I decided I'd like to try running far cry on it.  Problem is, it turns out I lost one of the install disks.  I decided to just download an iso and install it that way.  However, I'm still having problems getting it to install. Here's what I did:
1.) After downloading the iso, I mounted it with the Archive Mounter
2.) I then found the setup.exe file, then opened it with WINE, but nothing seems to happen when I do that.  
3.) I tried using WINE to open other .exe's in the iso, and either nothing happens when I run it, or I get a window with this message (I get it when I try to run FarCry.exe through WINE): Unhandled exception: page fault on read access to 0x00acb1be in 32-bit code (0xb75f6bd0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b75f6bd0 ESP:0033e0ac EBP:0033e12c EFLAGS:00010206(  R- --  I   - -P- )
 EAX:00acb1b6 EBX:7ed22ff4 ECX:00000280 EDX:00b1ad80
 ESI:00b1ad80 EDI:00acb1b6
Stack dump:
0x0033e0ac:  7ed22ff4 7ecba0bb 00b1ad80 00acb1b6
0x0033e0bc:  00000280 90909090 51ec8b55 07770b70
0x0033e0cc:  0374d287 eb90c087 03f37003 8d084d8a
0x0033e0dc:  c180fc45 0033e21c 00000000 6608c483
0x0033e0ec:  3475c085 db8b067b fffffd80 fffffd80
0x0033e0fc:  7b900174 08c087f1 07740b73 0377ed87
Backtrace:
=>0 0xb75f6bd0 in libc.so.6 (+0x133bd0) (0x0033e12c)
  1 0x7ecba0bb in gdi32 (+0x2a0ba) (0x0033e12c)
  2 0x7eca9333 in gdi32 (+0x19332) (0x0033e1ac)
  3 0x7eca9c0c in gdi32 (+0x19c0b) (0x0033e56c)
  4 0x7eca6414 in gdi32 (+0x16413) (0x0033eacc)
  5 0x7eca69a7 StretchDIBits+0x116() in gdi32 (0x0033ef7c)
  6 0x7eb6fcdd LoadImageW+0x65c() in user32 (0x0033f08c)
  7 0x7eb70296 LoadImageA+0x125() in user32 (0x0033f17c)
  8 0x10021c23 in ~de6cc8.tmp (+0x21c22) (0x0033f7b4)
  9 0x1002ea4b in ~de6cc8.tmp (+0x2ea4a) (0x0033f930)
  10 0x1002ed3f in ~de6cc8.tmp (+0x2ed3e) (0x0033f950)
  11 0x1002f2f5 in ~de6cc8.tmp (+0x2f2f4) (0x0033f97c)
  12 0x6671c89d in ~df394b.tmp (+0x1c89c) (0x0033f99c)
  13 0x6671c38e in ~df394b.tmp (+0x1c38d) (0x0033f9ec)
  14 0x66703683 in ~df394b.tmp (+0x3682) (0x0033fb3c)
  15 0x3700f435 in farcry (+0xf434) (0x3700f009)
0xb75f6bd0: repe movq    0x0(%eax),%mm0
Modules:
Module    Address            Debug info    Name (57 modules)
PE    10000000-1004d000    Export          ~de6cc8.tmp
PE    37000000-37013000    Export          farcry
PE    66700000-6686b000    Export          ~df394b.tmp
ELF    7b800000-7ba15000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e5c0000-7e5cb000    Deferred        libxcursor.so.1
ELF    7e64e000-7e678000    Deferred        libexpat.so.1
ELF    7e678000-7e6ac000    Deferred        libfontconfig.so.1
ELF    7e6ac000-7e6bc000    Deferred        libxi.so.6
ELF    7e6bc000-7e6c0000    Deferred        libxcomposite.so.1
ELF    7e6c0000-7e6c9000    Deferred        libxrandr.so.2
ELF    7e6c9000-7e6d3000    Deferred        libxrender.so.1
ELF    7e6d3000-7e6d9000    Deferred        libxxf86vm.so.1
ELF    7e6d9000-7e6dd000    Deferred        libxinerama.so.1
ELF    7e6dd000-7e6ff000    Deferred        imm32<elf>
  \-PE    7e6e0000-7e6ff000    \               imm32
ELF    7e6ff000-7e706000    Deferred        libxdmcp.so.6
ELF    7e706000-7e727000    Deferred        libxcb.so.1
ELF    7e727000-7e741000    Deferred        libice.so.6
ELF    7e741000-7e875000    Deferred        libx11.so.6
ELF    7e875000-7e887000    Deferred        libxext.so.6
ELF    7e88b000-7e891000    Deferred        libxfixes.so.3
ELF    7e89a000-7e92d000    Deferred        winex11<elf>
  \-PE    7e8a0000-7e92d000    \               winex11
ELF    7e92d000-7e943000    Deferred        libz.so.1
ELF    7e943000-7e9dd000    Deferred        libfreetype.so.6
ELF    7e9dd000-7ea6a000    Deferred        msvcrt<elf>
  \-PE    7e9f0000-7ea6a000    \               msvcrt
ELF    7ea6a000-7ea87000    Deferred        msvcr71<elf>
  \-PE    7ea70000-7ea87000    \               msvcr71
ELF    7ea87000-7eb24000    Deferred        msvcp71<elf>
  \-PE    7ea90000-7eb24000    \               msvcp71
ELF    7eb24000-7eb3d000    Deferred        version<elf>
  \-PE    7eb30000-7eb3d000    \               version
ELF    7eb3d000-7ec7d000    Dwarf           user32<elf>
  \-PE    7eb50000-7ec7d000    \               user32
ELF    7ec7d000-7ed3a000    Dwarf           gdi32<elf>
  \-PE    7ec90000-7ed3a000    \               gdi32
ELF    7ed3a000-7ed9a000    Deferred        advapi32<elf>
  \-PE    7ed50000-7ed9a000    \               advapi32
ELF    7ed9a000-7eda7000    Deferred        libnss_files.so.2
ELF    7eda7000-7edc1000    Deferred        libnsl.so.1
ELF    7efc1000-7efed000    Deferred        libm.so.6
ELF    7efef000-7eff3000    Deferred        libxau.so.6
ELF    7eff3000-7eff9000    Deferred        libuuid.so.1
ELF    b74b1000-b74bd000    Deferred        libnss_nis.so.2
ELF    b74be000-b74c3000    Deferred        libdl.so.2
ELF    b74c3000-b7668000    Dwarf           libc.so.6
ELF    b7669000-b7684000    Deferred        libpthread.so.0
ELF    b7684000-b768d000    Deferred        libsm.so.6
ELF    b768d000-b7696000    Deferred        libnss_compat.so.2
ELF    b7697000-b77d9000    Dwarf           libwine.so.1
ELF    b77db000-b77fd000    Deferred        ld-linux.so.2
ELF    b77fd000-b77fe000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000025    0
    00000024    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001a    0
    00000019    0
    00000014    0
    00000013    0
0000001b plugplay.exe
    00000020    0
    0000001d    0
    0000001c    0
00000021 winedevice.exe
    00000026    0
    00000023    0
    00000022    0
00000027 explorer.exe
    00000028    0
0000002b Steam.exe
    00000017    0
    00000067    0
    00000066    0
    00000065    1
    00000064    1
    0000005a    0
    00000059    0
    00000057    0
    00000056    0
    00000054    0
    00000053    1
    00000052    1
    00000051    0
    00000050    0
    0000004f    0
    0000004e    0
    0000004d    0
    0000004c    0
    0000004b    0
    0000004a    0
    00000049    0
    00000048    0
    00000042    0
    0000002f    0
    0000000d    0
    00000009    0
    00000029    0
    0000002a    0
    0000000b    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000041    0
    00000040    0
    0000003f    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
    00000036    0
    00000035    0
    00000034    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0
    0000002e    0
    0000002d    0
    0000002c    0
0000007a (D) Z:\home\nathan\.gvfs\dev-frcy.iso\FarCry.exe
    00000090    0 <==
0000005d ~e5.0001
    00000096    0
    0000006b    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-29-generic-pae

After I got this, I had absolutely no idea what to do, and I'd appreciate it if any of you had the slightest idea of how to fix it.

Thanks

---

