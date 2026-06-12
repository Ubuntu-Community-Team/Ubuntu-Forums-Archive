---
title: "32 bits problem - cannot install dotnet 20"
date: 2015-08-21
forum: Wine
---

### Post by gravor on 2015-08-21
Hi !
I would like to install dotnet 20 on my computer but I got a problem, it cannot install dotnet on a 64 bits computer ...
I'm using Ubuntu 14.04.3 version.
How can I do it ?

---

### Post by Toz on 2015-08-21
You need to create a 32-bit wine prefix to use within your 64-bit system. Here is how:

1. _Command-line version:_
You need to specify two environment variables when creating the new wine prefix: WINEARCH and WINEPREFIX. WINEARCH is used to specify that you want to create a 32-bit prefix, and WINEPREFIX is used to create a new wine instance within your system (you can have multiple wine instances). From a terminal window, the following command will create the proper wine prefix and install dotnet20:
```
WINEARCH=win32 WINEPREFIX=~/.wine32 winetricks dotnet20
```
When you want to install anything else into this instance, from the command line you need to specify the WINEPREFIX. Example:
```
WINEPREFIX=~/.wine32 wine /app/to/install
```
(Note that the WINEARCH only needs to be specified once - when you create the wine instance). You can then run the wine programs from the main menu.

2. _Graphical option_:
[PlayOnLinux]("https://www.playonlinux.com/en/") (available in the repositories) will be default create 32-bit wine prefixes in 64-bit systems. It is a good front-end for wine that has many features, including managing multiple versions of wine and having pre-install scripts for many popular apps and games. It will simplify the process of installing windows applications or games in Linux.

---

### Post by howefield on 2015-08-21
Thread moved to the "*Wine*" forum.

---

### Post by gravor on 2015-08-21
> **Toz said:**
> You need to create a 32-bit wine prefix to use within your 64-bit system. Here is how:

1. _Command-line version:_
You need to specify two environment variables when creating the new wine prefix: WINEARCH and WINEPREFIX. WINEARCH is used to specify that you want to create a 32-bit prefix, and WINEPREFIX is used to create a new wine instance within your system (you can have multiple wine instances). From a terminal window, the following command will create the proper wine prefix and install dotnet20:
```
WINEARCH=win32 WINEPREFIX=~/.wine32 winetricks dotnet20
```
When you want to install anything else into this instance, from the command line you need to specify the WINEPREFIX. Example:
```
WINEPREFIX=~/.wine32 wine /app/to/install
```
(Note that the WINEARCH only needs to be specified once - when you create the wine instance). You can then run the wine programs from the main menu.

2. _Graphical option_:
[PlayOnLinux]("https://www.playonlinux.com/en/") (available in the repositories) will be default create 32-bit wine prefixes in 64-bit systems. It is a good front-end for wine that has many features, including managing multiple versions of wine and having pre-install scripts for many popular apps and games. It will simplify the process of installing windows applications or games in Linux.


It works :) thank you.


But when I want to install vb2run, it tries to connect to : 64.4.17.176:21... and it fails ... why ?

---

### Post by Toz on 2015-08-21
Perhaps the place that your copy of winetricks is looking for vbrun200.exe is unavailable. 
Mine points to [ftp://ftp.chatnfiles.com/Winfilesdotcom/winfilesdotcom-june-98-4-of-4/required/VBRUN200.EXE]("ftp://ftp.chatnfiles.com/Winfilesdotcom/winfilesdotcom-june-98-4-of-4/required/VBRUN200.EXE")

Get the file from there, save it to ~/.cache/winetricks/vb2run (create the folder if it doesn't exist), and re-run your install command:
```
WINEARCH=win32 WINEPREFIX=~/.wine32 winetricks vb2run
```

EDIT: The latest version of winetricks script can always be found [here]("https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks").

---

### Post by gravor on 2015-08-21
> **Toz said:**
> Perhaps the place that your copy of winetricks is looking for vbrun200.exe is unavailable. 
Mine points to [ftp://ftp.chatnfiles.com/Winfilesdotcom/winfilesdotcom-june-98-4-of-4/required/VBRUN200.EXE](ftp://ftp.chatnfiles.com/Winfilesdotcom/winfilesdotcom-june-98-4-of-4/required/VBRUN200.EXE)

Get the file from there, save it to ~/.cache/winetricks/vb2run (create the folder if it doesn't exist), and re-run your install command:
```
WINEARCH=win32 WINEPREFIX=~/.wine32 winetricks vb2run
```

EDIT: The latest version of winetricks script can always be found [here]("https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks").


I forgot, I'm new to Ubuntu.
I got the file from the link, but How can I move the file to ~/.cache/winetricks/vb2run  ? (the folder exist)






But I can show you what is displayed on my terminal


```

 WINEARCH=win32 WINEPREFIX=~/.wine32 winetricks vb2run
Executing w_do_call vb2run
Executing load_vb2run
Downloading ftp://64.4.17.176/Softlib/MSLFILES/VBRUN200.EXE to /home/************/.cache/winetricks/vb2run
--2015-08-21 19:42:09--  ftp://64.4.17.176/Softlib/MSLFILES/VBRUN200.EXE
           => «VBRUN200.EXE»
Connexion to 64.4.17.176:21...

```



It works for vb3run, vb4run ...

---

### Post by Toz on 2015-08-21
> **gravor said:**
> I forgot, I'm new to Ubuntu.
I got the file from the link, but How can I move the file to ~/.cache/winetricks/vb2run  ? (the folder exist)
If you saved the file in your Downloads directory...

Then from the command line, you could:
```
mv ~/Downloads/VBRUN200.EXE ~/.cache/winetricks/vb2run
```

To do it graphically, fire up your file manager, go to the Downloads directory and right-click->copy on the file. Press Ctrl+H to show hidden files then go to your home directory and then over to .cache/winetricks/vb2run, right-click->paste to put it there.

---

### Post by gravor on 2015-08-22
> **Toz said:**
> If you saved the file in your Downloads directory...

Then from the command line, you could:
```
mv ~/Downloads/VBRUN200.EXE ~/.cache/winetricks/vb2run
```

To do it graphically, fire up your file manager, go to the Downloads directory and right-click->copy on the file. Press Ctrl+H to show hidden files then go to your home directory and then over to .cache/winetricks/vb2run, right-click->paste to put it there.


Ok, I got it

---

### Post by gravor on 2015-08-22
There's issue.
When I want to creat a matrix with microsoft office word, the software crashes :(

---

### Post by Toz on 2015-08-22
Not sure I'm going to be able to help since I don't use MS Office, but which version of Wine are you running and which version of Office have you installed?

Finally, can you detail the steps you take to get to the point that it crashes?

---

### Post by gravor on 2015-08-23
> **Toz said:**
> Not sure I'm going to be able to help since I don't use MS Office, but which version of Wine are you running and which version of Office have you installed?

Finally, can you detail the steps you take to get to the point that it crashes?

These are informations :

```

  Unhandled exception: page fault on read access to 0x0000007c in 32-bit code (0x7e62c120).Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e62c120 ESP:0033b760 EBP:0033b7a8 EFLAGS:00010212(  R- --  I   -A- - )
 EAX:0000007c EBX:7e6f2ab4 ECX:00000080 EDX:f75be428
 ESI:10663db8 EDI:0000000c
Stack dump:
0x0033b760:  1066425c 7db4fb30 0033b7b8 7c29ee5b
0x0033b770:  00000000 00000000 7db4fb30 ffffffff
0x0033b780:  1066425c 00000080 7db63135 0000007c
0x0033b790:  00000040 1064caf0 0033b7c0 7c2d1ce4
0x0033b7a0:  10663db8 0000000c 0033b838 7c29f1ef
0x0033b7b0:  10663da8 0000000c 0033b838 7c29f1ef
Backtrace:
=>0 0x7e62c120 SysFreeString+0x30() in oleaut32 (0x0033b7a8)
  1 0x7c29f1ef in msxml3 (+0x4f1ee) (0x0033b838)
  2 0x7baddced in libxml2.so.2 (+0x37cec) (0x7db43478)
  3 0x7bae42c8 in libxml2.so.2 (+0x3e2c7) (0x7dae2380)
  4 0x7bae59bc xmlParseChunk+0x13b() in libxml2.so.2 (0x7dae2380)
  5 0x7c2a04e6 in msxml3 (+0x504e5) (0x0033c2a8)
  6 0x7c2a06f3 in msxml3 (+0x506f2) (0x0033c318)
  7 0x7c2a0a9f in msxml3 (+0x50a9e) (0x0033c364)
  8 0x31b6581e in wwlib (+0x49581d) (0x0033d440)
  9 0x31eb12f4 in wwlib (+0x7e12f3) (0x0033d504)
  10 0x323fcbb3 in wwlib (+0xd2cbb2) (0x0033d938)
  11 0x323fcd8c in wwlib (+0xd2cd8b) (0x0033d950)
  12 0x323fcddd in wwlib (+0xd2cddc) (0x0033d9b4)
  13 0x39c3a252 in mso (+0xc3a251) (0x0033da04)
  14 0x39c3af57 in mso (+0xc3af56) (0x0033da40)
  15 0x39529da9 in mso (+0x529da8) (0x0033da5c)
  16 0x39529e18 in mso (+0x529e17) (0x0033dac0)
  17 0x391967c4 in mso (+0x1967c3) (0x0033dad4)
  18 0x390b34f6 in mso (+0xb34f5) (0x0033db3c)
  19 0x390b2f2d in mso (+0xb2f2c) (0x0033db64)
  20 0x390b2df2 in mso (+0xb2df1) (0x0033db70)
  21 0x3173c766 in wwlib (+0x6c765) (0x0033db84)
  22 0x3173c72f in wwlib (+0x6c72e) (0x0033dc00)
  23 0x31738f5e in wwlib (+0x68f5d) (0x0033dc14)
  24 0x31737386 in wwlib (+0x67385) (0x0033dc3c)
  25 0x317346d9 in wwlib (+0x646d8) (0x0033fdac)
  26 0x30001625 in winword (+0x1624) (0x0033fdd0)
  27 0x300015aa in winword (+0x15a9) (0x0033fe60)
  28 0x7b86249c call_process_entry+0xb() in kernel32 (0x0033fe78)
  29 0x7b865ffb in kernel32 (+0x55ffa) (0x0033feb8)
  30 0x7bc7da40 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  31 0x7bc7dc9d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  32 0x7bc7da1e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  33 0x7bc53dee in ntdll (+0x43ded) (0x0033ffe8)
0x7e62c120 SysFreeString+0x30 in oleaut32: movl    0xfffffffc(%ecx),%eax
Modules:
Module    Address            Debug info    Name (155 modules)
PE      5d0000-  833000    Deferred        msointl
PE      850000- 4d7a000    Deferred        msores
PE    10000000-1041a000    Deferred        office.odf
PE    30000000-3015d000    Export          winword
PE    316d0000-3294f000    Export          wwlib
PE    39000000-3a1ea000    Export          mso
PE    3a700000-3a7c9000    Deferred        wwintl
PE    42030000-4217f000    Deferred        riched20
PE    42280000-43614000    Deferred        oart
PE    437a0000-4394b000    Deferred        gfx
PE    44020000-441b4000    Deferred        ogl
PE    6bdc0000-6be7c000    Deferred        msptls
PE    6be90000-6beb0000    Deferred        osppc
PE    6bed0000-6c064000    Deferred        osppcext
ELF    7b800000-7ba4d000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba4d000    \               kernel32
ELF    7baa6000-7bc00000    Dwarf           libxml2.so.2
ELF    7bc00000-7bcd0000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcd0000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7c245000-7c2f3000    Dwarf           msxml3<elf>
  \-PE    7c250000-7c2f3000    \               msxml3
ELF    7c2f3000-7c400000    Deferred        actxprxy<elf>
  \-PE    7c310000-7c400000    \               actxprxy
ELF    7ce45000-7ce83000    Deferred        libxslt.so.1
ELF    7d014000-7d03a000    Deferred        liblzma.so.5
ELF    7d03a000-7d066000    Deferred        msxml6<elf>
  \-PE    7d040000-7d066000    \               msxml6
ELF    7d066000-7d087000    Deferred        localspl<elf>
  \-PE    7d070000-7d087000    \               localspl
ELF    7d087000-7d0d2000    Deferred        libdbus-1.so.3
ELF    7d0d2000-7d0de000    Deferred        libkrb5support.so.0
ELF    7d0de000-7d10e000    Deferred        libk5crypto.so.3
ELF    7d10e000-7d1cc000    Deferred        libkrb5.so.3
ELF    7d1cc000-7d1de000    Deferred        libavahi-client.so.3
ELF    7d1de000-7d1ec000    Deferred        libavahi-common.so.3
ELF    7d1ec000-7d231000    Deferred        libgssapi_krb5.so.2
ELF    7d231000-7d29e000    Deferred        libcups.so.2
ELF    7d2a2000-7d2bc000    Deferred        spoolss<elf>
  \-PE    7d2b0000-7d2bc000    \               spoolss
ELF    7d2bc000-7d2fb000    Deferred        winspool<elf>
  \-PE    7d2c0000-7d2fb000    \               winspool
ELF    7d2fb000-7d3bf000    Deferred        crypt32<elf>
  \-PE    7d310000-7d3bf000    \               crypt32
ELF    7d3bf000-7d3fc000    Deferred        rsaenh<elf>
  \-PE    7d3d0000-7d3fc000    \               rsaenh
ELF    7d3fc000-7d410000    Deferred        libtasn1.so.6
ELF    7d410000-7d440000    Deferred        p11-kit-trust.so
ELF    7d440000-7d47c000    Deferred        libp11-kit.so.0
ELF    7d47c000-7d502000    Deferred        libgcrypt.so.11
ELF    7d50d000-7d520000    Deferred        gnome-keyring-pkcs11.so
ELF    7d520000-7d5e9000    Deferred        libgnutls.so.26
ELF    7d5e9000-7d61b000    Deferred        ws2_32<elf>
  \-PE    7d5f0000-7d61b000    \               ws2_32
ELF    7d61b000-7d633000    Deferred        libresolv.so.2
ELF    7d633000-7d638000    Deferred        libcom_err.so.2
ELF    7d638000-7d63f000    Deferred        libffi.so.6
ELF    7d63f000-7d651000    Deferred        libtasn1.so.3
ELF    7d651000-7d675000    Deferred        iphlpapi<elf>
  \-PE    7d660000-7d675000    \               iphlpapi
ELF    7d675000-7d6a3000    Deferred        secur32<elf>
  \-PE    7d680000-7d6a3000    \               secur32
ELF    7d6a3000-7d742000    Deferred        msvcrt<elf>
  \-PE    7d6c0000-7d742000    \               msvcrt
ELF    7d742000-7d7a0000    Deferred        dbghelp<elf>
  \-PE    7d750000-7d7a0000    \               dbghelp
ELF    7d7a0000-7d7d3000    Deferred        mscoree<elf>
  \-PE    7d7b0000-7d7d3000    \               mscoree
ELF    7d7ea000-7d82c000    Deferred        usp10<elf>
  \-PE    7d7f0000-7d82c000    \               usp10
ELF    7d872000-7d88e000    Deferred        jsproxy<elf>
  \-PE    7d880000-7d88e000    \               jsproxy
ELF    7d88e000-7d8c5000    Deferred        winhttp<elf>
  \-PE    7d890000-7d8c5000    \               winhttp
ELF    7d8c5000-7d8e2000    Deferred        libgcc_s.so.1
ELF    7d8eb000-7d900000    Deferred        winscard<elf>
  \-PE    7d8f0000-7d900000    \               winscard
ELF    7da00000-7da2c000    Deferred        netapi32<elf>
  \-PE    7da10000-7da2c000    \               netapi32
ELF    7da2c000-7da4e000    Deferred        imm32<elf>
  \-PE    7da30000-7da4e000    \               imm32
ELF    7da94000-7dac7000    Deferred        uxtheme<elf>
  \-PE    7daa0000-7dac7000    \               uxtheme
ELF    7dac7000-7dacd000    Deferred        libxfixes.so.3
ELF    7dacd000-7dad8000    Deferred        libxcursor.so.1
ELF    7dbd8000-7dbe8000    Deferred        libxi.so.6
ELF    7dbe8000-7dbec000    Deferred        libxcomposite.so.1
ELF    7dbec000-7dbf7000    Deferred        libxrandr.so.2
ELF    7dbf7000-7dc02000    Deferred        libxrender.so.1
ELF    7dc02000-7dc08000    Deferred        libxxf86vm.so.1
ELF    7dc08000-7dc0c000    Deferred        libxinerama.so.1
ELF    7dc0c000-7dc13000    Deferred        libxdmcp.so.6
ELF    7dc13000-7dc35000    Deferred        libxcb.so.1
ELF    7dc35000-7dd69000    Deferred        libx11.so.6
ELF    7dd69000-7dd6d000    Deferred        libkeyutils.so.1
ELF    7dd6d000-7dd72000    Deferred        libgpg-error.so.0
ELF    7dd72000-7dd85000    Deferred        psapi<elf>
  \-PE    7dd80000-7dd85000    \               psapi
ELF    7dd87000-7de12000    Deferred        winex11<elf>
  \-PE    7dd90000-7de12000    \               winex11
ELF    7de12000-7de31000    Deferred        cabinet<elf>
  \-PE    7de20000-7de31000    \               cabinet
ELF    7de31000-7df2a000    Deferred        comctl32<elf>
  \-PE    7de40000-7df2a000    \               comctl32
ELF    7df2a000-7df4f000    Deferred        mpr<elf>
  \-PE    7df30000-7df4f000    \               mpr
ELF    7df4f000-7dfc3000    Deferred        wininet<elf>
  \-PE    7df60000-7dfc3000    \               wininet
ELF    7dfc3000-7e1e2000    Deferred        shell32<elf>
  \-PE    7dfd0000-7e1e2000    \               shell32
ELF    7e1e2000-7e275000    Deferred        urlmon<elf>
  \-PE    7e1f0000-7e275000    \               urlmon
ELF    7e2b8000-7e2bc000    Deferred        libxau.so.6
ELF    7e2bc000-7e2cf000    Deferred        libxext.so.6
ELF    7e2cf000-7e33f000    Deferred        shlwapi<elf>
  \-PE    7e2e0000-7e33f000    \               shlwapi
ELF    7e33f000-7e42b000    Deferred        msi<elf>
  \-PE    7e350000-7e42b000    \               msi
ELF    7e476000-7e49f000    Deferred        libexpat.so.1
ELF    7e49f000-7e4da000    Deferred        libfontconfig.so.1
ELF    7e4da000-7e502000    Deferred        libpng12.so.0
ELF    7e502000-7e51b000    Deferred        libz.so.1
ELF    7e51b000-7e5bb000    Deferred        libfreetype.so.6
ELF    7e5d9000-7e5ec000    Deferred        msimg32<elf>
  \-PE    7e5e0000-7e5ec000    \               msimg32
ELF    7e5ec000-7e602000    Deferred        wtsapi32<elf>
  \-PE    7e5f0000-7e602000    \               wtsapi32
ELF    7e602000-7e719000    Dwarf           oleaut32<elf>
  \-PE    7e620000-7e719000    \               oleaut32
ELF    7e719000-7e793000    Deferred        rpcrt4<elf>
  \-PE    7e720000-7e793000    \               rpcrt4
ELF    7e793000-7e8db000    Deferred        user32<elf>
  \-PE    7e7b0000-7e8db000    \               user32
ELF    7e8db000-7e9f3000    Deferred        ole32<elf>
  \-PE    7e8f0000-7e9f3000    \               ole32
ELF    7e9f3000-7eb01000    Deferred        gdi32<elf>
  \-PE    7ea00000-7eb01000    \               gdi32
ELF    7eb01000-7ebaa000    Deferred        msvcr90<elf>
  \-PE    7eb20000-7ebaa000    \               msvcr90
ELF    7ebd0000-7ec37000    Deferred        advapi32<elf>
  \-PE    7ebe0000-7ec37000    \               advapi32
ELF    7efa7000-7efb4000    Deferred        libnss_files.so.2
ELF    7efb4000-7efc0000    Deferred        libnss_nis.so.2
ELF    7efc0000-7efd9000    Deferred        libnsl.so.1
ELF    7efd9000-7efe2000    Deferred        libnss_compat.so.2
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f73c9000-f740f000    Deferred        libm.so.6
ELF    f740f000-f7414000    Deferred        libdl.so.2
ELF    f7414000-f75c2000    Deferred        libc.so.6
ELF    f75c2000-f75de000    Deferred        libpthread.so.0
ELF    f75f4000-f75fd000    Deferred        librt.so.1
ELF    f75fd000-f77b1000    Dwarf           libwine.so.1
ELF    f77b3000-f77d5000    Deferred        ld-linux.so.2
ELF    f77d5000-f77d6000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Microsoft Office\Office14\WINWORD.EXE
    00000079    0
    00000078    0
    00000077    0
    00000076    0
    00000075    0
    00000074    0
    00000073    0
    00000072    0
    00000071    0
    00000070    0
    0000006f    0
    0000006e    0
    0000006d    0
    0000006c    0
    0000006b    0
    00000068    0
    00000067    0
    00000066    0
    00000065    0
    0000005a    0
    00000059    0
    00000023   -2
    00000009    0 <==
0000000e services.exe
    0000002a    0
    00000029    0
    00000028    0
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
    00000021    0
00000026 OSPPSVC.EXE
    0000006a    0
    00000069    0
    00000057    0
    00000055    0
    00000053    0
    00000051    0
    0000004f    0
    0000004d    0
    0000004b    0
    00000049    0
    00000024    0
    0000000b    0
    0000000c    0
    00000046    0
    00000044    0
    00000042    0
    00000040    0
    0000003e    0
    0000003c    0
    0000003a    0
    00000038    0
    00000036    0
    00000034    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0
    0000002f    0
    0000002d    0
    0000002c    0
    0000002b    0
    00000027    0
0000005b rpcss.exe
    00000064    0
    00000063    0
    00000062    0
    00000061    0
    00000060    0
    0000005f    0
    0000005d    0
    0000005c    0
0000007d winedbg.exe
    0000007f    0
System information:
    Wine build: wine-1.7.22
    Platform: i386
    Host system: Linux
    Host version: 3.16.0-46-generic

```

And my wine version is 1.7.44
It happens when I want to use matrix.

---

