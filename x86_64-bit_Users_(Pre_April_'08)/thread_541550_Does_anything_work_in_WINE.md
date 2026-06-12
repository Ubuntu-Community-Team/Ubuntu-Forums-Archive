---
title: "Does anything work in WINE?"
date: 2007-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by SiouxerBrewer on 2007-09-02
I am relatively new to Linux and am still figuring most of it out.  I have a basic understanding of how things work but I just can't get some programs to run in WINE.  One program in particular (ProMash) is supposed to work in WINE and others have gotten it to work, but for some reason I can't yet.  When I try to start ProMash (in a terminal or by launcher) it says "Bad or missing system file!"  Here is what was on the terminal:

[email]ubuntu@ubuntu:~/.wine[/email]/drive_c/Program Files/ProMash$ wine ProMash.exe
wine: Unhandled page fault on read access to 0x0000000c at address 0x63def3 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000000c in 32-bit code (0x0063def3).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0063def3 ESP:0033edb4 EBP:0033edc8 EFLAGS:00010286(   - 00      -RISP1)
 EAX:00000000 EBX:7ee89c84 ECX:ffffffff EDX:00000004
 ESI:00000000 EDI:ffffffff
Stack dump:
0x0033edb4:  00010024 00010024 005c7ea3 00000000
0x0033edc4:  00000000 0033f054 004c8234 00010024
0x0033edd4:  7ffdc000 7bc8553c 00000000 00000000
0x0033ede4:  00000000 00000000 00000002 0033ee08
0x0033edf4:  00000000 7ed88d0c 00195f40 00195fc8
0x0033ee04:  0033ee08 00000000 00000000 00195ff8
Backtrace:
=>1 0x0063def3 in promash (+0x23def3) (0x0033edc8)
  2 0x004c8234 in promash (+0xc8234) (0x0033f054)
  3 0x7ee667fa WINPROC_wrapper+0x1a() in user32 (0x0033f084)
  4 0x7ee66f0e in user32 (+0xa6f0e) (0x0033f0c4)
  5 0x7ee6d5a3 WINPROC_call_window+0xd3() in user32 (0x0033f104)
  6 0x7ee3282c in user32 (+0x7282c) (0x0033f174)
  7 0x7ee36472 in user32 (+0x76472) (0x0033f1d4)
  8 0x7ee3688e SendMessageA+0x4e() in user32 (0x0033f214)
  9 0x7e755d17 X11DRV_CreateWindow+0xb77() in winex11 (0x0033f3d4)
  10 0x7ee603c3 in user32 (+0xa03c3) (0x0033f634)
  11 0x7ee61c72 CreateWindowExA+0x102() in user32 (0x0033f7b4)
  12 0x0052a1d4 in promash (+0x12a1d4) (0x0033fe7c)
  13 0x0063f523 in promash (+0x23f523) (0x0033ff08)
  14 0x7b87546e in kernel32 (+0x5546e) (0x0033ffe8)
  15 0xf7e2b9e7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0063def3: movl        0xc(%esi),%eax
Modules:
Module  Address                 Debug info      Name (61 modules)
PE        400000-  7e6000       Export          promash
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d593000-7d5c5000       Deferred        uxtheme<elf>
  \-PE  7d5a0000-7d5c5000       \               uxtheme
ELF     7d86c000-7d871000       Deferred        libxfixes.so.3
ELF     7d871000-7d87a000       Deferred        libxcursor.so.1
ELF     7d87a000-7d897000       Deferred        imm32<elf>
  \-PE  7d880000-7d897000       \               imm32
ELF     7d897000-7d89f000       Deferred        libxrender.so.1
ELF     7d89f000-7d8a2000       Deferred        libxinerama.so.1
ELF     7dbdd000-7dbdf000       Deferred        libnvidia-tls.so.1
ELF     7dbdf000-7e551000       Deferred        libglcore.so.1
ELF     7e551000-7e5e5000       Deferred        libgl.so.1
ELF     7e5e5000-7e5ea000       Deferred        libxdmcp.so.6
ELF     7e5ea000-7e6db000       Deferred        libx11.so.6
ELF     7e6db000-7e6e9000       Deferred        libxext.so.6
ELF     7e6ea000-7e6f0000       Deferred        libxrandr.so.2
ELF     7e6fa000-7e78a000       Export          winex11<elf>
  \-PE  7e710000-7e78a000       \               winex11
ELF     7e89f000-7e8bf000       Deferred        libexpat.so.1
ELF     7e8bf000-7e8ea000       Deferred        libfontconfig.so.1
ELF     7e8ea000-7e8fe000       Deferred        libz.so.1
ELF     7e8fe000-7e968000       Deferred        libfreetype.so.6
ELF     7e968000-7e97b000       Deferred        libresolv.so.2
ELF     7e97b000-7e999000       Deferred        iphlpapi<elf>
  \-PE  7e980000-7e999000       \               iphlpapi
ELF     7e999000-7e9f2000       Deferred        rpcrt4<elf>
  \-PE  7e9b0000-7e9f2000       \               rpcrt4
ELF     7e9f2000-7ea91000       Deferred        ole32<elf>
  \-PE  7ea00000-7ea91000       \               ole32
ELF     7ea91000-7eac4000       Deferred        winspool<elf>
  \-PE  7eaa0000-7eac4000       \               winspool
ELF     7eac4000-7eb1d000       Deferred        shlwapi<elf>
  \-PE  7ead0000-7eb1d000       \               shlwapi
ELF     7eb1d000-7ec20000       Deferred        shell32<elf>
  \-PE  7eb30000-7ec20000       \               shell32
ELF     7ec20000-7ecc1000       Deferred        comdlg32<elf>
  \-PE  7ec30000-7ecc1000       \               comdlg32
ELF     7ecc1000-7ed09000       Deferred        advapi32<elf>
  \-PE  7ecd0000-7ed09000       \               advapi32
ELF     7ed09000-7eda1000       Deferred        gdi32<elf>
  \-PE  7ed20000-7eda1000       \               gdi32
ELF     7eda1000-7eedf000       Export          user32<elf>
  \-PE  7edc0000-7eedf000       \               user32
ELF     7eedf000-7ef9c000       Deferred        comctl32<elf>
  \-PE  7eef0000-7ef9c000       \               comctl32
ELF     7ef9c000-7efa7000       Deferred        libnss_files.so.2
ELF     7efa7000-7efb1000       Deferred        libnss_nis.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     f7cb1000-f7cb4000       Deferred        libxau.so.6
ELF     f7cb6000-f7cba000       Deferred        libdl.so.2
ELF     f7cba000-f7dfb000       Deferred        libc.so.6
ELF     f7dfc000-f7e13000       Deferred        libpthread.so.0
ELF     f7e24000-f7f38000       Export          libwine.so.1
ELF     f7f3a000-f7f58000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000008 (D) C:\Program Files\ProMash\ProMash.exe
        00000009    0 <==
[email]ubuntu@ubuntu:~/.wine[/email]/drive_c/Program Files/ProMash$ 

Is there something I'm missing or will this program not work?  I also tried installing IL2 Forgotten Battles and that doesn't start either.  I will appreciate any help.

-James

---

### Post by stmiller on 2007-09-02
Depending on the program, sometimes you have to copy over windows .dll files from a Windows XP system. Just check out the WINE program database and read install notes for each program. 

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Photoshop 7.0 works 100%, for example:

[http://appdb.winehq.org/appview.php?iVersionId=1336](http://appdb.winehq.org/appview.php?iVersionId=1336)

So it all depends on the program.

---

### Post by buzzmandt on 2007-09-03
Did you install from the ubunut directions at winehq
and did you run winecfg after you installed it (sets up drives and such)

I have gotten diablo 2, silkroad online, teamspeak windows version, ww2 online (not well but runs), axis and allies 1998 version, .......that's all i can think of right the moment....to work in wine

---

### Post by ekravche on 2007-09-03
I have diablo 2 running in wine. It crashes maybe once a month...

---

### Post by justin whitaker on 2007-09-03
Dreamweaver, Flash, Office XP, Steam, World of Warcraft, Guild Wars....and most importantly, uTorrent! :)

Some things run. Most of the time, you get a whole lot of nothing. All I can say is: it is 1000x better than before.

---

### Post by SiouxerBrewer on 2007-09-03
> **buzzmandt said:**
> Did you install from the ubunut directions at winehq
and did you run winecfg after you installed it (sets up drives and such)


I followed a guide on this forum step by step as far as installing wine on a 64bit setup in Feisty.  IES4Linux works but I'm not sure if that is a WINE program or not.  I read about some people who got Promash to run on an older version of WINE that is not supported for Feisty.  I'll probably be stuck with a dual boot system and continue to use W*****s :roll:  I'll keep trying for now though.  Thank you for the replies.

---

