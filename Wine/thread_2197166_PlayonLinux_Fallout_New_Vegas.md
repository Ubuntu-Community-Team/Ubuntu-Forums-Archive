---
title: "PlayonLinux Fallout New Vegas"
date: 2014-01-02
forum: Wine
---

### Post by Jeff_Spitzer on 2014-01-02
Hey New vegas starts up ok, but when I go to load a new game my game crashes.

This is from the "Show Details" button:
```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00b4f0b9).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00b4f0b9 ESP:15f1df1c EBP:15f1e7bc EFLAGS:00210206(  R- --  I   - -P- )
 EAX:00000000 EBX:048bd9dc ECX:b6d45b02 EDX:16554148
 ESI:00000000 EDI:047ad020
Stack dump:
0x15f1df1c:  0000001d 047ad020 7ff98000 7bcbb624
0x15f1df2c:  00f99060 010e3b6c 048d3878 15f1df48
0x15f1df3c:  00a9e6a3 000003f0 01f97018 15f1df90
0x15f1df4c:  00a9ba1b 00000088 00110000 15f1dfb8
0x15f1df5c:  7bc4b897 00000000 b6d45a72 7ff98000
0x15f1df6c:  0030a8ab 7bcbb624 048d3c68 15f1df64
Backtrace:
=>0 0x00b4f0b9 in falloutnv (+0x74f0b9) (0x15f1e7bc)
  1 0x00611d48 in falloutnv (+0x211d47) (0x15f1e918)
  2 0x00605414 in falloutnv (+0x205413) (0x15f1e93c)
  3 0x0043edbb in falloutnv (+0x3edba) (0x15f1e970)
  4 0x00c36e34 in falloutnv (+0x836e33) (0x15f1e97c)
  5 0x00c38327 in falloutnv (+0x838326) (0x15f1ea10)
  6 0x00c39e4f in falloutnv (+0x839e4e) (0x15f1ea18)
  7 0x7bc78780 call_thread_func_wrapper+0xb() in ntdll (0x15f1ea28)
  8 0x7bc7b68d call_thread_func+0x7c() in ntdll (0x15f1eaf8)
  9 0x7bc7875e RtlRaiseException+0x21() in ntdll (0x15f1eb18)
  10 0x7bc816bd in ntdll (+0x716bc) (0x15f1f368)
  11 0xb75e6d78 start_thread+0xd7() in libpthread.so.0 (0x15f1f468)
  12 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  13 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  14 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  15 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  16 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  17 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  18 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  19 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  20 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  21 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  22 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  23 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  24 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  25 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  26 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  27 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  28 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  29 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  30 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  31 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  32 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  33 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  34 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  35 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  36 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  37 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  38 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  39 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  40 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  41 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  42 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  43 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  44 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  45 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  46 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  47 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  48 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  49 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  50 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  51 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  52 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  53 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  54 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  55 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  56 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  57 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  58 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  59 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  60 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  61 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  62 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  63 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  64 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  65 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  66 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  67 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  68 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  69 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  70 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  71 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  72 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  73 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  74 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  75 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  76 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  77 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  78 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  79 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  80 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  81 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  82 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  83 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  84 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  85 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  86 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  87 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  88 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  89 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  90 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  91 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  92 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  93 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  94 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  95 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  96 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  97 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  98 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  99 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  100 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  101 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  102 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  103 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  104 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  105 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  106 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  107 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  108 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  109 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  110 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  111 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  112 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  113 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  114 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  115 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  116 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  117 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  118 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  119 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  120 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  121 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  122 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  123 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  124 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  125 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  126 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  127 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  128 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  129 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  130 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  131 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  132 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  133 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  134 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  135 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  136 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  137 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  138 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  139 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  140 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  141 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  142 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  143 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  144 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  145 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  146 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  147 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  148 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  149 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  150 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  151 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  152 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  153 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  154 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  155 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  156 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  157 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  158 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  159 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  160 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  161 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  162 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  163 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  164 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  165 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  166 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  167 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  168 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  169 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  170 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  171 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  172 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  173 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  174 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  175 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  176 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  177 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  178 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  179 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  180 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  181 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  182 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  183 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  184 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  185 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  186 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  187 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  188 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  189 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  190 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  191 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  192 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  193 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  194 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  195 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  196 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  197 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  198 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  199 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
  200 0xb751cfee __clone+0x5d() in libc.so.6 (0x00000000)
0x00b4f0b9: movl    0x0(%esi),%eax
Modules:
Module    Address            Debug info    Name (141 modules)
PE      340000-  356000    Deferred        xinput1_3
PE      400000- 1400000    Export          falloutnv
PE     1400000- 17c8000    Deferred        d3dx9_38
PE     17d0000- 1903000    Deferred        libvorbis
PE    10000000-1001e000    Deferred        libvorbisfile
PE    18000000-18068000    Deferred        binkw32
PE    35500000-35708000    Deferred        quartz
PE    3b400000-3b41d000    Deferred        steam_api
ELF    7a299000-7b800000    Deferred        libllvm-3.2.so.1
ELF    7b800000-7b917000    Deferred        kernel32<elf>
  \-PE    7b810000-7b917000    \               kernel32
ELF    7bc00000-7bcd8000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcd8000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7c424000-7c483000    Deferred        libmpg123.so.0
ELF    7c529000-7c53e000    Deferred        winemp3<elf>
  \-PE    7c530000-7c53e000    \               winemp3
ELF    7c53e000-7c564000    Deferred        devenum<elf>
  \-PE    7c540000-7c564000    \               devenum
ELF    7c564000-7c590000    Deferred        libvorbis.so.0
ELF    7c590000-7c708000    Deferred        libvorbisenc.so.2
ELF    7c708000-7c758000    Deferred        libflac.so.8
ELF    7c758000-7c7cc000    Deferred        libsndfile.so.1
ELF    7c7cc000-7c816000    Deferred        libdbus-1.so.3
ELF    7c924000-7c939000    Deferred        midimap<elf>
  \-PE    7c930000-7c939000    \               midimap
ELF    7c939000-7c9a4000    Deferred        libpulsecommon-3.0.so
ELF    7c9a4000-7c9f3000    Deferred        libpulse.so.0
ELF    7c9f3000-7cae5000    Deferred        libasound.so.2
ELF    7caf7000-7cafe000    Deferred        libasound_module_pcm_pulse.so
ELF    7cb05000-7cb34000    Deferred        winealsa<elf>
  \-PE    7cb10000-7cb34000    \               winealsa
ELF    7cb34000-7cc6a000    Deferred        oleaut32<elf>
  \-PE    7cb50000-7cc6a000    \               oleaut32
ELF    7cc6a000-7cc8b000    Deferred        mmdevapi<elf>
  \-PE    7cc70000-7cc8b000    \               mmdevapi
ELF    7cc8b000-7ccd6000    Deferred        dinput<elf>
  \-PE    7cc90000-7ccd6000    \               dinput
ELF    7ccdd000-7ccf5000    Deferred        msacm32<elf>
  \-PE    7cce0000-7ccf5000    \               msacm32
ELF    7ccf5000-7cd09000    Deferred        avicap32<elf>
  \-PE    7cd00000-7cd09000    \               avicap32
ELF    7cd14000-7cd1c000    Deferred        libltdl.so.7
ELF    7cd9c000-7cdc0000    Deferred        imm32<elf>
  \-PE    7cda0000-7cdc0000    \               imm32
ELF    7cf25000-7d304000    Deferred        libgallium.so.0
ELF    7d304000-7d6bf000    Deferred        libdricore9.1.7.so.1
ELF    7d790000-7d798000    Deferred        libogg.so.0
ELF    7d798000-7d79f000    Deferred        libasyncns.so.0
ELF    7d81f000-7d853000    Deferred        libtxc_dxtn.so
ELF    7d853000-7d85a000    Deferred        libffi.so.6
ELF    7d85a000-7d877000    Deferred        libgcc_s.so.1
ELF    7d960000-7d968000    Deferred        libdrm_nouveau.so.2
ELF    7d968000-7da9b000    Deferred        nouveau_dri.so
ELF    7da9b000-7daa8000    Deferred        libdrm.so.2
ELF    7daa8000-7daad000    Deferred        libxcb-dri2.so.0
ELF    7daad000-7dac8000    Deferred        libxcb-glx.so.0
ELF    7dac8000-7db21000    Deferred        libgl.so.1
ELF    7db27000-7db31000    Deferred        libwrap.so.0
ELF    7db31000-7db3b000    Deferred        libjson.so.0
ELF    7db41000-7db77000    Deferred        uxtheme<elf>
  \-PE    7db50000-7db77000    \               uxtheme
ELF    7db77000-7db7e000    Deferred        libxfixes.so.3
ELF    7db7e000-7db89000    Deferred        libxcursor.so.1
ELF    7db89000-7db99000    Deferred        libxi.so.6
ELF    7db99000-7db9d000    Deferred        libxcomposite.so.1
ELF    7db9d000-7dba8000    Deferred        libxrandr.so.2
ELF    7dba8000-7dbb2000    Deferred        libxrender.so.1
ELF    7dbb2000-7dbb8000    Deferred        libxxf86vm.so.1
ELF    7dbb8000-7dbbc000    Deferred        libxinerama.so.1
ELF    7dbbc000-7dbc0000    Deferred        libxau.so.6
ELF    7dbc0000-7dbe5000    Deferred        libxcb.so.1
ELF    7dbe5000-7dbeb000    Deferred        libuuid.so.1
ELF    7dbeb000-7dd22000    Deferred        libx11.so.6
ELF    7dd22000-7dd34000    Deferred        libxext.so.6
ELF    7dd34000-7dd4e000    Deferred        libice.so.6
ELF    7dd4e000-7dd57000    Deferred        libsm.so.6
ELF    7dd57000-7dd5a000    Deferred        libx11-xcb.so.1
ELF    7dd5a000-7dd5e000    Deferred        libxdamage.so.1
ELF    7dd5e000-7dd75000    Deferred        libglapi.so.0
ELF    7dd77000-7de09000    Deferred        winex11<elf>
  \-PE    7dd80000-7de09000    \               winex11
ELF    7de61000-7de89000    Deferred        libexpat.so.1
ELF    7de89000-7dec2000    Deferred        libfontconfig.so.1
ELF    7dec2000-7ded6000    Deferred        libz.so.1
ELF    7ded6000-7df71000    Deferred        libfreetype.so.6
ELF    7df91000-7dfda000    Deferred        dsound<elf>
  \-PE    7dfa0000-7dfda000    \               dsound
ELF    7dfda000-7e004000    Deferred        msacm32<elf>
  \-PE    7dfe0000-7e004000    \               msacm32
ELF    7e004000-7e0be000    Deferred        winmm<elf>
  \-PE    7e010000-7e0be000    \               winmm
ELF    7e0be000-7e169000    Deferred        msvcrt<elf>
  \-PE    7e0d0000-7e169000    \               msvcrt
ELF    7e169000-7e180000    Deferred        libresolv.so.2
ELF    7e185000-7e1a0000    Deferred        dinput8<elf>
  \-PE    7e190000-7e1a0000    \               dinput8
ELF    7e1a0000-7e1c5000    Deferred        iphlpapi<elf>
  \-PE    7e1b0000-7e1c5000    \               iphlpapi
ELF    7e1c5000-7e1fa000    Deferred        ws2_32<elf>
  \-PE    7e1d0000-7e1fa000    \               ws2_32
ELF    7e1fa000-7e215000    Deferred        wsock32<elf>
  \-PE    7e200000-7e215000    \               wsock32
ELF    7e215000-7e353000    Deferred        ole32<elf>
  \-PE    7e230000-7e353000    \               ole32
ELF    7e353000-7e3cd000    Deferred        shlwapi<elf>
  \-PE    7e360000-7e3cd000    \               shlwapi
ELF    7e3cd000-7e601000    Deferred        shell32<elf>
  \-PE    7e3e0000-7e601000    \               shell32
ELF    7e601000-7e683000    Deferred        rpcrt4<elf>
  \-PE    7e610000-7e683000    \               rpcrt4
ELF    7e683000-7e6f3000    Deferred        setupapi<elf>
  \-PE    7e690000-7e6f3000    \               setupapi
ELF    7e6f3000-7e7fb000    Deferred        opengl32<elf>
  \-PE    7e710000-7e7fb000    \               opengl32
ELF    7e7fb000-7e93d000    Deferred        wined3d<elf>
  \-PE    7e810000-7e93d000    \               wined3d
ELF    7e93d000-7e979000    Deferred        d3d9<elf>
  \-PE    7e940000-7e979000    \               d3d9
ELF    7e979000-7e9e8000    Deferred        advapi32<elf>
  \-PE    7e990000-7e9e8000    \               advapi32
ELF    7e9e8000-7eb00000    Deferred        gdi32<elf>
  \-PE    7e9f0000-7eb00000    \               gdi32
ELF    7eb00000-7ec5c000    Deferred        user32<elf>
  \-PE    7eb10000-7ec5c000    \               user32
ELF    7ec5c000-7ed62000    Deferred        comctl32<elf>
  \-PE    7ec60000-7ed62000    \               comctl32
ELF    7ed62000-7ed6f000    Deferred        libnss_files.so.2
ELF    7ed6f000-7ed7b000    Deferred        libnss_nis.so.2
ELF    7ed7b000-7ed94000    Deferred        libnsl.so.1
ELF    7ed94000-7ed9d000    Deferred        libnss_compat.so.2
ELF    7ef9d000-7efe0000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    b7426000-b742b000    Deferred        libdl.so.2
ELF    b742b000-b75df000    Dwarf           libc.so.6
ELF    b75e0000-b75fb000    Dwarf           libpthread.so.0
ELF    b7612000-b761b000    Deferred        librt.so.1
ELF    b761b000-b77d0000    Dwarf           libwine.so.1
ELF    b77d2000-b77f4000    Deferred        ld-linux.so.2
ELF    b77f4000-b77f5000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001d    0
    0000001c    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    00000020    0
    00000018    0
    00000017    0
    00000013    0
0000001a plugplay.exe
    0000001f    0
    0000001e    0
    0000001b    0
00000021 explorer.exe
    00000023    0
    00000022    0
00000029 (D) C:\Program Files\Bethesda Softworks\Fallout New Vegas\FalloutNV.exe
    0000003f    0
    0000003e    0
    0000003c   15
    0000003b    0
    0000003a    0 <==
    00000038   -1
    00000037    1
    00000036    1
    00000035   15
    00000034    0
    00000033    0
    00000032   -1
    00000030    0
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    0000002b    0
    0000002a    0
System information:
    Wine build: wine-1.6
    Platform: i386
    Host system: Linux
    Host version: 3.8.0-35-generic
```

---

### Post by Mark Phelps on 2014-01-03
Here's a link to the WineHQ web page for that game -- perhaps something in this will help: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=21692]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=21692")

---

### Post by Jeff_Spitzer on 2014-01-03
I had no idea that website existed so thank you!  Thank actually helped me to get Project 64 to work haha.  Sadly I didn't have any luck with Fallout.  It crashed at the same place.

Here is the crash log:

```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00b4f0b9).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00b4f0b9 ESP:15f8df1c EBP:15f8e7bc EFLAGS:00210206(  R- --  I   - -P- )
 EAX:00000000 EBX:0486a608 ECX:f5dc0b34 EDX:1667b4e8
 ESI:00000000 EDI:0478d9a0
Stack dump:
0x15f8df1c:  0000001d 0478d9a0 00c39e30 7bcb2ca0
0x15f8df2c:  00f68400 010e3b6c 048b24a8 15f8df48
0x15f8df3c:  00a9e6a3 000003f0 01f663b8 15f8df90
0x15f8df4c:  00a9ba1b 000003f0 00000000 0e880c8c
0x15f8df5c:  01f663b8 00000000 f5dc0a44 00c39e30
0x15f8df6c:  7bc3ba87 7bcb2ca0 048b2898 7bc4fd11
Backtrace:
=>0 0x00b4f0b9 in falloutnv (+0x74f0b9) (0x15f8e7bc)
  1 0x00611d48 in falloutnv (+0x211d47) (0x15f8e918)
  2 0x00605414 in falloutnv (+0x205413) (0x15f8e93c)
  3 0x0043edbb in falloutnv (+0x3edba) (0x15f8e970)
  4 0x00c36e34 in falloutnv (+0x836e33) (0x15f8e97c)
  5 0x00c38327 in falloutnv (+0x838326) (0x15f8ea10)
  6 0x00c39e4f in falloutnv (+0x839e4e) (0x15f8ea18)
  7 0x7bc7cfc0 call_thread_func_wrapper+0xb() in ntdll (0x15f8ea28)
  8 0x7bc7d21d call_thread_func+0x7c() in ntdll (0x15f8eaf8)
  9 0x7bc7cf9e RtlRaiseException+0x21() in ntdll (0x15f8eb18)
  10 0x7bc87539 in ntdll (+0x77538) (0x15f8f368)
  11 0xf75c2d78 start_thread+0xd7() in libpthread.so.0 (0x15f8f468)
  12 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  13 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  14 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  15 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  16 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  17 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  18 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  19 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  20 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  21 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  22 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  23 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  24 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  25 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  26 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  27 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  28 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  29 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  30 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  31 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  32 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  33 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  34 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  35 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  36 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  37 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  38 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  39 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  40 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  41 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  42 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  43 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  44 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  45 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  46 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  47 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  48 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  49 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  50 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  51 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  52 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  53 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  54 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  55 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  56 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  57 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  58 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  59 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  60 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  61 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  62 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  63 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  64 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  65 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  66 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  67 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  68 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  69 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  70 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  71 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  72 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  73 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  74 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  75 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  76 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  77 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  78 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  79 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  80 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  81 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  82 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  83 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  84 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  85 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  86 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  87 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  88 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  89 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  90 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  91 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  92 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  93 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  94 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  95 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  96 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  97 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  98 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  99 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  100 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  101 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  102 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  103 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  104 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  105 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  106 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  107 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  108 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  109 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  110 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  111 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  112 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  113 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  114 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  115 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  116 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  117 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  118 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  119 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  120 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  121 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  122 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  123 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  124 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  125 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  126 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  127 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  128 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  129 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  130 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  131 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  132 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  133 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  134 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  135 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  136 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  137 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  138 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  139 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  140 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  141 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  142 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  143 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  144 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  145 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  146 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  147 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  148 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  149 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  150 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  151 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  152 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  153 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  154 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  155 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  156 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  157 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  158 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  159 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  160 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  161 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  162 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  163 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  164 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  165 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  166 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  167 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  168 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  169 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  170 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  171 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  172 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  173 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  174 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  175 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  176 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  177 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  178 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  179 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  180 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  181 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  182 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  183 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  184 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  185 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  186 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  187 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  188 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  189 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  190 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  191 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  192 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  193 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  194 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  195 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  196 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  197 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  198 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  199 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
  200 0xf74f901e __clone+0x5d() in libc.so.6 (0x00000000)
0x00b4f0b9: movl    0x0(%esi),%eax
Modules:
Module    Address            Debug info    Name (138 modules)
PE      340000-  356000    Deferred        xinput1_3
PE      400000- 1400000    Export          falloutnv
PE     1400000- 17c8000    Deferred        d3dx9_38
PE     17d0000- 1903000    Deferred        libvorbis
PE    10000000-1001e000    Deferred        libvorbisfile
PE    18000000-18068000    Deferred        binkw32
PE    35500000-35708000    Deferred        quartz
PE    3b400000-3b41d000    Deferred        steam_api
ELF    7a12c000-7b800000    Deferred        libllvm-3.3.so.1
ELF    7b800000-7ba4b000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba4b000    \               kernel32
ELF    7baa1000-7bb00000    Deferred        libmpg123.so.0
ELF    7bc00000-7bccf000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bccf000    \               ntdll
ELF    7bcd9000-7bce1000    Deferred        libltdl.so.7
ELF    7bce1000-7bcf6000    Deferred        winemp3<elf>
  \-PE    7bcf0000-7bcf6000    \               winemp3
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7c40e000-7c422000    Deferred        avicap32<elf>
  \-PE    7c410000-7c422000    \               avicap32
ELF    7c422000-7c446000    Deferred        devenum<elf>
  \-PE    7c430000-7c446000    \               devenum
ELF    7c454000-7c45d000    Deferred        libogg.so.0
ELF    7c45d000-7c489000    Deferred        libvorbis.so.0
ELF    7c489000-7c601000    Deferred        libvorbisenc.so.2
ELF    7c601000-7c635000    Deferred        libflac.so.8
ELF    7c635000-7c6a7000    Deferred        libsndfile.so.1
ELF    7c6a7000-7c6f2000    Deferred        libdbus-1.so.3
ELF    7c6f2000-7c761000    Deferred        libpulsecommon-4.0.so
ELF    7c761000-7c7b0000    Deferred        libpulse.so.0
ELF    7c7b0000-7c8a6000    Deferred        libasound.so.2
ELF    7c8a6000-7c8d3000    Deferred        winealsa<elf>
  \-PE    7c8b0000-7c8d3000    \               winealsa
ELF    7c8d3000-7c9eb000    Deferred        oleaut32<elf>
  \-PE    7c8f0000-7c9eb000    \               oleaut32
ELF    7c9eb000-7ca31000    Deferred        dinput<elf>
  \-PE    7c9f0000-7ca31000    \               dinput
ELF    7ca5f000-7ca77000    Deferred        msacm32<elf>
  \-PE    7ca60000-7ca77000    \               msacm32
ELF    7ccf7000-7cd0c000    Deferred        midimap<elf>
  \-PE    7cd00000-7cd0c000    \               midimap
ELF    7cd0c000-7cd13000    Deferred        libasound_module_pcm_pulse.so
ELF    7cd1a000-7cd3a000    Deferred        mmdevapi<elf>
  \-PE    7cd20000-7cd3a000    \               mmdevapi
ELF    7cd3a000-7cd5c000    Deferred        imm32<elf>
  \-PE    7cd40000-7cd5c000    \               imm32
ELF    7ce80000-7d288000    Deferred        libgallium.so.0
ELF    7d383000-7d38a000    Deferred        libasyncns.so.0
ELF    7d38a000-7d394000    Deferred        libwrap.so.0
ELF    7d394000-7d39f000    Deferred        libjson-c.so.2
ELF    7d422000-7d456000    Deferred        libtxc_dxtn.so
ELF    7d456000-7d45d000    Deferred        libffi.so.6
ELF    7d45d000-7d47a000    Deferred        libgcc_s.so.1
ELF    7d563000-7d56b000    Deferred        libdrm_nouveau.so.2
ELF    7d56b000-7d953000    Deferred        libdricore9.2.1.so.1
ELF    7d953000-7da9f000    Deferred        nouveau_dri.so
ELF    7da9f000-7daac000    Deferred        libdrm.so.2
ELF    7daac000-7dab1000    Deferred        libxcb-dri2.so.0
ELF    7dab1000-7dacc000    Deferred        libxcb-glx.so.0
ELF    7dacc000-7db25000    Deferred        libgl.so.1
ELF    7db47000-7db7a000    Deferred        uxtheme<elf>
  \-PE    7db50000-7db7a000    \               uxtheme
ELF    7db7a000-7db80000    Deferred        libxfixes.so.3
ELF    7db80000-7db8b000    Deferred        libxcursor.so.1
ELF    7db8b000-7db9c000    Deferred        libxi.so.6
ELF    7db9c000-7dba0000    Deferred        libxcomposite.so.1
ELF    7dba0000-7dbab000    Deferred        libxrandr.so.2
ELF    7dbab000-7dbb6000    Deferred        libxrender.so.1
ELF    7dbb6000-7dbbc000    Deferred        libxxf86vm.so.1
ELF    7dbbc000-7dbc0000    Deferred        libxinerama.so.1
ELF    7dbc0000-7dbc4000    Deferred        libxau.so.6
ELF    7dbc4000-7dbe9000    Deferred        libxcb.so.1
ELF    7dbe9000-7dd1e000    Deferred        libx11.so.6
ELF    7dd1e000-7dd31000    Deferred        libxext.so.6
ELF    7dd34000-7dd37000    Deferred        libx11-xcb.so.1
ELF    7dd37000-7dd3b000    Deferred        libxdamage.so.1
ELF    7dd3b000-7dd51000    Deferred        libglapi.so.0
ELF    7dd53000-7ddde000    Deferred        winex11<elf>
  \-PE    7dd60000-7ddde000    \               winex11
ELF    7de18000-7de41000    Deferred        libexpat.so.1
ELF    7de41000-7de7b000    Deferred        libfontconfig.so.1
ELF    7de7b000-7de8f000    Deferred        libz.so.1
ELF    7de8f000-7df2e000    Deferred        libfreetype.so.6
ELF    7df50000-7df95000    Deferred        dsound<elf>
  \-PE    7df60000-7df95000    \               dsound
ELF    7df95000-7dfbd000    Deferred        msacm32<elf>
  \-PE    7dfa0000-7dfbd000    \               msacm32
ELF    7dfbd000-7e070000    Deferred        winmm<elf>
  \-PE    7dfd0000-7e070000    \               winmm
ELF    7e070000-7e10c000    Deferred        msvcrt<elf>
  \-PE    7e090000-7e10c000    \               msvcrt
ELF    7e10c000-7e123000    Deferred        libresolv.so.2
ELF    7e12a000-7e145000    Deferred        dinput8<elf>
  \-PE    7e130000-7e145000    \               dinput8
ELF    7e145000-7e169000    Deferred        iphlpapi<elf>
  \-PE    7e150000-7e169000    \               iphlpapi
ELF    7e169000-7e19a000    Deferred        ws2_32<elf>
  \-PE    7e170000-7e19a000    \               ws2_32
ELF    7e19a000-7e1b4000    Deferred        wsock32<elf>
  \-PE    7e1a0000-7e1b4000    \               wsock32
ELF    7e1b4000-7e2ca000    Deferred        ole32<elf>
  \-PE    7e1d0000-7e2ca000    \               ole32
ELF    7e2ca000-7e33a000    Deferred        shlwapi<elf>
  \-PE    7e2e0000-7e33a000    \               shlwapi
ELF    7e33a000-7e557000    Deferred        shell32<elf>
  \-PE    7e350000-7e557000    \               shell32
ELF    7e557000-7e5d1000    Deferred        rpcrt4<elf>
  \-PE    7e560000-7e5d1000    \               rpcrt4
ELF    7e5d1000-7e63b000    Deferred        setupapi<elf>
  \-PE    7e5e0000-7e63b000    \               setupapi
ELF    7e63b000-7e720000    Deferred        opengl32<elf>
  \-PE    7e660000-7e720000    \               opengl32
ELF    7e720000-7e851000    Deferred        wined3d<elf>
  \-PE    7e730000-7e851000    \               wined3d
ELF    7e851000-7e888000    Deferred        d3d9<elf>
  \-PE    7e860000-7e888000    \               d3d9
ELF    7e888000-7e8ee000    Deferred        advapi32<elf>
  \-PE    7e890000-7e8ee000    \               advapi32
ELF    7e8ee000-7e9fc000    Deferred        gdi32<elf>
  \-PE    7e900000-7e9fc000    \               gdi32
ELF    7e9fc000-7eb44000    Deferred        user32<elf>
  \-PE    7ea10000-7eb44000    \               user32
ELF    7eb44000-7ec3c000    Deferred        comctl32<elf>
  \-PE    7eb50000-7ec3c000    \               comctl32
ELF    7ec3c000-7ec49000    Deferred        libnss_files.so.2
ELF    7ec49000-7ec55000    Deferred        libnss_nis.so.2
ELF    7ec55000-7ec6e000    Deferred        libnsl.so.1
ELF    7ec78000-7ec90000    Deferred        version<elf>
  \-PE    7ec80000-7ec90000    \               version
ELF    f73b5000-f73be000    Deferred        libnss_compat.so.2
ELF    f73bf000-f7402000    Deferred        libm.so.6
ELF    f7402000-f7407000    Deferred        libdl.so.2
ELF    f7407000-f75bb000    Dwarf           libc.so.6
ELF    f75bc000-f75d7000    Dwarf           libpthread.so.0
ELF    f75f0000-f75f9000    Deferred        librt.so.1
ELF    f75f9000-f77ac000    Dwarf           libwine.so.1
ELF    f77ae000-f77d0000    Deferred        ld-linux.so.2
ELF    f77d0000-f77d1000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000020    0
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
00000021 explorer.exe
    00000022    0
00000029 (D) C:\Program Files\Bethesda Softworks\Fallout New Vegas\FalloutNV.exe
    00000040    0
    0000003f    0
    0000003d   15
    0000003c    0
    0000003b    0 <==
    00000039   -1
    00000038    1
    00000037    1
    00000036   15
    00000035    0
    00000034    0
    00000033    0
    00000032   -1
    00000030    0
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    0000002b    0
    0000002a    0
System information:
    Wine build: wine-1.7.9
    Platform: i386
    Host system: Linux
    Host version: 3.11.0-15-generic
```

---

