---
title: "Xubuntu 12.04: wine internal errors - invalid parameters received"
date: 2012-05-06
forum: Wine
---

### Post by Cæncel on 2012-05-06
Hi, my problem is that i can't install anything via Wine no matter what version of Wine i'm using, also deleting the ".wine" folder does nothing so i'm quite confused because some days back everything ran good, i could install Flash 8 and Bejeweled 3, every time i try to run an "exe" program for installation i have this output:

```
$ wine "Bejeweled 3.exe"
err:virtual:map_image failed to set 60000020 protection on section .text, noexec filesystem?
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
wine: Unhandled page fault on read access to 0x00402fb9 at address 0x402fb9 (thread 0009), starting debugger...
err:virtual:map_file_into_view failed to set 00000005 protection on file map, noexec filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x340000 c932000 000000000 failed
couldn't load main module (5)
Unhandled exception: page fault on read access to 0x00402fb9 in 32-bit code (0x00402fb9).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00402fb9 ESP:0032fe74 EBP:0032fe88 EFLAGS:00210212(  R- --  I   -A- - )
 EAX:00000000 EBX:7b89aff4 ECX:0032fef0 EDX:0032fef0
 ESI:7ffdf000 EDI:00402fb9
Stack dump:
0x0032fe74:  7b85a5ac 7ffdf000 7bc4bd4a 7b89aff4
0x0032fe84:  7ffdf000 0032fec8 7b85b81f 7ffdf000
0x0032fe94:  00402fb9 00000000 00000000 00000000
0x0032fea4:  00000000 00000000 00000000 00000000
0x0032feb4:  00000000 00000000 7bca6ff4 bffca514
0x0032fec4:  001107c8 0032fed8 7bc71d80 7ffdf000
Backtrace:
=>0 0x00402fb9 (0x0032fe88)
  1 0x7b85b81f in kernel32 (+0x4b81e) (0x0032fec8)
  2 0x7bc71d80 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  3 0x7bc7485d call_thread_func+0x7c() in ntdll (0x0032ffa8)
  4 0x7bc71d5e RtlRaiseException+0x21() in ntdll (0x0032ffc8)
  5 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0032ffe8)
0x00402fb9: call    0x00405dea
Modules:
Module    Address            Debug info    Name (59 modules)
PE    71590000-71617000    Deferred        comctl32
ELF    7b800000-7ba2f000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba2f000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e296000-7e30b000    Deferred        rpcrt4<elf>
  \-PE    7e2a0000-7e30b000    \               rpcrt4
ELF    7e30b000-7e413000    Deferred        ole32<elf>
  \-PE    7e320000-7e413000    \               ole32
ELF    7e429000-7e42f000    Deferred        libxfixes.so.3
ELF    7e42f000-7e43a000    Deferred        libxcursor.so.1
ELF    7e4c4000-7e4ee000    Deferred        libexpat.so.1
ELF    7e4ee000-7e522000    Deferred        libfontconfig.so.1
ELF    7e522000-7e532000    Deferred        libxi.so.6
ELF    7e532000-7e536000    Deferred        libxcomposite.so.1
ELF    7e536000-7e53f000    Deferred        libxrandr.so.2
ELF    7e53f000-7e549000    Deferred        libxrender.so.1
ELF    7e549000-7e54f000    Deferred        libxxf86vm.so.1
ELF    7e54f000-7e553000    Deferred        libxinerama.so.1
ELF    7e553000-7e575000    Deferred        imm32<elf>
  \-PE    7e560000-7e575000    \               imm32
ELF    7e575000-7e57c000    Deferred        libxdmcp.so.6
ELF    7e57c000-7e59d000    Deferred        libxcb.so.1
ELF    7e59d000-7e5b7000    Deferred        libice.so.6
ELF    7e5b7000-7e6eb000    Deferred        libx11.so.6
ELF    7e6eb000-7e6fd000    Deferred        libxext.so.6
ELF    7e6fd000-7e706000    Deferred        libsm.so.6
ELF    7e706000-7e78f000    Deferred        winex11<elf>
  \-PE    7e710000-7e78f000    \               winex11
ELF    7e78f000-7e7a5000    Deferred        libz.so.1
ELF    7e7a5000-7e83f000    Deferred        libfreetype.so.6
ELF    7e83f000-7e85e000    Deferred        libtinfo.so.5
ELF    7e85e000-7e880000    Deferred        libncurses.so.5
ELF    7e89e000-7e908000    Deferred        shlwapi<elf>
  \-PE    7e8b0000-7e908000    \               shlwapi
ELF    7e908000-7eb1a000    Deferred        shell32<elf>
  \-PE    7e910000-7eb1a000    \               shell32
ELF    7eb1a000-7eb7c000    Deferred        advapi32<elf>
  \-PE    7eb30000-7eb7c000    \               advapi32
ELF    7eb7c000-7ec3a000    Deferred        gdi32<elf>
  \-PE    7eb90000-7ec3a000    \               gdi32
ELF    7ec3a000-7ed7a000    Deferred        user32<elf>
  \-PE    7ec50000-7ed7a000    \               user32
ELF    7ef7a000-7ef87000    Deferred        libnss_files.so.2
ELF    7ef87000-7ef93000    Deferred        libnss_nis.so.2
ELF    7ef93000-7efad000    Deferred        libnsl.so.1
ELF    7efad000-7efb6000    Deferred        libnss_compat.so.2
ELF    7efb6000-7efe2000    Deferred        libm.so.6
ELF    7efe3000-7efe7000    Deferred        libxau.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    b7463000-b7468000    Deferred        libdl.so.2
ELF    b7468000-b760d000    Deferred        libc.so.6
ELF    b760e000-b7629000    Deferred        libpthread.so.0
ELF    b7640000-b7646000    Deferred        libuuid.so.1
ELF    b7647000-b7789000    Dwarf           libwine.so.1
ELF    b778b000-b77ad000    Deferred        ld-linux.so.2
ELF    b77ad000-b77ae000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\H.Misc\Bejeweled 3\Bejeweled 3.exe
    00000009    0 <==
0000000e services.exe
    00000029    0
    00000028    0
    00000021    0
    00000019    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 mscorsvw.exe
    0000001b    0
    0000001a    0
    00000014    0
    00000013    0
0000001c winedevice.exe
    00000024    0
    00000023    0
    00000020    0
    0000001d    0
0000001e explorer.exe
    0000001f    0
00000025 plugplay.exe
    0000002a    0
    00000027    0
    00000026    0

```

i have no clue what is going on and i tried searching in google, i have no problems with programs that i had installed before like WinKawaks or Mugen, i also tried using another kernel but it makes no difference, any help would be appreciated.

---

### Post by spiralofhope on 2012-05-06
Well I had a nice reply but this craptastic forum ate it.

Same issue, lubuntu.  World of Warcraft in my case.
also tried wine 1.5 beta, see [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by ringo28 on 2012-05-06
hmmm in my case i had on xubuntu11.10 need for speed most wanted.. i upgraded to xubuntu12 then i get internal error.. strangly my football manager 2006 still working..


seems to be a Direx problem?? i tried new and old wine and different versions of windows from xp too 2008rc , .....



what next?

---

### Post by spiralofhope on 2012-05-06
> **ringo28 said:**
> seems to be a Direx problem?? i tried new and old wine and different versions of windows from xp too 2008rc , .....

what next?

Perhaps getting directx?

```
\sudo \apt-get install winetricks
\winetricks d3dx9

```I'm trying this now.

edit:  No luck, but it explodes differently:

```
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0033fbe4 EBP:0033fc44 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:000083f1 EBX:00008000 ECX:00000de1 EDX:1d19d7d0
 ESI:00000000 EDI:1cdf4c60
Stack dump:
0x0033fbe4:  00868f05 00000de1 00000000 000083f1
0x0033fbf4:  00000100 00000100 00000000 00008000
0x0033fc04:  1d19d7d0 00000100 1cdf4c60 00000100
0x0033fc14:  00000000 00000000 00000100 00000100
0x0033fc24:  0000813d 00000008 00000000 00000200
0x0033fc34:  1d1a57d0 00008000 1d19d7d0 000083f1
Backtrace:
=>0 0x00000000 (0x0033fc44)
  1 0x00869119 in wow (+0x469118) (0x0033fc98)
  2 0x008691c2 in wow (+0x4691c1) (0x0033fca8)
  3 0x00843aea in wow (+0x443ae9) (0x0033fcb4)
  4 0x00840ea5 in wow (+0x440ea4) (0x0033fcd8)
  5 0x006fada0 in wow (+0x2fad9f) (0x0033fd18)
  6 0x008a3e09 in wow (+0x4a3e08) (0x0033fd48)
  7 0x008a0d8c in wow (+0x4a0d8b) (0x0033fd70)
  8 0x008a240a in wow (+0x4a2409) (0x0033fdc4)
  9 0x008a2451 in wow (+0x4a2450) (0x0033fddc)
  10 0x00408458 in wow (+0x8457) (0x0033fe70)
  11 0x7b85a5ac call_process_entry+0xb() in kernel32 (0x0033fe88)
  12 0x7b85b81f in kernel32 (+0x4b81e) (0x0033fec8)
  13 0x7bc71d80 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  14 0x7bc7485d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  15 0x7bc71d5e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  16 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x00000000: -- no code accessible --
Modules:
Module    Address            Debug info    Name (155 modules)
PE      400000- 10dc000    Export          wow
PE    3c910000-3cbc4000    Deferred        battle.net
ELF    7a4a9000-7b800000    Deferred        libllvm-3.0.so.1
ELF    7b800000-7ba2f000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba2f000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c0b8000-7c0cb000    Deferred        gnome-keyring-pkcs11.so
ELF    7c0cb000-7c0d0000    Deferred        libgpg-error.so.0
ELF    7c0d0000-7c0e8000    Deferred        libresolv.so.2
ELF    7c0e8000-7c0ec000    Deferred        libkeyutils.so.1
ELF    7c0ec000-7c135000    Deferred        libdbus-1.so.3
ELF    7c135000-7c147000    Deferred        libp11-kit.so.0
ELF    7c147000-7c1cc000    Deferred        libgcrypt.so.11
ELF    7c1cc000-7c1de000    Deferred        libtasn1.so.3
ELF    7c1de000-7c1e7000    Deferred        libkrb5support.so.0
ELF    7c1e7000-7c20f000    Deferred        libk5crypto.so.3
ELF    7c20f000-7c2de000    Deferred        libkrb5.so.3
ELF    7c2de000-7c2f0000    Deferred        libavahi-client.so.3
ELF    7c2f0000-7c2fe000    Deferred        libavahi-common.so.3
ELF    7c2fe000-7c3c2000    Deferred        libgnutls.so.26
ELF    7c3c2000-7c400000    Deferred        libgssapi_krb5.so.2
ELF    7c405000-7c458000    Deferred        libcups.so.2
ELF    7c458000-7c48c000    Deferred        uxtheme<elf>
  \-PE    7c460000-7c48c000    \               uxtheme
ELF    7d022000-7d040000    Deferred        libgcc_s.so.1
ELF    7d051000-7d410000    Deferred        libgallium.so
ELF    7d410000-7d52d000    Deferred        libglsl.so
ELF    7d52d000-7d7a6000    Deferred        libdricore.so
ELF    7d7a6000-7da66000    Deferred        r600_dri.so
ELF    7da66000-7da71000    Deferred        libxcursor.so.1
ELF    7da74000-7da79000    Deferred        libcom_err.so.2
ELF    7da79000-7da80000    Deferred        libffi.so.6
ELF    7dacc000-7daf6000    Deferred        libexpat.so.1
ELF    7daf6000-7db2a000    Deferred        libfontconfig.so.1
ELF    7db2a000-7db3a000    Deferred        libxi.so.6
ELF    7db3a000-7db3e000    Deferred        libxcomposite.so.1
ELF    7db3e000-7db47000    Deferred        libxrandr.so.2
ELF    7db47000-7db51000    Deferred        libxrender.so.1
ELF    7dc51000-7dcda000    Deferred        winex11<elf>
  \-PE    7dc60000-7dcda000    \               winex11
ELF    7dcda000-7dd74000    Deferred        libfreetype.so.6
ELF    7dd74000-7dd93000    Deferred        libtinfo.so.5
ELF    7dd93000-7ddb5000    Deferred        libncurses.so.5
ELF    7ddb5000-7dddd000    Deferred        msacm32<elf>
  \-PE    7ddc0000-7dddd000    \               msacm32
ELF    7dddd000-7de8a000    Deferred        winmm<elf>
  \-PE    7dde0000-7de8a000    \               winmm
ELF    7de8a000-7dec5000    Deferred        winspool<elf>
  \-PE    7de90000-7dec5000    \               winspool
ELF    7dec5000-7df2c000    Deferred        setupapi<elf>
  \-PE    7ded0000-7df2c000    \               setupapi
ELF    7df2c000-7dfa1000    Deferred        rpcrt4<elf>
  \-PE    7df40000-7dfa1000    \               rpcrt4
ELF    7dfc4000-7dfc8000    Deferred        libxinerama.so.1
ELF    7dfc8000-7dfdd000    Deferred        hid<elf>
  \-PE    7dfd0000-7dfdd000    \               hid
ELF    7dfdd000-7e0e5000    Deferred        ole32<elf>
  \-PE    7dff0000-7e0e5000    \               ole32
ELF    7e0e5000-7e101000    Deferred        dinput8<elf>
  \-PE    7e0f0000-7e101000    \               dinput8
ELF    7e101000-7e133000    Deferred        ws2_32<elf>
  \-PE    7e110000-7e133000    \               ws2_32
ELF    7e133000-7e22c000    Deferred        comctl32<elf>
  \-PE    7e140000-7e22c000    \               comctl32
ELF    7e22c000-7e43e000    Deferred        shell32<elf>
  \-PE    7e240000-7e43e000    \               shell32
ELF    7e43e000-7e4a8000    Deferred        shlwapi<elf>
  \-PE    7e450000-7e4a8000    \               shlwapi
ELF    7e4a8000-7e4ce000    Deferred        mpr<elf>
  \-PE    7e4b0000-7e4ce000    \               mpr
ELF    7e4ce000-7e4e4000    Deferred        libz.so.1
ELF    7e4e4000-7e553000    Deferred        wininet<elf>
  \-PE    7e4f0000-7e553000    \               wininet
ELF    7e553000-7e575000    Deferred        imm32<elf>
  \-PE    7e560000-7e575000    \               imm32
ELF    7e575000-7e6a7000    Deferred        wined3d<elf>
  \-PE    7e580000-7e6a7000    \               wined3d
ELF    7e6a7000-7e6df000    Deferred        d3d9<elf>
  \-PE    7e6b0000-7e6df000    \               d3d9
ELF    7e6df000-7e6e8000    Deferred        librt.so.1
ELF    7e6e8000-7e6ef000    Deferred        libxdmcp.so.6
ELF    7e6ef000-7e6f3000    Deferred        libxau.so.6
ELF    7e6f3000-7e700000    Deferred        libdrm.so.2
ELF    7e700000-7e706000    Deferred        libxxf86vm.so.1
ELF    7e706000-7e727000    Deferred        libxcb.so.1
ELF    7e727000-7e73f000    Deferred        libxcb-glx.so.0
ELF    7e73f000-7e873000    Deferred        libx11.so.6
ELF    7e873000-7e876000    Deferred        libx11-xcb.so.1
ELF    7e876000-7e87c000    Deferred        libxfixes.so.3
ELF    7e87c000-7e880000    Deferred        libxdamage.so.1
ELF    7e880000-7e892000    Deferred        libxext.so.6
ELF    7e892000-7e8a8000    Deferred        libglapi.so.0
ELF    7e8a8000-7e8c2000    Deferred        libice.so.6
ELF    7e8c2000-7e91b000    Deferred        libgl.so.1
ELF    7e91b000-7e924000    Deferred        libsm.so.6
ELF    7e924000-7e9de000    Deferred        opengl32<elf>
  \-PE    7e940000-7e9de000    \               opengl32
ELF    7e9de000-7e9f7000    Deferred        version<elf>
  \-PE    7e9e0000-7e9f7000    \               version
ELF    7e9f7000-7ea59000    Deferred        advapi32<elf>
  \-PE    7ea00000-7ea59000    \               advapi32
ELF    7ea59000-7eb17000    Deferred        gdi32<elf>
  \-PE    7ea70000-7eb17000    \               gdi32
ELF    7eb17000-7ec57000    Deferred        user32<elf>
  \-PE    7eb30000-7ec57000    \               user32
ELF    7ef90000-7ef9d000    Deferred        libnss_files.so.2
ELF    7ef9d000-7efa9000    Deferred        libnss_nis.so.2
ELF    7efa9000-7efc3000    Deferred        libnsl.so.1
ELF    7efc3000-7efef000    Deferred        libm.so.6
ELF    7eff1000-7eff7000    Deferred        libuuid.so.1
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    b171d000-b177b000    Deferred        dbghelp<elf>
  \-PE    b1720000-b177b000    \               dbghelp
ELF    b177b000-b17b3000    Deferred        winhttp<elf>
  \-PE    b1780000-b17b3000    \               winhttp
ELF    b17b3000-b186d000    Deferred        crypt32<elf>
  \-PE    b17c0000-b186d000    \               crypt32
ELF    b186d000-b18fb000    Deferred        msvcrt<elf>
  \-PE    b1880000-b18fb000    \               msvcrt
ELF    b1e66000-b1e88000    Deferred        iphlpapi<elf>
  \-PE    b1e70000-b1e88000    \               iphlpapi
ELF    b1e88000-b1eb7000    Deferred        msvcr90<elf>
  \-PE    b1e90000-b1eb7000    \               msvcr90
ELF    b1eb7000-b1ee2000    Deferred        msvcr80<elf>
  \-PE    b1ec0000-b1ee2000    \               msvcr80
ELF    b6071000-b6085000    Deferred        psapi<elf>
  \-PE    b6080000-b6085000    \               psapi
ELF    b6092000-b609a000    Deferred        libogg.so.0
ELF    b609a000-b60c5000    Deferred        libvorbis.so.0
ELF    b60c5000-b623d000    Deferred        libvorbisenc.so.2
ELF    b623d000-b628b000    Deferred        libflac.so.8
ELF    b628b000-b62fd000    Deferred        libsndfile.so.1
ELF    b62fd000-b6307000    Deferred        libwrap.so.0
ELF    b6307000-b636c000    Deferred        libpulsecommon-1.1.so
ELF    b636c000-b6374000    Deferred        libjson.so.0
ELF    b6374000-b63c2000    Deferred        libpulse.so.0
ELF    b63c2000-b63e8000    Deferred        winepulse<elf>
  \-PE    b63d0000-b63e8000    \               winepulse
ELF    b63e8000-b64da000    Deferred        oleaut32<elf>
  \-PE    b6400000-b64da000    \               oleaut32
ELF    b64da000-b64fd000    Deferred        mmdevapi<elf>
  \-PE    b64e0000-b64fd000    \               mmdevapi
ELF    b7400000-b7407000    Deferred        libasyncns.so.0
ELF    b7418000-b745c000    Deferred        dsound<elf>
  \-PE    b7420000-b745c000    \               dsound
ELF    b7484000-b748b000    Deferred        libnss_dns.so.2
ELF    b748b000-b748f000    Deferred        libnss_mdns4_minimal.so.2
ELF    b74a1000-b74a6000    Deferred        libdl.so.2
ELF    b74a6000-b764b000    Deferred        libc.so.6
ELF    b764c000-b7667000    Deferred        libpthread.so.0
ELF    b7678000-b77ba000    Dwarf           libwine.so.1
ELF    b77bc000-b77de000    Deferred        ld-linux.so.2
ELF    b77de000-b77df000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\1\wow\_game\Wow.exe
    0000004b    0
    0000004a    0
    00000049    0
    00000048    0
    00000030    0
    0000000d    0
    0000000b    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003f    0
    0000003b    1
    00000038    1
    00000036    0
    00000035    0
    00000034    0
    00000033    2
    00000032   15
    00000031   15
    0000002f    0
    0000002e    0
    0000002d   15
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
    00000028    0
    00000027    0
    00000026    0
    00000024    0
    00000009    0 <==
0000000e services.exe
    0000001f    0
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
00000021 explorer.exe
    00000022    0
System information:
    Wine build: wine-1.5.3
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-24-generic-pae

```

---

### Post by Toz on 2012-05-06
> err:virtual:map_image failed to set 60000020 protection on section .text, **[COLOR="Red"]noexec filesystem[/COLOR]**?

On what filesytem/drive are you running this on? The filesystem/drive doesn't appear to be set executable. Can you maybe try copying the file to ~/Downloads and running it from there?

Also, how are you running ubuntu? LiveCD? wubi? installed on HD?

---

### Post by Cæncel on 2012-05-06
> **Toz said:**
> On what filesytem/drive are you running this on? The filesystem/drive doesn't appear to be set executable. Can you maybe try copying the file to ~/Downloads and running it from there?

Also, how are you running ubuntu? LiveCD? wubi? installed on HD?

oh! indeed it may be related to partitions, i have Xubuntu installed in my hard drive and at the time of installing Bejeweled 3 i had the installation executable at ~/Downloads that's why the program installed flawlessly, but then i moved the executable to a permanent location in a secondary partition, file system EXT3 that i use as my main storage location, that filesystem may be actually the one protected, this solves the mistery, many thanks!

---

### Post by spiralofhope on 2012-05-06
I'm glad it worked out for you.

It turns out that my issue was very different.  Permissions were all working correctly, but on a hunch I decided to install my proprietary video drivers.  I'm working fine now.

---

### Post by Cæncel on 2012-05-06
silly question, how do i setup my filesystem properly? i tought it would be enough with Mount Manager but either is not saving the changes i'm doing or i'm needing changes that are not included, in this partition i have some programs installed like mugen and winkawaks and i can run them without problems, that means i'm able to run binaries and executables but not installers, how is this? never mind, indeed the problem comes from wine itself

[http://forum.winehq.org/viewtopic.php?p=75766#75766](http://forum.winehq.org/viewtopic.php?p=75766#75766)

---

### Post by Cæncel on 2012-05-06
i just added this line in my fstab file

atime,suid,mand,users,auto,rw,dev,exec,async,noacl,orlov,nouser_xattr,nocheck,errors=remount-ro,nogrpid,commit=5

the "exec" was all what i needed but on my way i added some other things, thanks for the support!

---

### Post by Toz on 2012-05-06
No worries, glad it worked out for you. If you don't mind, can you mark this thread as Solved from the "Thread Tools" link above so others can find it when searching?

---

### Post by raj7749 on 2012-05-07
i am trying to install oracle 8i client in wine and i facing the same issue "internal errors - invalid parameters received". please need help... tried installing older version of wine with clean .wine folder... still facing the prob.. m using 12.04 LTS...

---

### Post by Toz on 2012-05-07
> **raj7749 said:**
> i am trying to install oracle 8i client in wine and i facing the same issue "internal errors - invalid parameters received". please need help... tried installing older version of wine with clean .wine folder... still facing the prob.. m using 12.04 LTS...

Why are you installing oracle in wine??? Why not use the native linux client? (See: [http://www.oracle.com/us/technologies/linux/index.html]("http://www.oracle.com/us/technologies/linux/index.html"))

---

### Post by Smakone on 2012-05-08
Also experiencing this issue

Read more about the issue here

[http://ubuntuforums.org/showthread.php?t=1969597&page=2](http://ubuntuforums.org/showthread.php?t=1969597&page=2)

Would appreciate a solution I have tried almost everything

---

