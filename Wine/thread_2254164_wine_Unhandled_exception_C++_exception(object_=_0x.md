---
title: "wine: Unhandled exception: C++ exception(object = 0x033db7dc, type = 0x10124cc8) in 3"
date: 2014-11-25
forum: Wine
---

### Post by marchello_lippi2 on 2014-11-25
Hi all, 

I tried to install checkpoint vpn client for windows under wine, it thrown exception. 
Somebody help? 


```

Unhandled exception: C++ exception(object = 0x033db7dc, type = 0x10124cc8) in 32-bit code (0x7b83b31e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b83b31e ESP:033dafe4 EBP:033db058 EFLAGS:00200283(   - --  I S - - -C)
 EAX:7b826da1 EBX:7b8ba000 ECX:10124cc8 EDX:033db010
 ESI:e06d7363 EDI:033db0a0
Stack dump:
0x033dafe4:  033db094 0000000c 1005948f e06d7363
0x033daff4:  00000001 00000000 7b83b31e 00000003
0x033db004:  19930520 033db7dc 10124cc8 033db034
0x033db014:  033db034 033daff0 033daff0 033db044
0x033db024:  033db044 00000000 033db034 027b6470
0x033db034:  00000000 033db044 027b6470 033dafe4
Backtrace:
=>0 0x7b83b31e in kernel32 (+0x2b31e) (0x033db058)
  1 0x100926f2 in msi9c81.tmp (+0x926f1) (0x033db0a0)
  2 0x1007459d in msi9c81.tmp (+0x7459c) (0x033dbb5c)
  3 0x100768d1 in msi9c81.tmp (+0x768d0) (0x033dbb70)
  4 0x10075e23 in msi9c81.tmp (+0x75e22) (0x033dbcbc)
  5 0x10002278 in msi9c81.tmp (+0x2277) (0x033dc20c)
  6 0x10021ea8 in msi9c81.tmp (+0x21ea7) (0x033de70c)
  7 0x7eb1a7db CUSTOMPROC_wrapper+0xa() in msi (0x033de718)
  8 0x7eb1c750 in msi (+0x2c74f) (0x033de9a8)
  9 0x7eb1c9a7 in msi (+0x2c9a6) (0x033de9d8)
  10 0x7bc80840 call_thread_func_wrapper+0xb() in ntdll (0x033de9e8)
  11 0x7bc83a0d call_thread_func+0x7c() in ntdll (0x033deab8)
  12 0x7bc8081e RtlRaiseException+0x21() in ntdll (0x033dead8)
  13 0x7bc8a8d9 in ntdll (+0x7a8d8) (0x033df358)
  14 0xb7561f70 start_thread+0xcf() in libpthread.so.0 (0x033df428)
  15 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  16 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  17 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  18 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  19 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  20 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  21 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  22 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  23 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  24 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  25 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  26 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  27 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  28 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  29 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  30 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  31 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  32 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  33 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  34 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  35 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  36 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  37 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  38 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  39 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  40 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  41 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  42 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  43 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  44 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  45 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  46 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  47 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  48 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  49 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  50 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  51 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  52 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  53 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  54 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  55 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  56 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  57 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  58 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  59 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  60 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  61 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  62 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  63 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  64 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  65 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  66 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  67 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  68 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  69 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  70 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  71 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  72 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  73 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  74 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  75 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  76 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  77 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  78 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  79 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  80 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  81 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  82 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  83 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  84 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  85 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  86 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  87 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  88 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  89 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  90 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  91 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  92 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  93 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  94 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  95 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  96 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  97 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  98 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  99 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  100 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  101 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  102 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  103 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  104 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  105 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  106 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  107 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  108 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  109 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  110 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  111 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  112 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  113 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  114 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  115 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  116 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  117 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  118 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  119 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  120 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  121 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  122 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  123 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  124 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  125 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  126 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  127 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  128 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  129 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  130 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  131 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  132 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  133 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  134 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  135 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  136 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  137 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  138 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  139 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  140 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  141 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  142 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  143 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  144 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  145 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  146 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  147 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  148 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  149 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  150 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  151 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  152 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  153 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  154 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  155 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  156 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  157 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  158 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  159 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  160 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  161 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  162 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  163 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  164 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  165 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  166 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  167 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  168 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  169 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  170 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  171 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  172 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  173 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  174 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  175 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  176 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  177 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  178 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  179 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  180 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  181 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  182 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  183 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  184 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  185 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  186 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  187 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  188 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  189 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  190 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  191 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  192 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  193 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  194 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  195 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  196 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  197 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  198 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  199 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
  200 0xb74914ce __clone+0x5d() in libc.so.6 (0x00000000)
0x7b83b31e: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (88 modules)
PE    10000000-10153000    Export          msi9c81.tmp
ELF    7b800000-7ba60000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba60000    \               kernel32
ELF    7bc00000-7bce6000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bce6000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d796000-7d7b4000    Deferred        fusion<elf>
  \-PE    7d7a0000-7d7b4000    \               fusion
ELF    7d7b4000-7d81c000    Deferred        dbghelp<elf>
  \-PE    7d7c0000-7d81c000    \               dbghelp
ELF    7d81c000-7d853000    Deferred        mscoree<elf>
  \-PE    7d820000-7d853000    \               mscoree
ELF    7d853000-7d897000    Deferred        usp10<elf>
  \-PE    7d860000-7d897000    \               usp10
ELF    7d957000-7d9b2000    Deferred        libjpeg.so.8
ELF    7d9be000-7d9d2000    Deferred        psapi<elf>
  \-PE    7d9c0000-7d9d2000    \               psapi
ELF    7d9d2000-7da91000    Deferred        windowscodecs<elf>
  \-PE    7d9e0000-7da91000    \               windowscodecs
ELF    7db1b000-7db52000    Deferred        uxtheme<elf>
  \-PE    7db20000-7db52000    \               uxtheme
ELF    7db52000-7db58000    Deferred        libxfixes.so.3
ELF    7db58000-7db63000    Deferred        libxcursor.so.1
ELF    7db63000-7db74000    Deferred        libxi.so.6
ELF    7db74000-7db78000    Deferred        libxcomposite.so.1
ELF    7db78000-7db83000    Deferred        libxrandr.so.2
ELF    7db83000-7db8e000    Deferred        libxrender.so.1
ELF    7db8e000-7db94000    Deferred        libxxf86vm.so.1
ELF    7db94000-7db98000    Deferred        libxinerama.so.1
ELF    7db98000-7db9f000    Deferred        libxdmcp.so.6
ELF    7db9f000-7dba3000    Deferred        libxau.so.6
ELF    7dba3000-7dbc5000    Deferred        libxcb.so.1
ELF    7dbc5000-7dcf9000    Deferred        libx11.so.6
ELF    7dcf9000-7dd0c000    Deferred        libxext.so.6
ELF    7dd10000-7dd2a000    Deferred        sxs<elf>
  \-PE    7dd20000-7dd2a000    \               sxs
ELF    7dd2c000-7ddc0000    Deferred        winex11<elf>
  \-PE    7dd40000-7ddc0000    \               winex11
ELF    7ddc0000-7dde5000    Deferred        imm32<elf>
  \-PE    7ddd0000-7dde5000    \               imm32
ELF    7de58000-7de81000    Deferred        libexpat.so.1
ELF    7de81000-7debc000    Deferred        libfontconfig.so.1
ELF    7debc000-7dee4000    Deferred        libpng12.so.0
ELF    7dee4000-7df84000    Deferred        libfreetype.so.6
ELF    7df84000-7dfa5000    Deferred        cabinet<elf>
  \-PE    7df90000-7dfa5000    \               cabinet
ELF    7dfa5000-7e0ae000    Deferred        comctl32<elf>
  \-PE    7dfb0000-7e0ae000    \               comctl32
ELF    7e0ae000-7e0d6000    Deferred        mpr<elf>
  \-PE    7e0b0000-7e0d6000    \               mpr
ELF    7e0d6000-7e0f0000    Deferred        libz.so.1
ELF    7e110000-7e18d000    Deferred        wininet<elf>
  \-PE    7e120000-7e18d000    \               wininet
ELF    7e18d000-7e207000    Deferred        shlwapi<elf>
  \-PE    7e1a0000-7e207000    \               shlwapi
ELF    7e207000-7e43d000    Deferred        shell32<elf>
  \-PE    7e210000-7e43d000    \               shell32
ELF    7e43d000-7e586000    Deferred        oleaut32<elf>
  \-PE    7e450000-7e586000    \               oleaut32
ELF    7e586000-7e609000    Deferred        rpcrt4<elf>
  \-PE    7e590000-7e609000    \               rpcrt4
ELF    7e609000-7e728000    Deferred        gdi32<elf>
  \-PE    7e620000-7e728000    \               gdi32
ELF    7e728000-7e884000    Deferred        user32<elf>
  \-PE    7e740000-7e884000    \               user32
ELF    7e884000-7e8f7000    Deferred        advapi32<elf>
  \-PE    7e890000-7e8f7000    \               advapi32
ELF    7e8f7000-7ea39000    Deferred        ole32<elf>
  \-PE    7e910000-7ea39000    \               ole32
ELF    7ea39000-7eadc000    Deferred        urlmon<elf>
  \-PE    7ea40000-7eadc000    \               urlmon
ELF    7eadc000-7ebd9000    Dwarf           msi<elf>
  \-PE    7eaf0000-7ebd9000    \               msi
ELF    7ebd9000-7ebfd000    Deferred        msiexec<elf>
  \-PE    7ebe0000-7ebfd000    \               msiexec
ELF    7ebfd000-7ec0a000    Deferred        libnss_files.so.2
ELF    7ec0a000-7ec16000    Deferred        libnss_nis.so.2
ELF    7ec16000-7ec2f000    Deferred        libnsl.so.1
ELF    7ef9a000-7efe0000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    b73a5000-b7555000    Dwarf           libc.so.6
ELF    b7555000-b755a000    Deferred        libdl.so.2
ELF    b755b000-b7577000    Dwarf           libpthread.so.0
ELF    b7577000-b7580000    Deferred        libnss_compat.so.2
ELF    b7597000-b774d000    Dwarf           libwine.so.1
ELF    b774f000-b7771000    Deferred        ld-linux.so.2
ELF    b7771000-b7772000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001c    0
    0000001b    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001f    0
    00000018    0
    00000017    0
    00000013    0
00000019 plugplay.exe
    0000001e    0
    0000001d    0
    0000001a    0
00000020 explorer.exe
    00000021    0
00000025 (D) C:\windows\system32\msiexec.exe
    00000027    0 <==
    00000026    0
System information:
    Wine build: wine-1.7.31
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-40-generic



```

---

