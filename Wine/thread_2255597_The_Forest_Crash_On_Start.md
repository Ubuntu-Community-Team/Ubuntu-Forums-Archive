---
title: "The Forest Crash On Start"
date: 2014-12-06
forum: Wine
---

### Post by jason147 on 2014-12-06
Heya Guys,

So I've just tryed to run the forest Via Wine on My Ubuntu 14.04 Machine...

I Recieved an Error on startup saying this:
```
Unity Player [version: Unity 4.5.5p1_7c778773db1c]

Unknown caused an Access Violation (0xc0000005)
  in module Unknown at 0023:f75273b8.

Error occurred at 2014-12-05_162300.
Z:\home\jason\Downloads\The Forest\TheForest.exe, run by jason.
19% memory in use.
3944 MB physical memory [3194 MB free].
0 MB paging file [2951 MB free].
0 MB user address space [0 MB free].
Read from location f72f2c98 caused an access violation.

Context:
EDI:    0x00000000  ESI: 0x00000000  EAX:   0xf72f2c98
EBX:    0xf713f000  ECX: 0x00000072  EDX:   0x00c58996
EIP:    0xf75273b8  EBP: 0x00c58996  SegCs: 0x00000023
EFlags: 0x00010246  ESP: 0x0033fa6c  SegSs: 0x0000002b

Bytes at CS:EIP:
0f b6 08 38 0a 0f 85 4d 14 00 00 83 f9 00 0f 84 

Stack:
0x0033fa6c: f712ffbe 00c58996 f72f2c98 0033fac8 .........,/...3.
0x0033fa7c: 7dd34004 7dc0a0a0 00000501 0000004f .@.}...}....O...
0x0033fa8c: f71438a0 7eb19b19 7dd80000 f712ff59 .8.....~...}Y...
0x0033fa9c: f713f000 00000001 00c58996 0033fb38 ............8.3.
0x0033faac: f712fb5c 00c58996 00000001 0033fb18 \.............3.
0x0033fabc: f712fb2d f713f000 00000053 00c58994 -.......S.......
0x0033facc: f712fded 00001f03 0460000c f58e6818 ..........`..h..
0x0033fadc: f71d2000 00000053 f712fddb f71d2000 . ..S........ ..
0x0033faec: f715b4c7 00c58994 00c58994 00000004 ................
0x0033fafc: f715b45a 7dd80000 00c58995 7dd66d90 Z......}.....m.}
0x0033fb0c: 7dd349fc 00c58994 7e2fbba0 00000016 .I.}....../~....
0x0033fb1c: 7e2fbba0 000006da 000006e3 7dd349d0 ../~.........I.}
0x0033fb2c: 7e354000 000006d1 000006e3 0033fba8 .@5~..........3.
0x0033fb3c: 7e2eba79 00c58994 7e2f65eb 0033fb8c y..~.....e/~..3.
0x0033fb4c: 007c50c6 0041a23e 007c50c6 0031003a .P|.>.A..P|.:.1.
0x0033fb5c: 00030000 00000000 7e30a7f0 20000001 ..........0~... 
0x0033fb6c: 00000015 7dd82f80 7dd8502c 7e2fbbb6 ...../.},P.}../~
0x0033fb7c: f4533100 7dd82f80 00c58994 7e35226c .1S../.}....l"5~
0x0033fb8c: 7e35226c 007c51a3 012f5e8c 0033fbb4 l"5~.Q|..^/...3.
0x0033fb9c: 00000001 7e2eb8c0 00000000 0033fbe0 .......~......3.
0x0033fbac: 0041b0a2 0041b0a2 00c58994 012f5a60 ..A...A.....`Z/.
0x0033fbbc: 007c4b04 012f5e8c 00000000 00800000 .K|..^/.........
0x0033fbcc: 0033fbec 00000011 00000017 00000004 ..3.............
0x0033fbdc: 012f5e8c 0033fbf8 00839364 00000000 .^/...3.d.......
0x0033fbec: 00000000 012f5a60 028b1264 0033fc24 ....`Z/.d...$.3.
0x0033fbfc: 00832a70 00000000 028b1201 00000000 p*..............
0x0033fc0c: 012f4428 00000000 00000001 012f4401 (D/..........D/.
0x0033fc1c: 00000000 0033fc00 0033fc54 004fde9d ......3.T.3...O.
0x0033fc2c: 00000000 00000001 00000000 00000000 ................
0x0033fc3c: 00c657f8 00c6582c 00000010 00000000 .W..,X..........
0x0033fc4c: 00000001 0189354b 0033fc9c 0058ce10 ....K5....3...X.
0x0033fc5c: 0057c76f 00000000 0000444e 00000000 o.W.....ND......
0x0033fc6c: 0000000a 0000000f 00000000 00000008 ................
0x0033fc7c: 0041dd2d 0033fdb8 0033fdb8 005f49ea -.A...3...3..I_.
0x0033fc8c: 012f4384 0000000f 00000000 012f445c .C/.........\D/.
0x0033fc9c: 0033fdb8 005f4ab9 00000000 008955e3 ..3..J_......U..
0x0033fcac: 00000000 7b8b5000 012c9a70 010b9470 .....P.{p.,.p...
0x0033fcbc: 7bc37239 7fffffff 00000022 0000002f 9r.{....".../...
0x0033fccc: 010b7000 012ca200 7bcbf000 0033fd48 .p....,....{H.3.
0x0033fcdc: 7bc4cf76 00000000 0000000f 0033fd48 v..{........H.3.
0x0033fcec: 6f6e6f00 6374652f 00000000 0033fd48 .ono/etc....H.3.
0x0033fcfc: 00000000 0000000f 0000000f 012ca13c ............<.,.
0x0033fd0c: 012ca174 012ca174 010b7000 012c9a24 t.,.t.,..p..$.,.
0x0033fd1c: 00000400 0033fd00 0033fd54 00000031 ......3.T.3.1...
0x0033fd2c: 0000003f 00d7b570 011ca8cc 012c9b08 ?...p.........,.
0x0033fd3c: 00000003 0033fc78 00000284 00000040 ....x.3.....@...
0x0033fd4c: 0000004f 49656e69 012ca200 00000000 O...ineI..,.....
0x0033fd5c: 7bc6c09b 0033fd74 00000000 0000000f ...{t.3.........
0x0033fd6c: 0033fd9c 00000000 616e614d 00646567 ..3.....Managed.
0x0033fd7c: 00898a5b 00000000 00000007 0000000f [...............
0x0033fd8c: 00898a68 011ca8cc 6f6e6f4d 6e6f6d2f h.......Mono/mon
0x0033fd9c: 6c642e6f 0000006c 0000000d 0000000f o.dll...........
0x0033fdac: 010b8588 00000000 00000000 0033fdd0 ..............3.
0x0033fdbc: 008606b8 00400000 00000000 00136d2a ......@.....*m..
0x0033fdcc: 0000000a 0033fe60 00895590 00400000 ....`.3..U....@.
0x0033fddc: 00000000 00136d2a 0000000a 30a5ab0d ....*m.........0
0x0033fdec: 008955e3 7ffdf000 7b8b5000 00000044 .U.......P.{D...
0x0033fdfc: 00000000 002206e2 00220680 00000000 ......"...".....
0x0033fe0c: 00000000 00000000 00000000 00000000 ................
0x0033fe1c: 00000000 00000000 00000000 00000000 ................
0x0033fe2c: 00000000 00000004 ffffffff ffffffff ................
0x0033fe3c: c0000005 7ffdf000 00000000 0033fde8 ..............3.
0x0033fe4c: 0033f5d0 0033fef0 00897370 3048349d ..3...3.ps...4H0
0x0033fe5c: 00000000 0033fe78 7b85e5cc 7ffdf000 ....x.3....{....
0x0033fe6c: 7b8b5000 7ffdf000 008955e3 0033feb8 .P.{.....U....3.
0x0033fe7c: 7b85f653 7ffdf000 008955e3 00000000 S..{.....U......
0x0033fe8c: 00000000 00000000 00000000 00000000 ................
0x0033fe9c: 00000000 00000000 00000000 0033fed0 ..............3.
0x0033feac: 7bcbf000 fffed524 7ffdf000 0033fed8 ...{$.........3.
0x0033febc: 7bc799b0 00000000 00000000 00000000 ...{............
0x0033fecc: 7bc799b0 7ffdf000 7bcbf000 0033ffa8 ...{.......{..3.
0x0033fedc: 7bc7c93d 7b85f5f0 7ffdf000 00000000 =..{...{........
0x0033feec: 00000000 ffffffff 7bc90dc0 7b83b730 ...........{0..{
0x0033fefc: 7bcbf000 fffed524 7ffdf000 0033ffa8 ...{$.........3.
0x0033ff0c: 3551228c dd3ec67b 00000000 00000000 ."Q5{.>.........
0x0033ff1c: 00000000 00000000 00000000 00000000 ................
0x0033ff2c: 00000000 00000000 00000000 00000000 ................
0x0033ff3c: 00000000 00000000 00000000 00000000 ................
0x0033ff4c: 00000000 00000000 00000000 00000000 ................
0x0033ff5c: 00000000 00000000 00000000 00000000 ................
0x0033ff6c: 00000000 00000000 00000000 00000000 ................
0x0033ff7c: 00000000 00000000 00000000 00000000 ................
0x0033ff8c: 00000000 00000000 00000000 00000000 ................
0x0033ff9c: 00000000 7bc7c8c9 f777d000 0033ffc8 .......{..w...3.
0x0033ffac: 7bc7998e 7b85f5f0 7ffdf000 0033ffc8 ...{...{......3.
0x0033ffbc: 7ffdf000 fffed524 f777d000 0033ffe8 ....$.....w...3.
0x0033ffcc: 7bc4e8fe 7b85f5f0 7ffdf000 00000000 ...{...{........
0x0033ffdc: 00000000 00000000 00000000 00000000 ................
0x0033ffec: f75e550d 7b85f5f0 00000000 00000000 .U^....{........
0x0033fffc: 00000000                            ....

Module 1
Z:\home\jason\Downloads\The Forest\TheForest.exe
Image Base: 0x00400000  Image Size: 0x00ba7000
File Size:  11547136    File Time:  2014-12-05_153532
Version:
   Company:    
   Product:    
   FileDesc:   
   FileVer:    4.5.5.38902
   ProdVer:    4.5.5.38902

Module 2
Z:\home\jason\Downloads\The Forest\TheForest_Data\Mono\mono.dll
Image Base: 0x10000000  Image Size: 0x0022f000
File Size:  2101760     File Time:  2014-12-05_150742
Version:
   Company:    
   Product:    
   FileDesc:   
   FileVer:    0.0.0.0
   ProdVer:    0.0.0.0

Module 3
C:\windows\system32\KERNEL32.dll
Image Base: 0x7b810000  Image Size: 0x0024b000
File Size:  1677736     File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    5.1.2600.2180
   ProdVer:    5.1.2600.2180

Module 4
C:\windows\system32\ntdll.dll
Image Base: 0x7bc10000  Image Size: 0x000cb000
File Size:  2468        File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine ntdll
   FileVer:    5.1.2600.2180
   ProdVer:    5.1.2600.2180

Module 5
C:\windows\system32\uxtheme.dll
Image Base: 0x7da70000  Image Size: 0x00035000
File Size:  2448        File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    10.0.0.0
   ProdVer:    1.0.0.0

Module 6
C:\windows\system32\winex11.drv
Image Base: 0x7dd00000  Image Size: 0x0008b000
File Size:  2452        File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine X11 driver
   FileVer:    10.0.0.0
   ProdVer:    1.0.0.0

Module 7
C:\windows\system32\winhttp.dll
Image Base: 0x7df30000  Image Size: 0x00036000
File Size:  17444       File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine HTTP Library
   FileVer:    5.1.2600.2180
   ProdVer:    1.0.0.0

Module 8
C:\windows\system32\iphlpapi.dll
Image Base: 0x7df70000  Image Size: 0x0001c000
File Size:  2480        File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine iphlpapi
   FileVer:    5.1.2600.2180
   ProdVer:    5.1.2600.2180

Module 9
C:\windows\system32\netapi32.dll
Image Base: 0x7df90000  Image Size: 0x00029000
File Size:  1032        File Time:  2014-11-17_182230
Version:
   Company:    
   Product:    
   FileDesc:   
   FileVer:    0.0.0.0
   ProdVer:    0.0.0.0

Module 10
C:\windows\system32\dnsapi.dll
Image Base: 0x7dff0000  Image Size: 0x0001e000
File Size:  2452        File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine dnsapi
   FileVer:    5.2.3790.4318
   ProdVer:    1.0.0.0

Module 11
C:\windows\system32\imm32.dll
Image Base: 0x7e010000  Image Size: 0x00023000
File Size:  2468        File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine imm32
   FileVer:    5.1.2600.2180
   ProdVer:    5.1.2600.2180

Module 12
C:\windows\system32\oleaut32.dll
Image Base: 0x7e050000  Image Size: 0x00119000
File Size:  21416       File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine OLE dll
   FileVer:    6.0.6001.18000
   ProdVer:    1.0.0.0

Module 13
C:\windows\system32\msacm32.dll
Image Base: 0x7e170000  Image Size: 0x00024000
File Size:  22744       File Time:  2014-11-17_182228
Version:
   Company:    
   Product:    
   FileDesc:   
   FileVer:    0.0.0.0
   ProdVer:    0.0.0.0

Module 14
C:\windows\system32\winmm.dll
Image Base: 0x7e1a0000  Image Size: 0x000ae000
File Size:  475716      File Time:  2014-11-17_182230
Version:
   Company:    
   Product:    
   FileDesc:   
   FileVer:    0.0.0.0
   ProdVer:    0.0.0.0

Module 15
C:\windows\system32\opengl32.dll
Image Base: 0x7e270000  Image Size: 0x000ed000
File Size:  2472        File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine OpenGL Client
   FileVer:    5.1.2600.2082
   ProdVer:    5.1.2600.2082

Module 16
C:\windows\system32\comctl32.dll
Image Base: 0x7e360000  Image Size: 0x00104000
File Size:  178076      File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine Common Controls
   FileVer:    5.81.4704.1100
   ProdVer:    5.81.4704.1100

Module 17
C:\windows\system32\shell32.dll
Image Base: 0x7e470000  Image Size: 0x00227000
File Size:  1416836     File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    5.0.3900.6975
   ProdVer:    1.0.0.0

Module 18
C:\windows\system32\shlwapi.dll
Image Base: 0x7e6a0000  Image Size: 0x00071000
File Size:  19932       File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    6.0.2800.1692
   ProdVer:    6.0.2800.1692

Module 19
C:\windows\system32\rpcrt4.dll
Image Base: 0x7e720000  Image Size: 0x00072000
File Size:  2472        File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine rpcrt4
   FileVer:    5.1.2600.2180
   ProdVer:    5.1.2600.2180

Module 20
C:\windows\system32\ole32.dll
Image Base: 0x7e7b0000  Image Size: 0x0011e000
File Size:  19576       File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    10.0.0.0
   ProdVer:    1.0.0.0

Module 21
C:\windows\system32\version.dll
Image Base: 0x7e8d0000  Image Size: 0x00018000
File Size:  2484        File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine version dll
   FileVer:    5.1.2600.2180
   ProdVer:    5.1.2600.2180

Module 22
C:\windows\system32\advapi32.dll
Image Base: 0x7e8f0000  Image Size: 0x0006a000
File Size:  2488        File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine advapi32 dll
   FileVer:    5.1.2600.2180
   ProdVer:    5.1.2600.2180

Module 23
C:\windows\system32\gdi32.dll
Image Base: 0x7e970000  Image Size: 0x00107000
File Size:  16152       File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    10.0.0.0
   ProdVer:    1.0.0.0

Module 24
C:\windows\system32\user32.dll
Image Base: 0x7ea90000  Image Size: 0x00141000
File Size:  227780      File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    5.1.2600.2180
   ProdVer:    5.1.2600.2180

Module 25
C:\windows\system32\ws2_32.dll
Image Base: 0x7ebe0000  Image Size: 0x00027000
File Size:  2476        File Time:  2014-11-17_182228
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    5.1.2600.5512
   ProdVer:    5.1.2600.5512

Module 26
C:\windows\system32\hid.dll
Image Base: 0x7eff0000  Image Size: 0x00010000
File Size:  2440        File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    10.0.0.0
   ProdVer:    1.0.0.0

Module 27
C:\windows\system32\msvcrt.dll
Image Base: 0xf56e0000  Image Size: 0x00095000
File Size:  2456        File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine CRT library
   FileVer:    7.0.2600.2180
   ProdVer:    1.0.0.0

Module 28
C:\windows\system32\dbghelp.dll
Image Base: 0xf7310000  Image Size: 0x00061000
File Size:  2484        File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine Image Helper
   FileVer:    5.1.2600.3264
   ProdVer:    5.1.2600.3264

Module 29
C:\windows\system32\mswsock.dll
Image Base: 0xf73c0000  Image Size: 0x0000c000
File Size:  2444        File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine core dll
   FileVer:    4.0.0.0
   ProdVer:    4.0.0.0

Module 30
C:\windows\system32\psapi.dll
Image Base: 0xf73d0000  Image Size: 0x00010000
File Size:  2500        File Time:  2014-11-17_182230
Version:
   Company:    Microsoft Corporation
   Product:    Wine
   FileDesc:   Wine Process Status Helper
   FileVer:    5.1.2600.3264
   ProdVer:    5.1.2600.3264


== [end of error.log] ==
```

Please Let me Know if you have any Answers, Or questions to help find out how to sort this out! 

Any help is much appreciated :D

Cheers,
Jason

---

### Post by Mark Phelps on 2014-12-07
Wine doesn't do well with games. The WineHQ website rates this one as Garbage: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=16332]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=16332")

---

