---
title: "Error running guild wars 2"
date: 2012-12-06
forum: Wine
---

### Post by thedork01 on 2012-12-06
I am attempting to run guild wars 2 using wine, but I am getting some strange errors just as the client starts.

Here is the full crash report

```

*--> Crash <--*
Assertion: error
File: ..\..\..\Engine\Gr\Dx9\Dx9Tex.cpp(1414)
App: Gw2.exe 
Pid: 35
Cmdline: 
BaseAddr: 00400000
ProgramId: 101
Build: 14058
When: 2012-12-06T23:58:34Z 2012-12-06T18:58:34-05:00
Uptime:   0 days  0:00:01
Flags: 0

*--> System <--*
Name: john-Studio-XPS
IpAddr: 192.168.1.147
Processors: 8 [GenuineIntel:6:14:5]
OSVersion: Windows 5.1 (64 bit)

*--> System Memory <--*
Physical:  2974MB/ 3943MB  75%
Paged:     6879MB/ 7849MB  87%
Virtual:   4095MB/ 4095MB  100%
Load: 24%

*--> Process Memory <--*
Private:            0MB
WorkingSet:         0MB
PeakWorkingSet:     0MB
PageFaults:         0

*--> Game Context <--*
MapId: 0
Flags: 0x241
ElapsedTime: 00:00:00

*--> World State <--*
<WorldState/> 

[DbgHelp.dll is C:\windows\system32\dbghelp.dll]
[DbgHelp.dll version 5.1.2600.3264 (64/32-bit compatible)]

*--> ClientContextThreadProc Thread 0x35 <--*

*--> Trace <--*
Pc:006a89bd Fr:3135e684 Rt:006a9539 Arg:00000000 00000470 00000002 081050b0 
Pc:006a9539 Fr:3135e6a0 Rt:006a9780 Arg:081050b0 3135e6d4 00000001 00080160 
Pc:006a9780 Fr:3135e6e0 Rt:0067b1af Arg:000003d0 00000001 00000001 00000002 
Pc:0067b1af Fr:3135e70c Rt:0063c475 Arg:000003d0 00000001 00000001 00000002 
Pc:0063c475 Fr:3135e760 Rt:0063f1fd Arg:00000001 00000470 000003d0 08109938 
Pc:0063f1fd Fr:3135e7a0 Rt:0064227e Arg:00000000 00000002 0156d408 00000000 
Pc:0064227e Fr:3135e7dc Rt:00b47ebc Arg:00000002 00000000 00000000 00000000 
Pc:00b47ebc Fr:3135e80c Rt:00b484cd Arg:16d60cb8 080ebc90 00b4851c 16d60cb8 
Pc:00b484cd Fr:3135e86c Rt:00a3687f Arg:00000002 080e3410 16d60ca8 00000002 
Pc:00a3687f Fr:3135e8ac Rt:00a3229d Arg:080e3410 080e3484 080ebb70 000000f8 
Pc:00a3229d Fr:3135e8e4 Rt:00a323eb Arg:00000004 000000f8 00000000 00000000 
Pc:00a323eb Fr:3135e92c Rt:00a32df3 Arg:0084dff2 080ebb90 7bca7000 0084dff2 
Pc:00a32df3 Fr:3135e984 Rt:00a33279 Arg:a9cf3de3 0084dff2 080ebb90 7bca7000 
Pc:00a33279 Fr:3135e9bc Rt:00a33346 Arg:0060a2ff 0084dff2 01b3cac8 00000000 
Pc:00a33346 Fr:3135e9d4 Rt:0084dfcc Arg:080ebb90 a9cf3e53 0084dff2 01b3cac8 
Pc:0084dfcc Fr:3135ea0c Rt:0084e074 Arg:81fbcf10 3135ea28 7bc71d90 01b3cac8 
Pc:0084e074 Fr:3135ea18 Rt:7bc71d90 Arg:01b3cac8 7bca7000 3135eaf8 7bc7486d 
Pc:7bc71d90 Fr:3135ea28 Rt:7bc7486d Arg:0084dff2 01b3cac8 00000000 00110014 
Pc:7bc7486d Fr:3135eaf8 Rt:7bc71d6e Arg:0084dff2 01b3cac8 3135eb18 0084dff2 
Pc:7bc71d6e Fr:3135eb18 Rt:7bc7a748 Arg:0084dff2 01b3cac8 00000000 00000000 
Pc:7bc7a748 Fr:3135f368 Rt:f75ced4c Arg:81fbcfb8 3135fb40 3135fb40 3135fb40 
Pc:f75ced4c Fr:3135f468 Rt:f750bd3e Arg:3135fb40 00000000 00000000 00000000 

*--> Thread registers <--*
eax=7b826255 ebx=7b895000 ecx=00000000 edx=00000000 esi=80000003 edi=00000000
eip=006a89bd esp=3135e674 ebp=3135e684
cs=0023 ss=002b ds=002b es=002b fs=0063 gs=006b efl=00200246

eax-32 7B826234  9000078c 000217e8 37a0ff00 9000078c 
eax-16 7B826244  00020be8 2fa0ff00 9000078c 0001ffe8 
eax +0 7B826254  27a0ff00 9000078c 0001f3e8 1fa0ff00 
eax+16 7B826264  9000078c 0001e7e8 17a0ff00 9000078c 
eax+32 7B826274  0001dbe8 0fa0ff00 9000078c 0001cfe8 
eax+48 7B826284  07a0ff00 9000078c 0001c3e8 ffa0ff00 
ebx-32 7B894FE0  7b850fd0 00000000 f7707b00 7b839dc0 
ebx-16 7B894FF0  00000000 00000000 00000000 00000000 
ebx +0 7B895000  7b894ee8 00000000 00000000 f7444740 
ebx+16 7B895010  f7486d40 f75fffb0 f74fbd30 f75ffc30 
ebx+32 7B895020  f754e440 f7600d40 f74faf30 f7602710 
ebx+48 7B895030  f7602130 f75d5990 f7600010 f76078c0 
esi-32 7FFFFFE0  00000000 00000000 00000000 00000000 
esi-16 7FFFFFF0  00000000 00000000 00000000 00000000 

*--> Code <--*
006A899D  cccccc55 8bec5657 8b7d088b f185ff75 ...U..VW.}.....u
006A89AD  14688605 0000bae8 c11b01b9 00c61b01 .h..............
006A89BD  e8ee8ff6 ff8b4708 8946088b 088b5104 ......G..F....Q.
006A89CD  50ffd281 4e280000 40008b47 28894628 P...N(..@..G(.F(
006A89DD  8b4f1c89 4e1c8b57 20895620 8b472489 .O..N..W .V .G$.
006A89ED  46248b4f 38894e38 8b572c89 562c8b47 F$.O8.N8.W,.V,.G

*--> Stack <--*
3135E674  006a89c2 00000586 081050b0 0810999c ..j......P......
3135E684  3135e6a0 006a9539 00000000 00000470 ..519.j.....p...
3135E694  00000002 081050b0 00000470 3135e6e0 .....P..p.....51
3135E6A4  006a9780 081050b0 3135e6d4 00000001 ..j..P....51....
3135E6B4  00080160 00000000 00000002 00000000 `...............
3135E6C4  0000002e 00000005 00000000 00000470 ............p...
3135E6D4  00000470 000003d0 00000001 3135e70c p.............51
3135E6E4  0067b1af 000003d0 00000001 00000001 ..g.............
3135E6F4  00000002 00000000 00080160 0000002e ........`.......
3135E704  00000005 00080160 3135e760 0063c475 ....`...`.51u.c.
3135E714  000003d0 00000001 00000001 00000002 ................
3135E724  00000000 00080160 00000000 0000002e ....`...........
3135E734  00000005 00000000 081098f0 000003d0 ................
3135E744  07d70528 07d70528 015b6530 015b7cf8 (...(...0e[..|[.
3135E754  3135e768 7bc3512f 00000001 3135e7a0 h.51/Q.{......51
3135E764  0063f1fd 00000001 00000470 000003d0 ..c.....p.......
3135E774  08109938 00000000 00000000 00000000 8...............
3135E784  0000002e 00000005 0000002e 081098f0 ................
3135E794  0156d408 00000002 00000001 3135e7dc ..V...........51
3135E7A4  0064227e 00000000 00000002 0156d408 ~"d...........V.
3135E7B4  00000000 00000001 00000000 00000001 ................
3135E7C4  00000001 0000002e 00000005 00000000 ................
3135E7D4  0805ead0 00000000 3135e80c 00b47ebc ..........51.~..
3135E7E4  00000002 00000000 00000000 00000000 ................
3135E7F4  0805ead0 0000000c 00000000 00000000 ................
3135E804  0136dbd4 00000000 3135e86c 00b484cd ..6.....l.51....
3135E814  16d60cb8 080ebc90 00b4851c 16d60cb8 ................
3135E824  080ebc90 00b16fb6 16d60cb8 00000000 .....o..........
3135E834  00402a2f 080ebb7c 3135e8a0 015b7cf8 /*@.|.....51.|[.
3135E844  0000000b 3135e86c 00a6c9fe 00000000 ....l.51........
3135E854  16d60cb8 00000000 16d60ca8 3135e8ac ..............51
3135E864  00a367aa 00000000 3135e8ac 00a3687f .g........51.h..
3135E874  00000002 080e3410 16d60ca8 00000002 .....4..........
3135E884  00000004 000000f8 3135e8a8 00000000 ..........51....
3135E894  00000001 000000b0 00000000 080ebb7c ............|...
3135E8A4  080e347d 00000000 3135e8e4 00a3229d }4........51."..
3135E8B4  080e3410 080e3484 080ebb70 000000f8 .4...4..p.......
3135E8C4  16d60ca8 00000000 00000000 00000001 ................
3135E8D4  00000000 00000001 3135e8f4 00000000 ..........51....
3135E8E4  3135e92c 00a323eb 00000004 000000f8 ,.51.#..........
3135E8F4  00000000 00000000 00000001 080e3410 .............4..
3135E904  080e36d4 00000000 16d60c90 16d60c90 .6..............
3135E914  00000005 080e36dc 080e36c9 00000004 .....6...6......
3135E924  000000f8 00000001 3135e984 00a32df3 ..........51.-..
3135E934  0084dff2 080ebb90 7bca7000 0084dff2 .........p.{....
3135E944  3135e974 7b844a3e 00bd0394 00168d86 t.51>J.{........
3135E954  00000000 00000065 3135e98c 7b86c1f2 ....e.....51...{
3135E964  00000001 01cdd40d 7b8449f9 7b895000 .........I.{.P.{
3135E974  3135e984 7b844a67 7b844a59 a9cf3ddb ..51gJ.{YJ.{.=..
3135E984  3135e9bc 00a33279 a9cf3de3 0084dff2 ..51y2...=......
3135E994  080ebb90 7bca7000 000010c8 80000003 .....p.{........
3135E9A4  3135e98c 3135ddd0 3135e9fc 0084e130 ..51..51..510...
3135E9B4  99b5ce17 00000000 3135e9d4 00a33346 ..........51F3..
3135E9C4  0060a2ff 0084dff2 01b3cac8 00000000 ..`.............
3135E9D4  3135ea0c 0084dfcc 080ebb90 a9cf3e53 ..51........S>..
3135E9E4  0084dff2 01b3cac8 7bca7000 3135e9e0 .........p.{..51
3135E9F4  3135e9e0 3135ea40 3135ea40 0084e130 ..51@.51@.510...
3135EA04  99b5d7af 00000000 3135ea18 0084e074 ..........51t...
3135EA14  81fbcf10 3135ea28 7bc71d90 01b3cac8 ....(.51...{....
3135EA24  7bca7000 3135eaf8 7bc7486d 0084dff2 .p.{..51mH.{....
3135EA34  01b3cac8 00000000 00110014 ffffffff ................
3135EA44  7bc894d0 7b839dc0 7bca7000 81fbcf10 ...{...{.p.{....
3135EA54  0084dff2 3135eaf8 934e9bc5 760a7f50 ......51..N.P..v
3135EA64  00000000 00000000 00000000 00000000 ................

*--> Error Logs <--*
GetLogicalProcessorInformation failed, increase buffer bytes to 1536
Shader model 3.0 is required 

*--> DirectX Device Info <--*
VendorId    = 0x1002
DeviceId    = 0x9495
Version     = 6.14.0010.8681
Description = ATI Radeon HD 4600 Series
Compat      = 0x00000000
VidMem      = 281 MB


```

The strange parts are:
```

Shader model 3.0 is required

```

I have a Dell laptop with a Radeon HD 4600 which has shader model 4.1

```

VidMem = 281 MB
```

my video card has 1 GB of memory

I am using ubuntu 12.10 with the legacy fglrx drivers installed
Wine version 1.4.1

Any help or suggestions would be appreciated.

---

