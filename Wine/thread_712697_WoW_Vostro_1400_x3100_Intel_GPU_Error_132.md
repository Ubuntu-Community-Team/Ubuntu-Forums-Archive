---
title: "WoW Vostro 1400 x3100 Intel GPU Error 132"
date: 2008-03-02
forum: Wine
---

### Post by norsk on 2008-03-02
Here is a thread I found with an identical problem that is explained better

[http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/cc16d0d13ade8b9a](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/cc16d0d13ade8b9a)

Probably a hopeless thread since every post I've read regarding this combination has not ended well, but here goes

I'm new to Linux as of 9 hours ago, but have been using this laptop with Vista for awhile and World of Warcraft runs decently on it.

I have:
Ubuntu 7.10
Latest Wine (followed directions from sticky)
Vostro 1400 Laptop (Intel x3100 GPU)

I've used 3 separate howtos on installing WoW with wine, but I am not able to install warcraft from the disks since I do not have those, I do however have the wow folder copied from my windows installation installed in my .wine program file's directory.  I have made the edits to the config.wtf file and tried all the little things I've read, but I receieve [B]:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7DF2A6F5[/B] when I run wine wow.exe and this is what shows up in the terminal window
```

[email]jensbodal@jensbodal-laptop:~/.wine[/email]/drive_c/Program Files/World of Warcraft$ wine wow.exe
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed78,0x00000000), stub!
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
wine: Unhandled page fault on read access to 0x00000010 at address 0x7df2a6f5 (thread 0026), starting debugger...
Unhandled exception: page fault on read access to 0x00000010 in 32-bit code (0x7df2a6f5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7df2a6f5 ESP:0034e930 EBP:0034e934 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:7c2e87f8 ECX:7c29b338 EDX:00000005
 ESI:0034e9dc EDI:7e7e9fe7
Stack dump:
0x0034e930:  7e808b9c 0034ec24 7e768cf3 7c2e87f8
0x0034e940:  00008620 7c29b338 7e7e9f74 7e8097ac
0x0034e950:  b7ea18ac 00000320 0000000a 00000001
0x0034e960:  7e0f04c0 b7ea0541 7c30f528 7c2e87f8
0x0034e970:  79800000 0034e9a4 7df05906 7e0f04c0
0x0034e980:  b7ea18ac b7ea0541 0034eafc 00000378
Backtrace:
=>1 0x7df2a6f5 in i965_dri.so (+0x856f5) (0x0034e934)
  2 0x7e768cf3 IWineD3DImpl_FillGLCaps+0x818b() in wined3d (0x0034ec24)
  3 0x7e771091 InitAdapters+0x1f16() in wined3d (0x0034f074)
  4 0x7e7ded42 WineDirect3DCreate+0x22() in wined3d (0x0034f0a4)
  5 0x7e81ffb9 Direct3DCreate9+0x77() in d3d9 (0x0034f0d4)
  6 0x0059effa in wow (+0x19effa) (0x0034f0e8)
  7 0x00598ee7 in wow (+0x198ee7) (0x0034f710)
  8 0x0063b17a in wow (+0x23b17a) (0x0034fb44)
  9 0x0063763f in wow (+0x23763f) (0x0034fbf4)
  10 0x00405fd8 in wow (+0x5fd8) (0x0034fe5c)
  11 0x004060d6 in wow (+0x60d6) (0x0034fe6c)
  12 0x00406128 in wow (+0x6128) (0x0034ff08)
  13 0x7b86e7a5 in kernel32 (+0x4e7a5) (0x0034ffe8)
  14 0xb7ec41cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7df2a6f5: movl        0x10(%eax),%eax
Modules:
Module  Address                 Debug info      Name (97 modules)
PE        400000-  e6e000       Export          wow
PE      10000000-10069000       Deferred        divxdecoder
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c855000-7c8ba000       Deferred        msvcrt<elf>
  \-PE  7c860000-7c8ba000       \               msvcrt
ELF     7c8ba000-7c8cf000       Deferred        psapi<elf>
  \-PE  7c8c0000-7c8cf000       \               psapi
ELF     7c8cf000-7c917000       Deferred        dbghelp<elf>
  \-PE  7c8e0000-7c917000       \               dbghelp
ELF     7ca3e000-7ca70000       Deferred        uxtheme<elf>
  \-PE  7ca40000-7ca70000       \               uxtheme
ELF     7ca90000-7caa4000       Deferred        midimap<elf>
  \-PE  7caa0000-7caa4000       \               midimap
ELF     7caa4000-7cabb000       Deferred        msacm32<elf>
  \-PE  7cab0000-7cabb000       \               msacm32
ELF     7cabb000-7cb81000       Deferred        libasound.so.2
ELF     7cb8d000-7cbc2000       Deferred        winealsa<elf>
  \-PE  7cba0000-7cbc2000       \               winealsa
ELF     7cbc2000-7cbcb000       Deferred        libxcursor.so.1
ELF     7cbcb000-7cbd1000       Deferred        libxrandr.so.2
ELF     7cbd1000-7cbd9000       Deferred        libxrender.so.1
ELF     7dea5000-7e0fc000       Export          i965_dri.so
ELF     7e0fc000-7e18c000       Deferred        winex11<elf>
  \-PE  7e110000-7e18c000       \               winex11
ELF     7e1ec000-7e20c000       Deferred        libexpat.so.1
ELF     7e20c000-7e237000       Deferred        libfontconfig.so.1
ELF     7e237000-7e23a000       Deferred        libxcomposite.so.1
ELF     7e243000-7e258000       Deferred        libz.so.1
ELF     7e258000-7e2c8000       Deferred        libfreetype.so.6
ELF     7e2c8000-7e2dc000       Deferred        lz32<elf>
  \-PE  7e2d0000-7e2dc000       \               lz32
ELF     7e2dc000-7e2f5000       Deferred        version<elf>
  \-PE  7e2e0000-7e2f5000       \               version
ELF     7e2f5000-7e353000       Deferred        rpcrt4<elf>
  \-PE  7e300000-7e353000       \               rpcrt4
ELF     7e353000-7e3f4000       Deferred        ole32<elf>
  \-PE  7e360000-7e3f4000       \               ole32
ELF     7e3f4000-7e407000       Deferred        libresolv.so.2
ELF     7e407000-7e425000       Deferred        iphlpapi<elf>
  \-PE  7e410000-7e425000       \               iphlpapi
ELF     7e425000-7e450000       Deferred        ws2_32<elf>
  \-PE  7e430000-7e450000       \               ws2_32
ELF     7e450000-7e476000       Deferred        msacm32<elf>
  \-PE  7e460000-7e476000       \               msacm32
ELF     7e476000-7e535000       Deferred        comctl32<elf>
  \-PE  7e480000-7e535000       \               comctl32
ELF     7e535000-7e639000       Deferred        shell32<elf>
  \-PE  7e540000-7e639000       \               shell32
ELF     7e639000-7e690000       Deferred        shlwapi<elf>
  \-PE  7e650000-7e690000       \               shlwapi
ELF     7e690000-7e6b1000       Deferred        mpr<elf>
  \-PE  7e6a0000-7e6b1000       \               mpr
ELF     7e6b1000-7e6fc000       Deferred        wininet<elf>
  \-PE  7e6c0000-7e6fc000       \               wininet
ELF     7e6fc000-7e719000       Deferred        imm32<elf>
  \-PE  7e700000-7e719000       \               imm32
ELF     7e719000-7e80b000       Export          wined3d<elf>
  \-PE  7e730000-7e80b000       \               wined3d
ELF     7e80b000-7e83a000       Export          d3d9<elf>
  \-PE  7e810000-7e83a000       \               d3d9
ELF     7e83a000-7e845000       Deferred        libgcc_s.so.1
ELF     7e938000-7e942000       Deferred        libdrm.so.2
ELF     7e942000-7e947000       Deferred        libxfixes.so.3
ELF     7e947000-7e94a000       Deferred        libxdamage.so.1
ELF     7e94a000-7e94f000       Deferred        libxdmcp.so.6
ELF     7e94f000-7e952000       Deferred        libxau.so.6
ELF     7e952000-7e9d5000       Deferred        libglu.so.1
ELF     7e9d5000-7ea36000       Deferred        libgl.so.1
ELF     7ea36000-7eb27000       Deferred        libx11.so.6
ELF     7eb27000-7eb35000       Deferred        libxext.so.6
ELF     7eb35000-7eb3a000       Deferred        libxxf86vm.so.1
ELF     7eb3a000-7eb52000       Deferred        libice.so.6
ELF     7eb52000-7eb5a000       Deferred        libsm.so.6
ELF     7eb66000-7ebe6000       Deferred        opengl32<elf>
  \-PE  7eb80000-7ebe6000       \               opengl32
ELF     7ebe6000-7ec30000       Deferred        advapi32<elf>
  \-PE  7ebf0000-7ec30000       \               advapi32
ELF     7ec30000-7ecc7000       Deferred        gdi32<elf>
  \-PE  7ec40000-7ecc7000       \               gdi32
ELF     7ecc7000-7edfe000       Deferred        user32<elf>
  \-PE  7ece0000-7edfe000       \               user32
ELF     7edfe000-7ee8a000       Deferred        winmm<elf>
  \-PE  7ee10000-7ee8a000       \               winmm
ELF     7efac000-7efb7000       Deferred        libnss_files.so.2
ELF     7efb7000-7efcf000       Deferred        libnsl.so.1
ELF     7efcf000-7eff4000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d40000-b7d49000       Deferred        libnss_compat.so.2
ELF     b7d4a000-b7d4e000       Deferred        libdl.so.2
ELF     b7d4e000-b7e98000       Deferred        libc.so.6
ELF     b7e99000-b7eb1000       Deferred        libpthread.so.0
ELF     b7ebd000-b7fd1000       Export          libwine.so.1
ELF     b7fd3000-b7fef000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000010 
        00000012    0
        00000011    0
00000014 
        00000015    0
0000001e 
        0000001f    0
00000025 (D) C:\Program Files\World of Warcraft\wow.exe
        00000026    0 <==
Backtrace:
=>1 0x7df2a6f5 in i965_dri.so (+0x856f5) (0x0034e934)
  2 0x7e768cf3 IWineD3DImpl_FillGLCaps+0x818b() in wined3d (0x0034ec24)
  3 0x7e771091 InitAdapters+0x1f16() in wined3d (0x0034f074)
  4 0x7e7ded42 WineDirect3DCreate+0x22() in wined3d (0x0034f0a4)
  5 0x7e81ffb9 Direct3DCreate9+0x77() in d3d9 (0x0034f0d4)
  6 0x0059effa in wow (+0x19effa) (0x0034f0e8)
  7 0x00598ee7 in wow (+0x198ee7) (0x0034f710)
  8 0x0063b17a in wow (+0x23b17a) (0x0034fb44)
  9 0x0063763f in wow (+0x23763f) (0x0034fbf4)
  10 0x00405fd8 in wow (+0x5fd8) (0x0034fe5c)
  11 0x004060d6 in wow (+0x60d6) (0x0034fe6c)
  12 0x00406128 in wow (+0x6128) (0x0034ff08)
  13 0x7b86e7a5 in kernel32 (+0x4e7a5) (0x0034ffe8)
  14 0xb7ec41cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

---

### Post by norsk on 2008-03-02
Well I found the installers from what I downloaded a few months ago to play wow under windows, and I ran those under wine.  The launcher for BC will load but as soon as I hit play I still receive error 132.  This leads me to believe that my problem is pre 2.3 patch since the BC installer I would assume is version 2.0

---

### Post by Quwel on 2008-03-18
im having this same error trying to start wow after install

please if some one knows more on this reply plz

---

### Post by Resonance378 on 2008-03-20
If you go to the main wow thread under this forum for installing WoW with Wine someone recently regressed as far back as Wine 0.9.29 to get it working with the intel X3100 (i915)

This may be a bug introduced to Wine since 0.9.30 since according to that person they get the same Error 132 on version 0.9.30 - 0.9.47.

Best of luck!

---

