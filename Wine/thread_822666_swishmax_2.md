---
title: "swishmax 2"
date: 2008-06-08
forum: Wine
---

### Post by Grone1985 on 2008-06-08
Hi everyone,
I'm trying to get SwishMax 2 (A flash editor program) working on wine but after the install I get this error...

```
wine: Unhandled page fault on execute access to 0x7c801d77 at address 0x7c801d77 (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x7c801d77 in 32-bit code (0x7c801d77).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7c801d77 ESP:0032fd34 EBP:0032fd44 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000001 EBX:00000002 ECX:00d2b862 EDX:00079b00
 ESI:00928000 EDI:00b2fabc
Stack dump:
0x0032fd34:  00d2b5ec 00a42d74 00d09862 00906000
0x0032fd44:  0032fd58 00d095ec 00a42d74 00d06862
0x0032fd54:  00903000 0032fd6c 00d065ec 00a42d74
0x0032fd64:  00079b00 00d065a6 0032fd84 00750422
0x0032fd74:  00a42d74 00b66da0 00000000 7b8b2888
0x0032fd84:  0032fdd8 0074f233 00a42d74 00a42e68
Backtrace:
=>1 0x7c801d77 (0x0032fd44)
  2 0x00d095ec in swishmax2 (+0x9095ec) (0x0032fd58)
  3 0x00d065ec in swishmax2 (+0x9065ec) (0x0032fd6c)
  4 0x00750422 in swishmax2 (+0x350422) (0x0032fd84)
  5 0x0074f233 in swishmax2 (+0x34f233) (0x0032fdd8)
  6 0x007ce327 in swishmax2 (+0x3ce327) (0x0032ff08)
  7 0x7b876367 in kernel32 (+0x56367) (0x0032ffe8)
  8 0xf7e0ea07 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7c801d77: -- no code accessible --
Modules:
Module	Address			Debug info	Name (104 modules)
PE	  400000-  d35000	Export          swishmax2
ELF	7b800000-7b92c000	Export          kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7deea000-7deee000	Deferred        libgpg-error.so.0
ELF	7deee000-7df3b000	Deferred        libgcrypt.so.11
ELF	7df3b000-7df4b000	Deferred        libtasn1.so.3
ELF	7df4b000-7df4e000	Deferred        libkeyutils.so.1
ELF	7df4e000-7df56000	Deferred        libkrb5support.so.0
ELF	7df56000-7df88000	Deferred        libcrypt.so.1
ELF	7df88000-7dffd000	Deferred        libgnutls.so.13
ELF	7dffd000-7e020000	Deferred        libk5crypto.so.3
ELF	7e020000-7e0ad000	Deferred        libkrb5.so.3
ELF	7e0ad000-7e0d6000	Deferred        libgssapi_krb5.so.2
ELF	7e0d6000-7e109000	Deferred        libcups.so.2
ELF	7e163000-7e195000	Deferred        uxtheme<elf>
  \-PE	7e170000-7e195000	\               uxtheme
ELF	7e195000-7e1a9000	Deferred        midimap<elf>
  \-PE	7e1a0000-7e1a9000	\               midimap
ELF	7e1a9000-7e1c0000	Deferred        msacm32<elf>
  \-PE	7e1b0000-7e1c0000	\               msacm32
ELF	7e1c0000-7e1fb000	Deferred        wineoss<elf>
  \-PE	7e1d0000-7e1fb000	\               wineoss
ELF	7e1fb000-7e204000	Deferred        libxcursor.so.1
ELF	7e204000-7e209000	Deferred        libxfixes.so.3
ELF	7e209000-7e20c000	Deferred        libxcomposite.so.1
ELF	7e20c000-7e212000	Deferred        libxrandr.so.2
ELF	7e212000-7e21a000	Deferred        libxrender.so.1
ELF	7e21a000-7e21d000	Deferred        libxinerama.so.1
ELF	7e21d000-7e222000	Deferred        libxdmcp.so.6
ELF	7e222000-7e23a000	Deferred        libxcb.so.1
ELF	7e23a000-7e23c000	Deferred        libxcb-xlib.so.0
ELF	7e23c000-7e23f000	Deferred        libxau.so.6
ELF	7e23f000-7e326000	Deferred        libx11.so.6
ELF	7e326000-7e334000	Deferred        libxext.so.6
ELF	7e334000-7e339000	Deferred        libxxf86vm.so.1
ELF	7e345000-7e348000	Deferred        libcom_err.so.2
ELF	7e34a000-7e3db000	Deferred        winex11<elf>
  \-PE	7e360000-7e3db000	\               winex11
ELF	7e416000-7e437000	Deferred        libexpat.so.1
ELF	7e437000-7e461000	Deferred        libfontconfig.so.1
ELF	7e461000-7e476000	Deferred        libz.so.1
ELF	7e476000-7e4e6000	Deferred        libfreetype.so.6
ELF	7e4e6000-7e507000	Deferred        mpr<elf>
  \-PE	7e4f0000-7e507000	\               mpr
ELF	7e507000-7e555000	Deferred        wininet<elf>
  \-PE	7e510000-7e555000	\               wininet
ELF	7e555000-7e594000	Deferred        urlmon<elf>
  \-PE	7e560000-7e594000	\               urlmon
ELF	7e594000-7e63d000	Deferred        comdlg32<elf>
  \-PE	7e5a0000-7e63d000	\               comdlg32
ELF	7e63d000-7e669000	Deferred        ws2_32<elf>
  \-PE	7e640000-7e669000	\               ws2_32
ELF	7e669000-7e69f000	Deferred        winspool<elf>
  \-PE	7e670000-7e69f000	\               winspool
ELF	7e69f000-7e6f8000	Deferred        shlwapi<elf>
  \-PE	7e6b0000-7e6f8000	\               shlwapi
ELF	7e6f8000-7e802000	Deferred        shell32<elf>
  \-PE	7e710000-7e802000	\               shell32
ELF	7e802000-7e8a4000	Deferred        oleaut32<elf>
  \-PE	7e810000-7e8a4000	\               oleaut32
ELF	7e8a4000-7e8c3000	Deferred        imm32<elf>
  \-PE	7e8b0000-7e8c3000	\               imm32
ELF	7e8c3000-7e90d000	Deferred        dsound<elf>
  \-PE	7e8d0000-7e90d000	\               dsound
ELF	7e90d000-7e920000	Deferred        libresolv.so.2
ELF	7e931000-7e94f000	Deferred        iphlpapi<elf>
  \-PE	7e940000-7e94f000	\               iphlpapi
ELF	7e94f000-7e9af000	Deferred        rpcrt4<elf>
  \-PE	7e960000-7e9af000	\               rpcrt4
ELF	7e9af000-7ea53000	Deferred        ole32<elf>
  \-PE	7e9c0000-7ea53000	\               ole32
ELF	7ea53000-7eb12000	Deferred        comctl32<elf>
  \-PE	7ea60000-7eb12000	\               comctl32
ELF	7eb12000-7eb26000	Deferred        lz32<elf>
  \-PE	7eb20000-7eb26000	\               lz32
ELF	7eb26000-7eb3f000	Deferred        version<elf>
  \-PE	7eb30000-7eb3f000	\               version
ELF	7eb3f000-7eb67000	Deferred        msvfw32<elf>
  \-PE	7eb50000-7eb67000	\               msvfw32
ELF	7eb67000-7ec02000	Deferred        gdi32<elf>
  \-PE	7eb80000-7ec02000	\               gdi32
ELF	7ec02000-7ed48000	Deferred        user32<elf>
  \-PE	7ec20000-7ed48000	\               user32
ELF	7ed48000-7edd6000	Deferred        winmm<elf>
  \-PE	7ed50000-7edd6000	\               winmm
ELF	7edd6000-7edfc000	Deferred        msacm32<elf>
  \-PE	7ede0000-7edfc000	\               msacm32
ELF	7edfc000-7ee36000	Deferred        avifil32<elf>
  \-PE	7ee00000-7ee36000	\               avifil32
ELF	7ee36000-7ee87000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee87000	\               advapi32
ELF	7efa7000-7efb2000	Deferred        libnss_files.so.2
ELF	7efb2000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	f7c80000-f7c89000	Deferred        libnss_compat.so.2
ELF	f7c8a000-f7c8e000	Deferred        libdl.so.2
ELF	f7c8e000-f7ddd000	Deferred        libc.so.6
ELF	f7dde000-f7df6000	Deferred        libpthread.so.0
ELF	f7e07000-f7f1c000	Export          libwine.so.1
ELF	f7f1e000-f7f3d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\SWiSH Max2\SwishMax2.exe
	00000009    0 <==
0000000c 
	00000017    0
	00000016    0
	00000013    0
	00000010    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000014    0
	00000012    0
Backtrace:
=>1 0x7c801d77 (0x0032fd44)
  2 0x00d095ec in swishmax2 (+0x9095ec) (0x0032fd58)
  3 0x00d065ec in swishmax2 (+0x9065ec) (0x0032fd6c)
  4 0x00750422 in swishmax2 (+0x350422) (0x0032fd84)
  5 0x0074f233 in swishmax2 (+0x34f233) (0x0032fdd8)
  6 0x007ce327 in swishmax2 (+0x3ce327) (0x0032ff08)
  7 0x7b876367 in kernel32 (+0x56367) (0x0032ffe8)
  8 0xf7e0ea07 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

Please help! Thanks in advance!

---

### Post by Grone1985 on 2008-06-10
Anyone please?
Got no luck figuring it out on my own... A little more information on my system just in case it helps...

Amd - Ubuntu Hardy 64x
Wine 0.9.59 - Clean install.

Thanks in advance!

---

### Post by squinter on 2009-01-18
Hi, 

I'm able to install and run Swish Max 2 trial version under Ubuntu 8.10 with Wine 1.01. I seem to be able to do everything but export it to SWF or anything else than save it as SWI (Swish file format).

So closed :( *sigh*

My error is:

Fault occured in: C:\Program Files\SWiSH Max2\SwishMax2.exe
Fault occured at: Sunday, January 18, 2009 09:14:50 GMT
SWiSHmax2 Build: 2008.08.12
Operating System: Windows 2000 With Service Pack 4

Free Windows Resources: Sys=100% Gdi=100% Usr=100%
Memory in use: 65% in use
Physical Memory: 347 MB free of 1009 MB total
Paging File: 1036 MB free of 1705 MB total
Virtual Memory: 2047 MB free of 2047MB total

Exception code: C0000005 ACCESS_VIOLATION
Fault address:  00536DA1 01:00135DA1
in module: C:\Program Files\SWiSH Max2\SwishMax2.exe

Registers:
EAX:00000000
EBX:00000000
ECX:00000000
EDX:00BCC034
ESI:00329A3C
EDI:012256B8
CS:EIP:0073:00536DA1
SS:ESP:007B:00323AF8  EBP:00323BB4
DS:007B  ES:007B  FS:0033  GS:003B
Flags:00210246

IntelStackWalk : Call stack:
Address   Frame     Logical addr  Module
00536DA1  00323BB4  0001:00135DA1 C:\Program Files\SWiSH Max2\SwishMax2.exe
005397BF  00323C10  0001:001387BF C:\Program Files\SWiSH Max2\SwishMax2.exe
004A012C  0032F9F0  0001:0009F12C C:\Program Files\SWiSH Max2\SwishMax2.exe
006CC5F4  0032FA1C  0001:002CB5F4 C:\Program Files\SWiSH Max2\SwishMax2.exe
0098392A  0032FA2C  0001:0058292A C:\Program Files\SWiSH Max2\SwishMax2.exe
00983B0D  0032FA5C  0001:00582B0D C:\Program Files\SWiSH Max2\SwishMax2.exe
0098A7CA  0032FA78  0001:005897CA C:\Program Files\SWiSH Max2\SwishMax2.exe
0098D3E8  0032FAAC  0001:0058C3E8 C:\Program Files\SWiSH Max2\SwishMax2.exe
0099AAE9  0032FAE0  0001:00599AE9 C:\Program Files\SWiSH Max2\SwishMax2.exe
---End-of-Error-Report---

---

### Post by waterboy0911 on 2010-10-27
is this functional already with the new wine version?

what's the update for this?

---

