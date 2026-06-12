---
title: "msvcp80.dll - Voyage Century Online on Wine"
date: 2013-02-19
forum: Wine
---

### Post by DaMadHatter on 2013-02-19
Hi Guys,

  Working on getting this mmo Voyage Century Online working in wine, im using Ubuntu 12.04LTS amdx64, I have PlayOnLinux installed along with the latest version of Wine. 

  The game in reference is rather old, still its on the Wine list as Gold and Platinum unfortunately latest posts regarding this game are about 5 years old, and their appears to be no maintainers.

It installed and the updater ran up too latest version .110 but crashes as soon as I click the "start game" button from the launcher. I followed the guide in relation too this on the WineHQ AppzDB but I am seeing some errors. (Was expected.)

 I have tried using an x86 edition of Wine but was receiving the same error. So I tried adding the  msvcp80.dll in the override section of wine cfg, again nothing. I added msvcp60.dll through msvcp100.dll, still nothing. 

After ](*,) for a few days I could sure use some help here. Im sure I am missing a lib here or something rather easy, any help would be greatly appreciated. Thanks in advance.

Here is the output from the crash -

```
Unhandled exception: unimplemented function msvcp80.dll.??0?$basic_ifstream@DU?$char_traits@D@std@@@std@@QAE@PBDHH@Z called in 32-bit code (0x7b839cf2).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b839cf2 ESP:0033f6f8 EBP:0033f75c EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b826245 EBX:7b894ff4 ECX:00000000 EDX:80000100
 ESI:80000100 EDI:004084a4
Stack dump:
0x0033f6f8:  0033f77c 00000008 00000000 80000100
0x0033f708:  00000001 00000000 7b839cf2 00000002
0x0033f718:  7e94c3a2 7e94f708 00000000 00000000
0x0033f728:  00000000 00000000 00000000 00000000
0x0033f738:  00000000 00000000 00000000 00000000
0x0033f748:  00000000 00000000 7b839caa 00000000
000c: sel=0067 base=00000000 limit=00000000 16-bit --x
Backtrace:
=>0 0x7b839cf2 in kernel32 (+0x29cf2) (0x0033f75c)
  1 0x7e94c348 in msvcp80 (+0x1c347) (0x0033f78c)
  2 0x7e93c705 in msvcp80 (+0xc704) (0x0033fe70)
  3 0x004010d4 in core (+0x10d3) (0x0033fe70)
  4 0x7b859cdc call_process_entry+0xb() in kernel32 (0x0033fe88)
  5 0x7b85af4f in kernel32 (+0x4af4e) (0x0033fec8)
  6 0x7bc71db0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  7 0x7bc7486d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  8 0x7bc71d8e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  9 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x7b839cf2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (101 modules)
PE      400000-  413000    Export          core
PE    10000000-10092000    Deferred        core
ELF    7b800000-7ba15000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d801000-7d80a000    Deferred        librt.so.1
ELF    7d80a000-7d80f000    Deferred        libgpg-error.so.0
ELF    7d80f000-7d827000    Deferred        libresolv.so.2
ELF    7d827000-7d82b000    Deferred        libkeyutils.so.1
ELF    7d82b000-7d874000    Deferred        libdbus-1.so.3
ELF    7d874000-7d886000    Deferred        libp11-kit.so.0
ELF    7d886000-7d90b000    Deferred        libgcrypt.so.11
ELF    7d90b000-7d91d000    Deferred        libtasn1.so.3
ELF    7d91d000-7d926000    Deferred        libkrb5support.so.0
ELF    7d926000-7d94e000    Deferred        libk5crypto.so.3
ELF    7d94e000-7da1d000    Deferred        libkrb5.so.3
ELF    7da1d000-7da2f000    Deferred        libavahi-client.so.3
ELF    7da2f000-7daf3000    Deferred        libgnutls.so.26
ELF    7daf3000-7db31000    Deferred        libgssapi_krb5.so.2
ELF    7db31000-7db84000    Deferred        libcups.so.2
ELF    7dbca000-7dbfe000    Deferred        uxtheme<elf>
  \-PE    7dbd0000-7dbfe000    \               uxtheme
ELF    7dbfe000-7dc04000    Deferred        libxfixes.so.3
ELF    7dc04000-7dc0f000    Deferred        libxcursor.so.1
ELF    7dc12000-7dc17000    Deferred        libcom_err.so.2
ELF    7dc17000-7dc25000    Deferred        libavahi-common.so.3
ELF    7dc80000-7dcaa000    Deferred        libexpat.so.1
ELF    7dcaa000-7dcde000    Deferred        libfontconfig.so.1
ELF    7dcde000-7dcee000    Deferred        libxi.so.6
ELF    7dcee000-7dcf7000    Deferred        libxrandr.so.2
ELF    7dcf7000-7dd01000    Deferred        libxrender.so.1
ELF    7dd01000-7dd07000    Deferred        libxxf86vm.so.1
ELF    7dd07000-7dd29000    Deferred        imm32<elf>
  \-PE    7dd10000-7dd29000    \               imm32
ELF    7dd29000-7dd30000    Deferred        libxdmcp.so.6
ELF    7dd30000-7dd51000    Deferred        libxcb.so.1
ELF    7dd51000-7dd57000    Deferred        libuuid.so.1
ELF    7dd57000-7dd71000    Deferred        libice.so.6
ELF    7dd71000-7dea5000    Deferred        libx11.so.6
ELF    7dea5000-7deb7000    Deferred        libxext.so.6
ELF    7deb7000-7dec0000    Deferred        libsm.so.6
ELF    7dec0000-7df53000    Deferred        winex11<elf>
  \-PE    7ded0000-7df53000    \               winex11
ELF    7df53000-7df69000    Deferred        libz.so.1
ELF    7df69000-7e003000    Deferred        libfreetype.so.6
ELF    7e01b000-7e079000    Deferred        dbghelp<elf>
  \-PE    7e020000-7e079000    \               dbghelp
ELF    7e079000-7e0a8000    Deferred        msvcr90<elf>
  \-PE    7e080000-7e0a8000    \               msvcr90
ELF    7e0a8000-7e0d3000    Deferred        msvcr80<elf>
  \-PE    7e0b0000-7e0d3000    \               msvcr80
ELF    7e0d3000-7e10d000    Deferred        winspool<elf>
  \-PE    7e0e0000-7e10d000    \               winspool
ELF    7e10d000-7e177000    Deferred        shlwapi<elf>
  \-PE    7e120000-7e177000    \               shlwapi
ELF    7e177000-7e388000    Deferred        shell32<elf>
  \-PE    7e180000-7e388000    \               shell32
ELF    7e388000-7e467000    Deferred        comdlg32<elf>
  \-PE    7e390000-7e467000    \               comdlg32
ELF    7e467000-7e48f000    Deferred        msacm32<elf>
  \-PE    7e470000-7e48f000    \               msacm32
ELF    7e48f000-7e504000    Deferred        rpcrt4<elf>
  \-PE    7e4a0000-7e504000    \               rpcrt4
ELF    7e504000-7e60c000    Deferred        ole32<elf>
  \-PE    7e520000-7e60c000    \               ole32
ELF    7e60c000-7e6b9000    Deferred        winmm<elf>
  \-PE    7e610000-7e6b9000    \               winmm
ELF    7e6b9000-7e7b1000    Deferred        comctl32<elf>
  \-PE    7e6c0000-7e7b1000    \               comctl32
ELF    7e7b1000-7e83e000    Deferred        msvcrt<elf>
  \-PE    7e7c0000-7e83e000    \               msvcrt
ELF    7e83e000-7e923000    Deferred        msvcp90<elf>
  \-PE    7e860000-7e923000    \               msvcp90
ELF    7e923000-7e9cc000    Dwarf           msvcp80<elf>
  \-PE    7e930000-7e9cc000    \               msvcp80
ELF    7e9cc000-7e9e5000    Deferred        version<elf>
  \-PE    7e9d0000-7e9e5000    \               version
ELF    7e9e5000-7ea45000    Deferred        advapi32<elf>
  \-PE    7e9f0000-7ea45000    \               advapi32
ELF    7ea45000-7eb02000    Deferred        gdi32<elf>
  \-PE    7ea50000-7eb02000    \               gdi32
ELF    7eb02000-7ec42000    Deferred        user32<elf>
  \-PE    7eb10000-7ec42000    \               user32
ELF    7ec42000-7ec4f000    Deferred        libnss_files.so.2
ELF    7ec4f000-7ec69000    Deferred        libnsl.so.1
ELF    7ec69000-7ec72000    Deferred        libnss_compat.so.2
ELF    7ec72000-7ec76000    Deferred        libxcomposite.so.1
ELF    7ec76000-7ec8a000    Deferred        psapi<elf>
  \-PE    7ec80000-7ec8a000    \               psapi
ELF    7efbc000-7efe8000    Deferred        libm.so.6
ELF    7efe9000-7efed000    Deferred        libxinerama.so.1
ELF    7eff4000-7f000000    Deferred        libnss_nis.so.2
ELF    f7402000-f7407000    Deferred        libdl.so.2
ELF    f7407000-f75b1000    Deferred        libc.so.6
ELF    f75b2000-f75cd000    Deferred        libpthread.so.0
ELF    f75e1000-f75e5000    Deferred        libxau.so.6
ELF    f75e5000-f7727000    Dwarf           libwine.so.1
ELF    f7729000-f774b000    Deferred        ld-linux.so.2
ELF    f774b000-f774c000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000040    0
    0000003f    0
    0000003e    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
0000002d explorer.exe
    0000002e    0
00000017 (D) C:\Program Files (x86)\Voyage Century Online\voyage\Core.exe
    00000027    0
    00000018    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.2.0-37-generic
```

---

### Post by DaMadHatter on 2013-02-20
So after recieving some helpful info from the WineHQ folks, I just figured I would add an update here, on the off chance their might be another VCO goer around.   Updating Wine from version 1.4 to 1.5.24 has solved the msvcp80.dll error, and instead of it crashing immediately it now hangs on a black screen playing the opening sound file until crashing and displaying the new in game error bug recorder. However even the Program Error Dialogue window is now hanging, and will not generate its crash output.  Will keep trying and update here as things develop.

---

