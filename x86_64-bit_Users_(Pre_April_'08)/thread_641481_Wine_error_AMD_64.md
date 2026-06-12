---
title: "Wine error AMD 64"
date: 2007-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by adt41287 on 2007-12-15
Im getting a nasty error when i try to run WoW.exe in wine.  I just cant make anysense of the errors can someone help? heres what i get in terminal

```
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
wine: Unhandled page fault on execute access to 0x10035a21 at address 0x10035a21 (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x10035a21 in 32-bit code (0x10035a21).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:10035a21 ESP:0034fd5c EBP:0034fd78 EFLAGS:00010216(   - 00      -RIAP1)
 EAX:10035a21 EBX:7bc87b24 ECX:10000000 EDX:00000001
 ESI:00000001 EDI:00111700
Stack dump:
0x0034fd5c:  7bc43f55 10000000 00000001 00000001
0x0034fd6c:  7bc45f94 008e9520 7bc87b24 0034fe08
0x0034fd7c:  7bc4592d 10035a21 10000000 00000001
0x0034fd8c:  00000001 f7cd486d 00000001 00000000
0x0034fd9c:  0034fdec 7bc87b24 00111870 00000001
0x0034fdac:  10035a21 10000000 00111110 0034fe08
Backtrace:
=>1 0x10035a21 EntryPoint() in divxdecoder (0x0034fd78)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
  2 0x7bc4592d MODULE_InitDLL+0x8d(wm=<register EDI not in topmost frame>, reason=<register ESI not in topmost frame>, lpReserved=0x1) [/home/adam/wine-0.9.51/dlls/ntdll/loader.c:909] in ntdll (0x0034fe08)
  3 0x7bc45f94 process_attach+0x174(wm=<register EDI not in topmost frame>, lpReserved=0x1) [/home/adam/wine-0.9.51/dlls/ntdll/loader.c:982] in ntdll (0x0034fe58)
  4 0x7bc45ec2 process_attach+0xa2(wm=<register EDI not in topmost frame>, lpReserved=0x1) [/home/adam/wine-0.9.51/dlls/ntdll/loader.c:974] in ntdll (0x0034fea8)
  5 0x7bc48b8a LdrInitializeThunk+0x2ba(unknown1=0x0, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/home/adam/wine-0.9.51/dlls/ntdll/loader.c:1027] in ntdll (0x0034ff08)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value __wine_dbch___default (1)
  6 0x7b87615a start_process+0xba(arg=0x0) [/home/adam/wine-0.9.51/dlls/kernel32/process.c:829] in kernel32 (0x0034ffe8)
  7 0xf7e14957 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x10035a21 EntryPoint in divxdecoder: pushl     %ebp
Modules:
Module  Address                 Debug info      Name (88 modules)
PE        400000-  e65000       Deferred        wow
PE      10000000-10069000       Export          divxdecoder
ELF     7b800000-7b92b000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7bc00000-7bca3000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cd4a000-7cd7c000       Deferred        uxtheme<elf>
  \-PE  7cd50000-7cd7c000       \               uxtheme
ELF     7cd9c000-7ce62000       Deferred        libasound.so.2
ELF     7d11e000-7d133000       Deferred        midimap<elf>
  \-PE  7d120000-7d133000       \               midimap
ELF     7d133000-7d14b000       Deferred        msacm32<elf>
  \-PE  7d140000-7d14b000       \               msacm32
ELF     7d14b000-7d181000       Deferred        winealsa<elf>
  \-PE  7d160000-7d181000       \               winealsa
ELF     7d181000-7d186000       Deferred        libxfixes.so.3
ELF     7d192000-7d19b000       Deferred        libxcursor.so.1
ELF     7d19b000-7d19e000       Deferred        libxcomposite.so.1
ELF     7d19e000-7d1a4000       Deferred        libxrandr.so.2
ELF     7d1a4000-7d1ac000       Deferred        libxrender.so.1
ELF     7d1ac000-7d1af000       Deferred        libxinerama.so.1
ELF     7d6ef000-7d780000       Deferred        winex11<elf>
  \-PE  7d700000-7d780000       \               winex11
ELF     7d7e0000-7d800000       Deferred        libexpat.so.1
ELF     7d800000-7d82b000       Deferred        libfontconfig.so.1
ELF     7d82b000-7d840000       Deferred        libz.so.1
ELF     7d855000-7d8c5000       Deferred        libfreetype.so.6
ELF     7d8c5000-7d8d9000       Deferred        lz32<elf>
  \-PE  7d8d0000-7d8d9000       \               lz32
ELF     7d8d9000-7d8f3000       Deferred        version<elf>
  \-PE  7d8e0000-7d8f3000       \               version
ELF     7d8f3000-7d94f000       Deferred        rpcrt4<elf>
  \-PE  7d900000-7d94f000       \               rpcrt4
ELF     7d94f000-7d9f2000       Deferred        ole32<elf>
  \-PE  7d960000-7d9f2000       \               ole32
ELF     7d9f2000-7da05000       Deferred        libresolv.so.2
ELF     7da05000-7da23000       Deferred        iphlpapi<elf>
  \-PE  7da10000-7da23000       \               iphlpapi
ELF     7da23000-7da50000       Deferred        ws2_32<elf>
  \-PE  7da30000-7da50000       \               ws2_32
ELF     7da50000-7da77000       Deferred        msacm32<elf>
  \-PE  7da60000-7da77000       \               msacm32
ELF     7da77000-7db35000       Deferred        comctl32<elf>
  \-PE  7da80000-7db35000       \               comctl32
ELF     7db35000-7dc3a000       Deferred        shell32<elf>
  \-PE  7db50000-7dc3a000       \               shell32
ELF     7dc3a000-7dc93000       Deferred        shlwapi<elf>
  \-PE  7dc50000-7dc93000       \               shlwapi
ELF     7dc93000-7dcb4000       Deferred        mpr<elf>
  \-PE  7dca0000-7dcb4000       \               mpr
ELF     7dcb4000-7dd01000       Deferred        wininet<elf>
  \-PE  7dcc0000-7dd01000       \               wininet
ELF     7dd01000-7dd1f000       Deferred        imm32<elf>
  \-PE  7dd10000-7dd1f000       \               imm32
ELF     7dd1f000-7de0c000       Deferred        wined3d<elf>
  \-PE  7dd30000-7de0c000       \               wined3d
ELF     7de0c000-7de3a000       Deferred        d3d9<elf>
  \-PE  7de10000-7de3a000       \               d3d9
ELF     7de95000-7dea0000       Deferred        libgcc_s.so.1
ELF     7df93000-7e92b000       Deferred        libglcore.so.1
ELF     7e92b000-7e9ae000       Deferred        libglu.so.1
ELF     7e9ae000-7ea44000       Deferred        libgl.so.1
ELF     7ea44000-7eb35000       Deferred        libx11.so.6
ELF     7eb35000-7ebb6000       Deferred        opengl32<elf>
  \-PE  7eb50000-7ebb6000       \               opengl32
ELF     7ebb6000-7ec02000       Deferred        advapi32<elf>
  \-PE  7ebc0000-7ec02000       \               advapi32
ELF     7ec02000-7ec9b000       Deferred        gdi32<elf>
  \-PE  7ec10000-7ec9b000       \               gdi32
ELF     7ec9b000-7edd8000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd8000       \               user32
ELF     7edd8000-7ee66000       Deferred        winmm<elf>
  \-PE  7ede0000-7ee66000       \               winmm
ELF     7ef85000-7ef90000       Deferred        libnss_files.so.2
ELF     7ef92000-7ef97000       Deferred        libxdmcp.so.6
ELF     7ef97000-7efa5000       Deferred        libxext.so.6
ELF     7efa5000-7efbd000       Deferred        libnsl.so.1
ELF     7efbe000-7efc0000       Deferred        libnvidia-tls.so.1
ELF     7efc0000-7efc3000       Deferred        libxau.so.6
ELF     7efc8000-7efd2000       Deferred        libnss_nis.so.2
ELF     7efd2000-7efdb000       Deferred        libnss_compat.so.2
ELF     7efdb000-7f000000       Deferred        libm.so.6
ELF     f7ca6000-f7caa000       Deferred        libdl.so.2
ELF     f7caa000-f7df4000       Deferred        libc.so.6
ELF     f7df5000-f7e0d000       Deferred        libpthread.so.0
ELF     f7e0d000-f7f21000       Dwarf           libwine.so.1
ELF     f7f23000-f7f41000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) Z:\media\Movies\WoW\WoW.exe
        00000009    0 <==
Backtrace:
=>1 0x10035a21 EntryPoint() in divxdecoder (0x0034fd78)
  2 0x7bc4592d MODULE_InitDLL+0x8d(wm=<register EDI not in topmost frame>, reason=<register ESI not in topmost frame>, lpReserved=0x1) [/home/adam/wine-0.9.51/dlls/ntdll/loader.c:909] in ntdll (0x0034fe08)
  3 0x7bc45f94 process_attach+0x174(wm=<register EDI not in topmost frame>, lpReserved=0x1) [/home/adam/wine-0.9.51/dlls/ntdll/loader.c:982] in ntdll (0x0034fe58)
  4 0x7bc45ec2 process_attach+0xa2(wm=<register EDI not in topmost frame>, lpReserved=0x1) [/home/adam/wine-0.9.51/dlls/ntdll/loader.c:974] in ntdll (0x0034fea8)
  5 0x7bc48b8a LdrInitializeThunk+0x2ba(unknown1=0x0, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/home/adam/wine-0.9.51/dlls/ntdll/loader.c:1027] in ntdll (0x0034ff08)
  6 0x7b87615a start_process+0xba(arg=0x0) [/home/adam/wine-0.9.51/dlls/kernel32/process.c:829] in kernel32 (0x0034ffe8)
  7 0xf7e14957 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

---

### Post by P.tritas on 2007-12-16
Maybe upgrade your Wine Version?
Have you ever played WoW using Wine, or is it the first time?
Have you tried "PlayOnLinux" ?

---

### Post by Kilz on 2007-12-16
You may want to go to the wine application database.[ Its wow page]("http://appdb.winehq.org/appview.php?iVersionId=6482") has a wiki dealing with getting wow running under wine.

---

### Post by adt41287 on 2007-12-16
yes i am familiar with running WoW under wine.  the wow directory was installed in wine under a 32 bit machine but now i am running in 64 bit.  would this make a difference? dont believe it should because wine is only 32 bit anyways right? i think i may just switch back to 32 bit ive encountered a few problems with 64 bit, whats your guys' suggestions??

---

### Post by adt41287 on 2007-12-16
and yes that is the newest version of wine.

---

