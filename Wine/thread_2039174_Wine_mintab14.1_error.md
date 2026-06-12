---
title: "Wine mintab14.1 error"
date: 2012-08-08
forum: Wine
---

### Post by stangw on 2012-08-08
it can run and generate random data , but when a use to calculate the cpk it generate error like this :
Unhandled exception: page fault on read access to 0x0802a2b2 in 32-bit code (0x02958698).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:02958698 ESP:0033f394 EBP:0033f3d8 EFLAGS:00210202(  R- --  I   - - - )
 EAX:02a2b2a0 EBX:00000000 ECX:02958698 EDX:0275e5d0
 ESI:00000001 EDI:0033f3b4
Stack dump:
0x0033f394:  30002e97 00000001 0033f684 029518e8
0x0033f3a4:  00000000 30002268 0033f3b4 310137a8
0x0033f3b4:  b9587a30 02a278a0 02a278a4 02a278a4
0x0033f3c4:  0275e5d0 3000220a 0033f408 30024a44
0x0033f3d4:  00000000 0033f414 31006076 0033f684
0x0033f3e4:  029a83f8 00000000 fffffff0 462f2a28
Backtrace:
=>0 0x02958698 (0x0033f3d8)
  1 0x31006076 in mtb14cmndframework (+0x6075) (0x0033f414)
  2 0x31002f8e in mtb14cmndframework (+0x2f8d) (0x0033f690)
  3 0x006ba8fc in mtb14 (+0x2ba8fb) (0x0033f7a4)
  4 0x0045d945 in mtb14 (+0x5d944) (0x0033f8d0)
  5 0x004be5b4 in mtb14 (+0xbe5b3) (0x0033f8fc)
  6 0x00916b24 in mtb14 (+0x516b23) (0x0033f944)
  7 0x005f222f in mtb14 (+0x1f222e) (0x0033f9d8)
  8 0x5f848eaa in mfc42lu (+0x48ea9) (0x0033f9f8)
  9 0x005f2077 in mtb14 (+0x1f2076) (0x0033fb18)
  10 0x5f847e09 in mfc42lu (+0x47e08) (0x0033fb78)
  11 0x5f84800c in mfc42lu (+0x4800b) (0x0033fb94)
  12 0x5f8708b1 in mfc42lu (+0x708b0) (0x0033fbc0)
  13 0x7eba9f8a WINPROC_wrapper+0x19() in user32 (0x0033fbf0)
  14 0x7ebaa6dc in user32 (+0x9a6db) (0x0033fc40)
  15 0x7ebacced in user32 (+0x9ccec) (0x0033fc90)
  16 0x7eb6ec9e DispatchMessageW+0x9d() in user32 (0x0033fd80)
  17 0x5f84dc06 in mfc42lu (+0x4dc05) (0x00b64b44)
  18 0x00000111 (0x0001017e)
0x02958698: movb    0x0802a2b2,%al
Modules:
Module    Address            Debug info    Name (172 modules)
PE      340000-  348000    Deferred        mtb14unicows
PE      350000-  372000    Deferred        mtb14utl
PE      380000-  3a7000    Deferred        mtb14edt
PE      3b0000-  3ca000    Deferred        mtb14rch
PE      400000-  f3e000    Export          mtb14
PE      f40000- 101c000    Deferred        mtb14bcg
PE     1020000- 1184000    Deferred        mtb14oxs
PE     1190000- 1286000    Deferred        mtb14hvw
PE     1290000- 12d1000    Deferred        mtb14sed
PE     12e0000- 135f000    Deferred        mtb14hob
PE     1360000- 13c9000    Deferred        ltkrn12n
PE     13d0000- 1413000    Deferred        r2netdll
PE     20c0000- 224a000    Deferred        mtb14resources
PE    10000000-10073000    Deferred        dformd
PE    1c000000-1c2e6000    Deferred        mtb14gr
PE    1ffc0000-1ffe6000    Deferred        ltfil12n
PE    20000000-20009000    Deferred        mtb14bt
PE    21000000-210f6000    Deferred        mtb14dlg
PE    22000000-2200c000    Deferred        mtb14messaging
PE    23000000-23027000    Deferred        mtb14streams
PE    24000000-24038000    Deferred        mtb14strings
PE    25000000-2500d000    Deferred        mtb14msg
PE    26000000-2605b000    Deferred        mtb14math
PE    27000000-2700a000    Deferred        mtb14exceptions
PE    28000000-28007000    Deferred        mtb14memory
PE    29000000-29042000    Deferred        mtb14mvt
PE    2a000000-2a01f000    Deferred        mtb14gui
PE    2b000000-2b01e000    Deferred        mtb14datetime
PE    2c000000-2c00b000    Deferred        mtb14observer
PE    2d000000-2d011000    Deferred        mtb14format
PE    2e000000-2e071000    Deferred        mtb14book
PE    2f000000-2f03b000    Deferred        mtb14cdl
PE    30000000-30059000    Deferred        mtb14out
PE    31000000-31017000    Export          mtb14cmndframework
PE    32000000-3200b000    Deferred        mtb14sortcmnd
PE    36000000-36035000    Deferred        mtb14io
PE    37000000-37073000    Deferred        mtb14ged
PE    38000000-3800d000    Deferred        mtb14dde
PE    3b000000-3b05f000    Deferred        mtb14statutil
PE    3c000000-3c03f000    Deferred        mtb14workvar
PE    3d000000-3d017000    Deferred        mtb14graphicsftn
PE    3e000000-3e033000    Deferred        mtb14cdlvalidation
PE    3f000000-3f343000    Deferred        mtb14graphicscmnd
PE    41000000-41033000    Deferred        mtb14prefs
PE    42000000-4200f000    Deferred        mtb14graphattributes
PE    43000000-43549000    Deferred        mtb14graphics
PE    5f800000-5f8f8000    Export          mfc42lu
PE    78000000-7803f000    Deferred        mslurt
PE    780c0000-78120000    Deferred        mslup60
ELF    7b800000-7ba15000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c715000-7c729000    Deferred        comm.drv16.so
PE    7c720000-7c729000    Deferred        comm.drv16
ELF    7c92a000-7c9c9000    Deferred        krnl386.exe16.so
PE    7c940000-7c9c9000    Deferred        krnl386.exe16
ELF    7c9c9000-7c9f1000    Deferred        msacm32<elf>
  \-PE    7c9d0000-7c9f1000    \               msacm32
ELF    7c9f1000-7ca9e000    Deferred        winmm<elf>
  \-PE    7ca00000-7ca9e000    \               winmm
ELF    7d03b000-7d094000    Deferred        riched20<elf>
  \-PE    7d040000-7d094000    \               riched20
ELF    7d094000-7d0c8000    Deferred        vbscript<elf>
  \-PE    7d0a0000-7d0c8000    \               vbscript
ELF    7d0c8000-7d100000    Deferred        usp10<elf>
  \-PE    7d0d0000-7d100000    \               usp10
ELF    7d205000-7d21a000    Deferred        system.drv16.so
PE    7d210000-7d21a000    Deferred        system.drv16
ELF    7d21a000-7d22e000    Deferred        riched32<elf>
  \-PE    7d220000-7d22e000    \               riched32
ELF    7d22e000-7d34b000    Deferred        libglsl.so
ELF    7d34b000-7d5c4000    Deferred        libdricore.so
ELF    7d764000-7d76f000    Deferred        libpciaccess.so.0
ELF    7d76f000-7d78e000    Deferred        libdrm_intel.so.1
ELF    7d78e000-7d86d000    Deferred        i965_dri.so
ELF    7d86d000-7d880000    Deferred        gnome-keyring-pkcs11.so
ELF    7d880000-7d885000    Deferred        libgpg-error.so.0
ELF    7d885000-7d89d000    Deferred        libresolv.so.2
ELF    7d89d000-7d8a1000    Deferred        libkeyutils.so.1
ELF    7d8a1000-7d8ea000    Deferred        libdbus-1.so.3
ELF    7d8ea000-7d8fc000    Deferred        libp11-kit.so.0
ELF    7d8fc000-7d981000    Deferred        libgcrypt.so.11
ELF    7d981000-7d993000    Deferred        libtasn1.so.3
ELF    7d993000-7d99c000    Deferred        libkrb5support.so.0
ELF    7d99c000-7d9a1000    Deferred        libcom_err.so.2
ELF    7d9a1000-7d9c9000    Deferred        libk5crypto.so.3
ELF    7d9c9000-7da98000    Deferred        libkrb5.so.3
ELF    7da98000-7daaa000    Deferred        libavahi-client.so.3
ELF    7daaa000-7db6e000    Deferred        libgnutls.so.26
ELF    7db6e000-7dbac000    Deferred        libgssapi_krb5.so.2
ELF    7dbac000-7dbff000    Deferred        libcups.so.2
ELF    7dc5f000-7dc93000    Deferred        uxtheme<elf>
  \-PE    7dc70000-7dc93000    \               uxtheme
ELF    7dc93000-7dc9e000    Deferred        libxcursor.so.1
ELF    7dc9e000-7dcac000    Deferred        libavahi-common.so.3
ELF    7dcf2000-7dd1c000    Deferred        libexpat.so.1
ELF    7dd1c000-7dd50000    Deferred        libfontconfig.so.1
ELF    7dd50000-7dd60000    Deferred        libxi.so.6
ELF    7dd60000-7dd69000    Deferred        libxrandr.so.2
ELF    7dd69000-7dd73000    Deferred        libxrender.so.1
ELF    7dd83000-7dda5000    Deferred        imm32<elf>
  \-PE    7dd90000-7dda5000    \               imm32
ELF    7dda5000-7de38000    Deferred        winex11<elf>
  \-PE    7ddb0000-7de38000    \               winex11
ELF    7de38000-7de4e000    Deferred        libz.so.1
ELF    7de4e000-7dee8000    Deferred        libfreetype.so.6
ELF    7dee8000-7df06000    Deferred        libgcc_s.so.1
ELF    7dfeb000-7e060000    Deferred        libglu.so.1
ELF    7e060000-7e077000    Deferred        glu32<elf>
  \-PE    7e070000-7e077000    \               glu32
ELF    7e077000-7e080000    Deferred        librt.so.1
ELF    7e080000-7e087000    Deferred        libxdmcp.so.6
ELF    7e087000-7e08b000    Deferred        libxau.so.6
ELF    7e08b000-7e098000    Deferred        libdrm.so.2
ELF    7e098000-7e09e000    Deferred        libxxf86vm.so.1
ELF    7e09e000-7e0bf000    Deferred        libxcb.so.1
ELF    7e0bf000-7e0d7000    Deferred        libxcb-glx.so.0
ELF    7e0d7000-7e20b000    Deferred        libx11.so.6
ELF    7e20b000-7e20e000    Deferred        libx11-xcb.so.1
ELF    7e20e000-7e214000    Deferred        libxfixes.so.3
ELF    7e214000-7e218000    Deferred        libxdamage.so.1
ELF    7e218000-7e22a000    Deferred        libxext.so.6
ELF    7e22a000-7e240000    Deferred        libglapi.so.0
ELF    7e240000-7e25a000    Deferred        libice.so.6
ELF    7e25a000-7e2b3000    Deferred        libgl.so.1
ELF    7e2b3000-7e36d000    Deferred        opengl32<elf>
  \-PE    7e2d0000-7e36d000    \               opengl32
ELF    7e36d000-7e3a7000    Deferred        winspool<elf>
  \-PE    7e370000-7e3a7000    \               winspool
ELF    7e3a7000-7e486000    Deferred        comdlg32<elf>
  \-PE    7e3b0000-7e486000    \               comdlg32
ELF    7e486000-7e697000    Deferred        shell32<elf>
  \-PE    7e490000-7e697000    \               shell32
ELF    7e697000-7e701000    Deferred        shlwapi<elf>
  \-PE    7e6a0000-7e701000    \               shlwapi
ELF    7e701000-7e727000    Deferred        mpr<elf>
  \-PE    7e710000-7e727000    \               mpr
ELF    7e727000-7e79c000    Deferred        rpcrt4<elf>
  \-PE    7e730000-7e79c000    \               rpcrt4
ELF    7e79c000-7e8a4000    Deferred        ole32<elf>
  \-PE    7e7b0000-7e8a4000    \               ole32
ELF    7e8a4000-7e996000    Deferred        oleaut32<elf>
  \-PE    7e8c0000-7e996000    \               oleaut32
ELF    7e996000-7ea23000    Deferred        msvcrt<elf>
  \-PE    7e9b0000-7ea23000    \               msvcrt
ELF    7ea23000-7ea3c000    Deferred        version<elf>
  \-PE    7ea30000-7ea3c000    \               version
ELF    7ea3c000-7eaf9000    Deferred        gdi32<elf>
  \-PE    7ea50000-7eaf9000    \               gdi32
ELF    7eaf9000-7ec39000    Dwarf           user32<elf>
  \-PE    7eb10000-7ec39000    \               user32
ELF    7ec39000-7ed31000    Deferred        comctl32<elf>
  \-PE    7ec40000-7ed31000    \               comctl32
ELF    7ed31000-7ed91000    Deferred        advapi32<elf>
  \-PE    7ed40000-7ed91000    \               advapi32
ELF    7ed91000-7ed9e000    Deferred        libnss_files.so.2
ELF    7ed9e000-7edaa000    Deferred        libnss_nis.so.2
ELF    7edaa000-7edc4000    Deferred        libnsl.so.1
ELF    7efc4000-7eff0000    Deferred        libm.so.6
ELF    7eff1000-7eff5000    Deferred        libxcomposite.so.1
ELF    7eff5000-7eff9000    Deferred        libxinerama.so.1
ELF    b73f1000-b73fa000    Deferred        libsm.so.6
ELF    b73fb000-b7400000    Deferred        libdl.so.2
ELF    b7400000-b75a5000    Deferred        libc.so.6
ELF    b75a6000-b75c1000    Deferred        libpthread.so.0
ELF    b75c1000-b75c7000    Deferred        libuuid.so.1
ELF    b75c7000-b75d0000    Deferred        libnss_compat.so.2
ELF    b75d1000-b7713000    Dwarf           libwine.so.1
ELF    b7715000-b7737000    Deferred        ld-linux.so.2
ELF    b7737000-b7738000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000c services.exe
    00000029    0
    00000028    0
    0000000e    0
    0000000d    0
00000012 explorer.exe
    00000013    0
00000025 winedevice.exe
    0000002c    0
    0000002b    0
    00000027    0
    00000026    0
0000002d (D) Z:\home\stan\Downloads\Minitab R14\Mtb14.exe
    00000032   -1
    00000031    0
    00000030    0
    0000002f    0
    0000002e    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-23-generic-pae
Any help? thanks!

---

