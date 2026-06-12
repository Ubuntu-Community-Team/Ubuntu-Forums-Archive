---
title: "Error in running Magic Farm game using wine"
date: 2019-05-19
forum: Wine
---

### Post by sam-mo on 2019-05-19
Hi everyone
I'm using wine on Linux Mint 19.1 and Ubuntu 18.10, and I have downloaded a game from gametop.com that is Magic Farm, and when I try to open it using wine, it gives me this error message :

```

Exception: Access Violation (code 0xc0000005) at address 006AA273 in thread 2E
Module: game.exe
Logical Address: 0001:002A9273

0033F734 006AA273 0001:002A9273 game.exe
Params: 8B18AC4A 0033F81C 00C8E7C0 00000000

0033F7BC 005CDF91 EntryPoint+FFFFFFFF
Params: 00C8F368 8B18A2BA 00400000 00C8E7C0

0033F94C 0054B47D EntryPoint+FFFFFFFF
Params: 8B18A136 00400000 00C8E7C0 00000000

0033FAC0 005FC9BB EntryPoint+FFFFFFFF
Params: 8B18A09A 00400000 00000000 00000000

0033FB6C 004FC27B EntryPoint+FFFFFFFF
Params: 8B18A5D2 00000000 00000000 7B63D000

0033FE24 004FEEDA EntryPoint+FFFFFFFF
Params: 00400000 0033FEC0 0067FF98 00400000

0033FE30 004FF9DC EntryPoint+FFFFFFFF
Params: 00400000 00000000 00153F70 0000000A

0033FEC0 0067FF98 EntryPoint+FFFFFFFF
Params: 7FFDF000 7B46591E 7B46591E 7B46591E

0033FED8 7B4636A2 call_process_entry+12
Params: 7FFDF000 0067FFEB 00000000 00000000

0033FFD8 7B46591E ExitProcess+226E
Params: 7B4636AE 0067FFEB 7FFDF000 00000000

0033FFEC 7B4636AE call_process_entry+1E
Params: 00000000 00000000 00000000 DE010101

StackWalk failed (error 126)

EAX:00000000 EBX:00000000 ECX:8B2B5BF6 EDX:00000000 ESI:00C8F120 EDI:00000000
EIP:006AA273 ESP:0033E6E4  EBP:0033F734
CS:0023 SS:002B DS:002B ES:002B FS:0063 GS:006B
Flags:00010246

Windows Ver: NT 5.1 Service Pack 3 Build 2600

```

and then a window pops up saying that the problem might be a deficiency in Wine


when clicking on "Show Details" it gives this :

```

Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x006aa273).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:006aa273 ESP:0033e6e4 EBP:0033f734 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00000000 ECX:9ca7f703 EDX:00000000
 ESI:00c8f120 EDI:00000000
Stack dump:
0x0033e6e4:  008faf54 9c940037 00c8f368 00c8f120
0x0033e6f4:  00000000 00000000 00000000 00000000
0x0033e704:  00000000 00000000 00000000 00000000
0x0033e714:  00000000 00000000 00000000 00000000
0x0033e724:  00000000 00000000 00000000 00000000
0x0033e734:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x006aa273 in game (+0x2aa273) (0x0033f734)
  1 0x005cdf91 EntryPoint+0xffffffff() in game (0x0033f7bc)
  2 0x0054b47d EntryPoint+0xffffffff() in game (0x0033f94c)
  3 0x005fc9bb EntryPoint+0xffffffff() in game (0x0033fac0)
  4 0x004fc27b EntryPoint+0xffffffff() in game (0x0033fb6c)
  5 0x004feeda EntryPoint+0xffffffff() in game (0x0033fe24)
  6 0x004ff9dc EntryPoint+0xffffffff() in game (0x0033fe30)
  7 0x0067ff98 EntryPoint+0xffffffff() in game (0x0033fec0)
  8 0x7b4636a2 call_process_entry+0x11() in kernel32 (0x0033fed8)
  9 0x7b46591e ExitProcess+0x226d() in kernel32 (0x0033ffd8)
  10 0x7b4636ae call_process_entry+0x1d() in kernel32 (0x0033ffec)
0x006aa273: movl    0x0(%eax),%ecx
Modules:
Module    Address            Debug info    Name (116 modules)
PE      400000-  b51000    Export          game
ELF    7a800000-7a93e000    Deferred        opengl32<elf>
  \-PE    7a820000-7a93e000    \               opengl32
ELF    7b400000-7b7f9000    Dwarf           kernel32<elf>
  \-PE    7b420000-7b7f9000    \               kernel32
ELF    7bc00000-7bd00000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bd00000    \               ntdll
ELF    7beb0000-7bece000    Deferred        libgcc_s.so.1
ELF    7bf13000-7bfcb000    Deferred        msvcrt<elf>
  \-PE    7bf30000-7bfcb000    \               msvcrt
ELF    7c000000-7c004000    Deferred        <wine-loader>
ELF    7c557000-7c59d000    Deferred        usp10<elf>
  \-PE    7c560000-7c59d000    \               usp10
ELF    7c674000-7c6bf000    Deferred        dsound<elf>
  \-PE    7c680000-7c6bf000    \               dsound
ELF    7c6bf000-7c736000    Deferred        ddraw<elf>
  \-PE    7c6d0000-7c736000    \               ddraw
ELF    7c736000-7c73d000    Deferred        libxfixes.so.3
ELF    7c73d000-7c749000    Deferred        libxcursor.so.1
ELF    7c749000-7c75c000    Deferred        libxi.so.6
ELF    7c75c000-7c760000    Deferred        libxcomposite.so.1
ELF    7c760000-7c76d000    Deferred        libxrandr.so.2
ELF    7c76d000-7c779000    Deferred        libxrender.so.1
ELF    7c779000-7c780000    Deferred        libxxf86vm.so.1
ELF    7c780000-7c784000    Deferred        libxinerama.so.1
ELF    7c784000-7c78e000    Deferred        librt.so.1
ELF    7c78e000-7c7a9000    Deferred        libbsd.so.0
ELF    7c7a9000-7c7b0000    Deferred        libxdmcp.so.6
ELF    7c7b0000-7c7b4000    Deferred        libxau.so.6
ELF    7c7b4000-7c7e0000    Deferred        libxcb.so.1
ELF    7c7e0000-7c92a000    Deferred        libx11.so.6
ELF    7c92a000-7c93f000    Deferred        libxext.so.6
ELF    7c95b000-7c9eb000    Deferred        winex11<elf>
  \-PE    7c970000-7c9eb000    \               winex11
ELF    7c9eb000-7ca0f000    Deferred        imm32<elf>
  \-PE    7c9f0000-7ca0f000    \               imm32
ELF    7cc10000-7cc42000    Deferred        libexpat.so.1
ELF    7cc42000-7cc8d000    Deferred        libfontconfig.so.1
ELF    7cc8d000-7ccc7000    Deferred        libpng16.so.16
ELF    7ccc7000-7cd84000    Deferred        libfreetype.so.6
ELF    7cd84000-7cead000    Deferred        oleaut32<elf>
  \-PE    7cda0000-7cead000    \               oleaut32
ELF    7cead000-7ceb6000    Deferred        libffi.so.6
ELF    7ceb6000-7cee8000    Deferred        libcrypt.so.1
ELF    7cee8000-7d006000    Deferred        libsqlite3.so.0
ELF    7d006000-7d055000    Deferred        libhx509.so.5
ELF    7d055000-7d066000    Deferred        libheimbase.so.1
ELF    7d066000-7d090000    Deferred        libwind.so.0
ELF    7d090000-7d11b000    Deferred        libgmp.so.10
ELF    7d11b000-7d151000    Deferred        libhogweed.so.4
ELF    7d151000-7d18d000    Deferred        libnettle.so.6
ELF    7d18d000-7d1a2000    Deferred        libtasn1.so.6
ELF    7d1a2000-7d323000    Deferred        libunistring.so.2
ELF    7d323000-7d341000    Deferred        libidn2.so.0
ELF    7d341000-7d48f000    Deferred        libp11-kit.so.0
ELF    7d48f000-7d4a7000    Deferred        libroken.so.18
ELF    7d4a7000-7d4e3000    Deferred        libhcrypto.so.4
ELF    7d4e3000-7d4e8000    Deferred        libcom_err.so.2
ELF    7d4e8000-7d59b000    Deferred        libasn1.so.8
ELF    7d59b000-7d638000    Deferred        libkrb5.so.26
ELF    7d638000-7d642000    Deferred        libheimntlm.so.0
ELF    7d642000-7d7d8000    Deferred        libgnutls.so.30
ELF    7d7d8000-7d81f000    Deferred        libgssapi.so.3
ELF    7d81f000-7d83d000    Deferred        libsasl2.so.2
ELF    7d83d000-7d855000    Deferred        libresolv.so.2
ELF    7d855000-7d865000    Deferred        liblber-2.4.so.2
ELF    7d865000-7d8c1000    Deferred        libldap_r-2.4.so.2
ELF    7d8dd000-7d938000    Deferred        wldap32<elf>
  \-PE    7d8f0000-7d938000    \               wldap32
ELF    7d938000-7d94c000    Deferred        psapi<elf>
  \-PE    7d940000-7d94c000    \               psapi
ELF    7d94c000-7d977000    Deferred        iphlpapi<elf>
  \-PE    7d950000-7d977000    \               iphlpapi
ELF    7d977000-7d9ae000    Deferred        ws2_32<elf>
  \-PE    7d980000-7d9ae000    \               ws2_32
ELF    7d9ae000-7d9da000    Deferred        msacm32<elf>
  \-PE    7d9b0000-7d9da000    \               msacm32
ELF    7d9da000-7da94000    Deferred        winmm<elf>
  \-PE    7d9e0000-7da94000    \               winmm
ELF    7da94000-7dbe5000    Deferred        wined3d<elf>
  \-PE    7daa0000-7dbe5000    \               wined3d
ELF    7dbe5000-7dc27000    Deferred        d3d9<elf>
  \-PE    7dbf0000-7dc27000    \               d3d9
ELF    7dc27000-7dc46000    Deferred        libz.so.1
ELF    7dc48000-7dc62000    Deferred        wsock32<elf>
  \-PE    7dc50000-7dc62000    \               wsock32
ELF    7dc62000-7dcca000    Deferred        dbghelp<elf>
  \-PE    7dc70000-7dcca000    \               dbghelp
ELF    7dcca000-7dd4f000    Deferred        rpcrt4<elf>
  \-PE    7dce0000-7dd4f000    \               rpcrt4
ELF    7dd4f000-7deaa000    Deferred        ole32<elf>
  \-PE    7dd70000-7deaa000    \               ole32
ELF    7deaa000-7dece000    Deferred        shcore<elf>
  \-PE    7deb0000-7dece000    \               shcore
ELF    7dece000-7df3d000    Deferred        shlwapi<elf>
  \-PE    7dee0000-7df3d000    \               shlwapi
ELF    7df3d000-7e901000    Deferred        shell32<elf>
  \-PE    7df50000-7e901000    \               shell32
ELF    7e901000-7e97a000    Deferred        advapi32<elf>
  \-PE    7e910000-7e97a000    \               advapi32
ELF    7e97a000-7eaa9000    Deferred        gdi32<elf>
  \-PE    7e990000-7eaa9000    \               gdi32
ELF    7eaa9000-7ecb3000    Deferred        user32<elf>
  \-PE    7eac0000-7ecb3000    \               user32
ELF    7ecb3000-7ecc7000    Deferred        libnss_files.so.2
ELF    7ecc7000-7ece2000    Deferred        libnsl.so.1
ELF    7ece4000-7ecfe000    Deferred        version<elf>
  \-PE    7ecf0000-7ecfe000    \               version
ELF    7eefe000-7f000000    Deferred        libm.so.6
ELF    f7b82000-f7b87000    Deferred        libdl.so.2
ELF    f7b87000-f7d63000    Deferred        libc.so.6
ELF    f7d63000-f7d82000    Deferred        libpthread.so.0
ELF    f7d82000-f7d90000    Deferred        libnss_nis.so.2
ELF    f7d90000-f7d9a000    Deferred        libnss_compat.so.2
ELF    f7d9e000-f7f55000    Dwarf           libwine.so.1
ELF    f7f57000-f7f7f000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000024    0
    00000021    0
    0000001c    0
    00000018    0
    00000013    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000019    0
    00000017    0
    00000016    0
    00000012    0
0000001a plugplay.exe
    0000001e    0
    0000001d    0
    0000001b    0
0000001f winedevice.exe
    00000027    0
    00000023    0
    00000022    0
    00000020    0
00000025 explorer.exe
    0000002a    0
    00000029    0
    00000028    0
    00000026    0
0000002b (D) C:\Program Files (x86)\GameTop.com\Magic Farm\game.exe
    0000002c    0 <==
System information:
    Wine build: wine-4.0.1
    Platform: i386 (WOW64)
    Version: Windows 5.1 (0)
    Host system: Linux
    Host version: 4.15.0-50-generic


```

Any help ?

---

### Post by DuckHook on 2019-05-19
Welcome to the forums, sam-mo.

I cannot even find this game on WINE's [app database]("https://appdb.winehq.org/"). Therefore, you are likely out of luck trying to get it running under WINE.

FWIW, WINE has natural limitations since it is an attempt to reverse-engineer native Linux system calls for Windows APIs. This is bound to result in various shades of success or, more often, failure.

If a game is not rated "Platinum" in the WineHQ AppDB, you are unlikely to enjoy the experience. If the game does not even exist on that database, it is likely not playable.

If you are new to Linux, please have a look at the link in my sig: Linux is Not Windows. If you are primarily a gamer with your computer, you may wish to re-examine using Linux as a platform altogether.

---

### Post by mastablasta on 2019-05-20
not all games will work on Wine. 

last time i received a similar error output turned out a native library was needed and was missing.

if the game needs directx9 you could try installing that first.

---

### Post by sam-mo on 2019-06-05
oh :( it's sad but thanks for your help

---

### Post by 5c0rch3r75 on 2019-10-21
It looks like the game is trying to write on a protected zone of the hdd (not sure,someone please correct me if i am wrong).
Make this,open a console and use winetricks to install these packages.Then rerun the game.
directx9 (as posted above)
dotnet40 (tricky,carefull with this one)
Vcrun2005 and 2008
Vb6run (all of the vbrun if possible)

See if it helps.

---

