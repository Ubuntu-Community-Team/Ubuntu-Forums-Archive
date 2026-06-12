---
title: "Office 2007 on Wine 0.9.53"
date: 2008-01-21
forum: Wine
---

### Post by evtedeschi3 on 2008-01-21
I have a tablet, and have been attempting to get OneNote 2007 working in Wine, since none of the Linux-based alternatives offer anything close to the same experience. A lower priority would be to get the rest of the Office 2007 suite up and running.

I'm running Ubuntu Gutsy with Wine 0.9.53, using an Office 2007 installation from my Windows XP Professional partition.

I started by directly copying my Office installation into my .wine/drive_c/Program Files directory, as well as the "Microsoft" folder from my "Application Data" folder and putting it in the corresponding .wine/drive_c/windows/profiles/[my name]/Application Data folder. I also exported the "Office" branch of my Windows XP registry and integrated it into Wine using [FONT="Courier New"]sudo wine regedit office.reg [/FONT]. Finally, I set "msvcr80.dll" to native in winecfg.

Running OneNote.exe with wine at this point yielded a C++ Runtime error, and the terminal output said it couldn't find "Microsoft.VC80.CRT".

I then downloaded the C++ runtime libraries [here,]("http://www.sweetpotatosoftware.com/SPSBlog/ct.ashx?id=91241006-595a-487d-ac06-d0fc1fc71632&url=http%3a%2f%2fwww.sweetpotatosoftware.com%2ffiles%2fmicrosoft.vc80.crt.zip") and placed the resulting Microsoft.VC80.CRT folder in the same one as OneNote.exe (which I think is the OFFICE12 folder). Here's the error I'm getting now:

```
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
wine: Unhandled exception 0xe06d7363 at address 0x7b840f9c (thread 0016), starting debugger...
Unhandled exception: C++ exception(object = 0x0033fb70, type = 0x343a9b1c) in 32-bit code (0x7b841016).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b841016 ESP:0033fac4 EBP:0033fb28 EFLAGS:00200216(   - 00      - IAP1)
 EAX:7b82c411 EBX:7b8ab8a0 ECX:00000000 EDX:0033fb54
 ESI:0033fb54 EDI:009e8020
Stack dump:
0x0033fac4:  0033fb54 0000000c 000000a0 e06d7363
0x0033fad4:  00000001 00000000 7b840f9c 00000003
0x0033fae4:  19930520 0033fb70 343a9b1c 0033fb20
0x0033faf4:  7bc482e7 7bc8d684 00000a30 001105b0
0x0033fb04:  0033fb10 7bc8d684 00000000 0000e181
0x0033fb14:  00000000 34494dec 7b840fa6 009e8024
Backtrace:
=>1 0x7b841016 RaiseException+0x7a() in kernel32 (0x0033fb28)
  2 0x78158dd3 in msvcr80 (+0x28dd3) (0x0033fb60)
  3 0x343a9b18 in onmain (+0x4e9b18) (0x0033fb7c)
  4 0x343a91b5 in onmain (+0x4e91b5) (0x0033fba4)
  5 0x343a9b4d in onmain (+0x4e9b4d) (0x0033fbd8)
  6 0x33ec8a81 in onmain (+0x8a81) (0x0033fbf0)
  7 0x33ec819a in onmain (+0x819a) (0x0033fc64)
  8 0x33ec7999 in onmain (+0x7999) (0x0033fc90)
  9 0x3000280e in onenote (+0x280e) (0x0033fe50)
  10 0x300025b4 in onenote (+0x25b4) (0x0033fe60)
  11 0x300024f0 in onenote (+0x24f0) (0x0033fe78)
  12 0x300024a6 in onenote (+0x24a6) (0x0033ff08)
  13 0x7b86eb3d in kernel32 (+0x4eb3d) (0x0033ffe8)
  14 0xb7df01cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7b841016 RaiseException+0x7a in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (88 modules)
PE        a40000-  d03000       Deferred        onintl
PE      30000000-300fb000       Export          onenote
PE      32600000-3361a000       Deferred        mso
PE      33ec0000-34509000       Export          onmain
PE      78130000-781cb000       Export          msvcr80
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dfd0000-7e071000       Deferred        oleaut32<elf>
  \-PE  7dfe0000-7e071000       \               oleaut32
ELF     7e071000-7e091000       Deferred        cabinet<elf>
  \-PE  7e080000-7e091000       \               cabinet
ELF     7e091000-7e0b2000       Deferred        mpr<elf>
  \-PE  7e0a0000-7e0b2000       \               mpr
ELF     7e0b2000-7e0fd000       Deferred        wininet<elf>
  \-PE  7e0c0000-7e0fd000       \               wininet
ELF     7e0fd000-7e13b000       Deferred        urlmon<elf>
  \-PE  7e110000-7e13b000       \               urlmon
ELF     7e13b000-7e1dc000       Deferred        msi<elf>
  \-PE  7e150000-7e1dc000       \               msi
ELF     7e2be000-7e2f0000       Deferred        uxtheme<elf>
  \-PE  7e2d0000-7e2f0000       \               uxtheme
ELF     7e2f0000-7e2f9000       Deferred        libxcursor.so.1
ELF     7e2f9000-7e316000       Deferred        imm32<elf>
  \-PE  7e300000-7e316000       \               imm32
ELF     7e316000-7e319000       Deferred        libxcomposite.so.1
ELF     7e319000-7e31f000       Deferred        libxrandr.so.2
ELF     7e31f000-7e327000       Deferred        libxrender.so.1
ELF     7e327000-7e331000       Deferred        libdrm.so.2
ELF     7e331000-7e336000       Deferred        libxfixes.so.3
ELF     7e336000-7e339000       Deferred        libxdamage.so.1
ELF     7e339000-7e39a000       Deferred        libgl.so.1
ELF     7e39a000-7e39f000       Deferred        libxdmcp.so.6
ELF     7e39f000-7e3a2000       Deferred        libxau.so.6
ELF     7e3a2000-7e493000       Deferred        libx11.so.6
ELF     7e493000-7e4a1000       Deferred        libxext.so.6
ELF     7e4a1000-7e4a6000       Deferred        libxxf86vm.so.1
ELF     7e4a6000-7e4be000       Deferred        libice.so.6
ELF     7e4be000-7e4c6000       Deferred        libsm.so.6
ELF     7e4d4000-7e55e000       Deferred        winex11<elf>
  \-PE  7e4e0000-7e55e000       \               winex11
ELF     7e73e000-7e75e000       Deferred        libexpat.so.1
ELF     7e75e000-7e789000       Deferred        libfontconfig.so.1
ELF     7e797000-7e7ac000       Deferred        libz.so.1
ELF     7e7ac000-7e81c000       Deferred        libfreetype.so.6
ELF     7e81c000-7e847000       Deferred        ws2_32<elf>
  \-PE  7e820000-7e847000       \               ws2_32
ELF     7e847000-7e86d000       Deferred        netapi32<elf>
  \-PE  7e850000-7e86d000       \               netapi32
ELF     7e86d000-7e881000       Deferred        lz32<elf>
  \-PE  7e870000-7e881000       \               lz32
ELF     7e881000-7e89a000       Deferred        version<elf>
  \-PE  7e890000-7e89a000       \               version
ELF     7e89a000-7e8ae000       Deferred        msimg32<elf>
  \-PE  7e8a0000-7e8ae000       \               msimg32
ELF     7e8ae000-7e913000       Deferred        msvcrt<elf>
  \-PE  7e8c0000-7e913000       \               msvcrt
ELF     7e913000-7e9d2000       Deferred        comctl32<elf>
  \-PE  7e920000-7e9d2000       \               comctl32
ELF     7e9d2000-7ea29000       Deferred        shlwapi<elf>
  \-PE  7e9e0000-7ea29000       \               shlwapi
ELF     7ea29000-7eb2d000       Deferred        shell32<elf>
  \-PE  7ea40000-7eb2d000       \               shell32
ELF     7eb2d000-7eb40000       Deferred        libresolv.so.2
ELF     7eb4e000-7eb6d000       Deferred        iphlpapi<elf>
  \-PE  7eb60000-7eb6d000       \               iphlpapi
ELF     7eb6d000-7ebcb000       Deferred        rpcrt4<elf>
  \-PE  7eb80000-7ebcb000       \               rpcrt4
ELF     7ebcb000-7ed02000       Deferred        user32<elf>
  \-PE  7ebe0000-7ed02000       \               user32
ELF     7ed02000-7eda1000       Deferred        ole32<elf>
  \-PE  7ed10000-7eda1000       \               ole32
ELF     7eda1000-7edea000       Deferred        advapi32<elf>
  \-PE  7edb0000-7edea000       \               advapi32
ELF     7edea000-7ee81000       Deferred        gdi32<elf>
  \-PE  7ee00000-7ee81000       \               gdi32
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c74000-b7c78000       Deferred        libdl.so.2
ELF     b7c78000-b7dc2000       Deferred        libc.so.6
ELF     b7dc3000-b7ddb000       Deferred        libpthread.so.0
ELF     b7de9000-b7efd000       Export          libwine.so.1
ELF     b7eff000-b7f1b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000017 
        00000019    0
        00000018    0
00000015 (D) C:\Program Files\Microsoft Office\Office12\ONENOTE.EXE
        00000016    0 <==
0000000a 
        0000000b    0
Backtrace:
=>1 0x7b841016 RaiseException+0x7a() in kernel32 (0x0033fb28)
  2 0x78158dd3 in msvcr80 (+0x28dd3) (0x0033fb60)
  3 0x343a9b18 in onmain (+0x4e9b18) (0x0033fb7c)
  4 0x343a91b5 in onmain (+0x4e91b5) (0x0033fba4)
  5 0x343a9b4d in onmain (+0x4e9b4d) (0x0033fbd8)
  6 0x33ec8a81 in onmain (+0x8a81) (0x0033fbf0)
  7 0x33ec819a in onmain (+0x819a) (0x0033fc64)
  8 0x33ec7999 in onmain (+0x7999) (0x0033fc90)
  9 0x3000280e in onenote (+0x280e) (0x0033fe50)
  10 0x300025b4 in onenote (+0x25b4) (0x0033fe60)
  11 0x300024f0 in onenote (+0x24f0) (0x0033fe78)
  12 0x300024a6 in onenote (+0x24a6) (0x0033ff08)
  13 0x7b86eb3d in kernel32 (+0x4eb3d) (0x0033ffe8)
  14 0xb7df01cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

Can anyone help me interpret this log and suggest a possible next course of action? Thanks!

---

### Post by rubenvb on 2008-01-24
Sorry to be of no help at all, but do the rest of the Office apps run like that?? Thanx

---

### Post by Sammi on 2008-01-24
Of all the bright people lurking on appdb.winehq.org, the official place to post info about how win programs run in Wine, it seems no one has gotten Office 2007 final to run.

So my advice is: Stop wasting your time and wait 2 years until the development of Wine has progressed so much that it will run the newest win software.

Wine is still in active alpha development. Even though a lot of things already work, do not expect everything to work.

---

### Post by zp3dd4 on 2008-01-27
somebody on wine review has gotten office 2007 to run:
[http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html](http://wine-review.blogspot.com/2008/01/microsoft-office-2007-install-on-linux.html)
i wish i knew how...

---

