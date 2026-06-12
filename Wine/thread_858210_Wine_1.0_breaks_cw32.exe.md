---
title: "Wine 1.0 breaks cw32.exe"
date: 2008-07-13
forum: Wine
---

### Post by skunkTrader on 2008-07-13
I updated this morning and installed wine 1.0.  All the other legacy programs I have installed work correctly except for CodeWright 6.0e which dies after displaying the splash screen.  This used to work correctly with the prior version (0.9.59) from the repos.

This is the trace

```
fixme:heap:RtlCompactHeap (0xa60000, 0x0) stub
wine: Unhandled page fault on read access to 0x0972d80c at address 0x1013f282 (thread 0040), starting debugger...
Unhandled exception: page fault on read access to 0x0972d80c in 32-bit code (0x1013f282).
fixme:dbghelp_msc:pe_load_debug_directory This guy has FPO information
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:1013f282 ESP:0032edf4 EBP:0032ee08 EFLAGS:00010206(   - 00      - RIP1)
 EAX:09600000 EBX:7ee2b548 ECX:0012d7f8 EDX:00320000
 ESI:0032f75c EDI:000d0038
Stack dump:
0x0032edf4:  0012d7f8 ffffffff 7ee065ba 00640000
0x0032ee04:  0012d7f8 0032ee10 1019cc70 0032f050
0x0032ee14:  1012323e ffffffff 0032f75c 0014cde0
0x0032ee24:  00000024 0014cc90 7bc88444 0032ee90
0x0032ee34:  7bc4384e 00110048 00170054 fffffff0
0x0032ee44:  0000ba88 00000102 00000000 7ee2b548
Backtrace:
=>1 0x1013f282 in cwdll32 (+0x3f282) (0x0032ee08)
  2 0x1019cc70 in cwdll32 (+0x9cc70) (0x0032ee10)
  3 0x1012323e in cwdll32 (+0x2323e) (0x0032f050)
  4 0x7ee065ba WINPROC_wrapper+0x1a() in user32 (0x0032f080)
  5 0x7ee06c9e WINPROC_wrapper+0x6fe() in user32 (0x0032f0c0)
  6 0x7ee0b535 in user32 (+0xab535) (0x0032f590)
  7 0x7ee0c0fb in user32 (+0xac0fb) (0x0032f5d0)
  8 0x7edcf11a in user32 (+0x6f11a) (0x0032f640)
  9 0x7edd239d in user32 (+0x7239d) (0x0032f6a0)
  10 0x7edd280a SendMessageW+0x4a() in user32 (0x0032f6e0)
  11 0x7ee013fe in user32 (+0xa13fe) (0x0032f7a0)
  12 0x7edfcdfc in user32 (+0x9cdfc) (0x0032fa70)
  13 0x7edfedfd CreateWindowExA+0xbd() in user32 (0x0032fcd0)
  14 0x1011eebc in cwdll32 (+0x1eebc) (0x0032fd60)
  15 0x1012049b in cwdll32 (+0x2049b) (0x0032fdb8)
  16 0x1011fe47 in cwdll32 (+0x1fe47) (0x0032fe20)
  17 0x1011f6da in cwdll32 (+0x1f6da) (0x0032fe3c)
fixme:dbghelp_msc:pe_load_debug_directory This guy has FPO information
  18 0x00401288 in cw32 (+0x1288) (0x0032fe7c)
  19 0x00401db2 in cw32 (+0x1db2) (0x0032ff08)
  20 0x7b8773a7 in kernel32 (+0x573a7) (0x0032ffe8)
0x1013f282: movl        0x14(%ecx,%eax,1),%eax
Modules:
Module  Address                 Debug info      Name (75 modules)
PE        400000-  43c000       Export          cw32
PE      10100000-10235000       Export          cwdll32
PE      10500000-10573000       Deferred        cwctls32
ELF     7b800000-7b92d000       Export          kernel32<elf>
  \-PE  7b820000-7b92d000       \               kernel32
ELF     7bc00000-7bca4000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca4000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e291000-7e2a5000       Deferred        midimap<elf>
  \-PE  7e2a0000-7e2a5000       \               midimap
ELF     7e2a5000-7e2cb000       Deferred        msacm32<elf>
  \-PE  7e2b0000-7e2cb000       \               msacm32
ELF     7e2cb000-7e2e2000       Deferred        msacm32<elf>
  \-PE  7e2d0000-7e2e2000       \               msacm32
ELF     7e2e2000-7e3a5000       Deferred        libasound.so.2
ELF     7e3b8000-7e3ee000       Deferred        winealsa<elf>
  \-PE  7e3c0000-7e3ee000       \               winealsa
ELF     7e3ee000-7e480000       Deferred        winmm<elf>
  \-PE  7e400000-7e480000       \               winmm
ELF     7e4a4000-7e4b7000       Deferred        libresolv.so.2
ELF     7e4ca000-7e4e8000       Deferred        iphlpapi<elf>
  \-PE  7e4d0000-7e4e8000       \               iphlpapi
ELF     7e4e8000-7e549000       Deferred        rpcrt4<elf>
  \-PE  7e4f0000-7e549000       \               rpcrt4
ELF     7e549000-7e5ed000       Deferred        ole32<elf>
  \-PE  7e560000-7e5ed000       \               ole32
ELF     7e5f1000-7e624000       Deferred        uxtheme<elf>
  \-PE  7e600000-7e624000       \               uxtheme
ELF     7e624000-7e645000       Deferred        mpr<elf>
  \-PE  7e630000-7e645000       \               mpr
ELF     7e645000-7e704000       Deferred        comctl32<elf>
  \-PE  7e650000-7e704000       \               comctl32
ELF     7e704000-7e75d000       Deferred        shlwapi<elf>
  \-PE  7e710000-7e75d000       \               shlwapi
ELF     7e75d000-7e870000       Deferred        shell32<elf>
  \-PE  7e770000-7e870000       \               shell32
ELF     7e8f1000-7e8fa000       Deferred        libxcursor.so.1
ELF     7e8fa000-7e8ff000       Deferred        libxfixes.so.3
ELF     7e8ff000-7e902000       Deferred        libxcomposite.so.1
ELF     7e902000-7e908000       Deferred        libxrandr.so.2
ELF     7e908000-7e910000       Deferred        libxrender.so.1
ELF     7e910000-7e913000       Deferred        libxinerama.so.1
ELF     7e913000-7e933000       Deferred        imm32<elf>
  \-PE  7e920000-7e933000       \               imm32
ELF     7e933000-7e938000       Deferred        libxdmcp.so.6
ELF     7e938000-7e950000       Deferred        libxcb.so.1
ELF     7e950000-7e952000       Deferred        libxcb-xlib.so.0
ELF     7e952000-7e955000       Deferred        libxau.so.6
ELF     7e955000-7ea3c000       Deferred        libx11.so.6
ELF     7ea3c000-7ea4a000       Deferred        libxext.so.6
ELF     7ea4a000-7ea4f000       Deferred        libxxf86vm.so.1
ELF     7ea4f000-7ea67000       Deferred        libice.so.6
ELF     7ea67000-7ea6f000       Deferred        libsm.so.6
ELF     7ea82000-7eb19000       Deferred        winex11<elf>
  \-PE  7ea90000-7eb19000       \               winex11
ELF     7eb6e000-7eb8f000       Deferred        libexpat.so.1
ELF     7eb8f000-7ebb9000       Deferred        libfontconfig.so.1
ELF     7ebb9000-7ebce000       Deferred        libz.so.1
ELF     7ebce000-7ec3e000       Deferred        libfreetype.so.6
ELF     7ec51000-7eca3000       Deferred        advapi32<elf>
  \-PE  7ec60000-7eca3000       \               advapi32
ELF     7eca3000-7ed3e000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed3e000       \               gdi32
ELF     7ed3e000-7ee85000       Export          user32<elf>
  \-PE  7ed60000-7ee85000       \               user32
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c37000-b7c3b000       Deferred        libdl.so.2
ELF     b7c3b000-b7d8a000       Deferred        libc.so.6
ELF     b7d8b000-b7da3000       Deferred        libpthread.so.0
ELF     b7db6000-b7eec000       Deferred        libwine.so.1
ELF     b7eee000-b7f0a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008
        00000009    0
0000000c
        0000001d    0
        0000000e    0
        0000000d    0
0000000f
        00000010    0
0000001a
        00000020    0
        0000001f    0
        0000001c    0
        0000001b    0
0000003f (D) C:\CW32\cw32.exe
        00000040    2 <==
Backtrace:
=>1 0x1013f282 in cwdll32 (+0x3f282) (0x0032ee08)
  2 0x1019cc70 in cwdll32 (+0x9cc70) (0x0032ee10)
  3 0x1012323e in cwdll32 (+0x2323e) (0x0032f050)
  4 0x7ee065ba WINPROC_wrapper+0x1a() in user32 (0x0032f080)
  5 0x7ee06c9e WINPROC_wrapper+0x6fe() in user32 (0x0032f0c0)
  6 0x7ee0b535 in user32 (+0xab535) (0x0032f590)
  7 0x7ee0c0fb in user32 (+0xac0fb) (0x0032f5d0)
  8 0x7edcf11a in user32 (+0x6f11a) (0x0032f640)
  9 0x7edd239d in user32 (+0x7239d) (0x0032f6a0)
  10 0x7edd280a SendMessageW+0x4a() in user32 (0x0032f6e0)
  11 0x7ee013fe in user32 (+0xa13fe) (0x0032f7a0)
  12 0x7edfcdfc in user32 (+0x9cdfc) (0x0032fa70)
  13 0x7edfedfd CreateWindowExA+0xbd() in user32 (0x0032fcd0)
  14 0x1011eebc in cwdll32 (+0x1eebc) (0x0032fd60)
  15 0x1012049b in cwdll32 (+0x2049b) (0x0032fdb8)
  16 0x1011fe47 in cwdll32 (+0x1fe47) (0x0032fe20)
  17 0x1011f6da in cwdll32 (+0x1f6da) (0x0032fe3c)
  18 0x00401288 in cw32 (+0x1288) (0x0032fe7c)
  19 0x00401db2 in cw32 (+0x1db2) (0x0032ff08)
  20 0x7b8773a7 in kernel32 (+0x573a7) (0x0032ffe8)

```

Any ideas?

I rolled back to 0.9.59 and cw32.exe runs correctly again. fwiw, here is the trace when starting under 0.9.59

```
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:heap:RtlCompactHeap (0x7f9c0000, 0x0) stub
fixme:font:WineEngCreateFontInstance Untranslated charset 255

```

---

### Post by madewokherd on 2008-07-13
There is a Wine bug for this problem at [http://bugs.winehq.org/show_bug.cgi?id=14012](http://bugs.winehq.org/show_bug.cgi?id=14012)

The developers need someone who has this program to run a regression test to find out what patch broke it. See [http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting) for instructions if you're willing to do that.

---

### Post by skunkTrader on 2009-06-19
This appears to be fixed in Wine 1.1.24

---

