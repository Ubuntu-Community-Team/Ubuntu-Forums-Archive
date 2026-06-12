---
title: "Wine + Photoshop CS 3"
date: 2007-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by rentacop on 2007-08-10
Hey fellas i am trying to run Photoshop CS3 Using wine. 

I have converted my PS CS3 into a Portable Program so i can actually put it on a thumb drive and run it anywhere with out having to install it. Since there is no install i am assuming there is no need for Reg Hacking. 

I just tested it out on windows and it seems to run fine however when i try in wine, it spits out a bunch of errors.

First off. I am on ubuntu amd64 7.04 and i am running the latest version of wine.

I open Photoshop with.

```
 $wine Photoshop.exe -winver winxp 
```


I pop up comes up saying
"failed to create process default activation context"

the errors i get are


```
 fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:actctx:parse_manifest root element is "\x00?\x00x\x00m\x00l\x00", not <assembly>
fixme:advapi:SetEntriesInAclW 2 0x7ca95724 (nil) 0x7ca957a4
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1d464c 0x1d4658 (nil) (nil)
fixme:advapi:SetEntriesInAclW 2 0x7ca95740 (nil) 0x7ca957c0
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x1d467c 0x1d4688 (nil) (nil)
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
wine: Unhandled page fault on read access to 0x00000008 at address 0x32e9380 (thread 000b), starting debugger...
Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x032e9380).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:032e9380 ESP:0033dd5c EBP:0033dd7c EFLAGS:00010206(   - 00      - RIP1)
 EAX:0033dd70 EBX:00000000 ECX:00000000 EDX:035a0000
 ESI:00000008 EDI:0033ddc0
Stack dump:
0x0033dd5c:  65a2f787 0033ddc0 03ae0128 00000000
0x0033dd6c:  032eeb45 0033dd9c 0336a064 ffffffff
0x0033dd7c:  0033dda8 032e40a7 65a2f753 00000000
0x0033dd8c:  03ae0128 00000000 00000000 0033dd84
0x0033dd9c:  0033de94 0336141b 00000000 0033dea0
0x0033ddac:  0068339b 015062cc 0033ddc0 035ca450
Backtrace:
=>1 0x032e9380 (0x0033dd7c)
  2 0x032e40a7 (0x0033dda8)
  3 0x0068339b in photoshop (+0x28339b) (0x0033dea0)
  4 0x00f88fed in photoshop (+0xb88fed) (0x00007562)
  5 0x00000000 (0x00000000)
0x032e9380: movl        0x0(%esi),%eax
Modules:
Module  Address                 Debug info      Name (83 modules)
PE        400000- 3006000       Export          photoshop
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c8ae000-7c8c2000       Deferred        msimg32<elf>
  \-PE  7c8b0000-7c8c2000       \               msimg32
ELF     7cba8000-7cbbc000       Deferred        sti<elf>
  \-PE  7cbb0000-7cbbc000       \               sti
ELF     7cca6000-7cd26000       Deferred        libglu.so.1
ELF     7cd34000-7cdb5000       Deferred        opengl32<elf>
  \-PE  7cd50000-7cdb5000       \               opengl32
ELF     7cdb5000-7cde2000       Deferred        ws2_32<elf>
  \-PE  7cdc0000-7cde2000       \               ws2_32
ELF     7cde2000-7ce07000       Deferred        netapi32<elf>
  \-PE  7cdf0000-7ce07000       \               netapi32
ELF     7ce07000-7ce3a000       Deferred        winspool<elf>
  \-PE  7ce10000-7ce3a000       \               winspool
ELF     7ce3a000-7cedb000       Deferred        comdlg32<elf>
  \-PE  7ce40000-7cedb000       \               comdlg32
ELF     7cedb000-7cf04000       Deferred        gdiplus<elf>
  \-PE  7cee0000-7cf04000       \               gdiplus
ELF     7cf04000-7cfa1000       Deferred        oleaut32<elf>
  \-PE  7cf20000-7cfa1000       \               oleaut32
ELF     7cfa1000-7cfb6000       Deferred        psapi<elf>
  \-PE  7cfb0000-7cfb6000       \               psapi
ELF     7cfda000-7d00c000       Deferred        uxtheme<elf>
  \-PE  7cfe0000-7d00c000       \               uxtheme
ELF     7d00c000-7d0c9000       Deferred        comctl32<elf>
  \-PE  7d020000-7d0c9000       \               comctl32
ELF     7d0c9000-7d122000       Deferred        shlwapi<elf>
  \-PE  7d0e0000-7d122000       \               shlwapi
ELF     7d122000-7d220000       Deferred        shell32<elf>
  \-PE  7d130000-7d220000       \               shell32
ELF     7d220000-7d234000       Deferred        shfolder<elf>
  \-PE  7d230000-7d234000       \               shfolder
ELF     7d4e0000-7d4f4000       Deferred        lz32<elf>
  \-PE  7d4f0000-7d4f4000       \               lz32
ELF     7d4f4000-7d50e000       Deferred        version<elf>
  \-PE  7d500000-7d50e000       \               version
ELF     7d50e000-7d521000       Deferred        libresolv.so.2
ELF     7d52f000-7d588000       Deferred        rpcrt4<elf>
  \-PE  7d540000-7d588000       \               rpcrt4
ELF     7d588000-7d627000       Deferred        ole32<elf>
  \-PE  7d5a0000-7d627000       \               ole32
ELF     7d8af000-7d8cd000       Deferred        iphlpapi<elf>
  \-PE  7d8c0000-7d8cd000       \               iphlpapi
ELF     7d8cd000-7d8ea000       Deferred        imm32<elf>
  \-PE  7d8d0000-7d8ea000       \               imm32
ELF     7d8ea000-7d8f0000       Deferred        libxrandr.so.2
ELF     7d8f0000-7d8f8000       Deferred        libxrender.so.1
ELF     7d8f8000-7d8fb000       Deferred        libxinerama.so.1
ELF     7d8fb000-7d907000       Deferred        libgcc_s.so.1
ELF     7e055000-7e057000       Deferred        libnvidia-tls.so.1
ELF     7e057000-7e9ef000       Deferred        libglcore.so.1
ELF     7e9ef000-7ea85000       Deferred        libgl.so.1
ELF     7ea85000-7ea8a000       Deferred        libxdmcp.so.6
ELF     7ea8a000-7ea8d000       Deferred        libxau.so.6
ELF     7ea8d000-7eb7e000       Deferred        libx11.so.6
ELF     7eb7e000-7eb8c000       Deferred        libxext.so.6
ELF     7eb9a000-7ec29000       Deferred        winex11<elf>
  \-PE  7ebb0000-7ec29000       \               winex11
ELF     7ecb9000-7ecd9000       Deferred        libexpat.so.1
ELF     7ecd9000-7ed04000       Deferred        libfontconfig.so.1
ELF     7ed04000-7ed18000       Deferred        libz.so.1
ELF     7ed18000-7ed82000       Deferred        libfreetype.so.6
ELF     7ed82000-7edca000       Deferred        advapi32<elf>
  \-PE  7ed90000-7edca000       \               advapi32
ELF     7edca000-7ee62000       Deferred        gdi32<elf>
  \-PE  7ede0000-7ee62000       \               gdi32
ELF     7ee62000-7ef9f000       Deferred        user32<elf>
  \-PE  7ee80000-7ef9f000       \               user32
ELF     7ef9f000-7efaa000       Deferred        libnss_files.so.2
ELF     7efaa000-7efb4000       Deferred        libnss_nis.so.2
ELF     7efb4000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     f7d48000-f7d4c000       Deferred        libdl.so.2
ELF     f7d4c000-f7e8d000       Deferred        libc.so.6
ELF     f7e8e000-f7ea5000       Deferred        libpthread.so.0
ELF     f7eb3000-f7fc7000       Deferred        libwine.so.1
ELF     f7fc9000-f7fe7000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        0000000d    0
0000000a (D) C:\Program Files\Photoshop\Photoshop.exe
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000b    0 <==
00000008 
        00000009    0
 
```

I can see the photoshop cs3 menu open for a few seconds then it crashes.

---

### Post by Kilz on 2007-08-10
You may want to look at the Wine Application Database, and bookmark it for future reference.. Its a website devoted to making Windows applications run in wine. [Here is the Photoshop CS3 page.]("http://appdb.winehq.org/appview.php?iVersionId=6584")

---

### Post by proxess on 2007-08-19
ok maybe i shouldn't bother bumping this topic, but I'm very close to getting photoshop CS3 working properly (the lite edition, payed version seems too complex). It actually is working, except for the interface, it just isn't right.

---

