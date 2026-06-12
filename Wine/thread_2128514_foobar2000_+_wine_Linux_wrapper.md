---
title: "foobar2000 + wine Linux wrapper"
date: 2013-03-23
forum: Wine
---

### Post by BeZet on 2013-03-23
Hello fellow Ubuntians,

Some of you might be fans of foobar2000 and perhaps run it in Ubuntu using Wine.

Here's a "wrapper" written in Bash that can help you integrate this music player more easily into your system:

[https://github.com/MaciekBaron/linux-foobar2000-wrapper](https://github.com/MaciekBaron/linux-foobar2000-wrapper)

I hope someone will find it useful.

Cheers

Maciej

---

### Post by kamelie1706 on 2013-12-14
Hi,

trying to install latest version of foobar2000 (1.2.9) with wine but without success:
- I downloaded here 
[http://www.foobar2000.org/download](http://www.foobar2000.org/download)
- wine version is 1.7.6
- lubuntu 13.10

When I execute the installation file with wine I get the following:
**********************************
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7d72f0f8).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d72f0f8 ESP:0033f610 EBP:0033f688 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7d754000 ECX:0033f66c EDX:0042ae74
 ESI:0013af24 EDI:0013af20
Stack dump:
0x0033f610:  00437bc0 0033f660 0033f65c 7d737df8
0x0033f620:  f73b24e7 0033f6cc 7d754000 7d737df8
0x0033f630:  0013af24 0042b3b8 00000010 7d737cc0
0x0033f640:  0013af20 00000001 0000002b 00437bc0
0x0033f650:  0000c04e 00000000 0033f680 004383b4
0x0033f660:  00000000 00437bb8 0033f688 0013af20
000c: sel=0067 base=00000000 limit=00000000 32-bit --x
Backtrace:
=>0 0x7d72f0f8 in ieframe (+0x1f0f8) (0x0033f688)
  1 0x0041761b in bisetup45605 (+0x1761a) (0x004383b4)
  2 0x0042adb4 in bisetup45605 (+0x2adb3) (0x0013af20)
  3 0x7d753920 in ieframe (+0x4391f) (0x7d753d60)
  4 0x7d736bc0 in ieframe (+0x26bbf) (0x7d737d80)
  5 0xfff0e483 (0x04244c8d)
0x7d72f0f8: movl    0x0(%eax),%edx
Modules:
Module    Address            Debug info    Name (100 modules)
PE      400000-  445000    Export          bisetup45605
ELF    7b800000-7ba5b000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7bc00000-7bce4000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bce4000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d660000-7d702000    Deferred        urlmon<elf>
  \-PE    7d670000-7d702000    \               urlmon
ELF    7d702000-7d776000    Dwarf           ieframe<elf>
  \-PE    7d710000-7d776000    \               ieframe
ELF    7d83c000-7d861000    Deferred        imm32<elf>
  \-PE    7d840000-7d861000    \               imm32
ELF    7d861000-7d931000    Deferred        crypt32<elf>
  \-PE    7d870000-7d931000    \               crypt32
ELF    7d931000-7d973000    Deferred        rsaenh<elf>
  \-PE    7d940000-7d973000    \               rsaenh
ELF    7d9b9000-7d9c2000    Deferred        librt.so.1
ELF    7d9c2000-7d9c7000    Deferred        libgpg-error.so.0
ELF    7d9c7000-7d9de000    Deferred        libresolv.so.2
ELF    7d9de000-7d9e2000    Deferred        libkeyutils.so.1
ELF    7d9e2000-7da2d000    Deferred        libdbus-1.so.3
ELF    7da2d000-7da4c000    Deferred        libp11-kit.so.0
ELF    7da4c000-7da5e000    Deferred        libtasn1.so.3
ELF    7da5e000-7dae2000    Deferred        libgcrypt.so.11
ELF    7dae2000-7db0a000    Deferred        libk5crypto.so.3
ELF    7db0a000-7dbd9000    Deferred        libkrb5.so.3
ELF    7dbd9000-7dbeb000    Deferred        libavahi-client.so.3
ELF    7dbeb000-7dcb1000    Deferred        libgnutls.so.26
ELF    7dcb1000-7dcee000    Deferred        libgssapi_krb5.so.2
ELF    7dcee000-7dd5a000    Deferred        libcups.so.2
ELF    7dd68000-7dd7b000    Deferred        gnome-keyring-pkcs11.so
ELF    7dd7b000-7ddb1000    Deferred        uxtheme<elf>
  \-PE    7dd80000-7ddb1000    \               uxtheme
ELF    7ddb1000-7ddb7000    Deferred        libxfixes.so.3
ELF    7ddb7000-7ddc2000    Deferred        libxcursor.so.1
ELF    7ddc2000-7ddd3000    Deferred        libxi.so.6
ELF    7ddd3000-7ddd7000    Deferred        libxcomposite.so.1
ELF    7ddd7000-7dde2000    Deferred        libxrandr.so.2
ELF    7dde2000-7dded000    Deferred        libxrender.so.1
ELF    7dded000-7ddf3000    Deferred        libxxf86vm.so.1
ELF    7ddf3000-7ddf7000    Deferred        libxinerama.so.1
ELF    7ddf7000-7ddfe000    Deferred        libxdmcp.so.6
ELF    7ddfe000-7de02000    Deferred        libxau.so.6
ELF    7de02000-7de23000    Deferred        libxcb.so.1
ELF    7de23000-7df58000    Deferred        libx11.so.6
ELF    7df58000-7df6b000    Deferred        libxext.so.6
ELF    7df6e000-7df77000    Deferred        libkrb5support.so.0
ELF    7df77000-7df7c000    Deferred        libcom_err.so.2
ELF    7df7c000-7df8a000    Deferred        libavahi-common.so.3
ELF    7df8c000-7e01f000    Deferred        winex11<elf>
  \-PE    7dfa0000-7e01f000    \               winex11
ELF    7e06a000-7e093000    Deferred        libexpat.so.1
ELF    7e093000-7e0cd000    Deferred        libfontconfig.so.1
ELF    7e0cd000-7e16c000    Deferred        libfreetype.so.6
ELF    7e18d000-7e1a6000    Deferred        userenv<elf>
  \-PE    7e190000-7e1a6000    \               userenv
ELF    7e1a6000-7e2dc000    Deferred        oleaut32<elf>
  \-PE    7e1c0000-7e2dc000    \               oleaut32
ELF    7e2dc000-7e35f000    Deferred        rpcrt4<elf>
  \-PE    7e2f0000-7e35f000    \               rpcrt4
ELF    7e35f000-7e49d000    Deferred        ole32<elf>
  \-PE    7e380000-7e49d000    \               ole32
ELF    7e49d000-7e4e0000    Deferred        winspool<elf>
  \-PE    7e4a0000-7e4e0000    \               winspool
ELF    7e4e0000-7e5e7000    Deferred        comctl32<elf>
  \-PE    7e4f0000-7e5e7000    \               comctl32
ELF    7e5e7000-7e6d2000    Deferred        comdlg32<elf>
  \-PE    7e5f0000-7e6d2000    \               comdlg32
ELF    7e6d2000-7e6f8000    Deferred        iphlpapi<elf>
  \-PE    7e6e0000-7e6f8000    \               iphlpapi
ELF    7e6f8000-7e70c000    Deferred        psapi<elf>
  \-PE    7e700000-7e70c000    \               psapi
ELF    7e70c000-7e93f000    Deferred        shell32<elf>
  \-PE    7e720000-7e93f000    \               shell32
ELF    7e93f000-7e9b9000    Deferred        shlwapi<elf>
  \-PE    7e950000-7e9b9000    \               shlwapi
ELF    7e9b9000-7ea2b000    Deferred        advapi32<elf>
  \-PE    7e9d0000-7ea2b000    \               advapi32
ELF    7ea2b000-7eb48000    Deferred        gdi32<elf>
  \-PE    7ea40000-7eb48000    \               gdi32
ELF    7eb48000-7eca3000    Deferred        user32<elf>
  \-PE    7eb60000-7eca3000    \               user32
ELF    7eca3000-7eccb000    Deferred        mpr<elf>
  \-PE    7ecb0000-7eccb000    \               mpr
ELF    7eccb000-7ece5000    Deferred        libz.so.1
ELF    7ece5000-7ed61000    Deferred        wininet<elf>
  \-PE    7ecf0000-7ed61000    \               wininet
ELF    7ed61000-7ed6e000    Deferred        libnss_files.so.2
ELF    7ed6e000-7ed7a000    Deferred        libnss_nis.so.2
ELF    7ed7a000-7ed93000    Deferred        libnsl.so.1
ELF    7ed93000-7ed9c000    Deferred        libnss_compat.so.2
ELF    7ef9c000-7efdf000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7333000-f74e7000    Deferred        libc.so.6
ELF    f74e7000-f74ec000    Deferred        libdl.so.2
ELF    f74ed000-f7508000    Deferred        libpthread.so.0
ELF    f7529000-f76de000    Dwarf           libwine.so.1
ELF    f76e0000-f7702000    Deferred        ld-linux.so.2
ELF    f7702000-f7703000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000020    0
    0000001f    0
    0000001d    0
    0000001c    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000017    0
    00000013    0
00000019 plugplay.exe
    00000021    0
    0000001e    0
    0000001a    0
00000022 explorer.exe
    00000023    0
0000002a (D) C:\users\cyril\Temp\nsd2359.tmp\biSetup45605.exe
    0000002b    0 <==
System information:
    Wine build: wine-1.7.6
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.11.0-13-generic
**********************************

Any idea ... seems people can usually install it

One detail, I am running 64bits version

---

### Post by kamelie1706 on 2013-12-14
Hi,

I was actually downloading the wrong file from foobar server .... but now wine is say "Windows XP SP2 or later needed to run foobar2000" ....

---

### Post by oldos2er on 2013-12-14
Moved to Wine.

---

### Post by kamelie1706 on 2013-12-14
Story continue .... I managed to actually install it with "playonlinux" as probably my wine settings are screwed.

Now I can launch the program, start to read a file for few seconds and then crash
*************************
Illegal operation:
Code: C0000005h, flags: 00000000h, address: F6BBEF38h
Access violation, operation: read, address: F6BBEF38h
Last win32 error: 6


Call path not available.


Stack (025AE9A4h):
025AE984h:  F6BD26F0 025AE9D8 F6BBEF38 F6BD26F0
025AE994h:  F6BD2000 F6BBDDB5 F6BBEF38 00000134
025AE9A4h:  025AE9BC 00000000 018FF8B7 00000000
025AE9B4h:  00000000 025AEA5C 00000000 00000000
025AE9C4h:  00000000 00000029 025AE9F0 7BCC7000
025AE9D4h:  81FE4000 025AE9F8 7BC7F9C0 00000000
025AE9E4h:  00000000 4D430000 7BC7F9C0 00000000
025AE9F4h:  7BCC7000 025AEAC8 7BC8294D F6BBEEA0
025AEA04h:  00000000 025AEAB8 DCA7CFDE FFFFFFFF
025AEA14h:  7BC97060 7B83B520 7BCC7000 81FE4000
025AEA24h:  81FE4FB8 025AEAC8 DCA12FDE F9276B2D
025AEA34h:  00000000 025AEA60 7BCC7000 00000008
025AEA44h:  7BCCFD00 025AEAB8 7BC53EDA 00000000
025AEA54h:  F749B645 7BCC7000 7BC53F4F 00184D83
025AEA64h:  00000000 00000000 C30807F8 01CEF906
025AEA74h:  00000000 000001C3 7BC3CBCB 00000000
025AEA84h:  00000000 7BCA11AC 7BC3CCB9 00184970
025AEA94h:  00000001 00184D88 00000003 025AEAC0
025AEAA4h:  7BCC7000 025AEAE8 7BC56C43 00143D40
025AEAB4h:  7BCE2DFC 025AEAE8 7BC56C43 7BC828D9


Registers:
EAX: 00000000, EBX: F6BD2000, ECX: 025AE9A0, EDX: C0000008
ESI: F6BD26F0, EDI: 81FE4FB8, EBP: 025AE9D8, ESP: 025AE9A4


Unable to identify crash location!


Loaded modules:
winealsa                         loaded at F6630000h - F665C000h
mmdevapi                         loaded at F6BE0000h - F6BF5000h
usp10                            loaded at F7160000h - F719D000h
foo_converter                    loaded at 018C0000h - 0193F000h
foo_freedb2                      loaded at 01760000h - 017AE000h
foo_unpack                       loaded at 01620000h - 0164F000h
foo_cdda                         loaded at 014C0000h - 0150F000h
foo_rgscan                       loaded at 01360000h - 013AC000h
avutil-fb2k-52                   loaded at 635C0000h - 635F9000h
avcodec-fb2k-54                  loaded at 6F080000h - 6F322000h
winmm                            loaded at F71A0000h - F7255000h
msacm32                          loaded at F7260000h - F7280000h
foo_input_std                    loaded at 00FC0000h - 01132000h
foo_dsp_std                      loaded at 00E70000h - 00EA6000h
foo_fileops                      loaded at 00D10000h - 00D5A000h
foo_albumlist                    loaded at 00380000h - 003DC000h
msimg32                          loaded at F7290000h - F7294000h
foo_ui_std                       loaded at 00A00000h - 00AE9000h
foo_dsp_eq                       loaded at 00340000h - 00376000h
imm32                            loaded at F72A0000h - F72B9000h
winex11                          loaded at 7DB60000h - 7DBE2000h
winhttp                          loaded at 7DE30000h - 7DE67000h
oleaut32                         loaded at 7DE80000h - 7DF9D000h
gdiplus                          loaded at 7DFB0000h - 7E028000h
ws2_32                           loaded at 7E030000h - 7E05F000h
iphlpapi                         loaded at 7E070000h - 7E085000h
netapi32                         loaded at 7E090000h - 7E0B2000h
secur32                          loaded at 7E0C0000h - 7E0E5000h
crypt32                          loaded at 7E0F0000h - 7E1B5000h
winspool                         loaded at 7E1C0000h - 7E1F8000h
comdlg32                         loaded at 7E200000h - 7E2E3000h
psapi                            loaded at 7E430000h - 7E437000h
dbghelp                          loaded at 7E2F0000h - 7E34B000h
imagehlp                         loaded at 7E480000h - 7E48C000h
shared                           loaded at 10000000h - 1002B000h
msvcrt                           loaded at 7E360000h - 7E3F4000h
zlib1                            loaded at 62E80000h - 62E9F000h
shell32                          loaded at 7E4A0000h - 7E6BF000h
uxtheme                          loaded at 7E6D0000h - 7E6F5000h
shlwapi                          loaded at 7E700000h - 7E76F000h
rpcrt4                           loaded at 7E780000h - 7E7F2000h
ole32                            loaded at 7E810000h - 7E930000h
dsound                           loaded at 7E940000h - 7E979000h
version                          loaded at 7EFF0000h - 7F000000h
advapi32                         loaded at 7E990000h - 7E9EB000h
gdi32                            loaded at 7EA00000h - 7EB08000h
user32                           loaded at 7EB20000h - 7EC63000h
comctl32                         loaded at 7EC70000h - 7ED6A000h
kernel32                         loaded at 7B810000h - 7BA5B000h
ntdll                            loaded at 7BC10000h - 7BCE4000h
foobar2000                       loaded at 00400000h - 005BF000h


Stack dump analysis:
Address: 018FF8B7h (foo_converter+3F8B7h)
Address: 7BCC7000h (ntdll+B7000h)
Address: 7BC7F9C0h (ntdll+6F9C0h), symbol: "call_thread_func_wrapper" (+Ch)
Address: 7BC7F9C0h (ntdll+6F9C0h), symbol: "call_thread_func_wrapper" (+Ch)
Address: 7BCC7000h (ntdll+B7000h)
Address: 7BC8294Dh (ntdll+7294Dh), symbol: "call_thread_func" (+7Dh)
Address: 7BC97060h (ntdll+87060h)
Address: 7B83B520h (kernel32+2B520h), symbol: "UnhandledExceptionFilter" (+0h)
Address: 7BCC7000h (ntdll+B7000h)
Address: 7BCC7000h (ntdll+B7000h)
Address: 7BCCFD00h (ntdll+BFD00h)
Address: 7BC53EDAh (ntdll+43EDAh), symbol: "call_dll_entry_point" (+EAh)
Address: F749B645h (libc.so.6+137645h)
Address: 7BCC7000h (ntdll+B7000h)
Address: 7BC53F4Fh (ntdll+43F4Fh), symbol: "call_dll_entry_point" (+15Fh)
Address: 7BC3CBCBh (ntdll+2CBCBh), symbol: "RtlEnterCriticalSection" (+1Bh)
Address: 7BCA11ACh (ntdll+911ACh)
Address: 7BC3CCB9h (ntdll+2CCB9h), symbol: "RtlLeaveCriticalSection" (+19h)
Address: 7BCC7000h (ntdll+B7000h)
Address: 7BC56C43h (ntdll+46C43h)
Address: 7BCE2DFCh (ntdll+D2DFCh)
Address: 7BC56C43h (ntdll+46C43h)
Address: 7BC828D9h (ntdll+728D9h), symbol: "call_thread_func" (+9h)
Address: 7BCC7000h (ntdll+B7000h)
Address: 7BC7F99Eh (ntdll+6F99Eh), symbol: "RtlRaiseException" (+22h)
Address: 7BCC7000h (ntdll+B7000h)
Address: 7BC88F8Eh (ntdll+78F8Eh)
Address: F7536000h (libpthread.so.0+18000h), symbol: "_GLOBAL_OFFSET_TABLE_" (+0h)
Address: F7524D78h (libpthread.so.0+6D78h), symbol: "start_thread" (+D8h)
Address: F7536000h (libpthread.so.0+18000h), symbol: "_GLOBAL_OFFSET_TABLE_" (+0h)
Address: 003D0F00h (foo_albumlist+50F00h)
Address: F7524CA0h (libpthread.so.0+6CA0h), symbol: "start_thread" (+0h)
Address: 003D0F00h (foo_albumlist+50F00h)
Address: F745601Eh (libc.so.6+F201Eh), symbol: "clone" (+5Eh)


Environment:
App: foobar2000 v1.2.9
UI: Default User Interface 0.9.5


Components:
Core (2013-07-10 12:45:36 UTC)
    foobar2000 core 1.2.9
foo_albumlist.dll (2013-02-11 11:28:58 UTC)
    Album List 4.5
foo_cdda.dll (2013-03-07 09:48:32 UTC)
    CD Audio Decoder 3.0
foo_converter.dll (2013-07-10 12:25:32 UTC)
    Converter 1.5
foo_dsp_eq.dll (2013-02-11 11:28:58 UTC)
    Equalizer 1.0
foo_dsp_std.dll (2013-07-10 12:25:50 UTC)
    Standard DSP Array 1.3
foo_fileops.dll (2013-02-11 11:28:10 UTC)
    File Operations 2.2
foo_freedb2.dll (2013-02-11 11:27:56 UTC)
    Online Tagger 0.7
foo_input_std.dll (2013-07-10 12:45:38 UTC)
    Standard Input Array 1.0
foo_rgscan.dll (2013-07-10 12:25:36 UTC)
    ReplayGain Scanner 2.2
foo_ui_std.dll (2013-07-10 12:45:36 UTC)
    Default User Interface 0.9.5
foo_unpack.dll (2013-02-11 11:28:10 UTC)
    ZIP/GZIP/RAR Reader 1.6


Recent events:
No main configuration file found.
RegisterShellHookWindow failure
Watching: C:\users\XXXX\My Music
Album List refreshed in: 0:00.000326
Startup time : 0:00.222073
Opening track for playback: "C:\users\XXXX\XXXX"




Machine specifications:
OS: wine-1.7.6, on: Linux / 3.11.0-13-generic
CPU: AMD Phenom(tm) II X2 550 Processor, features: 3DNow!ex MMX SSE SSE2 SSE3
Audio: Out: default; Out: HDA ATI SB - ALC892 Analog; Out: HDA ATI HDMI - HDMI 0; Out: HDA ATI SB - ALC892 Digital
**************************

---

### Post by kamelie1706 on 2013-12-14
Seems problem was temporary and not everything was setup properly (audio service?) .... after reboot everything works fine. Next steps I will try to make pulse / rygel solution working :-)

---

