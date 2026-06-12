---
title: "cant get wine to work"
date: 2014-04-30
forum: Wine
---

### Post by mike-feith on 2014-04-30
hello i cant get wine to work with every application all the applications worked perfectly when i was on ubuntu 13.

now i get this error on ubuntu 14.04.

```
Unhandled exception: unimplemented function IPHLPAPI.DLL.CreateSortedAddressPairs called in 32-bit code (0x7bc54030).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc54030 ESP:0033e554 EBP:0033e5b8 EFLAGS:00000206(   - --  I   - -P- )
 EAX:004bebe0 EBX:7bcc8000 ECX:00000012 EDX:00500eb0
 ESI:0033e560 EDI:00000012
Stack dump:
0x0033e554:  0013a110 7e6dc315 7e6ed019 80000100
0x0033e564:  00000001 00000000 7bc54030 00000002
0x0033e574:  004bd2c0 004bebe0 00000000 0033e5d8
0x0033e584:  0048cfff 0033e5a8 000001f8 0033efa8
0x0033e594:  00000012 0000000e 0033e5a8 0048d478
0x0033e5a4:  0033e5b0 0033e5bc 0048d48a 00000000
000c: sel=0067 base=00000000 limit=00000000 32-bit rw-
Backtrace:
=>0 0x7bc54030 call_dll_entry_point+0x2f0() in ntdll (0x0033e5b8)
  1 0x0034002d (0x0033ef6c)
  2 0x0048cb1a in setup.x86.nl-nl_o365homepremretaZ:\home\mike\Downloads\Setup.X86.nl-NL_O365HomePremRetail_9424ff88-3ee4-4a18-ac69-a54648aa7058_TX_DB_(1).exe (+0x8cb19) (0x0033ef80)
  3 0x00474e27 in setup.x86.nl-nl_o365homepremretaZ:\home\mike\Downloads\Setup.X86.nl-NL_O365HomePremRetail_9424ff88-3ee4-4a18-ac69-a54648aa7058_TX_DB_(1).exe (+0x74e26) (0x0033f0b0)
  4 0x0046ada1 in setup.x86.nl-nl_o365homepremretaZ:\home\mike\Downloads\Setup.X86.nl-NL_O365HomePremRetail_9424ff88-3ee4-4a18-ac69-a54648aa7058_TX_DB_(1).exe (+0x6ada0) (0x0033fd08)
  5 0x0042e4aa in setup.x86.nl-nl_o365homepremretaZ:\home\mike\Downloads\Setup.X86.nl-NL_O365HomePremRetail_9424ff88-3ee4-4a18-ac69-a54648aa7058_TX_DB_(1).exe (+0x2e4a9) (0x0033fdd0)
  6 0x00454158 in setup.x86.nl-nl_o365homepremretaZ:\home\mike\Downloads\Setup.X86.nl-NL_O365HomePremRetail_9424ff88-3ee4-4a18-ac69-a54648aa7058_TX_DB_(1).exe (+0x54157) (0x0033fe60)
  7 0x7b85f13c call_process_entry+0xb() in kernel32 (0x0033fe78)
  8 0x7b8601c3 in kernel32 (+0x501c2) (0x0033feb8)
  9 0x7bc802f0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  10 0x7bc8327d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  11 0x7bc802ce RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  12 0x7bc5413e call_dll_entry_point+0x3fd() in ntdll (0x0033ffe8)
  13 0xf760963d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  14 0xf76096fb wine_switch_to_stack+0x2a() in libwine.so.1 (0xffb9bd78)
  15 0x7bc59c09 LdrInitializeThunk+0x238() in ntdll (0xffb9bdb8)
  16 0x7b866a13 __wine_kernel_init+0xa12() in kernel32 (0xffb9ced8)
  17 0x7bc5ab33 __wine_process_init+0x192() in ntdll (0xffb9cf68)
  18 0xf7606da8 wine_init+0x327() in libwine.so.1 (0xffb9cfc8)
  19 0x7bf0100c main+0xfb() in <wine-loader> (0xffb9d418)
  20 0xf7421a83 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x7bc54030 call_dll_entry_point+0x2f0 in ntdll: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (73 modules)
PE      400000-  4ec000    Export          setup.x86.nl-nl_o365homepremretaZ:\home\mike\Downloads\Setup.X86.nl-NL_O365HomePremRetail_9424ff88-3ee4-4a18-ac69-a54648aa7058_TX_DB_(1).exe
ELF    7b800000-7ba5b000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7bc00000-7bce5000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bce5000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7dbe8000-7dc00000    Deferred        libresolv.so.2
ELF    7dd10000-7dd35000    Deferred        imm32<elf>
  \-PE    7dd20000-7dd35000    \               imm32
ELF    7dd98000-7ddaf000    Deferred        netprofm<elf>
  \-PE    7dda0000-7ddaf000    \               netprofm
ELF    7ddb0000-7ddb6000    Deferred        libxfixes.so.3
ELF    7ddb8000-7ddc3000    Deferred        libxcursor.so.1
ELF    7ddc8000-7ddd9000    Deferred        libxi.so.6
ELF    7dde0000-7dde4000    Deferred        libxcomposite.so.1
ELF    7dde8000-7ddf3000    Deferred        libxrandr.so.2
ELF    7ddf8000-7de03000    Deferred        libxrender.so.1
ELF    7de08000-7de0e000    Deferred        libxxf86vm.so.1
ELF    7de10000-7de14000    Deferred        libxinerama.so.1
ELF    7de18000-7de1f000    Deferred        libxdmcp.so.6
ELF    7de20000-7de24000    Deferred        libxau.so.6
ELF    7de28000-7de4a000    Deferred        libxcb.so.1
ELF    7de50000-7df84000    Deferred        libx11.so.6
ELF    7df88000-7df9b000    Deferred        libxext.so.6
ELF    7dfb0000-7dfb7000    Deferred        libnss_dns.so.2
ELF    7dfc0000-7e054000    Deferred        winex11<elf>
  \-PE    7dfd0000-7e054000    \               winex11
ELF    7e138000-7e161000    Deferred        libexpat.so.1
ELF    7e168000-7e1a3000    Deferred        libfontconfig.so.1
ELF    7e1a8000-7e1d0000    Deferred        libpng12.so.0
ELF    7e1d0000-7e26f000    Deferred        libfreetype.so.6
ELF    7e270000-7e2e1000    Deferred        setupapi<elf>
  \-PE    7e280000-7e2e1000    \               setupapi
ELF    7e2e8000-7e302000    Deferred        libz.so.1
ELF    7e328000-7e349000    Deferred        cabinet<elf>
  \-PE    7e330000-7e349000    \               cabinet
ELF    7e350000-7e420000    Deferred        crypt32<elf>
  \-PE    7e360000-7e420000    \               crypt32
ELF    7e420000-7e457000    Deferred        wintrust<elf>
  \-PE    7e430000-7e457000    \               wintrust
ELF    7e458000-7e47e000    Deferred        iphlpapi<elf>
  \-PE    7e460000-7e47e000    \               iphlpapi
ELF    7e480000-7e5b7000    Deferred        oleaut32<elf>
  \-PE    7e4a0000-7e5b7000    \               oleaut32
ELF    7e5b8000-7e632000    Deferred        shlwapi<elf>
  \-PE    7e5d0000-7e632000    \               shlwapi
ELF    7e638000-7e6c4000    Deferred        gdiplus<elf>
  \-PE    7e650000-7e6c4000    \               gdiplus
ELF    7e6c8000-7e700000    Deferred        ws2_32<elf>
  \-PE    7e6d0000-7e700000    \               ws2_32
ELF    7e700000-7e784000    Deferred        rpcrt4<elf>
  \-PE    7e710000-7e784000    \               rpcrt4
ELF    7e788000-7e8a7000    Deferred        gdi32<elf>
  \-PE    7e790000-7e8a7000    \               gdi32
ELF    7e8a8000-7ea03000    Deferred        user32<elf>
  \-PE    7e8c0000-7ea03000    \               user32
ELF    7ea08000-7eb47000    Deferred        ole32<elf>
  \-PE    7ea20000-7eb47000    \               ole32
ELF    7eb48000-7ebba000    Deferred        advapi32<elf>
  \-PE    7eb50000-7ebba000    \               advapi32
ELF    7ebc0000-7ebcd000    Deferred        libnss_files.so.2
ELF    7ebd0000-7ebdc000    Deferred        libnss_nis.so.2
ELF    7ebe0000-7ebf9000    Deferred        libnsl.so.1
ELF    7ec08000-7ec22000    Deferred        version<elf>
  \-PE    7ec10000-7ec22000    \               version
ELF    7ef98000-7efde000    Deferred        libm.so.6
ELF    7eff0000-7eff9000    Deferred        libnss_compat.so.2
ELF    f7408000-f75b7000    Dwarf           libc.so.6
ELF    f75b8000-f75bd000    Deferred        libdl.so.2
ELF    f75c0000-f75dc000    Deferred        libpthread.so.0
ELF    f7600000-f77b5000    Dwarf           libwine.so.1
ELF    f77b8000-f77da000    Deferred        ld-linux.so.2
ELF    f77df000-f77e0000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
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
    00000021    0
00000022 (D) Z:\home\mike\Downloads\Setup.X86.nl-NL_O365HomePremRetail_9424ff88-3ee4-4a18-ac69-a54648aa7058_TX_DB_(1).exe
    00000025    0
    00000024    0
    00000023    0 <==
System information:
    Wine build: wine-1.7.17
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.13.0-24-generic
```

i hope anywone has a solution

---

### Post by Toz on 2014-04-30
Hello and welcome to the forums.

Which application are you trying to install that results in that code dump?

EDIT: How/where did you install wine 1.7.17? Its not the standard version that comes with 14.04.

---

