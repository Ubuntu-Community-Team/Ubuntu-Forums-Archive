---
title: "Need help with Pepakura for .pdo files"
date: 2018-08-15
forum: Wine
---

### Post by winterswan127 on 2018-08-15
I have a few .pdo files I would like to open but after looking through  the internet the only program I found that can open the filetype was  Pepakura viewer and editor. Both are windows only, and I couldn't find a  linux equivalent so naturally I used WINE - Play on Linux in my case. I  used the latest version of WINE with the current Play on Linux on the  Ubuntu store (I know there is an update available for it), but upon  opening up the program I receive errors until it says the program has  crashed.

I'm wondering if anyone else has a similar problem to me and if there is a native linux alternative to view .pdo files.

This is the log file I received when it crashed.

 	```
 Unhandled exception: page fault on read access to 0xfffffff8 in 32-bit code (0x0048e365).Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0048e365 ESP:0032bbd0 EBP:0032bbf4 EFLAGS:00210282(  R- --  I S - - - )
 EAX:0032bbe8 EBX:00629410 ECX:00629410 EDX:00000000
 ESI:ffffffec EDI:00629320
Stack dump:
0x0032bbd0:  a20e8b34 00629320 00629410 00000004
0x0032bbe0:  0032bc40 0032bbd0 0032bc30 004db4fe
0x0032bbf0:  ffffffff 0032bcd4 004136e6 ffffffff
0x0032bc00:  004dff40 00000001 a20e8ccc 00629320
0x0032bc10:  00000000 0032bcd4 00413430 0049fea3
0x0032bc20:  00629320 00000007 004e0f20 0032bcd4
000c: sel=0067 base=00000000 limit=00000000 16-bit --x
Backtrace:
=>0 0x0048e365 in pepakura_viewer3 (+0x8e365) (0x0032bbf4)
  1 0x004136e6 in pepakura_viewer3 (+0x136e5) (0x0032bcd4)
  2 0x0047ae80 in pepakura_viewer3 (+0x7ae7f) (0x0032bcf4)
  3 0x0047d63a in pepakura_viewer3 (+0x7d639) (0x0032bd5c)
  4 0x0047d6c7 in pepakura_viewer3 (+0x7d6c6) (0x0032bd7c)
  5 0x7e9e9f8a WINPROC_wrapper+0x19() in user32 (0x0032bdac)
  6 0x7e9ea6dc in user32 (+0x9a6db) (0x0032bdfc)
  7 0x7e9eb4ca in user32 (+0x9b4c9) (0x0032c2cc)
  8 0x7e9ecda9 in user32 (+0x9cda8) (0x0032c31c)
  9 0x7e9aec9e DispatchMessageW+0x9d() in user32 (0x0032c40c)
  10 0x7e97c6eb in user32 (+0x2c6ea) (0x0032c47c)
  11 0x7e97e873 DialogBoxIndirectParamAorW+0x52() in user32 (0x0032c4ac)
  12 0x7e97e8c1 DialogBoxIndirectParamW+0x40() in user32 (0x0032c4dc)
  13 0x7e9b9157 MessageBoxIndirectW+0x96() in user32 (0x0032c53c)
  14 0x7e9b9334 MessageBoxIndirectA+0xa3() in user32 (0x0032c59c)
  15 0x7e9b943f MessageBoxExA+0x5e() in user32 (0x0032c5ec)
  16 0x7e9b951a MessageBoxA+0x39() in user32 (0x0032c61c)
  17 0x0047b733 in pepakura_viewer3 (+0x7b732) (0x0032c668)
  18 0x004882fb in pepakura_viewer3 (+0x882fa) (0x0032c70c)
  19 0x00000000 (0xf763ed27)
  20 0x7d8bf875 _mesa_meta_glsl_Clear+0x3d4() in libdricore9.0.3.so.1 (0x8bf45d8b)
0x0048e365: testb    $0x1,0xc(%esi)
Modules:
Module    Address            Debug info    Name (113 modules)
PE      400000-  625000    Export          pepakura_viewer3
ELF    7b800000-7ba15000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d15f000-7d17a000    Deferred        spoolss<elf>
  \-PE    7d160000-7d17a000    \               spoolss
ELF    7d17a000-7d19b000    Deferred        localspl<elf>
  \-PE    7d180000-7d19b000    \               localspl
ELF    7d19b000-7d1b3000    Deferred        libresolv.so.2
ELF    7d1b3000-7d1fc000    Deferred        libdbus-1.so.3
ELF    7d1fc000-7d20e000    Deferred        libp11-kit.so.0
ELF    7d20e000-7d293000    Deferred        libgcrypt.so.11
ELF    7d293000-7d2a5000    Deferred        libtasn1.so.3
ELF    7d2a5000-7d2ae000    Deferred        libkrb5support.so.0
ELF    7d2ae000-7d2d6000    Deferred        libk5crypto.so.3
ELF    7d2d6000-7d3a5000    Deferred        libkrb5.so.3
ELF    7d3a5000-7d469000    Deferred        libgnutls.so.26
ELF    7d469000-7d4a7000    Deferred        libgssapi_krb5.so.2
ELF    7d4a7000-7d4fa000    Deferred        libcups.so.2
ELF    7d542000-7d576000    Deferred        uxtheme<elf>
  \-PE    7d550000-7d576000    \               uxtheme
ELF    7d576000-7d5aa000    Deferred        libtxc_dxtn.so
ELF    7d6aa000-7d6b5000    Deferred        libpciaccess.so.0
ELF    7d6b5000-7d6d7000    Deferred        libdrm_intel.so.1
ELF    7d6d7000-7da76000    Dwarf           libdricore9.0.3.so.1
ELF    7da7e000-7da90000    Deferred        libavahi-client.so.3
ELF    7da90000-7db5c000    Deferred        i965_dri.so
ELF    7db5c000-7db67000    Deferred        libxcursor.so.1
ELF    7db67000-7db6c000    Deferred        libgpg-error.so.0
ELF    7db6c000-7db71000    Deferred        libcom_err.so.2
ELF    7db71000-7db7f000    Deferred        libavahi-common.so.3
ELF    7dc48000-7dc72000    Deferred        libexpat.so.1
ELF    7dc72000-7dca6000    Deferred        libfontconfig.so.1
ELF    7dca6000-7dcb6000    Deferred        libxi.so.6
ELF    7dcb6000-7dcba000    Deferred        libxcomposite.so.1
ELF    7dcba000-7dcc3000    Deferred        libxrandr.so.2
ELF    7dcc3000-7dccd000    Deferred        libxrender.so.1
ELF    7dccd000-7dcd1000    Deferred        libxinerama.so.1
ELF    7dcd1000-7dcf3000    Deferred        imm32<elf>
  \-PE    7dce0000-7dcf3000    \               imm32
ELF    7dcf3000-7dd86000    Deferred        winex11<elf>
  \-PE    7dd00000-7dd86000    \               winex11
ELF    7dd86000-7de20000    Deferred        libfreetype.so.6
ELF    7de20000-7de46000    Deferred        mpr<elf>
  \-PE    7de30000-7de46000    \               mpr
ELF    7de46000-7de5c000    Deferred        libz.so.1
ELF    7de5c000-7decb000    Deferred        wininet<elf>
  \-PE    7de70000-7decb000    \               wininet
ELF    7decb000-7df03000    Deferred        oledlg<elf>
  \-PE    7ded0000-7df03000    \               oledlg
ELF    7df03000-7df3d000    Deferred        winspool<elf>
  \-PE    7df10000-7df3d000    \               winspool
ELF    7df3d000-7e035000    Deferred        comctl32<elf>
  \-PE    7df40000-7e035000    \               comctl32
ELF    7e035000-7e246000    Deferred        shell32<elf>
  \-PE    7e040000-7e246000    \               shell32
ELF    7e246000-7e325000    Deferred        comdlg32<elf>
  \-PE    7e250000-7e325000    \               comdlg32
ELF    7e325000-7e39a000    Deferred        rpcrt4<elf>
  \-PE    7e330000-7e39a000    \               rpcrt4
ELF    7e39a000-7e4a2000    Deferred        ole32<elf>
  \-PE    7e3b0000-7e4a2000    \               ole32
ELF    7e4a2000-7e594000    Deferred        oleaut32<elf>
  \-PE    7e4c0000-7e594000    \               oleaut32
ELF    7e594000-7e609000    Deferred        gdiplus<elf>
  \-PE    7e5a0000-7e609000    \               gdiplus
ELF    7e609000-7e673000    Deferred        shlwapi<elf>
  \-PE    7e620000-7e673000    \               shlwapi
ELF    7e673000-7e691000    Deferred        libgcc_s.so.1
ELF    7e776000-7e7eb000    Deferred        libglu.so.1
ELF    7e7eb000-7e7ef000    Deferred        libkeyutils.so.1
ELF    7e805000-7e81c000    Deferred        glu32<elf>
  \-PE    7e810000-7e81c000    \               glu32
ELF    7e81c000-7e87c000    Deferred        advapi32<elf>
  \-PE    7e830000-7e87c000    \               advapi32
ELF    7e87c000-7e939000    Deferred        gdi32<elf>
  \-PE    7e890000-7e939000    \               gdi32
ELF    7e939000-7ea79000    Dwarf           user32<elf>
  \-PE    7e950000-7ea79000    \               user32
ELF    7ea79000-7ea82000    Deferred        librt.so.1
ELF    7ea82000-7ea89000    Deferred        libxdmcp.so.6
ELF    7ea89000-7ea8d000    Deferred        libxau.so.6
ELF    7ea8d000-7ea9a000    Deferred        libdrm.so.2
ELF    7ea9a000-7eaa0000    Deferred        libxxf86vm.so.1
ELF    7eaa0000-7eac1000    Deferred        libxcb.so.1
ELF    7eac1000-7ead9000    Deferred        libxcb-glx.so.0
ELF    7ead9000-7ec0d000    Deferred        libx11.so.6
ELF    7ec0d000-7ec13000    Deferred        libxfixes.so.3
ELF    7ec13000-7ec25000    Deferred        libxext.so.6
ELF    7ec25000-7ec3c000    Deferred        libglapi.so.0
ELF    7ec3c000-7ec42000    Deferred        libuuid.so.1
ELF    7ec42000-7eca1000    Deferred        libgl.so.1
ELF    7eca1000-7ecaa000    Deferred        libsm.so.6
ELF    7ecab000-7ecc4000    Deferred        version<elf>
  \-PE    7ecb0000-7ecc4000    \               version
ELF    7ecc4000-7ed7e000    Deferred        opengl32<elf>
  \-PE    7ece0000-7ed7e000    \               opengl32
ELF    7ef7e000-7ef8b000    Deferred        libnss_files.so.2
ELF    7ef8b000-7ef97000    Deferred        libnss_nis.so.2
ELF    7ef97000-7efb1000    Deferred        libnsl.so.1
ELF    7efb1000-7efba000    Deferred        libnss_compat.so.2
ELF    7efba000-7efe6000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        libice.so.6
ELF    f7450000-f7454000    Deferred        libxdamage.so.1
ELF    f7455000-f745a000    Deferred        libdl.so.2
ELF    f745a000-f7604000    Deferred        libc.so.6
ELF    f7605000-f7620000    Deferred        libpthread.so.0
ELF    f7630000-f7633000    Deferred        libx11-xcb.so.1
ELF    f763a000-f777c000    Dwarf           libwine.so.1
ELF    f777e000-f77a0000    Deferred        ld-linux.so.2
ELF    f77a0000-f77a1000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files (x86)\tamasoftware\pepakura3en\viewer\pepakura_viewer3.exe
    00000009    0 <==
0000000e services.exe
    0000001f    0
    0000001e    0
    00000018    0
    00000017    0
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
    Wine build: wine-1.4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.5.0-27-generic 
```

---

### Post by QIII on 2018-08-15
Moved to Wine

---

### Post by kc1di on 2018-08-16
According to wine [applications data base]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=5592") workability of that program is very dependent upon which version your trying to install. and there are a few dependencies you need to install also. 
[this tutorial]("https://www.instructables.com/id/Pepakura-Convert-PDO-to-PDF-/") on converting pdo to pdf files may be of help also. Good Luck.

---

### Post by Holger_Gehrke on 2018-08-16
The current version (4.07) of pepakura from Tamasofts website works quite well on XUbuntu 18.04 with wine 3.0 (stock version from the Ubuntu repos). Both the Designer and the viewer complain a bit when started, but they **do** run. If you just want to take a look at the contents of a .pdo file, the viewer is quite enough, so no need to buy a license key to activate save and export in the designer. AFAIK there's no other program that can open a pdo file.

Holger

---

