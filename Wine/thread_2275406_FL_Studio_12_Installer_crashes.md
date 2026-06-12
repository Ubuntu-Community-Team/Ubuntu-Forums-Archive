---
title: "FL Studio 12 Installer crashes"
date: 2015-04-25
forum: Wine
---

### Post by SnizzyFuzz on 2015-04-25
The FL Studio 12 install .exe works fine up until it crashes before it would typically bring up the ASIO install window. The crash details:
```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x04b3f136).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:04b3f136 ESP:04e2e970 EBP:04e2e98c EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7bcbf000 ECX:8ee5feda EDX:00000000
 ESI:024b1048 EDI:7ffc8fb8
Stack dump:
0x04e2e970:  00002710 8ee5fe3a 0249bd18 0249bcd0
0x04e2e980:  04e2e9bc 04c346a8 00000000 04e2e994
0x04e2e990:  04b483d2 04e2e9cc 04c138ba 024b1048
0x04e2e9a0:  8ee5fe7a 7ffc8fb8 0249bd18 7bcbf000
0x04e2e9b0:  c0000005 04e2e9a0 04e2e4e0 04e2ea00
0x04e2e9c0:  04c189f0 8ece9c16 00000000 04e2e9d8
Backtrace:
=>0 0x04b3f136 in fldownload (+0x5f136) (0x04e2e98c)
  1 0x04b483d2 in fldownload (+0x683d1) (0x04e2e994)
  2 0x04c138ba in fldownload (+0x1338b9) (0x04e2e9cc)
  3 0x04c139e2 in fldownload (+0x1339e1) (0x04e2e9d8)
  4 0x7bc799b0 call_thread_func_wrapper+0xb() in ntdll (0x04e2e9e8)
  5 0x7bc7c93d call_thread_func+0x7c() in ntdll (0x04e2eab8)
  6 0x7bc7998e RtlRaiseException+0x21() in ntdll (0x04e2ead8)
  7 0x7bc82dce in ntdll (+0x72dcd) (0x04e2f358)
  8 0xf7566f70 start_thread+0xcf() in libpthread.so.0 (0x04e2f428)
  9 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  10 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  11 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  12 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  13 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  14 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  15 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  16 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  17 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  18 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  19 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  20 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  21 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  22 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  23 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  24 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  25 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  26 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  27 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  28 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  29 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  30 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  31 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  32 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  33 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  34 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  35 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  36 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  37 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  38 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  39 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  40 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  41 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  42 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  43 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  44 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  45 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  46 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  47 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  48 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  49 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  50 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  51 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  52 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  53 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  54 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  55 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  56 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  57 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  58 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  59 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  60 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  61 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  62 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  63 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  64 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  65 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  66 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  67 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  68 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  69 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  70 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  71 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  72 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  73 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  74 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  75 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  76 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  77 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  78 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  79 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  80 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  81 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  82 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  83 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  84 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  85 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  86 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  87 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  88 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  89 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  90 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  91 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  92 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  93 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  94 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  95 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  96 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  97 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  98 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  99 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  100 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  101 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  102 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  103 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  104 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  105 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  106 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  107 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  108 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  109 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  110 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  111 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  112 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  113 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  114 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  115 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  116 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  117 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  118 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  119 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  120 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  121 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  122 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  123 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  124 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  125 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  126 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  127 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  128 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  129 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  130 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  131 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  132 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  133 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  134 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  135 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  136 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  137 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  138 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  139 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  140 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  141 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  142 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  143 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  144 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  145 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  146 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  147 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  148 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  149 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  150 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  151 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  152 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  153 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  154 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  155 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  156 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  157 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  158 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  159 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  160 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  161 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  162 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  163 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  164 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  165 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  166 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  167 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  168 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  169 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  170 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  171 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  172 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  173 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  174 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  175 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  176 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  177 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  178 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  179 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  180 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  181 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  182 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  183 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  184 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  185 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  186 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  187 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  188 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  189 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  190 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  191 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  192 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  193 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  194 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  195 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  196 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  197 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  198 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  199 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
  200 0xf7493bee __clone+0x5d() in libc.so.6 (0x00000000)
0x04b3f136: movl    0x0(%eax,%edx,4),%eax
Modules:
Module    Address            Debug info    Name (140 modules)
PE      3c0000-  3de000    Deferred        usermgr
PE      3e0000-  3e6000    Deferred        system
PE      400000-  444000    Deferred        flstudio_12.0.1
PE     1010000- 10e2000    Deferred        ocsetuphlp
PE     1210000- 1219000    Deferred        installoptions
PE     1220000- 1228000    Deferred        nsdialogs
PE     12b0000- 133e000    Deferred        quickfontcache
PE     26e0000- 2818000    Deferred        ilextra
PE     2a70000- 442b000    Deferred        dsp_ipp
PE     4540000- 45b7000    Deferred        freetype
PE     4ae0000- 4d24000    Export          fldownload
PE    10000000-10007000    Deferred        uac
ELF    7ac00000-7ac5f000    Deferred        riched20<elf>
  \-PE    7ac10000-7ac5f000    \               riched20
ELF    7b800000-7ba5b000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7bc00000-7bcdb000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcdb000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cec8000-7cedc000    Deferred        olepro32<elf>
  \-PE    7ced0000-7cedc000    \               olepro32
ELF    7cee0000-7cef7000    Deferred        powrprof<elf>
  \-PE    7cef0000-7cef7000    \               powrprof
ELF    7cef8000-7cf0d000    Deferred        avrt<elf>
  \-PE    7cf00000-7cf0d000    \               avrt
ELF    7cf10000-7cf26000    Deferred        dwmapi<elf>
  \-PE    7cf20000-7cf26000    \               dwmapi
ELF    7cf28000-7cf53000    Deferred        msacm32<elf>
  \-PE    7cf30000-7cf53000    \               msacm32
ELF    7cf58000-7d012000    Deferred        winmm<elf>
  \-PE    7cf60000-7d012000    \               winmm
ELF    7d018000-7d0c0000    Deferred        msvcrt<elf>
  \-PE    7d030000-7d0c0000    \               msvcrt
ELF    7d0c0000-7d101000    Deferred        usp10<elf>
  \-PE    7d0d0000-7d101000    \               usp10
ELF    7d218000-7d263000    Deferred        libdbus-1.so.3
ELF    7d268000-7d298000    Deferred        libk5crypto.so.3
ELF    7d298000-7d356000    Deferred        libkrb5.so.3
ELF    7d358000-7d39d000    Deferred        libgssapi_krb5.so.2
ELF    7d3a0000-7d40d000    Deferred        libcups.so.2
ELF    7d410000-7d4fb000    Deferred        comdlg32<elf>
  \-PE    7d420000-7d4fb000    \               comdlg32
ELF    7d608000-7d611000    Deferred        librt.so.1
ELF    7d618000-7d624000    Deferred        libkrb5support.so.0
ELF    7d628000-7d668000    Deferred        winspool<elf>
  \-PE    7d630000-7d668000    \               winspool
ELF    7d668000-7d685000    Deferred        libgcc_s.so.1
ELF    7d690000-7d6a2000    Deferred        libavahi-client.so.3
ELF    7d6a8000-7d6c0000    Deferred        libresolv.so.2
ELF    7d6c8000-7d6cc000    Deferred        libkeyutils.so.1
ELF    7d6d0000-7d6de000    Deferred        libavahi-common.so.3
ELF    7d700000-7d78a000    Deferred        gdiplus<elf>
  \-PE    7d710000-7d78a000    \               gdiplus
ELF    7d790000-7d832000    Deferred        urlmon<elf>
  \-PE    7d7a0000-7d832000    \               urlmon
ELF    7d838000-7d96e000    Deferred        oleaut32<elf>
  \-PE    7d850000-7d96e000    \               oleaut32
ELF    7d9d0000-7d9d5000    Deferred        libcom_err.so.2
ELF    7d9d8000-7da00000    Deferred        mpr<elf>
  \-PE    7d9e0000-7da00000    \               mpr
ELF    7db08000-7db0f000    Deferred        libnss_dns.so.2
ELF    7db10000-7db8c000    Deferred        wininet<elf>
  \-PE    7db20000-7db8c000    \               wininet
ELF    7db90000-7dba4000    Deferred        msimg32<elf>
  \-PE    7dba0000-7dba4000    \               msimg32
ELF    7dba8000-7dbbc000    Deferred        psapi<elf>
  \-PE    7dbb0000-7dbbc000    \               psapi
ELF    7dbc0000-7dbc7000    Deferred        libffi.so.6
ELF    7dbc8000-7dc04000    Deferred        libp11-kit.so.0
ELF    7dc08000-7dc1c000    Deferred        libtasn1.so.6
ELF    7dc20000-7dca6000    Deferred        libgcrypt.so.11
ELF    7dca8000-7dd6e000    Deferred        libgnutls.so.26
ELF    7dd78000-7dd90000    Deferred        userenv<elf>
  \-PE    7dd80000-7dd90000    \               userenv
ELF    7dd90000-7ddc6000    Deferred        ws2_32<elf>
  \-PE    7dda0000-7ddc6000    \               ws2_32
ELF    7de28000-7de2d000    Deferred        libgpg-error.so.0
ELF    7de30000-7de56000    Deferred        iphlpapi<elf>
  \-PE    7de40000-7de56000    \               iphlpapi
ELF    7de58000-7de85000    Deferred        netapi32<elf>
  \-PE    7de60000-7de85000    \               netapi32
ELF    7de88000-7debb000    Deferred        secur32<elf>
  \-PE    7de90000-7debb000    \               secur32
ELF    7dec0000-7dee5000    Deferred        imm32<elf>
  \-PE    7ded0000-7dee5000    \               imm32
ELF    7df38000-7df6f000    Deferred        uxtheme<elf>
  \-PE    7df40000-7df6f000    \               uxtheme
ELF    7df70000-7df7b000    Deferred        libxcursor.so.1
ELF    7df80000-7df94000    Deferred        shfolder<elf>
  \-PE    7df90000-7df94000    \               shfolder
ELF    7dfa0000-7dfab000    Deferred        libxrandr.so.2
ELF    7dfb0000-7dfb6000    Deferred        libxfixes.so.3
ELF    7dfb8000-7dfc8000    Deferred        libxi.so.6
ELF    7dfc8000-7dfcc000    Deferred        libxcomposite.so.1
ELF    7dfd0000-7dfd7000    Deferred        libxdmcp.so.6
ELF    7dfd8000-7dfdc000    Deferred        libxau.so.6
ELF    7dfe0000-7e002000    Deferred        libxcb.so.1
ELF    7e008000-7e13c000    Deferred        libx11.so.6
ELF    7e140000-7e153000    Deferred        libxext.so.6
ELF    7e158000-7e163000    Deferred        libxrender.so.1
ELF    7e168000-7e16e000    Deferred        libxxf86vm.so.1
ELF    7e170000-7e174000    Deferred        libxinerama.so.1
ELF    7e178000-7e20a000    Deferred        winex11<elf>
  \-PE    7e180000-7e20a000    \               winex11
ELF    7e2d0000-7e2f9000    Deferred        libexpat.so.1
ELF    7e300000-7e33b000    Deferred        libfontconfig.so.1
ELF    7e360000-7e388000    Deferred        libpng12.so.0
ELF    7e388000-7e428000    Deferred        libfreetype.so.6
ELF    7e448000-7e46a000    Deferred        libtinfo.so.5
ELF    7e470000-7e495000    Deferred        libncurses.so.5
ELF    7e498000-7e4b2000    Deferred        libz.so.1
ELF    7e4b8000-7e539000    Deferred        rpcrt4<elf>
  \-PE    7e4c0000-7e539000    \               rpcrt4
ELF    7e540000-7e67c000    Deferred        ole32<elf>
  \-PE    7e560000-7e67c000    \               ole32
ELF    7e680000-7e787000    Deferred        comctl32<elf>
  \-PE    7e690000-7e787000    \               comctl32
ELF    7e788000-7e802000    Deferred        shlwapi<elf>
  \-PE    7e7a0000-7e802000    \               shlwapi
ELF    7e808000-7ea3b000    Deferred        shell32<elf>
  \-PE    7e820000-7ea3b000    \               shell32
ELF    7ea40000-7eab2000    Deferred        advapi32<elf>
  \-PE    7ea50000-7eab2000    \               advapi32
ELF    7eab8000-7ebd5000    Deferred        gdi32<elf>
  \-PE    7eac0000-7ebd5000    \               gdi32
ELF    7ebd8000-7ed32000    Deferred        user32<elf>
  \-PE    7ebf0000-7ed32000    \               user32
ELF    7ef38000-7ef45000    Deferred        libnss_files.so.2
ELF    7ef48000-7ef54000    Deferred        libnss_nis.so.2
ELF    7ef58000-7ef71000    Deferred        libnsl.so.1
ELF    7ef78000-7ef92000    Deferred        version<elf>
  \-PE    7ef80000-7ef92000    \               version
ELF    7ef98000-7efde000    Deferred        libm.so.6
ELF    7eff0000-7eff9000    Deferred        libnss_compat.so.2
ELF    f73a8000-f7556000    Dwarf           libc.so.6
ELF    f7558000-f755d000    Deferred        libdl.so.2
ELF    f7560000-f757c000    Dwarf           libpthread.so.0
ELF    f75a0000-f7755000    Dwarf           libwine.so.1
ELF    f7758000-f777a000    Deferred        ld-linux.so.2
ELF    f7781000-f7782000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\hoffy\desktop\flstudio_12.0.1.exe
    00000055    0 <==
    00000029    0
    00000024    0
    00000009    0
0000000e services.exe
    0000001e    0
    0000001d    0
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
00000025 rundll32.exe
    00000026    0
System information:
    Wine build: wine-1.6.2
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-49-lowlatency


```

I got FL12 to install fine earlier today. I had the same problem of it crashing before, and then one time it just inexplicably worked. I can't think of anything I might've done to fix it.

Loads of searching for answers hasn't worked out... I'd be super happy if someone knows what to do :D

---

