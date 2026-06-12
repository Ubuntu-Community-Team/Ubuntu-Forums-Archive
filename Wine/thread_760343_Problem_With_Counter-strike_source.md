---
title: "Problem With Counter-strike source"
date: 2008-04-20
forum: Wine
---

### Post by Inevitab13 on 2008-04-20
I am trying to run CSS in WINE, and when I run it like this:WINEDEBUG="fixme-all" wine Steam, here is what comes up
[HTML]
```

err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
Win32 MiniDump Helper version 1.0.0.0 (c) Copyright 2000-2003 Valve Corporation All rights reserved.

Expected argument 'ProcessId'.

Usage: WriteMiniDump [@argfile] [/?|h|help] [/v|version] [/Type <value>] <ProcessId> <DumpFile>

@argfile        Read arguments from a file.
/?              Show usage.
/v              Show version.
/Type <value>   Select dump type values are:
                   normal       
                   full         
ProcessId       Select process id for which to generate a dump
DumpFile        Select path of output dump file

err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
wine: Unhandled page fault on execute access to 0x7d2d9710 at address 0x7d2d9710 (thread 0054), starting debugger...
Unhandled exception: page fault on execute access to 0x7d2d9710 in 32-bit code (0x7d2d9710).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d2d9710 ESP:0033d6d4 EBP:0033d700 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7e0a0ab8 ECX:7d2d9710 EDX:7c003140
 ESI:00000001 EDI:0000015e
Stack dump:
0x0033d6d4:  7e02e213 7e0a0ab8 00015ab9 f7df8140
0x0033d6e4:  0033d700 f7d1db40 f7df8140 00000020
0x0033d6f4:  7e1333e9 f7df8170 00000000 0033d720
0x0033d704:  7d503d38 7e0a0ab8 00000000 f7df8140
0x0033d714:  7c07ba48 7e14f850 0000000b 0033d730
0x0033d724:  7d4712bb 7c07ba48 7c07d530 0033d750
Backtrace:
=>1 0x7d2d9710 (0x0033d700)
  2 0x7d503d38 in fglrx_dri.so (+0x1fbd38) (0x0033d720)
  3 0x7d4712bb in fglrx_dri.so (+0x1692bb) (0x0033d730)
  4 0x7db21b1c in fglrx_dri.so (+0x819b1c) (0x0033d750)
  5 0x7e0359f4 in fglrx_dri.so (+0xd2d9f4) (0x0033d770)
  6 0x7ddf13c8 in fglrx_dri.so (+0xae93c8) (0x0033d780)
  7 0x7e0843c1 in fglrx_dri.so (+0xd7c3c1) (0x0033d790)
  8 0x7d46ff45 in fglrx_dri.so (+0x167f45) (0x0033d7a0)
  9 0xf7f47050 in ld-linux.so.2 (+0xf050) (0x0033d7d0)
  10 0xf7f47183 in ld-linux.so.2 (+0xf183) (0x0033d810)
  11 0xf7f4b09c in ld-linux.so.2 (+0x1309c) (0x0033d880)
  12 0xf7f46c96 in ld-linux.so.2 (+0xec96) (0x0033d960)
  13 0xf7f4a6ee in ld-linux.so.2 (+0x126ee) (0x0033d9c0)
  14 0xf7cadc19 GLIBC_2+0xc19() in libdl.so.2 (0x0033da00)
  15 0xf7f46c96 in ld-linux.so.2 (+0xec96) (0x0033dae0)
  16 0xf7cae2bc in libdl.so.2 (+0x12bc) (0x0033db00)
  17 0xf7cadb51 GLIBC_2+0xb51() in libdl.so.2 (0x0033db30)
  18 0xf7e280d6 wine_dlopen+0x36() in libwine.so.1 (0x0033db60)
  19 0x7bc446a4 in ntdll (+0x346a4) (0x0033ddf0)
  20 0x7bc48b88 in ntdll (+0x38b88) (0x0033df20)
  21 0x7bc490a0 LdrLoadDll+0x50() in ntdll (0x0033df40)
  22 0x7b864be7 in kernel32 (+0x44be7) (0x0033e1b0)
  23 0x7b864ec3 LoadLibraryExW+0x43() in kernel32 (0x0033e1d0)
  24 0x7ea2728b in version (+0x728b) (0x0033e210)
  25 0x7ea27991 GetFileVersionInfoSizeW+0xc1() in version (0x0033e250)
  26 0x7e53232d in dbghelp (+0x1232d) (0x0033eac0)
  27 0x7e532ecd MiniDumpWriteDump+0x9fd() in dbghelp (0x0033f980)
  28 0x0040fb64 in writeminidump (+0xfb64) (0x7b872910)
  29 0x2400e853 (0x56e58955)
  30 0x00000000 (0x00000000)
0x7d2d9710: -- no code accessible --
Modules:
Module  Address                 Debug info      Name (74 modules)
PE        400000-  43e000       Export          writeminidump
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca4000       Export          ntdll<elf>
  \-PE  7bc10000-7bca4000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d308000-7e313000       Export          fglrx_dri.so
ELF     7e313000-7e328000       Deferred        midimap<elf>
  \-PE  7e320000-7e328000       \               midimap
ELF     7e328000-7e34e000       Deferred        msacm32<elf>
  \-PE  7e330000-7e34e000       \               msacm32
ELF     7e34e000-7e366000       Deferred        msacm32<elf>
  \-PE  7e350000-7e366000       \               msacm32
ELF     7e366000-7e3f3000       Deferred        winmm<elf>
  \-PE  7e370000-7e3f3000       \               winmm
ELF     7e3f3000-7e4b9000       Deferred        libasound.so.2
ELF     7e4c7000-7e4fc000       Deferred        winealsa<elf>
  \-PE  7e4d0000-7e4fc000       \               winealsa
ELF     7e4fc000-7e511000       Deferred        psapi<elf>
  \-PE  7e500000-7e511000       \               psapi
ELF     7e511000-7e55a000       Export          dbghelp<elf>
  \-PE  7e520000-7e55a000       \               dbghelp
ELF     7e57e000-7e591000       Deferred        libresolv.so.2
ELF     7e59f000-7e5bd000       Deferred        iphlpapi<elf>
  \-PE  7e5b0000-7e5bd000       \               iphlpapi
ELF     7e5bd000-7e61d000       Deferred        rpcrt4<elf>
  \-PE  7e5d0000-7e61d000       \               rpcrt4
ELF     7e61d000-7e6c0000       Deferred        ole32<elf>
  \-PE  7e630000-7e6c0000       \               ole32
ELF     7e6e5000-7e717000       Deferred        uxtheme<elf>
  \-PE  7e6f0000-7e717000       \               uxtheme
ELF     7e717000-7e720000       Deferred        libxcursor.so.1
ELF     7e720000-7e725000       Deferred        libxfixes.so.3
ELF     7e725000-7e728000       Deferred        libxcomposite.so.1
ELF     7e728000-7e72e000       Deferred        libxrandr.so.2
ELF     7e72e000-7e736000       Deferred        libxrender.so.1
ELF     7e736000-7e739000       Deferred        libxinerama.so.1
ELF     7e739000-7e73e000       Deferred        libxdmcp.so.6
ELF     7e73e000-7e741000       Deferred        libxau.so.6
ELF     7e741000-7e832000       Deferred        libx11.so.6
ELF     7e832000-7e840000       Deferred        libxext.so.6
ELF     7e843000-7e84c000       Deferred        librt.so.1
ELF     7e84e000-7e8dc000       Deferred        winex11<elf>
  \-PE  7e860000-7e8dc000       \               winex11
ELF     7e922000-7e942000       Deferred        libexpat.so.1
ELF     7e942000-7e96d000       Deferred        libfontconfig.so.1
ELF     7e97b000-7e990000       Deferred        libz.so.1
ELF     7e990000-7ea00000       Deferred        libfreetype.so.6
ELF     7ea00000-7ea14000       Deferred        lz32<elf>
  \-PE  7ea10000-7ea14000       \               lz32
ELF     7ea14000-7ea2d000       Export          version<elf>
  \-PE  7ea20000-7ea2d000       \               version
ELF     7ea2d000-7eaef000       Deferred        comctl32<elf>
  \-PE  7ea40000-7eaef000       \               comctl32
ELF     7eaef000-7eb47000       Deferred        shlwapi<elf>
  \-PE  7eb00000-7eb47000       \               shlwapi
ELF     7eb47000-7ec51000       Deferred        shell32<elf>
  \-PE  7eb60000-7ec51000       \               shell32
ELF     7ec51000-7eca1000       Deferred        advapi32<elf>
  \-PE  7ec60000-7eca1000       \               advapi32
ELF     7eca1000-7ed3b000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed3b000       \               gdi32
ELF     7ed3b000-7ee7f000       Deferred        user32<elf>
  \-PE  7ed50000-7ee7f000       \               user32
ELF     7ee7f000-7ee97000       Deferred        libnsl.so.1
ELF     7ee97000-7eea0000       Deferred        libnss_compat.so.2
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     f7ca2000-f7cac000       Deferred        libnss_nis.so.2
ELF     f7cad000-f7cb1000       Export          libdl.so.2
ELF     f7cb1000-f7dfb000       Deferred        libc.so.6
ELF     f7dfc000-f7e14000       Deferred        libpthread.so.0
ELF     f7e22000-f7f36000       Export          libwine.so.1
ELF     f7f38000-f7f56000       Export          ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
        0000004e    1
        00000049    0
        00000048    0
        00000010    0
        00000011    0
        00000017    1
        0000003a    0
        0000003f    1
        00000039    0
        00000033    1
        00000030    0
        0000002e    1
        00000025    0
        00000023    1
        0000000f    0
        0000000b    1
        00000047    0
        00000046    1
        00000045    0
        00000044    1
        00000042    0
        00000041    0
        00000040    0
        0000003e    0
        0000003d    0
        0000003c    0
        0000003b    0
        00000038    0
        00000037    0
        00000036    1
        00000035    0
        00000034    0
        00000032    0
        00000031    1
        0000002f    0
        0000002d   15
        0000002b    0
        0000002a   15
        00000029   15
        00000028    0
        00000027    0
        00000026    0
        00000024    0
        00000022    0
        00000021    1
        00000020    0
        0000001f    0
        0000001e    0
        0000001d    0
        0000001c    0
        0000001b    0
        0000001a    0
        00000009    0
0000000c 
        00000016    0
        0000000e    0
        0000000d    0
00000012 
        00000015    0
        00000014    0
        00000013    0
00000018 
        00000019    0
0000004a 
        00000052   15
        00000051    2
        00000050    0
        0000004f    0
        0000004d    0
        0000004c    2
        0000004b    0
00000053 (D) C:\Program Files\Steam\WriteMiniDump.exe
        00000054    0 <==
Backtrace:
=>1 0x7d2d9710 (0x0033d700)
  2 0x7d503d38 in fglrx_dri.so (+0x1fbd38) (0x0033d720)
  3 0x7d4712bb in fglrx_dri.so (+0x1692bb) (0x0033d730)
  4 0x7db21b1c in fglrx_dri.so (+0x819b1c) (0x0033d750)
  5 0x7e0359f4 in fglrx_dri.so (+0xd2d9f4) (0x0033d770)
  6 0x7ddf13c8 in fglrx_dri.so (+0xae93c8) (0x0033d780)
  7 0x7e0843c1 in fglrx_dri.so (+0xd7c3c1) (0x0033d790)
  8 0x7d46ff45 in fglrx_dri.so (+0x167f45) (0x0033d7a0)
  9 0xf7f47050 in ld-linux.so.2 (+0xf050) (0x0033d7d0)
  10 0xf7f47183 in ld-linux.so.2 (+0xf183) (0x0033d810)
  11 0xf7f4b09c in ld-linux.so.2 (+0x1309c) (0x0033d880)
  12 0xf7f46c96 in ld-linux.so.2 (+0xec96) (0x0033d960)
  13 0xf7f4a6ee in ld-linux.so.2 (+0x126ee) (0x0033d9c0)
  14 0xf7cadc19 GLIBC_2+0xc19() in libdl.so.2 (0x0033da00)
  15 0xf7f46c96 in ld-linux.so.2 (+0xec96) (0x0033dae0)
  16 0xf7cae2bc in libdl.so.2 (+0x12bc) (0x0033db00)
  17 0xf7cadb51 GLIBC_2+0xb51() in libdl.so.2 (0x0033db30)
  18 0xf7e280d6 wine_dlopen+0x36() in libwine.so.1 (0x0033db60)
  19 0x7bc446a4 in ntdll (+0x346a4) (0x0033ddf0)
  20 0x7bc48b88 in ntdll (+0x38b88) (0x0033df20)
  21 0x7bc490a0 LdrLoadDll+0x50() in ntdll (0x0033df40)
  22 0x7b864be7 in kernel32 (+0x44be7) (0x0033e1b0)
  23 0x7b864ec3 LoadLibraryExW+0x43() in kernel32 (0x0033e1d0)
  24 0x7ea2728b in version (+0x728b) (0x0033e210)
  25 0x7ea27991 GetFileVersionInfoSizeW+0xc1() in version (0x0033e250)
  26 0x7e53232d in dbghelp (+0x1232d) (0x0033eac0)
  27 0x7e532ecd MiniDumpWriteDump+0x9fd() in dbghelp (0x0033f980)
  28 0x0040fb64 in writeminidump (+0xfb64) (0x7b872910)
  29 0x2400e853 (0x56e58955)
  30 0x00000000 (0x00000000)
err:ole:RevokeDragDrop invalid hwnd 0x1003a
err:ole:RevokeDragDrop invalid hwnd 0x10044
err:ole:RevokeDragDrop invalid hwnd 0x10046
err:ole:RevokeDragDrop invalid hwnd 0x10048
err:ole:RevokeDragDrop invalid hwnd 0x1004a
err:ole:RevokeDragDrop invalid hwnd 0x10090
err:ole:RevokeDragDrop invalid hwnd 0x10092
err:ole:RevokeDragDrop invalid hwnd 0x10094
err:ole:RevokeDragDrop invalid hwnd 0x10096
err:ole:RevokeDragDrop invalid hwnd 0x10098
err:ole:RevokeDragDrop invalid hwnd 0x1009a
err:ole:RevokeDragDrop invalid hwnd 0x1009c
err:ole:RevokeDragDrop invalid hwnd 0x20030
Shutting down. . .

```
[/HTML]
When That happens, Counter-strike:Source crashes
Please Help!!!

---

### Post by syczu on 2008-04-20
First install Gecko engine :

> wine iexplore [http://winehq.org](http://winehq.org)

Then you should run steam like this :

>  WINEDEBUG=-all wine Steam

Hope this helps.

---

### Post by Inevitab13 on 2008-04-20
how does that install gecko engine? nothing comes up saying that I have or haven't
EDIT:Never mind

---

### Post by Inevitab13 on 2008-04-20
Now it just gets to the loading screen with the two CT's and just crashes to the desktop

---

### Post by syczu on 2008-04-20
Try this :

```
sudo gedit /etc/sysctl.conf
```

And paste this into the file :

```
# Send and receive buffer sizes to make steam happy
net.core.rmem_max = 131072
net.core.wmem_max = 131072
```

---

### Post by Inevitab13 on 2008-04-20
Still doing the same thing, I started steam with terminal and after cs quit itself this message popped up in the terminal:

```

fixme:avifile:AVIFileExit (): stub!

```

Help?

---

### Post by syczu on 2008-04-20
Try :

```
WINEDEBUG=-all wine Steam -novid
```

to turn off intros.

---

### Post by Inevitab13 on 2008-04-20
Nope, still the same thing, here is what I get from the terminal:
```

dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
Win32 MiniDump Helper version 1.0.0.0 (c) Copyright 2000-2003 Valve Corporation All rights reserved.

Expected argument 'ProcessId'.

Usage: WriteMiniDump [@argfile] [/?|h|help] [/v|version] [/Type <value>] <ProcessId> <DumpFile>

@argfile        Read arguments from a file.
/?              Show usage.
/v              Show version.
/Type <value>   Select dump type values are:
                   normal       
                   full         
ProcessId       Select process id for which to generate a dump
DumpFile        Select path of output dump file

wine: Unhandled page fault on execute access to 0x7d2d0710 at address 0x7d2d0710 (thread 0056), starting debugger...
Unhandled exception: page fault on execute access to 0x7d2d0710 in 32-bit code (0x7d2d0710).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d2d0710 ESP:0033d6d4 EBP:0033d700 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7e097ab8 ECX:7d2d0710 EDX:7c003140
 ESI:00000001 EDI:0000015e
Stack dump:
0x0033d6d4:  7e025213 7e097ab8 00015ab1 f7e0f140
0x0033d6e4:  0033d700 f7d34b40 f7e0f140 00000020
0x0033d6f4:  7e12a3e9 f7e0f170 00000000 0033d720
0x0033d704:  7d4fad38 7e097ab8 00000000 f7e0f140
0x0033d714:  7c07ba50 7e146850 0000000b 0033d730
0x0033d724:  7d4682bb 7c07ba50 7c07d538 0033d750
Backtrace:
=>1 0x7d2d0710 (0x0033d700)
  2 0x7d4fad38 in fglrx_dri.so (+0x1fbd38) (0x0033d720)
  3 0x7d4682bb in fglrx_dri.so (+0x1692bb) (0x0033d730)
  4 0x7db18b1c in fglrx_dri.so (+0x819b1c) (0x0033d750)
  5 0x7e02c9f4 in fglrx_dri.so (+0xd2d9f4) (0x0033d770)
  6 0x7dde83c8 in fglrx_dri.so (+0xae93c8) (0x0033d780)
  7 0x7e07b3c1 in fglrx_dri.so (+0xd7c3c1) (0x0033d790)
  8 0x7d466f45 in fglrx_dri.so (+0x167f45) (0x0033d7a0)
  9 0xf7f5e050 in ld-linux.so.2 (+0xf050) (0x0033d7d0)
  10 0xf7f5e183 in ld-linux.so.2 (+0xf183) (0x0033d810)
  11 0xf7f6209c in ld-linux.so.2 (+0x1309c) (0x0033d880)
  12 0xf7f5dc96 in ld-linux.so.2 (+0xec96) (0x0033d960)
  13 0xf7f616ee in ld-linux.so.2 (+0x126ee) (0x0033d9c0)
  14 0xf7cc4c19 GLIBC_2+0xc19() in libdl.so.2 (0x0033da00)
  15 0xf7f5dc96 in ld-linux.so.2 (+0xec96) (0x0033dae0)
  16 0xf7cc52bc in libdl.so.2 (+0x12bc) (0x0033db00)
  17 0xf7cc4b51 GLIBC_2+0xb51() in libdl.so.2 (0x0033db30)
  18 0xf7e3f0d6 wine_dlopen+0x36() in libwine.so.1 (0x0033db60)
  19 0x7bc446a4 in ntdll (+0x346a4) (0x0033ddf0)
  20 0x7bc48b88 in ntdll (+0x38b88) (0x0033df20)
  21 0x7bc490a0 LdrLoadDll+0x50() in ntdll (0x0033df40)
  22 0x7b864be7 in kernel32 (+0x44be7) (0x0033e1b0)
  23 0x7b864ec3 LoadLibraryExW+0x43() in kernel32 (0x0033e1d0)
  24 0x7ea1c28b in version (+0xc28b) (0x0033e210)
  25 0x7ea1c991 GetFileVersionInfoSizeW+0xc1() in version (0x0033e250)
  26 0x7e52932d in dbghelp (+0x1932d) (0x0033eac0)
  27 0x7e529ecd MiniDumpWriteDump+0x9fd() in dbghelp (0x0033f980)
  28 0x0040fb64 in writeminidump (+0xfb64) (0x7b872910)
  29 0x2400e853 (0x56e58955)
  30 0x00000000 (0x00000000)
0x7d2d0710: -- no code accessible --
Modules:
Module  Address                 Debug info      Name (74 modules)
PE        400000-  43e000       Export          writeminidump
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca4000       Export          ntdll<elf>
  \-PE  7bc10000-7bca4000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d2ff000-7e30a000       Export          fglrx_dri.so
ELF     7e30a000-7e31f000       Deferred        midimap<elf>
  \-PE  7e310000-7e31f000       \               midimap
ELF     7e31f000-7e345000       Deferred        msacm32<elf>
  \-PE  7e330000-7e345000       \               msacm32
ELF     7e345000-7e35d000       Deferred        msacm32<elf>
  \-PE  7e350000-7e35d000       \               msacm32
ELF     7e35d000-7e3ea000       Deferred        winmm<elf>
  \-PE  7e370000-7e3ea000       \               winmm
ELF     7e3ea000-7e4b0000       Deferred        libasound.so.2
ELF     7e4be000-7e4f3000       Deferred        winealsa<elf>
  \-PE  7e4d0000-7e4f3000       \               winealsa
ELF     7e4f3000-7e508000       Deferred        psapi<elf>
  \-PE  7e500000-7e508000       \               psapi
ELF     7e508000-7e551000       Export          dbghelp<elf>
  \-PE  7e510000-7e551000       \               dbghelp
ELF     7e575000-7e588000       Deferred        libresolv.so.2
ELF     7e596000-7e5b4000       Deferred        iphlpapi<elf>
  \-PE  7e5a0000-7e5b4000       \               iphlpapi
ELF     7e5b4000-7e614000       Deferred        rpcrt4<elf>
  \-PE  7e5c0000-7e614000       \               rpcrt4
ELF     7e614000-7e6b7000       Deferred        ole32<elf>
  \-PE  7e620000-7e6b7000       \               ole32
ELF     7e6dc000-7e70e000       Deferred        uxtheme<elf>
  \-PE  7e6e0000-7e70e000       \               uxtheme
ELF     7e70e000-7e717000       Deferred        libxcursor.so.1
ELF     7e717000-7e71c000       Deferred        libxfixes.so.3
ELF     7e71c000-7e71f000       Deferred        libxcomposite.so.1
ELF     7e71f000-7e725000       Deferred        libxrandr.so.2
ELF     7e725000-7e72d000       Deferred        libxrender.so.1
ELF     7e72d000-7e730000       Deferred        libxinerama.so.1
ELF     7e730000-7e735000       Deferred        libxdmcp.so.6
ELF     7e735000-7e738000       Deferred        libxau.so.6
ELF     7e738000-7e829000       Deferred        libx11.so.6
ELF     7e829000-7e837000       Deferred        libxext.so.6
ELF     7e83a000-7e843000       Deferred        librt.so.1
ELF     7e845000-7e8d3000       Deferred        winex11<elf>
  \-PE  7e850000-7e8d3000       \               winex11
ELF     7e917000-7e937000       Deferred        libexpat.so.1
ELF     7e937000-7e962000       Deferred        libfontconfig.so.1
ELF     7e970000-7e985000       Deferred        libz.so.1
ELF     7e985000-7e9f5000       Deferred        libfreetype.so.6
ELF     7e9f5000-7ea09000       Deferred        lz32<elf>
  \-PE  7ea00000-7ea09000       \               lz32
ELF     7ea09000-7ea22000       Export          version<elf>
  \-PE  7ea10000-7ea22000       \               version
ELF     7ea22000-7eae4000       Deferred        comctl32<elf>
  \-PE  7ea30000-7eae4000       \               comctl32
ELF     7eae4000-7eb3c000       Deferred        shlwapi<elf>
  \-PE  7eaf0000-7eb3c000       \               shlwapi
ELF     7eb3c000-7ec46000       Deferred        shell32<elf>
  \-PE  7eb50000-7ec46000       \               shell32
ELF     7ec46000-7ec96000       Deferred        advapi32<elf>
  \-PE  7ec50000-7ec96000       \               advapi32
ELF     7ec96000-7ed30000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed30000       \               gdi32
ELF     7ed30000-7ee74000       Deferred        user32<elf>
  \-PE  7ed50000-7ee74000       \               user32
ELF     7ee74000-7ee7f000       Deferred        libnss_files.so.2
ELF     7ee7f000-7ee97000       Deferred        libnsl.so.1
ELF     7ee97000-7eea0000       Deferred        libnss_compat.so.2
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     f7cc4000-f7cc8000       Export          libdl.so.2
ELF     f7cc8000-f7e12000       Deferred        libc.so.6
ELF     f7e13000-f7e2b000       Deferred        libpthread.so.0
ELF     f7e39000-f7f4d000       Export          libwine.so.1
ELF     f7f4f000-f7f6d000       Export          ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
        00000050    1
        0000004b    0
        0000004a    0
        00000048    0
        00000011    0
        00000017    1
        00000010    0
        0000003a    1
        0000003f    0
        00000039    1
        00000033    0
        00000030    1
        00000025    0
        00000023    1
        0000000f    0
        0000000b    1
        00000047    0
        00000046    1
        00000045    0
        00000044    1
        00000042    0
        00000041    0
        00000040    0
        0000003e    0
        0000003d    0
        0000003c    0
        0000003b    0
        00000038    0
        00000037    0
        00000036    1
        00000035    0
        00000034    0
        00000032    0
        00000031    1
        0000002f    0
        0000002e    0
        0000002d   15
        0000002b    0
        0000002a   15
        00000029   15
        00000028    0
        00000027    0
        00000026    0
        00000024    0
        00000022    0
        00000021    1
        00000020    0
        0000001f    0
        0000001e    0
        0000001d    0
        0000001c    0
        0000001b    0
        0000001a    0
        00000009    0
0000000c 
        00000016    0
        0000000e    0
        0000000d    0
00000012 
        00000015    0
        00000014    0
        00000013    0
00000018 
        00000019    0
0000004c 
        00000054   15
        00000053    2
        00000052    0
        00000051    0
        0000004f    0
        0000004e    2
        0000004d    0
00000055 (D) C:\Program Files\Steam\WriteMiniDump.exe
        00000056    0 <==
Backtrace:
=>1 0x7d2d0710 (0x0033d700)
  2 0x7d4fad38 in fglrx_dri.so (+0x1fbd38) (0x0033d720)
  3 0x7d4682bb in fglrx_dri.so (+0x1692bb) (0x0033d730)
  4 0x7db18b1c in fglrx_dri.so (+0x819b1c) (0x0033d750)
  5 0x7e02c9f4 in fglrx_dri.so (+0xd2d9f4) (0x0033d770)
  6 0x7dde83c8 in fglrx_dri.so (+0xae93c8) (0x0033d780)
  7 0x7e07b3c1 in fglrx_dri.so (+0xd7c3c1) (0x0033d790)
  8 0x7d466f45 in fglrx_dri.so (+0x167f45) (0x0033d7a0)
  9 0xf7f5e050 in ld-linux.so.2 (+0xf050) (0x0033d7d0)
  10 0xf7f5e183 in ld-linux.so.2 (+0xf183) (0x0033d810)
  11 0xf7f6209c in ld-linux.so.2 (+0x1309c) (0x0033d880)
  12 0xf7f5dc96 in ld-linux.so.2 (+0xec96) (0x0033d960)
  13 0xf7f616ee in ld-linux.so.2 (+0x126ee) (0x0033d9c0)
  14 0xf7cc4c19 GLIBC_2+0xc19() in libdl.so.2 (0x0033da00)
  15 0xf7f5dc96 in ld-linux.so.2 (+0xec96) (0x0033dae0)
  16 0xf7cc52bc in libdl.so.2 (+0x12bc) (0x0033db00)
  17 0xf7cc4b51 GLIBC_2+0xb51() in libdl.so.2 (0x0033db30)
  18 0xf7e3f0d6 wine_dlopen+0x36() in libwine.so.1 (0x0033db60)
  19 0x7bc446a4 in ntdll (+0x346a4) (0x0033ddf0)
  20 0x7bc48b88 in ntdll (+0x38b88) (0x0033df20)
  21 0x7bc490a0 LdrLoadDll+0x50() in ntdll (0x0033df40)
  22 0x7b864be7 in kernel32 (+0x44be7) (0x0033e1b0)
  23 0x7b864ec3 LoadLibraryExW+0x43() in kernel32 (0x0033e1d0)
  24 0x7ea1c28b in version (+0xc28b) (0x0033e210)
  25 0x7ea1c991 GetFileVersionInfoSizeW+0xc1() in version (0x0033e250)
  26 0x7e52932d in dbghelp (+0x1932d) (0x0033eac0)
  27 0x7e529ecd MiniDumpWriteDump+0x9fd() in dbghelp (0x0033f980)
  28 0x0040fb64 in writeminidump (+0xfb64) (0x7b872910)
  29 0x2400e853 (0x56e58955)
  30 0x00000000 (0x00000000)

```

---

### Post by syczu on 2008-04-20
In terminal :

```
sysctl -p
```

And add registry key 

```
echo -ne "REGEDIT4\n[HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Cryptography]\n\"MachineGuid\"=\"$(uuidgen)\"\n" | wine regedit -
```

---

### Post by Inevitab13 on 2008-04-20
Still exactly the same problem, the game still won't get past the first loading screen with the two ct's and the black loading box in the bottom right corner.

---

### Post by Inevitab13 on 2008-04-21
Okay now it won't even load up at all. I turned off steam community in game and now I get the error message "This Game is currently unavailable". plz help!

---

### Post by Inevitab13 on 2008-04-26
Could someone please help me. I think that this has something to do with my graphics card. Because just about every single directx game I try doesn't work. Including S.T.A.L.K.E.R, Oblivion, CSS, TF2 etc. And again, Please Help!!!!

---

### Post by Alex Carroll on 2008-04-27
If you've got an ATi card, you'll have to be pretty lucky to make any games work in Wine.

---

### Post by kalel90 on 2008-04-28
I have the same problem any soulutions yet?

---

### Post by situz on 2008-04-29
I've got an ATI card, finished downloading css now so gonna try to get the game running when i get home, I'll let you know if I find out anything.

but have you gotten cs 1.6 working? 
1.6 worked fine for me anyway =)

---

### Post by situz on 2008-04-29
So far I've learned that you need to install directx9.0c. I'm having some problems to do so for no obvious reason atm, but you should give it a shot:
follow this guide:
[http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html](http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html)
and the dll files you need to download are these 2:

[http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mscoree.dll/1.1.4322.5738/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mscoree.dll/1.1.4322.5738/download.html)
[http://www.dlldump.com/download-dll-files_new.php/dllfiles/S/streamci.dll/5.1.2600.0/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/S/streamci.dll/5.1.2600.0/download.html)

also when you install the directx, you need to set wine to windows 2000. 

this should make you able to run the game normally =)

tell me how this works out for ya!

I'll keep on trying to install directx *rips my hair of*

---

### Post by Inevitab13 on 2008-05-16
I apologise for BUMP'ing but I think I might have found the problem. DXDIAG displays my Graphics Card (Radeon 2600) as X11 Windowing system. Will installing the Windows Drivers for my card help?

Oh and BTW: Direct3d tests don't work

---

