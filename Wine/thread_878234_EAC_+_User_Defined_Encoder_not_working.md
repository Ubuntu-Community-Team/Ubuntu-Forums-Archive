---
title: "EAC + User Defined Encoder not working"
date: 2008-08-02
forum: Wine
---

### Post by HonorSystem on 2008-08-02
Hardy 8.04 AMD64

I'm using Wine 1.0 from the official repository.
Also, EAC v0.99 prebeta4.
External encoder I'm using is the generic windows compiled exe of aoTuV's latest libraries for oggenc2 at rarewares.

I have everything set up just how I like it, and I am able to rip CD's no problem.  The problem I have is that the convenience of having EAC encode for me as well as rip does not seem to be working.  Specifically, I tell EAC to call a windows executable located in the wine C drive (aoTuV's oggenc2.exe from rarewares) but when EAC reports that it is calling the external encoder during the rip/encode process, nothing happens and I end up only with a wav file.

I tried running EAC from terminal to see if I could get some verbage with this "error".  Here is what it spits out just as it is calling the external encoder:

```
wine: Unhandled page fault on read access to 0x00000000 at address 0x40a885 (thread 002a), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0040a885).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0040a885 ESP:0033fb80 EBP:0033feb8 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:0081113f ECX:00000000 EDX:00000004
 ESI:006f0410 EDI:00000000
Stack dump:
0x0033fb80:  7bc33dd1 00110048 4b4a4948 0033fe68
0x0033fb90:  0033fe60 0033fe64 0033fe5c 0033fe58
0x0033fba0:  0033fe54 00110048 8b8a8988 f7e6b9cb
0x0033fbb0:  7bc88444 001101e0 7bca2fac 0033fbdc
0x0033fbc0:  7bc5cad4 00000000 00110000 00000002
0x0033fbd0:  7bc88444 00111208 0033fc88 0033fcac
Backtrace:
=>1 0x0040a885 in oggenc2 (+0xa885) (0x0033feb8)
  2 0x0045b1ce in oggenc2 (+0x5b1ce) (0x0033ff08)
  3 0x7b877b27 in kernel32 (+0x57b27) (0x0033ffe8)
0x0040a885: movsbl	0x0(%edi),%edx
Modules:
Module	Address			Debug info	Name (43 modules)
PE	  400000-  6f6000	Export          oggenc2
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e718000-7e721000	Deferred        libxcursor.so.1
ELF	7e721000-7e726000	Deferred        libxfixes.so.3
ELF	7e726000-7e729000	Deferred        libxcomposite.so.1
ELF	7e729000-7e72f000	Deferred        libxrandr.so.2
ELF	7e72f000-7e737000	Deferred        libxrender.so.1
ELF	7e737000-7e73a000	Deferred        libxinerama.so.1
ELF	7e73a000-7e75a000	Deferred        imm32<elf>
  \-PE	7e740000-7e75a000	\               imm32
ELF	7e75a000-7e75f000	Deferred        libxdmcp.so.6
ELF	7e75f000-7e777000	Deferred        libxcb.so.1
ELF	7e777000-7e77a000	Deferred        libxau.so.6
ELF	7e77a000-7e861000	Deferred        libx11.so.6
ELF	7e861000-7e86f000	Deferred        libxext.so.6
ELF	7e86f000-7e874000	Deferred        libxxf86vm.so.1
ELF	7e88c000-7e923000	Deferred        winex11<elf>
  \-PE	7e8a0000-7e923000	\               winex11
ELF	7e930000-7e951000	Deferred        libexpat.so.1
ELF	7e951000-7e97b000	Deferred        libfontconfig.so.1
ELF	7e993000-7e9a8000	Deferred        libz.so.1
ELF	7e9a8000-7ea18000	Deferred        libfreetype.so.6
ELF	7ead7000-7eb29000	Deferred        advapi32<elf>
  \-PE	7eae0000-7eb29000	\               advapi32
ELF	7eb29000-7ebc4000	Deferred        gdi32<elf>
  \-PE	7eb40000-7ebc4000	\               gdi32
ELF	7ebc4000-7ed0b000	Deferred        user32<elf>
  \-PE	7ebe0000-7ed0b000	\               user32
ELF	7ee77000-7ee82000	Deferred        libnss_files.so.2
ELF	7ee82000-7ee8b000	Deferred        libnss_compat.so.2
ELF	7efc3000-7efe8000	Deferred        libm.so.6
ELF	7efe8000-7f000000	Deferred        libnsl.so.1
ELF	f7cd0000-f7cd2000	Deferred        libxcb-xlib.so.0
ELF	f7cd2000-f7cdc000	Deferred        libnss_nis.so.2
ELF	f7cdf000-f7ce3000	Deferred        libdl.so.2
ELF	f7ce3000-f7e32000	Deferred        libc.so.6
ELF	f7e33000-f7e4b000	Deferred        libpthread.so.0
ELF	f7e63000-f7f99000	Deferred        libwine.so.1
ELF	f7f9b000-f7fba000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000022    0
	0000001d   15
	0000001c   15
	00000019    0
	00000018    0
0000000c 
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
00000024 
	0000001e    0
	00000025    2
	00000047    0
	00000043    0
	00000046    0
	0000002f    0
	00000030    2
	00000028    2
	00000027    0
	00000026    0
0000003e 
	0000002c    0
	00000013    2
	00000040    0
	00000037    0
	00000033    0
	0000000b    0
	00000023    2
	00000029    2
	0000003a    0
	00000031    0
00000032 (D) C:\Program Files\aoTuV\oggenc2.exe
	0000002a    0 <==
Backtrace:
=>1 0x0040a885 in oggenc2 (+0xa885) (0x0033feb8)
  2 0x0045b1ce in oggenc2 (+0x5b1ce) (0x0033ff08)
  3 0x7b877b27 in kernel32 (+0x57b27) (0x0033ffe8)
```

Any help would be much appreciated.  Btw, I've tried setting EAC to not open an external compressor window, and to not start external compressors in the background, but the same thing happens.

---

