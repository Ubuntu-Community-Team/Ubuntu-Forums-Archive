---
title: "Problem with Wine"
date: 2014-09-15
forum: Wine
---

### Post by ibhollow1975 on 2014-09-15
I have a copy of MS office that I would like to use on Wine so I don't have to boot up my Win7 Drive. When I try to load the program I get the message posted below. Does anyone know what this means? I appreciate any help you can give me. Thanks. 

Unhandled exception: 0xc06d007f in 32-bit code (0x7b83aace).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b83aace ESP:0109e414 EBP:0109e488 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b82695d EBX:7b8b5000 ECX:00000000 EDX:c06d007f
 ESI:c06d007f EDI:7d7e0000
Stack dump:
0x0109e414:  0109e504 00000004 7bcc7be0 c06d007f
0x0109e424:  00000000 00000000 7b83aace 00000001
0x0109e434:  0109e4b8 0109e460 7bc4020b 0109e460
0x0109e444:  00000000 0109e498 7b85842d 00000000
0x0109e454:  7d7e0000 7b8268e5 7b85842d c000007a
0x0109e464:  0109e478 00000000 0109e474 0109e4ac
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x7b83aace in kernel32 (+0x2aace) (0x0109e488)
  1 0x00c2af8e in osetup (+0x4baf8d) (0x0109e4fc)
  2 0x00c5d017 in osetup (+0x4ed016) (0x0109e680)
  3 0x00b7476a in osetup (+0x404769) (0x0109e6c8)
  4 0x00b748b5 in osetup (+0x4048b4) (0x0109e718)
  5 0x00ba1be3 in osetup (+0x431be2) (0x0109e760)
  6 0x00ba0d71 in osetup (+0x430d70) (0x0109e9d0)
  7 0x00ba21e2 in osetup (+0x4321e1) (0x0109e9e8)
  8 0x7bc7c93d call_thread_func+0x7c() in ntdll (0x0109eab8)
  9 0x7bc7998e RtlRaiseException+0x21() in ntdll (0x0109ead8)
  10 0x7bc82dce in ntdll (+0x72dcd) (0x0109f358)
  11 0xf7507f70 start_thread+0xcf() in libpthread.so.0 (0x0109f428)
  12 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  13 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  14 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  15 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  16 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  17 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  18 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  19 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
 20 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  21 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  22 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  23 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  24 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  25 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  26 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  27 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  28 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  29 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  30 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  31 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  32 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  33 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  34 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  35 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  36 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  37 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  38 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  39 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  40 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  41 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  42 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  43 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  44 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  45 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  46 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  47 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  48 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  49 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  50 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  51 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  52 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
 53 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  54 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  55 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  56 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  57 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  58 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  59 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  60 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  61 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  62 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  63 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  64 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  65 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  66 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  67 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  68 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  69 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  70 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  71 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  72 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  73 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  74 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  75 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  76 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  77 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  78 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  79 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  80 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  81 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  82 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  83 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  84 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  85 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  86 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
87 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  88 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  89 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  90 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  91 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  92 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  93 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  94 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  95 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  96 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  97 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  98 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  99 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  100 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  101 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  102 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  103 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  104 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  105 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  106 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  107 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  108 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  109 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  110 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  111 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  112 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  113 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  114 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  115 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  116 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  117 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  118 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  119 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  120 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
 121 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  122 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  123 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  124 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  125 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  126 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  127 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  128 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  129 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  130 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  131 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  132 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  133 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  134 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  135 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  136 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  137 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  138 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  139 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  140 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  141 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  142 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  143 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  144 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  145 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  146 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  147 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  148 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  149 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  150 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  151 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  152 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  153 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
154 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  155 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  156 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  157 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  158 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  159 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  160 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  161 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  162 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  163 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  164 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  165 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  166 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  167 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  168 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  169 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  170 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  171 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  172 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  173 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  174 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  175 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  176 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  177 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  178 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  179 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  180 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  181 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  182 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  183 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  184 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  185 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  186 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  187 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
 188 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  189 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  190 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  191 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  192 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  193 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  194 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  195 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  196 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  197 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  198 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  199 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
  200 0xf74374ce __clone+0x5d() in libc.so.6 (0x00000000)
0x7b83aace: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (102 modules)
PE	  400000-  434000	Deferred        setup
PE	  770000-  e58000	Export          osetup
PE	  f70000-  f9f000	Deferred        osetupui
PE	10000000-100d3000	Deferred        setup
ELF	7b800000-7ba5b000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba5b000	\               kernel32
ELF	7bc00000-7bcdb000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcdb000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d58a000-7d699000	Deferred        opengl32<elf>
  \-PE	7d5b0000-7d699000	\               opengl32
ELF	7d699000-7d7d9000	Deferred        wined3d<elf>
  \-PE	7d6b0000-7d7d9000	\               wined3d
ELF	7d7d9000-7d800000	Deferred        dxgi<elf>
  \-PE	7d7e0000-7d800000	\               dxgi
ELF	7d91c000-7d940000	Deferred        dwrite<elf>
  \-PE	7d920000-7d940000	\               dwrite
ELF	7d940000-7d979000	Deferred        hhctrl<elf>
  \-PE	7d950000-7d979000	\               hhctrl
ELF	7d979000-7d999000	Deferred        cabinet<elf>
  \-PE	7d980000-7d999000	\               cabinet
ELF	7d999000-7d9c1000	Deferred        mpr<elf>
  \-PE	7d9a0000-7d9c1000	\               mpr
ELF	7d9c1000-7da3d000	Deferred        wininet<elf>
  \-PE	7d9d0000-7da3d000	\               wininet
ELF	7da3d000-7dadf000	Deferred        urlmon<elf>
  \-PE	7da50000-7dadf000	\               urlmon
ELF	7dadf000-7dbdb000	Deferred        msi<elf>
  \-PE	7daf0000-7dbdb000	\               msi
ELF	7dbdb000-7dbff000	Deferred        hlink<elf>
  \-PE	7dbe0000-7dbff000	\               hlink
ELF	7dbff000-7dc24000	Deferred        imm32<elf>
  \-PE	7dc10000-7dc24000	\               imm32
ELF	7dc24000-7dc46000	Deferred        oleacc<elf>
  \-PE	7dc30000-7dc46000	\               oleacc
ELF	7dc46000-7dc5c000	Deferred        hid<elf>
  \-PE	7dc50000-7dc5c000	\               hid
ELF	7dc5c000-7dc73000	Deferred        wer<elf>
  \-PE	7dc60000-7dc73000	\               wer
ELF	7dc73000-7dc8b000	Deferred        wtsapi32<elf>
  \-PE	7dc80000-7dc8b000	\               wtsapi32
ELF	7dc8b000-7dccd000	Deferred        rsaenh<elf>
  \-PE	7dc90000-7dccd000	\               rsaenh
ELF	7dccd000-7dd04000	Deferred        uxtheme<elf>
  \-PE	7dcd0000-7dd04000	\               uxtheme
ELF	7dd04000-7de0b000	Deferred        comctl32<elf>
  \-PE	7dd10000-7de0b000	\               comctl32
ELF	7de0b000-7de85000	Deferred        shlwapi<elf>
  \-PE	7de20000-7de85000	\               shlwapi
ELF	7de85000-7e0b8000	Deferred        shell32<elf>
  \-PE	7de90000-7e0b8000	\               shell32
ELF	7e0fe000-7e104000	Deferred        libxfixes.so.3
ELF	7e104000-7e10f000	Deferred        libxcursor.so.1
ELF	7e10f000-7e120000	Deferred        libxi.so.6
ELF	7e120000-7e124000	Deferred        libxcomposite.so.1
ELF	7e124000-7e12f000	Deferred        libxrandr.so.2
ELF	7e12f000-7e13a000	Deferred        libxrender.so.1
ELF	7e13a000-7e140000	Deferred        libxxf86vm.so.1
ELF	7e140000-7e144000	Deferred        libxinerama.so.1
ELF	7e144000-7e14b000	Deferred        libxdmcp.so.6
ELF	7e14b000-7e14f000	Deferred        libxau.so.6
ELF	7e14f000-7e171000	Deferred        libxcb.so.1
ELF	7e171000-7e2a5000	Deferred        libx11.so.6
ELF	7e2a5000-7e2b8000	Deferred        libxext.so.6
ELF	7e2bd000-7e2d7000	Deferred        imagehlp<elf>
  \-PE	7e2c0000-7e2d7000	\               imagehlp
ELF	7e2d9000-7e36b000	Deferred        winex11<elf>
  \-PE	7e2e0000-7e36b000	\               winex11
ELF	7e3ae000-7e3d7000	Deferred        libexpat.so.1
ELF	7e3d7000-7e412000	Deferred        libfontconfig.so.1
ELF	7e412000-7e43a000	Deferred        libpng12.so.0
ELF	7e43a000-7e454000	Deferred        libz.so.1
ELF	7e454000-7e4f4000	Deferred        libfreetype.so.6
ELF	7e515000-7e64b000	Deferred        oleaut32<elf>
  \-PE	7e530000-7e64b000	\               oleaut32
ELF	7e64b000-7e6cc000	Deferred        rpcrt4<elf>
  \-PE	7e660000-7e6cc000	\               rpcrt4
ELF	7e6cc000-7e808000	Deferred        ole32<elf>
  \-PE	7e6e0000-7e808000	\               ole32
ELF	7e808000-7e87a000	Deferred        advapi32<elf>
  \-PE	7e810000-7e87a000	\               advapi32
ELF	7e87a000-7e997000	Deferred        gdi32<elf>

  \-PE	7e890000-7e997000	\               gdi32
ELF	7e997000-7eaf1000	Deferred        user32<elf>
  \-PE	7e9b0000-7eaf1000	\               user32
ELF	7eaf1000-7ebc0000	Deferred        crypt32<elf>
  \-PE	7eb00000-7ebc0000	\               crypt32
ELF	7ebc0000-7ebf7000	Deferred        wintrust<elf>
  \-PE	7ebd0000-7ebf7000	\               wintrust
ELF	7ebf7000-7ec04000	Deferred        libnss_files.so.2
ELF	7ec04000-7ec10000	Deferred        libnss_nis.so.2
ELF	7ec10000-7ec29000	Deferred        libnsl.so.1
ELF	7ef99000-7efdf000	Deferred        libm.so.6
ELF	7efe6000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f734b000-f74fb000	Dwarf           libc.so.6
ELF	f74fb000-f7500000	Deferred        libdl.so.2
ELF	f7501000-f751d000	Dwarf           libpthread.so.0
ELF	f7534000-f753d000	Deferred        libnss_compat.so.2
ELF	f753e000-f76f3000	Dwarf           libwine.so.1
ELF	f76f5000-f7717000	Deferred        ld-linux.so.2
ELF	f7717000-f7718000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001e    0
	0000001d    0
	00000018    0
	00000016    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000019    0
	00000017    0


00000013    0
0000001a plugplay.exe
	00000020    0
	0000001f    0
	0000001b    0
00000021 explorer.exe
	00000023    0
	00000022    0
00000024 (D) Q:\setup.exe
	00000026    0 <==
	00000025    0
System information:
    Wine build: wine-1.6.2
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.13.0-32-generic

---

### Post by Toz on 2014-09-15
Which version of MS Office are you trying to install? 2013 doesn't currently work and 64-bit 2010 doesn't either.

[This page](https://appdb.winehq.org/objectManager.php?sClass=application&iId=31) has an overview of MS Office versions and their currrent statuses. Clicking on the correct version will get you to a page that usually has a HOW-TO section (if it works).

Please consider using [code tags]("http://ubuntuforums.org/misc.php?do=bbcode#code") in your outputs so that they are easier to read.

---

### Post by ibhollow1975 on 2014-09-16
Thanks for the reply! I am using the 2013 version. So that must be it.

---

