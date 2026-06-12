---
title: "Question about Terminal Outputs?"
date: 2008-02-25
forum: Wine
---

### Post by Dark Aspect on 2008-02-25
Where should I post em to help the wine project?

I have the terminal output of two games that don't work but one only has fixme messages.Can I give data to Bugzilla with nothing but fixme messages?The other game calls out to address zero:confused::confused: so that might be a bug IDK.If Bugzilla is not a good place to give such data can I use the wine wiki?

Thanks for any info.

---

### Post by Faud on 2008-02-26
You can use bugzilla but dont post the fixme messages, those are normal and can be disabled if you choose.

---

### Post by CarpKing on 2008-02-26
Calling to address zero seems to be a common problem in crashing Wine apps, so I suspect it may be more of a symptom than a bug in and of itself.  Any new information on this is of course welcome.

---

### Post by Dark Aspect on 2008-02-26
How can I disable the fixme messages in wine?

My Profile on wine's appDB is Dan Jenkins (a fake name).The game that gives me more then fixme messages and calls out to address zero is Silent hill 4.Can some one tell me if this is a bug:

> Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7bfcedf2).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:7bfcedf2 ESP:0033f8e0 EBP:0033f938 EFLAGS:00210202( - 00 - -RI1)
EAX:07f77430 EBX:7bffea8c ECX:00000000 EDX:00000004
ESI:019b1c58 EDI:07b6d820
Stack dump:
0x0033f8e0: 019b1c58 07e8cf50 00000008 e436eb84
0x0033f8f0: 11ce524f 2000539f 70a70baf 00000001
0x0033f900: 00000000 00000000 0f6417d6 11d0c318
0x0033f910: 07e8cf50 003122c9 00000000 07b6d820
0x0033f920: 00000004 ff0a0000 00000002 0150c138
0x0033f930: 0150c130 0150c134 0150c140 00413a4d
Backtrace:
=>1 0x7bfcedf2 in quartz (+0x1edf2) (0x0033f938)
2 0x00413a4d in silent hill 4 (+0x13a4d) (0x0150c140)
3 0x07ba3f90 (0x00000000)
0x7bfcedf2: movl 0x0(%ecx),%eax
Modules:
Module Address Debug info Name (84 modules)
PE 400000- 13e2b28 Export silent hill 4
ELF 7a515000-7a5d2000 Deferred comctl32
\-PE 7a520000-7a5d2000 \ comctl32
ELF 7b800000-7b929000 Deferred kernel32
\-PE 7b820000-7b929000 \ kernel32
ELF 7b934000-7b9d2000 Deferred oleaut32
\-PE 7b950000-7b9d2000 \ oleaut32
ELF 7bc00000-7bc97000 Deferred ntdll
\-PE 7bc10000-7bc97000 \ ntdll
ELF 7bf00000-7bf03000 Deferred
ELF 7bf4b000-7bf7d000 Deferred uxtheme
\-PE 7bf50000-7bf7d000 \ uxtheme
ELF 7bf7d000-7bfa4000 Deferred msvfw32
\-PE 7bf80000-7bfa4000 \ msvfw32
ELF 7bfa4000-7c000000 Export quartz
\-PE 7bfb0000-7c000000 \ quartz
ELF 7d203000-7d229000 Deferred msacm32
\-PE 7d210000-7d229000 \ msacm32
ELF 7d229000-7d241000 Deferred msacm32
\-PE 7d230000-7d241000 \ msacm32
ELF 7d241000-7d306000 Deferred libasound.so.2
ELF 7d552000-7d567000 Deferred midimap
\-PE 7d560000-7d567000 \ midimap
ELF 7d567000-7d599000 Deferred winealsa
\-PE 7d570000-7d599000 \ winealsa
ELF 7d59b000-7d5a0000 Deferred libxfixes.so.3
ELF 7d5a0000-7d5a9000 Deferred libxcursor.so.1
ELF 7d5a9000-7d5af000 Deferred libxrandr.so.2
ELF 7d5af000-7d5b7000 Deferred libxrender.so.1
ELF 7dadd000-7db66000 Deferred winex11
\-PE 7daf0000-7db66000 \ winex11
ELF 7dc0f000-7dc2f000 Deferred libexpat.so.1
ELF 7dc2f000-7dc5a000 Deferred libfontconfig.so.1
ELF 7dc5a000-7dc6e000 Deferred libz.so.1
ELF 7dc6e000-7dcd9000 Deferred libfreetype.so.6
ELF 7dcd9000-7dcf6000 Deferred imm32
\-PE 7dce0000-7dcf6000 \ imm32
ELF 7dcf6000-7dd3e000 Deferred dsound
\-PE 7dd00000-7dd3e000 \ dsound
ELF 7dd3e000-7dd74000 Deferred dinput
\-PE 7dd50000-7dd74000 \ dinput
ELF 7dd74000-7dd8d000 Deferred dinput8
\-PE 7dd80000-7dd8d000 \ dinput8
ELF 7dd8d000-7de1b000 Deferred winmm
\-PE 7dda0000-7de1b000 \ winmm
ELF 7de80000-7e706000 Deferred libglcore.so.1
ELF 7e706000-7e786000 Deferred libglu.so.1
ELF 7e786000-7e812000 Deferred libgl.so.1
ELF 7e812000-7e903000 Deferred libx11.so.6
ELF 7e903000-7e911000 Deferred libxext.so.6
ELF 7e911000-7e929000 Deferred libice.so.6
ELF 7e929000-7e9f4000 Deferred wined3d
\-PE 7e940000-7e9f4000 \ wined3d
ELF 7e9f4000-7ea1f000 Deferred d3d8
\-PE 7ea00000-7ea1f000 \ d3d8
ELF 7ea1f000-7ea32000 Deferred libresolv.so.2
ELF 7ea32000-7ea50000 Deferred iphlpapi
\-PE 7ea40000-7ea50000 \ iphlpapi
ELF 7ea50000-7eaa9000 Deferred rpcrt4
\-PE 7ea60000-7eaa9000 \ rpcrt4
ELF 7eaa9000-7eb48000 Deferred ole32
\-PE 7eac0000-7eb48000 \ ole32
ELF 7eb48000-7eb90000 Deferred advapi32
\-PE 7eb50000-7eb90000 \ advapi32
ELF 7eb90000-7eb9c000 Deferred libgcc_s.so.1
ELF 7eb9c000-7eba1000 Deferred libxdmcp.so.6
ELF 7eba1000-7eba4000 Deferred libxau.so.6
ELF 7eba4000-7ebad000 Deferred libsm.so.6
ELF 7ec97000-7ed57000 Deferred gdi32
\-PE 7ecb0000-7ed57000 \ gdi32
ELF 7ed57000-7ee94000 Deferred user32
\-PE 7ed70000-7ee94000 \ user32
ELF 7efa6000-7efb1000 Deferred libnss_files.so.2
ELF 7efb1000-7efc8000 Deferred libnsl.so.1
ELF 7efc8000-7efef000 Deferred libm.so.6
ELF 7efef000-7eff1000 Deferred libnvidia-tls.so.1
ELF 7eff1000-7eff6000 Deferred libxxf86vm.so.1
ELF 7eff6000-7f000000 Deferred libnss_nis.so.2
ELF b7c61000-b7c6a000 Deferred libnss_compat.so.2
ELF b7c6b000-b7c6f000 Deferred libdl.so.2
ELF b7c6f000-b7db0000 Deferred libc.so.6
ELF b7db1000-b7dc8000 Deferred libpthread.so.0
ELF b7dd9000-b7eed000 Deferred libwine.so.1
ELF b7eef000-b7f0a000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
0000000a
0000000c 0
0000000b 0
00000008 (D) C:\Program Files\Konami\SILENT HILL 4\SILENT HILL 4.exe
0000000e 15
0000000d 0
00000009 0

No fixme messages,So can I send this to bugzilla?

---

