---
title: "Ubuntu 14 and SPSS 20"
date: 2014-12-02
forum: Wine
---

### Post by Antonio_Martin on 2014-12-02
Hello to everyone!

I've installed the statistical package SPSS 20 on Ubuntu 14.04 LTS through Wine 1.6. Whenever trying to open it, Wine gives me this message:

---
Unhandled exception: C++ exception(object = 0x003ddff0, type = 0x140015118) in 64-bit code (0x000000007b847e21).
Register dump:
 rip:000000007b847e21 rsp:00000000003dddc0 rbp:00007fffff7e57d0 eflags:00000206 (   - --  I   - -P- )
 rax:00000000003dde00 rbx:00000000003ddde0 rcx:00000000003ddde0 rdx:0000000000000018
 rsi:00000000003ddf60 rdi:00000000003dde00  r8:0000000000000003  r9:00000000003ddf60 r10:0000000000000002
 r11:0000000000000202 r12:0000000000000000 r13:0000000000000000 r14:0000000078e7d7c8 r15:00000000003df700
Stack dump:
0x00000000003dddc0:  00000000003ddde0 0000000000000000
0x00000000003dddd0:  0000000000000000 0000000000000000
0x00000000003ddde0:  00000001e06d7363 0000000000000000
0x00000000003dddf0:  000000007b847e21 0000000000000003
0x00000000003dde00:  0000000019930520 00000000003ddff0
0x00000000003dde10:  0000000140015118 0000000000000000
0x00000000003dde20:  0000000000000000 0000000000000000
0x00000000003dde30:  0000000000000000 0000000000000000
0x00000000003dde40:  0000000000000000 0000000000000000
0x00000000003dde50:  0000000000000000 00ff0000000000ff
0x00000000003dde60:  0000000000000000 0000000000000000
0x00000000003dde70:  0000000000000000 0000000000000000
Backtrace:
=>0 0x000000007b847e21 in kernel32 (+0x27e21) (0x00007fffff7e57d0)
  1 0x00007f3167936561 _CxxThrowException+0x30() in msvcrt (0x00007fffff7e57d0)
  2 0x0000000140001763 in stats (+0x1762) (0x00007fffff7e57d0)
  3 0x00000001400015a9 in stats (+0x15a8) (0x00007fffff7e57d0)
  4 0x00000001400026e3 in stats (+0x26e2) (0x00007fffff7e57d0)
  5 0x00000001400017d4 in stats (+0x17d3) (0x00007fffff7e57d0)
  6 0x0000000140005bd0 in stats (+0x5bcf) (0x00007fffff7e57d0)
  7 0x00000001400082cc in stats (+0x82cb) (0x00007fffff7e57d0)
  8 0x0000000078e7d8c9 in mfc90u (+0x6d8c8) (0x00007fffff7e57d0)
  9 0x00007f31694260be call_thread_func+0x6d() in ntdll (0x00007fffff7e57d0)
  10 0x00007f316941f6ea RtlRaiseException+0x7d() in ntdll (0x00007fffff7e57d0)
  11 0x00007f316942e599 in ntdll (+0x7e598) (0x00007fffff7e57d0)
  12 0x00007f3169c63182 start_thread+0xc1() in libpthread.so.0 (0x0000000000000000)
  13 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  14 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  15 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  16 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  17 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  18 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  19 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  20 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  21 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  22 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  23 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  24 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  25 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  26 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  27 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  28 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  29 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  30 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  31 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  32 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  33 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  34 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  35 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  36 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  37 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  38 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  39 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  40 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  41 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  42 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  43 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  44 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  45 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  46 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  47 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  48 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  49 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  50 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  51 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  52 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  53 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  54 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  55 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  56 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  57 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  58 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  59 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  60 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  61 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  62 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  63 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  64 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  65 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  66 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  67 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  68 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  69 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  70 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  71 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  72 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  73 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  74 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  75 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  76 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  77 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  78 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  79 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  80 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  81 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  82 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  83 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  84 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  85 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  86 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  87 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  88 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  89 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  90 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  91 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  92 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  93 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  94 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  95 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  96 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  97 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  98 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  99 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  100 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  101 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  102 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  103 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  104 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  105 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  106 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  107 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  108 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  109 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  110 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  111 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  112 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  113 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  114 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  115 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  116 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  117 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  118 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  119 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  120 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  121 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  122 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  123 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  124 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  125 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  126 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  127 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  128 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  129 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  130 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  131 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  132 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  133 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  134 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  135 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  136 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  137 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  138 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  139 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  140 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  141 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  142 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  143 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  144 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  145 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  146 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  147 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  148 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  149 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  150 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  151 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  152 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  153 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  154 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  155 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  156 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  157 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  158 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  159 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  160 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  161 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  162 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  163 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  164 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  165 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  166 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  167 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  168 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  169 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  170 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  171 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  172 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  173 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  174 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  175 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  176 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  177 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  178 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  179 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  180 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  181 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  182 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  183 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  184 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  185 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  186 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  187 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  188 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  189 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  190 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  191 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  192 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  193 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  194 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  195 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  196 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  197 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  198 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  199 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
  200 0x00007f316978afbd __clone+0x6c() in libc.so.6 (0x0000000000000000)
0x000000007b847e21:     
Modules:
Module    Address                    Debug info    Name (76 modules)
PE            5d360000-        5d36d000    Deferred        mfc90enu
PE            78e10000-        792f9000    Export          mfc90u
ELF            7b800000-        7bc6f000    Dwarf           kernel32<elf>
  \-PE            7b820000-        7bc6f000    \               kernel32
ELF            7be00000-        7c103000    Deferred        <wine-loader>
PE           140000000-       140023000    Export          stats
ELF        7f31620d8000-    7f31622ff000    Deferred        imm32<elf>
  \-PE        7f31620e0000-    7f31622ff000    \               imm32
ELF        7f3162389000-    7f316259f000    Deferred        dwmapi<elf>
  \-PE        7f3162390000-    7f316259f000    \               dwmapi
ELF        7f316259f000-    7f31627d8000    Deferred        uxtheme<elf>
  \-PE        7f31625b0000-    7f31627d8000    \               uxtheme
ELF        7f31627d8000-    7f31629de000    Deferred        libxfixes.so.3
ELF        7f31629de000-    7f3162be8000    Deferred        libxcursor.so.1
ELF        7f3162be8000-    7f3162df8000    Deferred        libxi.so.6
ELF        7f3162df8000-    7f3162ffb000    Deferred        libxcomposite.so.1
ELF        7f3162ffb000-    7f3163205000    Deferred        libxrandr.so.2
ELF        7f3163205000-    7f316340f000    Deferred        libxrender.so.1
ELF        7f316340f000-    7f3163615000    Deferred        libxxf86vm.so.1
ELF        7f3163615000-    7f3163818000    Deferred        libxinerama.so.1
ELF        7f3163818000-    7f3163a1e000    Deferred        libxdmcp.so.6
ELF        7f3163a1e000-    7f3163c22000    Deferred        libxau.so.6
ELF        7f3163c22000-    7f3163e41000    Deferred        libxcb.so.1
ELF        7f3163e41000-    7f3164176000    Deferred        libx11.so.6
ELF        7f3164176000-    7f3164388000    Deferred        libxext.so.6
ELF        7f31643a6000-    7f3164640000    Deferred        winex11<elf>
  \-PE        7f31643c0000-    7f3164640000    \               winex11
ELF        7f31646d3000-    7f31648fd000    Deferred        libexpat.so.1
ELF        7f31648fd000-    7f3164b39000    Deferred        libfontconfig.so.1
ELF        7f3164b39000-    7f3164d5f000    Deferred        libpng12.so.0
ELF        7f3164d5f000-    7f3164f78000    Deferred        libz.so.1
ELF        7f3164f78000-    7f316521b000    Deferred        libfreetype.so.6
ELF        7f3165239000-    7f31654ca000    Deferred        rpcrt4<elf>
  \-PE        7f3165250000-    7f31654ca000    \               rpcrt4
ELF        7f31654ca000-    7f3165843000    Deferred        ole32<elf>
  \-PE        7f31654f0000-    7f3165843000    \               ole32
ELF        7f3165843000-    7f3165bb9000    Deferred        oleaut32<elf>
  \-PE        7f3165870000-    7f3165bb9000    \               oleaut32
ELF        7f3165bb9000-    7f3166015000    Deferred        shell32<elf>
  \-PE        7f3165bd0000-    7f3166015000    \               shell32
ELF        7f3166015000-    7f3166229000    Deferred        msimg32<elf>
  \-PE        7f3166020000-    7f3166229000    \               msimg32
ELF        7f3166229000-    7f3166529000    Deferred        comctl32<elf>
  \-PE        7f3166230000-    7f3166529000    \               comctl32
ELF        7f3166529000-    7f31667b6000    Deferred        shlwapi<elf>
  \-PE        7f3166540000-    7f31667b6000    \               shlwapi
ELF        7f31667b6000-    7f31669cf000    Deferred        version<elf>
  \-PE        7f31667c0000-    7f31669cf000    \               version
ELF        7f31669cf000-    7f3166c52000    Deferred        advapi32<elf>
  \-PE        7f31669e0000-    7f3166c52000    \               advapi32
ELF        7f3166c52000-    7f3166fb1000    Deferred        gdi32<elf>
  \-PE        7f3166c70000-    7f3166fb1000    \               gdi32
ELF        7f3166fb1000-    7f316734f000    Deferred        user32<elf>
  \-PE        7f3166fd0000-    7f316734f000    \               user32
ELF        7f316734f000-    7f31676c4000    Deferred        msvcp90<elf>
  \-PE        7f3167390000-    7f31676c4000    \               msvcp90
ELF        7f31676c4000-    7f3167902000    Deferred        msvcr100<elf>
  \-PE        7f31676d0000-    7f3167902000    \               msvcr100
ELF        7f3167902000-    7f3167bbf000    Dwarf           msvcrt<elf>
  \-PE        7f3167920000-    7f3167bbf000    \               msvcrt
ELF        7f3167bbf000-    7f3167df0000    Deferred        msvcr90<elf>
  \-PE        7f3167bd0000-    7f3167df0000    \               msvcr90
ELF        7f3167df0000-    7f3167ffc000    Deferred        libnss_files.so.2
ELF        7f3167ffc000-    7f3168208000    Deferred        libnss_nis.so.2
ELF        7f3168208000-    7f3168422000    Deferred        libnsl.so.1
ELF        7f3168422000-    7f316862c000    Deferred        libnss_compat.so.2
ELF        7f3168e7f000-    7f3169095000    Deferred        libgcc_s.so.1
ELF        7f3169095000-    7f316939b000    Deferred        libm.so.6
ELF        7f316939b000-    7f316968d000    Dwarf           ntdll<elf>
  \-PE        7f31693b0000-    7f316968d000    \               ntdll
ELF        7f3169690000-    7f3169a56000    Dwarf           libc.so.6
ELF        7f3169a56000-    7f3169c5a000    Deferred        libdl.so.2
ELF        7f3169c5b000-    7f3169e79000    Dwarf           libpthread.so.0
ELF        7f3169e97000-    7f316a23a000    Dwarf           libwine.so.1
ELF        7f316a23c000-    7f316a461000    Deferred        ld-linux-x86-64.so.2
ELF        7fff559fe000-    7fff559ff000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    0000001a    0
    00000017    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    00000020    0
    0000001c    0
00000022 explorer.exe
    00000026    0
    00000023    0
00000027 law.exe
    00000028    0
00000029 javaw.exe
    00000042    0
    00000039    0
    00000038    0
    00000036    0
    00000035    1
    00000033    2
    00000032    2
    00000030    0
    0000002f    0
    0000002e    0
    0000002d   15
    0000002c   15
    0000002b    0
    0000002a    0
00000040 echoid.exe
    00000041    0
00000016 (D) C:\Program Files\IBM\SPSS\Statistics\20\stats.exe
    00000018    0 <==
    00000019    0
System information:
    Wine build: wine-1.6.2
    Platform: x86_64
    Host system: Linux
    Host version: 3.13.0-40-generic
---

What should I do?

---

### Post by SeijiSensei on 2014-12-02
Depends on what you need from SPSS.  A lot of the basics are available in PSPP, a GPL clone that's available in the repositories.
```
sudo apt-get install pspp
```
Manual is here: [http://www.gnu.org/software/pspp/manual/html_node/index.html](http://www.gnu.org/software/pspp/manual/html_node/index.html)

---

### Post by Mark Phelps on 2014-12-04
According to the WineHQ webpage for SPSS, the version you're trying to install is rated Garbage (meaning, it's not going to work no matter what you do): [https://appdb.winehq.org/objectManager.php?sClass=application&iId=1028]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=1028")

---

### Post by Antonio_Martin on 2014-12-05
SeijiSensei, I'll try the program you've introduced. Thank you.

Mark Phelps, you're right... I supose I'll have to use the 19th version... T_T Thank you too.

---

