---
title: "error while installing steam"
date: 2013-12-29
forum: Wine
---

### Post by slayersmurf2 on 2013-12-29
Steam has crashed after I authenticate a new computer and hit the next button. Whenever I login and paste the code for Steam Guard authorization it  tells me it's authorizing but then it tells me steam has encountered an  error and must close. Here are the Program Error Details:
```

Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7bc57250).Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc57250 ESP:06e5b2ac EBP:06e5b384 EFLAGS:00210206(  R- --  I   - -P- )
 EAX:00000000 EBX:7bcc7000 ECX:00000000 EDX:00000010
 ESI:00000002 EDI:06e5b6c4
Stack dump:
0x06e5b2ac:  06e5b308 06e5b3ec 0000000c 001bb088
0x06e5b2bc:  00000002 001bb058 00000001 00000000
0x06e5b2cc:  001bb088 06e5b310 7bc484cd 00000000
0x06e5b2dc:  06e5b3e8 06e5b3f8 7bc33d00 0000010c
0x06e5b2ec:  ffffffff 06e5b310 7bc34964 00110064
0x06e5b2fc:  06e5b308 06e5b308 00000000 00000000
000c: sel=0067 base=00000000 limit=00000000 32-bit --x
Backtrace:
=>0 0x7bc57250 NtAdjustPrivilegesToken+0x1ed() in ntdll (0x06e5b384)
  1 0x7e8185f9 AdjustTokenPrivileges+0x8b() in advapi32 (0x06e5b3c4)
  2 0x3823574e in steamclient (+0x23574d) (0x06e5b410)
  3 0x38236284 in steamclient (+0x236283) (0x06e5b6e8)
  4 0x381e9739 in steamclient (+0x1e9738) (0x06e5b750)
  5 0x381eb712 in steamclient (+0x1eb711) (0x06e5b784)
  6 0x380ef0d9 in steamclient (+0xef0d8) (0x06e5b8ec)
  7 0x380efd3c in steamclient (+0xefd3b) (0x06e5cab0)
  8 0x3845e818 in steamclient (+0x45e817) (0x06e5cbc8)
  9 0x3845f140 in steamclient (+0x45f13f) (0x06e5cc18)
  10 0x380efba6 in steamclient (+0xefba5) (0x06e5dde0)
  11 0x3849ddc7 in steamclient (+0x49ddc6) (0x06e5e1f0)
  12 0x3849dfe4 in steamclient (+0x49dfe3) (0x06e5e204)
  13 0x384506d9 in steamclient (+0x4506d8) (0x06e5e428)
  14 0x3841cbf3 in steamclient (+0x41cbf2) (0x06e5e44c)
  15 0x3846249c in steamclient (+0x46249b) (0x06e5e458)
  16 0x38462123 in steamclient (+0x462122) (0x06e5e4e4)
  17 0x3819af12 in steamclient (+0x19af11) (0x06e5e554)
  18 0x3819b060 in steamclient (+0x19b05f) (0x06e5e568)
  19 0x3f00ca4f in tier0_s (+0xca4e) (0x06e5e598)
  20 0x3f00db0c in tier0_s (+0xdb0b) (0x06e5e5bc)
  21 0x3f011b70 in tier0_s (+0x11b6f) (0x06e5e9f8)
  22 0x7bc7edfc call_thread_func_wrapper+0xb() in ntdll (0x06e5ea08)
  23 0x7bc7ee4b call_thread_func+0x44() in ntdll (0x06e5eae8)
  24 0x7bc7edda in ntdll (+0x6edd9) (0x06e5eb08)
  25 0x7bc8674b in ntdll (+0x7674a) (0x06e5f368)
  26 0xf75e4d78 start_thread+0xd7() in libpthread.so.0 (0x06e5f468)
  27 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  28 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  29 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  30 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  31 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  32 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  33 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  34 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  35 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  36 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  37 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  38 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  39 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  40 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  41 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  42 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  43 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  44 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  45 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  46 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  47 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  48 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  49 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  50 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  51 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  52 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  53 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  54 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  55 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  56 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  57 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  58 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  59 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  60 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  61 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  62 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  63 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  64 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  65 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  66 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  67 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  68 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  69 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  70 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  71 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  72 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  73 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  74 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  75 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  76 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  77 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  78 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  79 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  80 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  81 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  82 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  83 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  84 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  85 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  86 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  87 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  88 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  89 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  90 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  91 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  92 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  93 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  94 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  95 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  96 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  97 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  98 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  99 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  100 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  101 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  102 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  103 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  104 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  105 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  106 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  107 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  108 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  109 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  110 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  111 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  112 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  113 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  114 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  115 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  116 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  117 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  118 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  119 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  120 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  121 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  122 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  123 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  124 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  125 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  126 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  127 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  128 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  129 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  130 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  131 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  132 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  133 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  134 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  135 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  136 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  137 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  138 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  139 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  140 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  141 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  142 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  143 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  144 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  145 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  146 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  147 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  148 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  149 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  150 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  151 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  152 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  153 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  154 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  155 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  156 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  157 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  158 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  159 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  160 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  161 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  162 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  163 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  164 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  165 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  166 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  167 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  168 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  169 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  170 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  171 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  172 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  173 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  174 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  175 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  176 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  177 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  178 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  179 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  180 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  181 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  182 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  183 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  184 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  185 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  186 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  187 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  188 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  189 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  190 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  191 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  192 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  193 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  194 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  195 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  196 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  197 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  198 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  199 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
  200 0xf751b01e __clone+0x5d() in libc.so.6 (0x00000000)
0x7bc57250 NtAdjustPrivilegesToken+0x1ed in ntdll: movl        %edx,0x0(%eax)
Modules:
Module        Address                        Debug info        Name (176 modules)
PE          400000-  63d000        Deferred        steam
PE         10d0000- 1187000        Deferred        sdl2
PE         43d0000- 44ea000        Deferred        chromehtml
PE         44f0000- 58cb000        Deferred        libcef
PE         6e60000- 716d000        Deferred        steamservice
PE        10000000-100b4000        Deferred        crashhandler
PE        30000000-302c1000        Deferred        steam
PE        38000000-38881000        Export          steamclient
PE        3a000000-3aaf4000        Deferred        steamui
PE        3f000000-3f0ac000        Export          tier0_s
PE        3f200000-3f2b1000        Deferred        vgui2_s
PE        3f600000-3f64b000        Deferred        vstdlib_s
PE        3f800000-3f82e000        Deferred        filesystem_stdio
PE        4ad00000-4b67f000        Deferred        icudt
PE        60000000-60021000        Deferred        cserhelper
PE        65ec0000-66072000        Deferred        avcodec-53
PE        68b80000-68ba7000        Deferred        avutil-51
PE        6ab00000-6ab33000        Deferred        avformat-53
ELF        78ac0000-78aec000        Deferred        libvorbis.so.0
ELF        78aec000-78c64000        Deferred        libvorbisenc.so.2
ELF        78c64000-78c98000        Deferred        libflac.so.8
ELF        78c98000-78d0a000        Deferred        libsndfile.so.1
ELF        78d0a000-78e00000        Deferred        libasound.so.2
ELF        78f22000-78f91000        Deferred        libpulsecommon-4.0.so
ELF        78f91000-78fe0000        Deferred        libpulse.so.0
ELF        78fea000-79000000        Deferred        wbemprox<elf>
  \-PE        78ff0000-79000000        \               wbemprox
ELF        79307000-7931c000        Deferred        hid<elf>
  \-PE        79310000-7931c000        \               hid
ELF        7931c000-7934d000        Deferred        winealsa<elf>
  \-PE        79320000-7934d000        \               winealsa
ELF        7934d000-7b800000        Deferred        fglrx_dri.so
ELF        7b800000-7ba43000        Deferred        kernel32<elf>
  \-PE        7b810000-7ba43000        \               kernel32
ELF        7ba44000-7ba69000        Deferred        mmdevapi<elf>
  \-PE        7ba50000-7ba69000        \               mmdevapi
ELF        7ba69000-7bab6000        Deferred        dsound<elf>
  \-PE        7ba70000-7bab6000        \               dsound
ELF        7bab6000-7bafa000        Deferred        rsaenh<elf>
  \-PE        7bac0000-7bafa000        \               rsaenh
ELF        7bafa000-7bb18000        Deferred        pdh<elf>
  \-PE        7bb00000-7bb18000        \               pdh
ELF        7bb5e000-7bc00000        Deferred        msvcrt<elf>
  \-PE        7bb70000-7bc00000        \               msvcrt
ELF        7bc00000-7bce3000        Dwarf           ntdll<elf>
  \-PE        7bc10000-7bce3000        \               ntdll
ELF        7bcf5000-7bd10000        Deferred        imagehlp<elf>
  \-PE        7bd00000-7bd10000        \               imagehlp
ELF        7bd54000-7be00000        Deferred        urlmon<elf>
  \-PE        7bd60000-7be00000        \               urlmon
ELF        7bf00000-7bf04000        Deferred        <wine-loader>
ELF        7bf06000-7bf0f000        Deferred        libogg.so.0
ELF        7bf0f000-7bf4f000        Deferred        usp10<elf>
  \-PE        7bf20000-7bf4f000        \               usp10
ELF        7bf4f000-7bfbf000        Deferred        setupapi<elf>
  \-PE        7bf60000-7bfbf000        \               setupapi
ELF        7c2c0000-7c2c7000        Deferred        libasound_module_pcm_pulse.so
ELF        7c2c7000-7c2d1000        Deferred        libwrap.so.0
ELF        7c2d1000-7c300000        Deferred        netapi32<elf>
  \-PE        7c2e0000-7c300000        \               netapi32
ELF        7c40a000-7c415000        Deferred        libjson-c.so.2
ELF        7c415000-7c449000        Deferred        secur32<elf>
  \-PE        7c420000-7c449000        \               secur32
ELF        7cdb8000-7ce1e000        Deferred        libatiadlxx.so
ELF        7ce1e000-7ce37000        Deferred        libatiuki.so.1
ELF        7ce37000-7cf27000        Deferred        libgl.so.1
ELF        7cf27000-7d000000        Deferred        opengl32<elf>
  \-PE        7cf40000-7d000000        \               opengl32
ELF        7d101000-7d108000        Deferred        libasyncns.so.0
ELF        7d108000-7d11d000        Deferred        dhcpcsvc<elf>
  \-PE        7d110000-7d11d000        \               dhcpcsvc
ELF        7d11d000-7d135000        Deferred        userenv<elf>
  \-PE        7d120000-7d135000        \               userenv
ELF        7d135000-7d149000        Deferred        msimg32<elf>
  \-PE        7d140000-7d149000        \               msimg32
ELF        7d149000-7d16e000        Deferred        iphlpapi<elf>
  \-PE        7d150000-7d16e000        \               iphlpapi
ELF        7d16e000-7d18b000        Deferred        libgcc_s.so.1
ELF        7d28b000-7d2d6000        Deferred        libdbus-1.so.3
ELF        7d2d6000-7d2f5000        Deferred        libp11-kit.so.0
ELF        7d2f5000-7d307000        Deferred        libtasn1.so.3
ELF        7d307000-7d38b000        Deferred        libgcrypt.so.11
ELF        7d38b000-7d45a000        Deferred        libkrb5.so.3
ELF        7d45a000-7d520000        Deferred        libgnutls.so.26
ELF        7d59b000-7d5a4000        Deferred        librt.so.1
ELF        7d5a4000-7d5cc000        Deferred        libk5crypto.so.3
ELF        7d5cc000-7d5de000        Deferred        libavahi-client.so.3
ELF        7d5de000-7d61b000        Deferred        libgssapi_krb5.so.2
ELF        7d61b000-7d687000        Deferred        libcups.so.2
ELF        7d687000-7d774000        Deferred        comdlg32<elf>
  \-PE        7d690000-7d774000        \               comdlg32
ELF        7d774000-7d84a000        Deferred        crypt32<elf>
  \-PE        7d780000-7d84a000        \               crypt32
ELF        7d84a000-7d900000        Deferred        winmm<elf>
  \-PE        7d850000-7d900000        \               winmm
ELF        7da01000-7da06000        Deferred        libgpg-error.so.0
ELF        7da06000-7da0f000        Deferred        libkrb5support.so.0
ELF        7da0f000-7da1d000        Deferred        libavahi-common.so.3
ELF        7da1d000-7da5e000        Deferred        winspool<elf>
  \-PE        7da20000-7da5e000        \               winspool
ELF        7da5e000-7da8b000        Deferred        msacm32<elf>
  \-PE        7da60000-7da8b000        \               msacm32
ELF        7da8b000-7daa2000        Deferred        libresolv.so.2
ELF        7daaf000-7dac2000        Deferred        gnome-keyring-pkcs11.so
ELF        7dac2000-7db00000        Deferred        winhttp<elf>
  \-PE        7dad0000-7db00000        \               winhttp
ELF        7dc03000-7dc07000        Deferred        libkeyutils.so.1
ELF        7dc07000-7dc0e000        Deferred        libnss_dns.so.2
ELF        7dc0e000-7dc7e000        Deferred        dbghelp<elf>
  \-PE        7dc20000-7dc7e000        \               dbghelp
ELF        7dc7e000-7dca7000        Deferred        mpr<elf>
  \-PE        7dc80000-7dca7000        \               mpr
ELF        7dca7000-7dd21000        Deferred        wininet<elf>
  \-PE        7dcb0000-7dd21000        \               wininet
ELF        7dd21000-7dd35000        Deferred        psapi<elf>
  \-PE        7dd30000-7dd35000        \               psapi
ELF        7dd4b000-7dd82000        Deferred        uxtheme<elf>
  \-PE        7dd50000-7dd82000        \               uxtheme
ELF        7dd82000-7dd88000        Deferred        libxfixes.so.3
ELF        7dd88000-7dd93000        Deferred        libxcursor.so.1
ELF        7dd94000-7dd99000        Deferred        libcom_err.so.2
ELF        7de2a000-7de53000        Deferred        libexpat.so.1
ELF        7de53000-7de8d000        Deferred        libfontconfig.so.1
ELF        7de8d000-7de9e000        Deferred        libxi.so.6
ELF        7de9e000-7dea2000        Deferred        libxcomposite.so.1
ELF        7dea2000-7dead000        Deferred        libxrandr.so.2
ELF        7dead000-7deb8000        Deferred        libxrender.so.1
ELF        7deb8000-7debe000        Deferred        libxxf86vm.so.1
ELF        7debe000-7dee2000        Deferred        imm32<elf>
  \-PE        7dec0000-7dee2000        \               imm32
ELF        7dee2000-7dee9000        Deferred        libxdmcp.so.6
ELF        7dee9000-7df0a000        Deferred        libxcb.so.1
ELF        7df0a000-7df24000        Deferred        libice.so.6
ELF        7df24000-7e059000        Deferred        libx11.so.6
ELF        7e059000-7e06c000        Deferred        libxext.so.6
ELF        7e06c000-7e075000        Deferred        libsm.so.6
ELF        7e075000-7e126000        Deferred        winex11<elf>
  \-PE        7e080000-7e126000        \               winex11
ELF        7e126000-7e140000        Deferred        libz.so.1
ELF        7e140000-7e1df000        Deferred        libfreetype.so.6
ELF        7e1ff000-7e288000        Deferred        rpcrt4<elf>
  \-PE        7e210000-7e288000        \               rpcrt4
ELF        7e288000-7e3e9000        Deferred        ole32<elf>
  \-PE        7e2a0000-7e3e9000        \               ole32
ELF        7e3e9000-7e52d000        Deferred        oleaut32<elf>
  \-PE        7e400000-7e52d000        \               oleaut32
ELF        7e52d000-7e5a3000        Deferred        shlwapi<elf>
  \-PE        7e540000-7e5a3000        \               shlwapi
ELF        7e5a3000-7e7e1000        Deferred        shell32<elf>
  \-PE        7e5b0000-7e7e1000        \               shell32
ELF        7e7e1000-7e852000        Dwarf           advapi32<elf>
  \-PE        7e7f0000-7e852000        \               advapi32
ELF        7e852000-7e931000        Deferred        gdi32<elf>
  \-PE        7e860000-7e931000        \               gdi32
ELF        7e931000-7eaa0000        Deferred        user32<elf>
  \-PE        7e940000-7eaa0000        \               user32
ELF        7eaa0000-7ebbf000        Deferred        comctl32<elf>
  \-PE        7eab0000-7ebbf000        \               comctl32
ELF        7ebbf000-7ebf2000        Deferred        ws2_32<elf>
  \-PE        7ebd0000-7ebf2000        \               ws2_32
ELF        7ebf2000-7ebff000        Deferred        libnss_files.so.2
ELF        7ebff000-7ec0b000        Deferred        libnss_nis.so.2
ELF        7ec0b000-7ec24000        Deferred        libnsl.so.1
ELF        7ec24000-7ec2d000        Deferred        libnss_compat.so.2
ELF        7ef9d000-7efe0000        Deferred        libm.so.6
ELF        7efe1000-7efe5000        Deferred        libxinerama.so.1
ELF        7efe5000-7f000000        Deferred        version<elf>
  \-PE        7eff0000-7f000000        \               version
ELF        f7424000-f7429000        Deferred        libdl.so.2
ELF        f7429000-f75dd000        Dwarf           libc.so.6
ELF        f75de000-f75f9000        Dwarf           libpthread.so.0
ELF        f75fc000-f7600000        Deferred        libxau.so.6
ELF        f7612000-f7618000        Deferred        libuuid.so.1
ELF        f7619000-f775d000        Dwarf           libwine.so.1
ELF        f775f000-f7781000        Deferred        ld-linux.so.2
ELF        f7781000-f7782000        Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
        0000001f    0
        0000001e    0
        00000015    0
        00000010    0
        0000000f    0
00000012 winedevice.exe
        0000001c    0
        00000019    0
        00000014    0
        00000013    0
0000001a plugplay.exe
        00000020    0
        0000001d    0
        0000001b    0
00000021 explorer.exe
        00000022    0
00000023 (D) C:\Program Files (x86)\Steam\Steam.exe
        0000000b    0
        00000046    0
        00000045    0
        00000044    0
        00000043    0
        00000042    0
        00000041    0
        00000040    0
        0000003f    0 <==
        0000003d    0
        0000003c    0
        0000003b    0
        0000003a    0
        00000039    0
        00000038    0
        00000037    0
        00000036    0
        00000035    0
        00000034    0
        00000033    0
        00000032    0
        00000031    0
        00000030    0
        0000002d    0
        0000002a    0
        00000029    0
        00000028    0
        00000024    0
0000000d steamerrorreporter.exe
        0000002c    0
        0000002b    0
System information:
    Wine build: wine-1.4.1
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.11.0-14-generic
```

---

