---
title: "Help please"
date: 2008-06-22
forum: Wine
---

### Post by HxC69 on 2008-06-22
Okay. So no matter what program i open under Wine, it shuts itself down right on startup of it. I can not find out whats wrong, It will just close right after i start it. Any help please?

---

### Post by HxC69 on 2008-06-22
Anyone?

---

### Post by karth on 2008-06-23
How do you start Wine? Does it return an error in the terminal?
Which version of Wine and Ubuntu?

Wine by itself does not _do_ anything, it has to take a windows .exe as an argument, so it is able to run.

```
$ wine foo.exe
```

Some commands you could try, type them in a terminal

```
wine notepad
wine iexplore
winecfg
```

---

### Post by HxC69 on 2008-06-24
I get this error when trying to open Photoshop CS3
```
  30 0x061ce490 (0x0033db14)
  31 0x061ce490 (0x0033db14)
  32 0x061ce490 (0x0033db14)
  33 0x061ce490 (0x0033db14)
  34 0x061ce490 (0x0033db14)
  35 0x061ce490 (0x0033db14)
  36 0x061ce490 (0x0033db14)
  37 0x061ce490 (0x0033db14)
  38 0x061ce490 (0x0033db14)
  39 0x061ce490 (0x0033db14)
  40 0x061ce490 (0x0033db14)
  41 0x061ce490 (0x0033db14)
  42 0x061ce490 (0x0033db14)
  43 0x061ce490 (0x0033db14)
  44 0x061ce490 (0x0033db14)
  45 0x061ce490 (0x0033db14)
  46 0x061ce490 (0x0033db14)
  47 0x061ce490 (0x0033db14)
  48 0x061ce490 (0x0033db14)
  49 0x061ce490 (0x0033db14)
  50 0x061ce490 (0x0033db14)
  51 0x061ce490 (0x0033db14)
  52 0x061ce490 (0x0033db14)
  53 0x061ce490 (0x0033db14)
  54 0x061ce490 (0x0033db14)
  55 0x061ce490 (0x0033db14)
  56 0x061ce490 (0x0033db14)
  57 0x061ce490 (0x0033db14)
  58 0x061ce490 (0x0033db14)
  59 0x061ce490 (0x0033db14)
  60 0x061ce490 (0x0033db14)
  61 0x061ce490 (0x0033db14)
  62 0x061ce490 (0x0033db14)
  63 0x061ce490 (0x0033db14)
  64 0x061ce490 (0x0033db14)
  65 0x061ce490 (0x0033db14)
  66 0x061ce490 (0x0033db14)
  67 0x061ce490 (0x0033db14)
  68 0x061ce490 (0x0033db14)
  69 0x061ce490 (0x0033db14)
  70 0x061ce490 (0x0033db14)
  71 0x061ce490 (0x0033db14)
  72 0x061ce490 (0x0033db14)
  73 0x061ce490 (0x0033db14)
  74 0x061ce490 (0x0033db14)
  75 0x061ce490 (0x0033db14)
  76 0x061ce490 (0x0033db14)
  77 0x061ce490 (0x0033db14)
  78 0x061ce490 (0x0033db14)
  79 0x061ce490 (0x0033db14)
  80 0x061ce490 (0x0033db14)
  81 0x061ce490 (0x0033db14)
  82 0x061ce490 (0x0033db14)
  83 0x061ce490 (0x0033db14)
  84 0x061ce490 (0x0033db14)
  85 0x061ce490 (0x0033db14)
  86 0x061ce490 (0x0033db14)
  87 0x061ce490 (0x0033db14)
  88 0x061ce490 (0x0033db14)
  89 0x061ce490 (0x0033db14)
  90 0x061ce490 (0x0033db14)
  91 0x061ce490 (0x0033db14)
  92 0x061ce490 (0x0033db14)
  93 0x061ce490 (0x0033db14)
  94 0x061ce490 (0x0033db14)
  95 0x061ce490 (0x0033db14)
  96 0x061ce490 (0x0033db14)
  97 0x061ce490 (0x0033db14)
  98 0x061ce490 (0x0033db14)
  99 0x061ce490 (0x0033db14)
  100 0x061ce490 (0x0033db14)
  101 0x061ce490 (0x0033db14)
  102 0x061ce490 (0x0033db14)
  103 0x061ce490 (0x0033db14)
  104 0x061ce490 (0x0033db14)
  105 0x061ce490 (0x0033db14)
  106 0x061ce490 (0x0033db14)
  107 0x061ce490 (0x0033db14)
  108 0x061ce490 (0x0033db14)
  109 0x061ce490 (0x0033db14)
  110 0x061ce490 (0x0033db14)
  111 0x061ce490 (0x0033db14)
  112 0x061ce490 (0x0033db14)
  113 0x061ce490 (0x0033db14)
  114 0x061ce490 (0x0033db14)
  115 0x061ce490 (0x0033db14)
  116 0x061ce490 (0x0033db14)
  117 0x061ce490 (0x0033db14)
  118 0x061ce490 (0x0033db14)
  119 0x061ce490 (0x0033db14)
  120 0x061ce490 (0x0033db14)
  121 0x061ce490 (0x0033db14)
  122 0x061ce490 (0x0033db14)
  123 0x061ce490 (0x0033db14)
  124 0x061ce490 (0x0033db14)
  125 0x061ce490 (0x0033db14)
  126 0x061ce490 (0x0033db14)
  127 0x061ce490 (0x0033db14)
  128 0x061ce490 (0x0033db14)
  129 0x061ce490 (0x0033db14)
  130 0x061ce490 (0x0033db14)
  131 0x061ce490 (0x0033db14)
  132 0x061ce490 (0x0033db14)
  133 0x061ce490 (0x0033db14)
  134 0x061ce490 (0x0033db14)
  135 0x061ce490 (0x0033db14)
  136 0x061ce490 (0x0033db14)
  137 0x061ce490 (0x0033db14)
  138 0x061ce490 (0x0033db14)
  139 0x061ce490 (0x0033db14)
  140 0x061ce490 (0x0033db14)
  141 0x061ce490 (0x0033db14)
  142 0x061ce490 (0x0033db14)
  143 0x061ce490 (0x0033db14)
  144 0x061ce490 (0x0033db14)
  145 0x061ce490 (0x0033db14)
  146 0x061ce490 (0x0033db14)
  147 0x061ce490 (0x0033db14)
  148 0x061ce490 (0x0033db14)
  149 0x061ce490 (0x0033db14)
  150 0x061ce490 (0x0033db14)
  151 0x061ce490 (0x0033db14)
  152 0x061ce490 (0x0033db14)
  153 0x061ce490 (0x0033db14)
  154 0x061ce490 (0x0033db14)
  155 0x061ce490 (0x0033db14)
  156 0x061ce490 (0x0033db14)
  157 0x061ce490 (0x0033db14)
  158 0x061ce490 (0x0033db14)
  159 0x061ce490 (0x0033db14)
  160 0x061ce490 (0x0033db14)
  161 0x061ce490 (0x0033db14)
  162 0x061ce490 (0x0033db14)
  163 0x061ce490 (0x0033db14)
  164 0x061ce490 (0x0033db14)
  165 0x061ce490 (0x0033db14)
  166 0x061ce490 (0x0033db14)
  167 0x061ce490 (0x0033db14)
  168 0x061ce490 (0x0033db14)
  169 0x061ce490 (0x0033db14)
  170 0x061ce490 (0x0033db14)
  171 0x061ce490 (0x0033db14)
  172 0x061ce490 (0x0033db14)
  173 0x061ce490 (0x0033db14)
  174 0x061ce490 (0x0033db14)
  175 0x061ce490 (0x0033db14)
  176 0x061ce490 (0x0033db14)
  177 0x061ce490 (0x0033db14)
  178 0x061ce490 (0x0033db14)
  179 0x061ce490 (0x0033db14)
  180 0x061ce490 (0x0033db14)
  181 0x061ce490 (0x0033db14)
  182 0x061ce490 (0x0033db14)
  183 0x061ce490 (0x0033db14)
  184 0x061ce490 (0x0033db14)
  185 0x061ce490 (0x0033db14)
  186 0x061ce490 (0x0033db14)
  187 0x061ce490 (0x0033db14)
  188 0x061ce490 (0x0033db14)
  189 0x061ce490 (0x0033db14)
  190 0x061ce490 (0x0033db14)
  191 0x061ce490 (0x0033db14)
  192 0x061ce490 (0x0033db14)
  193 0x061ce490 (0x0033db14)
  194 0x061ce490 (0x0033db14)
  195 0x061ce490 (0x0033db14)
  196 0x061ce490 (0x0033db14)
  197 0x061ce490 (0x0033db14)
  198 0x061ce490 (0x0033db14)
  199 0x061ce490 (0x0033db14)
  200 0x061ce490 (0x0033db14)
  201 0x061ce490 (0x0033db14)
0x7b844cc6: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (100 modules)
PE	  400000- 465d000	Deferred        photoshop
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7cfdb000-7cfee000	Deferred        msimg32<elf>
  \-PE	7cfe0000-7cfee000	\               msimg32
ELF	7cfee000-7d001000	Deferred        sti<elf>
  \-PE	7cff0000-7d001000	\               sti
ELF	7d387000-7de9c000	Deferred        libglcore.so.1
ELF	7de9c000-7df40000	Deferred        libgl.so.1
ELF	7df40000-7dfc1000	Deferred        opengl32<elf>
  \-PE	7df50000-7dfc1000	\               opengl32
ELF	7dfc1000-7dfed000	Deferred        ws2_32<elf>
  \-PE	7dfd0000-7dfed000	\               ws2_32
ELF	7dfed000-7e013000	Deferred        netapi32<elf>
  \-PE	7dff0000-7e013000	\               netapi32
ELF	7e013000-7e017000	Deferred        libgpg-error.so.0
ELF	7e017000-7e064000	Deferred        libgcrypt.so.11
ELF	7e064000-7e074000	Deferred        libtasn1.so.3
ELF	7e074000-7e07c000	Deferred        libkrb5support.so.0
ELF	7e07c000-7e0ae000	Deferred        libcrypt.so.1
ELF	7e0ae000-7e123000	Deferred        libgnutls.so.13
ELF	7e123000-7e146000	Deferred        libk5crypto.so.3
ELF	7e146000-7e1d3000	Deferred        libkrb5.so.3
ELF	7e1d3000-7e1fc000	Deferred        libgssapi_krb5.so.2
ELF	7e1fc000-7e22f000	Deferred        libcups.so.2
ELF	7e22f000-7e265000	Deferred        winspool<elf>
  \-PE	7e240000-7e265000	\               winspool
ELF	7e265000-7e310000	Deferred        comdlg32<elf>
  \-PE	7e270000-7e310000	\               comdlg32
ELF	7e310000-7e348000	Export          gdiplus<elf>
  \-PE	7e320000-7e348000	\               gdiplus
ELF	7e348000-7e3ea000	Deferred        oleaut32<elf>
  \-PE	7e360000-7e3ea000	\               oleaut32
ELF	7e3ea000-7e4a9000	Deferred        comctl32<elf>
  \-PE	7e3f0000-7e4a9000	\               comctl32
ELF	7e4a9000-7e502000	Deferred        shlwapi<elf>
  \-PE	7e4c0000-7e502000	\               shlwapi
ELF	7e502000-7e615000	Deferred        shell32<elf>
  \-PE	7e510000-7e615000	\               shell32
ELF	7e615000-7e628000	Deferred        shfolder<elf>
  \-PE	7e620000-7e628000	\               shfolder
ELF	7e628000-7e62a000	Deferred        libnvidia-tls.so.1
ELF	7e62a000-7e62d000	Deferred        libkeyutils.so.1
ELF	7e63c000-7e651000	Deferred        psapi<elf>
  \-PE	7e640000-7e651000	\               psapi
ELF	7e67e000-7e6b1000	Deferred        uxtheme<elf>
  \-PE	7e680000-7e6b1000	\               uxtheme
ELF	7e7ea000-7e7fe000	Deferred        lz32<elf>
  \-PE	7e7f0000-7e7fe000	\               lz32
ELF	7e7fe000-7e817000	Deferred        version<elf>
  \-PE	7e800000-7e817000	\               version
ELF	7e817000-7e82a000	Deferred        libresolv.so.2
ELF	7e82a000-7e848000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e848000	\               iphlpapi
ELF	7e848000-7e8a9000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e8a9000	\               rpcrt4
ELF	7e8a9000-7e94d000	Deferred        ole32<elf>
  \-PE	7e8c0000-7e94d000	\               ole32
ELF	7e94d000-7e956000	Deferred        libxcursor.so.1
ELF	7e956000-7e95b000	Deferred        libxfixes.so.3
ELF	7e95b000-7e95e000	Deferred        libxcomposite.so.1
ELF	7e95e000-7e964000	Deferred        libxrandr.so.2
ELF	7e964000-7e96c000	Deferred        libxrender.so.1
ELF	7e96c000-7e96f000	Deferred        libxinerama.so.1
ELF	7e96f000-7e98f000	Deferred        imm32<elf>
  \-PE	7e980000-7e98f000	\               imm32
ELF	7e98f000-7e994000	Deferred        libxdmcp.so.6
ELF	7e994000-7e9ac000	Deferred        libxcb.so.1
ELF	7e9ac000-7e9af000	Deferred        libxau.so.6
ELF	7e9af000-7ea96000	Deferred        libx11.so.6
ELF	7ea96000-7eaa4000	Deferred        libxext.so.6
ELF	7eaa4000-7eaa9000	Deferred        libxxf86vm.so.1
ELF	7eaaa000-7eaad000	Deferred        libcom_err.so.2
ELF	7eaad000-7eab8000	Deferred        libgcc_s.so.1
ELF	7eab8000-7eb4f000	Deferred        winex11<elf>
  \-PE	7ead0000-7eb4f000	\               winex11
ELF	7eb5d000-7eb7e000	Deferred        libexpat.so.1
ELF	7eb7e000-7eba8000	Deferred        libfontconfig.so.1
ELF	7ebb7000-7ebcc000	Deferred        libz.so.1
ELF	7ebcc000-7ec3c000	Deferred        libfreetype.so.6
ELF	7ec4b000-7ec9d000	Deferred        advapi32<elf>
  \-PE	7ec60000-7ec9d000	\               advapi32
ELF	7ec9d000-7ed38000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed38000	\               gdi32
ELF	7ed38000-7ee7f000	Deferred        user32<elf>
  \-PE	7ed50000-7ee7f000	\               user32
ELF	7ef9f000-7efaa000	Deferred        libnss_files.so.2
ELF	7efaa000-7efb4000	Deferred        libnss_nis.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7ce0000-f7ce2000	Deferred        libxcb-xlib.so.0
ELF	f7ce6000-f7cea000	Deferred        libdl.so.2
ELF	f7cea000-f7e39000	Deferred        libc.so.6
ELF	f7e3a000-f7e52000	Deferred        libpthread.so.0
ELF	f7e61000-f7f97000	Deferred        libwine.so.1
ELF	f7f99000-f7fb8000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\ryan\Desktop\Photoshop.exe
	0000001d    0
	0000001c    0
	0000001b    0
	0000001a    0
	00000009    0 <==
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:
=>1 0x7b844cc6 in kernel32 (+0x24cc6) (0x0033da0c)
  2 0x047e8ddc (0x0033da54)
  3 0x7e33a7c5 in gdiplus (+0x1a7c5) (0x0033da88)
  4 0x7e32733c in gdiplus (+0x733c) (0x0033dacc)
  5 0x04c5b393 (0x0033db14)
  6 0x061ce490 (0x0033db14)
  7 0x061ce490 (0x0033db14)
  8 0x061ce490 (0x0033db14)
  9 0x061ce490 (0x0033db14)
  10 0x061ce490 (0x0033db14)
  11 0x061ce490 (0x0033db14)
  12 0x061ce490 (0x0033db14)
  13 0x061ce490 (0x0033db14)
  14 0x061ce490 (0x0033db14)
  15 0x061ce490 (0x0033db14)
  16 0x061ce490 (0x0033db14)
  17 0x061ce490 (0x0033db14)
  18 0x061ce490 (0x0033db14)
  19 0x061ce490 (0x0033db14)
  20 0x061ce490 (0x0033db14)
  21 0x061ce490 (0x0033db14)
  22 0x061ce490 (0x0033db14)
  23 0x061ce490 (0x0033db14)
  24 0x061ce490 (0x0033db14)
  25 0x061ce490 (0x0033db14)
  26 0x061ce490 (0x0033db14)
  27 0x061ce490 (0x0033db14)
  28 0x061ce490 (0x0033db14)
  29 0x061ce490 (0x0033db14)
  30 0x061ce490 (0x0033db14)
  31 0x061ce490 (0x0033db14)
  32 0x061ce490 (0x0033db14)
  33 0x061ce490 (0x0033db14)
  34 0x061ce490 (0x0033db14)
  35 0x061ce490 (0x0033db14)
  36 0x061ce490 (0x0033db14)
  37 0x061ce490 (0x0033db14)
  38 0x061ce490 (0x0033db14)
  39 0x061ce490 (0x0033db14)
  40 0x061ce490 (0x0033db14)
  41 0x061ce490 (0x0033db14)
  42 0x061ce490 (0x0033db14)
  43 0x061ce490 (0x0033db14)
  44 0x061ce490 (0x0033db14)
  45 0x061ce490 (0x0033db14)
  46 0x061ce490 (0x0033db14)
  47 0x061ce490 (0x0033db14)
  48 0x061ce490 (0x0033db14)
  49 0x061ce490 (0x0033db14)
  50 0x061ce490 (0x0033db14)
  51 0x061ce490 (0x0033db14)
  52 0x061ce490 (0x0033db14)
  53 0x061ce490 (0x0033db14)
  54 0x061ce490 (0x0033db14)
  55 0x061ce490 (0x0033db14)
  56 0x061ce490 (0x0033db14)
  57 0x061ce490 (0x0033db14)
  58 0x061ce490 (0x0033db14)
  59 0x061ce490 (0x0033db14)
  60 0x061ce490 (0x0033db14)
  61 0x061ce490 (0x0033db14)
  62 0x061ce490 (0x0033db14)
  63 0x061ce490 (0x0033db14)
  64 0x061ce490 (0x0033db14)
  65 0x061ce490 (0x0033db14)
  66 0x061ce490 (0x0033db14)
  67 0x061ce490 (0x0033db14)
  68 0x061ce490 (0x0033db14)
  69 0x061ce490 (0x0033db14)
  70 0x061ce490 (0x0033db14)
  71 0x061ce490 (0x0033db14)
  72 0x061ce490 (0x0033db14)
  73 0x061ce490 (0x0033db14)
  74 0x061ce490 (0x0033db14)
  75 0x061ce490 (0x0033db14)
  76 0x061ce490 (0x0033db14)
  77 0x061ce490 (0x0033db14)
  78 0x061ce490 (0x0033db14)
  79 0x061ce490 (0x0033db14)
  80 0x061ce490 (0x0033db14)
  81 0x061ce490 (0x0033db14)
  82 0x061ce490 (0x0033db14)
  83 0x061ce490 (0x0033db14)
  84 0x061ce490 (0x0033db14)
  85 0x061ce490 (0x0033db14)
  86 0x061ce490 (0x0033db14)
  87 0x061ce490 (0x0033db14)
  88 0x061ce490 (0x0033db14)
  89 0x061ce490 (0x0033db14)
  90 0x061ce490 (0x0033db14)
  91 0x061ce490 (0x0033db14)
  92 0x061ce490 (0x0033db14)
  93 0x061ce490 (0x0033db14)
  94 0x061ce490 (0x0033db14)
  95 0x061ce490 (0x0033db14)
  96 0x061ce490 (0x0033db14)
  97 0x061ce490 (0x0033db14)
  98 0x061ce490 (0x0033db14)
  99 0x061ce490 (0x0033db14)
  100 0x061ce490 (0x0033db14)
  101 0x061ce490 (0x0033db14)
  102 0x061ce490 (0x0033db14)
  103 0x061ce490 (0x0033db14)
  104 0x061ce490 (0x0033db14)
  105 0x061ce490 (0x0033db14)
  106 0x061ce490 (0x0033db14)
  107 0x061ce490 (0x0033db14)
  108 0x061ce490 (0x0033db14)
  109 0x061ce490 (0x0033db14)
  110 0x061ce490 (0x0033db14)
  111 0x061ce490 (0x0033db14)
  112 0x061ce490 (0x0033db14)
  113 0x061ce490 (0x0033db14)
  114 0x061ce490 (0x0033db14)
  115 0x061ce490 (0x0033db14)
  116 0x061ce490 (0x0033db14)
  117 0x061ce490 (0x0033db14)
  118 0x061ce490 (0x0033db14)
  119 0x061ce490 (0x0033db14)
  120 0x061ce490 (0x0033db14)
  121 0x061ce490 (0x0033db14)
  122 0x061ce490 (0x0033db14)
  123 0x061ce490 (0x0033db14)
  124 0x061ce490 (0x0033db14)
  125 0x061ce490 (0x0033db14)
  126 0x061ce490 (0x0033db14)
  127 0x061ce490 (0x0033db14)
  128 0x061ce490 (0x0033db14)
  129 0x061ce490 (0x0033db14)
  130 0x061ce490 (0x0033db14)
  131 0x061ce490 (0x0033db14)
  132 0x061ce490 (0x0033db14)
  133 0x061ce490 (0x0033db14)
  134 0x061ce490 (0x0033db14)
  135 0x061ce490 (0x0033db14)
  136 0x061ce490 (0x0033db14)
  137 0x061ce490 (0x0033db14)
  138 0x061ce490 (0x0033db14)
  139 0x061ce490 (0x0033db14)
  140 0x061ce490 (0x0033db14)
  141 0x061ce490 (0x0033db14)
  142 0x061ce490 (0x0033db14)
  143 0x061ce490 (0x0033db14)
  144 0x061ce490 (0x0033db14)
  145 0x061ce490 (0x0033db14)
  146 0x061ce490 (0x0033db14)
  147 0x061ce490 (0x0033db14)
  148 0x061ce490 (0x0033db14)
  149 0x061ce490 (0x0033db14)
  150 0x061ce490 (0x0033db14)
  151 0x061ce490 (0x0033db14)
  152 0x061ce490 (0x0033db14)
  153 0x061ce490 (0x0033db14)
  154 0x061ce490 (0x0033db14)
  155 0x061ce490 (0x0033db14)
  156 0x061ce490 (0x0033db14)
  157 0x061ce490 (0x0033db14)
  158 0x061ce490 (0x0033db14)
  159 0x061ce490 (0x0033db14)
  160 0x061ce490 (0x0033db14)
  161 0x061ce490 (0x0033db14)
  162 0x061ce490 (0x0033db14)
  163 0x061ce490 (0x0033db14)
  164 0x061ce490 (0x0033db14)
  165 0x061ce490 (0x0033db14)
  166 0x061ce490 (0x0033db14)
  167 0x061ce490 (0x0033db14)
  168 0x061ce490 (0x0033db14)
  169 0x061ce490 (0x0033db14)
  170 0x061ce490 (0x0033db14)
  171 0x061ce490 (0x0033db14)
  172 0x061ce490 (0x0033db14)
  173 0x061ce490 (0x0033db14)
  174 0x061ce490 (0x0033db14)
  175 0x061ce490 (0x0033db14)
  176 0x061ce490 (0x0033db14)
  177 0x061ce490 (0x0033db14)
  178 0x061ce490 (0x0033db14)
  179 0x061ce490 (0x0033db14)
  180 0x061ce490 (0x0033db14)
  181 0x061ce490 (0x0033db14)
  182 0x061ce490 (0x0033db14)
  183 0x061ce490 (0x0033db14)
  184 0x061ce490 (0x0033db14)
  185 0x061ce490 (0x0033db14)
  186 0x061ce490 (0x0033db14)
  187 0x061ce490 (0x0033db14)
  188 0x061ce490 (0x0033db14)
  189 0x061ce490 (0x0033db14)
  190 0x061ce490 (0x0033db14)
  191 0x061ce490 (0x0033db14)
  192 0x061ce490 (0x0033db14)
  193 0x061ce490 (0x0033db14)
  194 0x061ce490 (0x0033db14)
  195 0x061ce490 (0x0033db14)
  196 0x061ce490 (0x0033db14)
  197 0x061ce490 (0x0033db14)
  198 0x061ce490 (0x0033db14)
  199 0x061ce490 (0x0033db14)
  200 0x061ce490 (0x0033db14)
  201 0x061ce490 (0x0033db14)
wine: Call from 0x7b844c50 to unimplemented function gdiplus.dll.GdipCreateHICONFromBitmap, aborting

```

---

### Post by karth on 2008-06-24
For specific help concerning Photoshop CS3, look here, and try to achieve the steps listed under the how-to section.
But keep in mind that Photoshop CS3 is barely runnable under Wine, if at all.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

Also, I believe you should provide the elements I asked for in my previous post concerning the versions of your different pieces of software, including the specific commands you are trying to run.

---

### Post by HxC69 on 2008-06-24
Wine 1.0
Ubuntu 8.04 (Hardy)
I downloaded the ddl i needed to download, or it said to at least.
And it started and stayed started, but then it just had all these error,
As far *** missing files for brushes and all that sit, then it just stayed at the Photoshop loading screen, and i killed it.

Would it matter if this is Portable Photoshop by the way?

---

### Post by madjr on 2008-06-24
> **HxC69 said:**
> I get this error when trying to open Photoshop CS3



Hi,

**Photoshop CS3** is still under heavy testing and improvement by the **Wine developers**

They're still working hard on it.

If you need photoshop get **CS2**, which runs great.

other alternatives are **Krita** and of course **Gimp**.

[IMG]http://www.koffice.org/krita/pics/bala_krita1.6_sm.png[/IMG]

[http://www.koffice.org/krita/](http://www.koffice.org/krita/)

Krita is in ADD/REMOVE catalog or synaptic.

---

### Post by HxC69 on 2008-06-24
Now im using Photoshop CS2, it works but i can't make Text, and when i closed it, the next time i tried to open it i got this:

[IMG]http://i29.tinypic.com/28tw6bk.png[/IMG]

And this is the output:
```
ryan@ryan-desktop:~$ err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
err:ole:create_server class {a1f4e726-8cf1-11d1-bf92-0060081ed811} not registered
err:ole:CoGetClassObject no class object {a1f4e726-8cf1-11d1-bf92-0060081ed811} could be created for context 0x4
fixme:keyboard:UnregisterHotKey (0x20026,99): stub
fixme:keyboard:RegisterHotKey (0x20026,99,0x00000000,27): stub
fixme:font:WineEngRemoveFontResourceEx :stub
err:twain:twain_add_onedriver Source->(DG_CONTROL,DAT_IDENTITY,MSG_GET) failed!
err:twain:twain_add_onedriver Source->(DG_CONTROL,DAT_IDENTITY,MSG_GET) failed!
fixme:font:WineEngRemoveFontResourceEx :stub

```

---

### Post by HxC69 on 2008-06-24
bump.

---

### Post by madjr on 2008-06-25
so, photoshop CS2 doesn't work anymore ?

you may try uninstall and then re-installing it.

or you could upgrade your Wine version to **1.0** (uninstall old one first)

anyway did you try the alternatives? what do you think?

---

### Post by HxC69 on 2008-06-26
When i try to uninstall Photoshop i get this Error.

```
fixme:advapi:LookupAccountNameW (null) L"ryan" (nil) 0x33f38c (nil) 0x33f390 0x33f384 - stub
fixme:advapi:LookupAccountNameW (null) L"ryan" 0x1307e8 0x33f38c 0x1304e0 0x33f390 0x33f384 - stub
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\temp\\install.adb" 1 4 (nil) (nil) (nil) (nil)
fixme:msi:msi_unimplemented_action_stub UnregisterFonts -> 1 ignored L"Font" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 129 ignored L"CreateFolder" table values
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
err:msi:source_matches_volume Failed to get volume information
err:msi:ready_media Cabinet not found: L"C:\\windows\\Installer\\Data1.cab"
err:msi:ACTION_InstallFiles Failed to ready media
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```

---

### Post by madjr on 2008-06-26
hmm i runned photoshop cs2 for a few months before i learned the others and switched.

never had those problems

---

