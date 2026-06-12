---
title: "Error running .exe file with wine"
date: 2016-09-01
forum: Wine
---

### Post by hunzelmann on 2016-09-01
hello people :)

i'm currently trying to get a programm running on my lubuntu 16.04 system, the name's EZ4_Client.exe
the error message i receive is the following and i, as a total newbie to linux, dont understand what i am reading

```
wine EZ4_Client.exe

err:shell:SHGetFileInfoW pidl is null!
wine: Unhandled page fault on read access to 0x00000004 at address 0x407628 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x00407628).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00407628 ESP:0032c288 EBP:0032f4c8 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:0032f368 ECX:0032e2ac EDX:5f45a668
 ESI:00000000 EDI:7ea8d8e0
Stack dump:
0x0032c288:  00010076 00010076 0032e2e8 7eafd000
0x0032c298:  0013f510 7bc36876 0032c2c0 7bcbe000
0x0032c2a8:  0032c468 7bc49f68 00000000 4d430000
0x0032c2b8:  7bc4952e 7bc49f68 00110060 00000000
0x0032c2c8:  0032c468 7bc498e5 00000001 00000002
0x0032c2d8:  00000000 00110000 7bcbe000 00110000
Backtrace:
=>0 0x00407628 in ez4_client (+0x7628) (0x0032f4c8)
  1 0x00000001 (0x004169b0)
  2 0x0040ce30 in ez4_client (+0xce2f) (0x004115d4)
0x00407628: movl    0x4(%esi),%ecx
Modules:
Module    Address            Debug info    Name (111 modules)
PE      330000-  362000    Deferred        unrar
PE      370000-  3f6000    Deferred        skinppwtl
PE      400000-  478000    Export          ez4_client
PE      480000-  4a3000    Deferred        ez4patch
PE    10000000-10011000    Deferred        zlib
PE    5f400000-5f4f2000    Deferred        mfc42
ELF    7b800000-7ba54000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba54000    \               kernel32
ELF    7bc00000-7bcda000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcda000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cb44000-7cb85000    Deferred        usp10<elf>
  \-PE    7cb50000-7cb85000    \               usp10
ELF    7d0bc000-7d0e0000    Deferred        imm32<elf>
  \-PE    7d0c0000-7d0e0000    \               imm32
ELF    7d1e0000-7d1f6000    Deferred        libgpg-error.so.0
ELF    7d1f6000-7d26b000    Deferred        libpcre.so.3
ELF    7d26b000-7d288000    Deferred        libgcc_s.so.1
ELF    7d288000-7d337000    Deferred        libgcrypt.so.20
ELF    7d337000-7d35d000    Deferred        liblzma.so.5
ELF    7d35d000-7d366000    Deferred        librt.so.1
ELF    7d366000-7d38c000    Deferred        libselinux.so.1
ELF    7d38c000-7d41a000    Deferred        libsystemd.so.0
ELF    7d41a000-7d423000    Deferred        libffi.so.6
ELF    7d423000-7d43c000    Deferred        libresolv.so.2
ELF    7d43c000-7d441000    Deferred        libkeyutils.so.1
ELF    7d441000-7d49b000    Deferred        libdbus-1.so.3
ELF    7d49b000-7d527000    Deferred        libgmp.so.10
ELF    7d527000-7d55c000    Deferred        libhogweed.so.4
ELF    7d55c000-7d598000    Deferred        libnettle.so.6
ELF    7d598000-7d5ad000    Deferred        libtasn1.so.6
ELF    7d5ad000-7d5e1000    Deferred        libidn.so.11
ELF    7d5e1000-7d643000    Deferred        libp11-kit.so.0
ELF    7d643000-7d650000    Deferred        libkrb5support.so.0
ELF    7d650000-7d681000    Deferred        libk5crypto.so.3
ELF    7d681000-7d758000    Deferred        libkrb5.so.3
ELF    7d758000-7d76c000    Deferred        libavahi-client.so.3
ELF    7d76c000-7d8c4000    Deferred        libgnutls.so.30
ELF    7d8c4000-7d916000    Deferred        libgssapi_krb5.so.2
ELF    7d916000-7d99d000    Deferred        libcups.so.2
ELF    7d9b3000-7d9e8000    Deferred        uxtheme<elf>
  \-PE    7d9c0000-7d9e8000    \               uxtheme
ELF    7d9e8000-7d9ef000    Deferred        libxfixes.so.3
ELF    7d9ef000-7d9fa000    Deferred        libxcursor.so.1
ELF    7d9fa000-7da0d000    Deferred        libxi.so.6
ELF    7da0d000-7da11000    Deferred        libxcomposite.so.1
ELF    7da11000-7da1e000    Deferred        libxrandr.so.2
ELF    7da1e000-7da2a000    Deferred        libxrender.so.1
ELF    7da2a000-7da31000    Deferred        libxxf86vm.so.1
ELF    7da31000-7da35000    Deferred        libxinerama.so.1
ELF    7da35000-7da3c000    Deferred        libxdmcp.so.6
ELF    7da3c000-7da40000    Deferred        libxau.so.6
ELF    7da40000-7da66000    Deferred        libxcb.so.1
ELF    7da66000-7dbb1000    Deferred        libx11.so.6
ELF    7dbb1000-7dbc6000    Deferred        libxext.so.6
ELF    7dbc7000-7dbcc000    Deferred        libcom_err.so.2
ELF    7dbcc000-7dbda000    Deferred        libavahi-common.so.3
ELF    7dbdc000-7dc69000    Deferred        winex11<elf>
  \-PE    7dbf0000-7dc69000    \               winex11
ELF    7dd8b000-7ddb5000    Deferred        libexpat.so.1
ELF    7ddb5000-7ddfe000    Deferred        libfontconfig.so.1
ELF    7ddfe000-7de29000    Deferred        libpng12.so.0
ELF    7de29000-7de44000    Deferred        libz.so.1
ELF    7de44000-7def4000    Deferred        libfreetype.so.6
ELF    7def4000-7dfe4000    Deferred        msvcp60<elf>
  \-PE    7df20000-7dfe4000    \               msvcp60
ELF    7dfe4000-7e111000    Deferred        oleaut32<elf>
  \-PE    7e000000-7e111000    \               oleaut32
ELF    7e13b000-7e15e000    Deferred        libtinfo.so.5
ELF    7e15e000-7e184000    Deferred        libncurses.so.5
ELF    7e19a000-7e1bd000    Deferred        msvcirt<elf>
  \-PE    7e1a0000-7e1bd000    \               msvcirt
ELF    7e1bd000-7e239000    Deferred        rpcrt4<elf>
  \-PE    7e1d0000-7e239000    \               rpcrt4
ELF    7e239000-7e368000    Deferred        ole32<elf>
  \-PE    7e250000-7e368000    \               ole32
ELF    7e368000-7e3a4000    Deferred        winspool<elf>
  \-PE    7e370000-7e3a4000    \               winspool
ELF    7e3a4000-7e499000    Deferred        comctl32<elf>
  \-PE    7e3b0000-7e499000    \               comctl32
ELF    7e499000-7e50f000    Deferred        shlwapi<elf>
  \-PE    7e4b0000-7e50f000    \               shlwapi
ELF    7e50f000-7e738000    Deferred        shell32<elf>
  \-PE    7e520000-7e738000    \               shell32
ELF    7e738000-7e81d000    Deferred        comdlg32<elf>
  \-PE    7e740000-7e81d000    \               comdlg32
ELF    7e81d000-7e8cc000    Deferred        msvcrt<elf>
  \-PE    7e830000-7e8cc000    \               msvcrt
ELF    7e8cc000-7e8e7000    Deferred        crtdll<elf>
  \-PE    7e8d0000-7e8e7000    \               crtdll
ELF    7e8e7000-7e900000    Deferred        version<elf>
  \-PE    7e8f0000-7e900000    \               version
ELF    7e900000-7ea17000    Deferred        gdi32<elf>
  \-PE    7e910000-7ea17000    \               gdi32
ELF    7ea17000-7eb65000    Deferred        user32<elf>
  \-PE    7ea30000-7eb65000    \               user32
ELF    7eb65000-7ebd1000    Deferred        advapi32<elf>
  \-PE    7eb70000-7ebd1000    \               advapi32
ELF    7ef50000-7ef63000    Deferred        libnss_files.so.2
ELF    7ef63000-7ef70000    Deferred        libnss_nis.so.2
ELF    7ef70000-7ef8b000    Deferred        libnsl.so.1
ELF    7ef8b000-7ef95000    Deferred        libnss_compat.so.2
ELF    7ef95000-7efea000    Deferred        libm.so.6
ELF    7efec000-7f000000    Deferred        msimg32<elf>
  \-PE    7eff0000-7f000000    \               msimg32
ELF    f73c6000-f73cb000    Deferred        libdl.so.2
ELF    f73cb000-f7581000    Deferred        libc.so.6
ELF    f7582000-f759f000    Deferred        libpthread.so.0
ELF    f75b5000-f776a000    Dwarf           libwine.so.1
ELF    f776c000-f7791000    Deferred        ld-linux.so.2
ELF    f7793000-f7794000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\horst\Downloads\EZ4\EZ4_Client.exe
    00000009    0 <==
0000000e services.exe
    0000001d    0
    0000001c    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000017    0
    00000013    0
00000019 plugplay.exe
    0000001f    0
    0000001e    0
    0000001a    0
00000020 explorer.exe
    00000022    0
    00000021    0
```

so .. i don't know if there's something more needed to know about that issue to help me, so please tell me if that's the case
hope someone can figure this out

greetings, hunzelmann

---

