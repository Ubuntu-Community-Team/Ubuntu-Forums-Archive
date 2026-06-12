---
title: "wine vs protel 99"
date: 2008-05-14
forum: Wine
---

### Post by supremedalek on 2008-05-14
I am having a bit of a problem with protel 99 under wine 0.9.46 in my ubuntu 7.10 laptop. It seemed to have installed without an hitch, but when I try to run it, this is what I get:

```
raub@monaco:~$ wine "C:\Program Files\Design Explorer 99 SE\Client99SE.exe"
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b843f50 (thread 0009), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc39b4c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc39b4c ESP:0033f8f4 EBP:0033f958 EFLAGS:00200282(   - 00      - -IS1)
 EAX:0033f900 EBX:7bc8443c ECX:00110020 EDX:0033fce0
 ESI:0033fce0 EDI:0033f964
Stack dump:
0x0033f8f4:  7bc60f0a 00000005 0033fa24 c0000025
0x0033f904:  00000001 0033fce0 00000003 00000000
0x0033f914:  7bc8443c 00000000 0033f9c4 0033fa00
0x0033f924:  7bc611b9 00000002 0033f944 00000000
0x0033f934:  0012b360 00000004 7b88c920 0033f944
0x0033f944:  00000000 00000000 7ee2a764 7bc39b00
Backtrace:
=>1 0x7bc39b4c __regs_RtlRaiseException+0x4c(rec=0x33fce0, context=0x33f970) [/build/buildd/wine-0.9.46/dlls/ntdll/exception.c:396] in ntdll (0x0033f958)
  2 0x7bc72d83 __wine_call_from_32_regs+0xc3() in ntdll (0x0033fcbc)
  3 0x7bc39116 RtlRaiseException+0x6() in ntdll (0x0033fd34)
  4 0x004d86a8 in csrtl50.bpl (+0x86a8) (0x0033fd88)
  5 0x004d8b91 in csrtl50.bpl (+0x8b91) (0x0033fdc8)
  6 0x004e1e3f in csrtl50.bpl (+0x11e3f) (0x0033fdec)
  7 0x40004766 in vcl50.bpl (+0x4766) (0x0033ff08)
  8 0x7b874c7e start_process+0xee(arg=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/process.c:839] in kernel32 (0x0033ffe8)
  9 0xb7e009d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc39b4c __regs_RtlRaiseException+0x4c [/build/buildd/wine-0.9.46/dlls/ntdll/exception.c:396] in ntdll: subl  $4,%esp
Unable to open file '/build/buildd/wine-0.9.46/dlls/ntdll/exception.c'
Modules:
Module  Address                 Debug info      Name (103 modules)
PE        340000-  3f8000       Deferred        protelcomponents50.bpl
PE        400000-  4c5000       Deferred        client99se
PE        4d0000-  598000       Export          csrtl50.bpl
PE      40000000-401f2000       Export          vcl50.bpl
PE      402f0000-40333000       Deferred        vclx50.bpl
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7df41000-7df56000       Deferred        midimap<elf>
  \-PE  7df50000-7df56000       \               midimap
ELF     7df56000-7df7d000       Deferred        msacm32<elf>
  \-PE  7df60000-7df7d000       \               msacm32
ELF     7df7d000-7df95000       Deferred        msacm32<elf>
  \-PE  7df80000-7df95000       \               msacm32
ELF     7df95000-7dfcf000       Deferred        wineoss<elf>
  \-PE  7dfa0000-7dfcf000       \               wineoss
ELF     7dfcf000-7e020000       Deferred        libgcrypt.so.11
ELF     7e020000-7e024000       Deferred        libgpg-error.so.0
ELF     7e024000-7e034000       Deferred        libtasn1.so.3
ELF     7e034000-7e036000       Deferred        libkeyutils.so.1
ELF     7e036000-7e03e000       Deferred        libkrb5support.so.0
ELF     7e03e000-7e06c000       Deferred        libcrypt.so.1
ELF     7e06c000-7e0dc000       Deferred        libgnutls.so.13
ELF     7e0dc000-7e101000       Deferred        libk5crypto.so.3
ELF     7e101000-7e189000       Deferred        libkrb5.so.3
ELF     7e189000-7e1b2000       Deferred        libgssapi_krb5.so.2
ELF     7e1b2000-7e1e7000       Deferred        libcups.so.2
ELF     7e224000-7e227000       Deferred        libcom_err.so.2
ELF     7e234000-7e266000       Deferred        uxtheme<elf>
  \-PE  7e240000-7e266000       \               uxtheme
ELF     7e266000-7e26b000       Deferred        libxfixes.so.3
ELF     7e26b000-7e288000       Deferred        imm32<elf>
  \-PE  7e270000-7e288000       \               imm32
ELF     7e288000-7e290000       Deferred        libxrender.so.1
ELF     7e29f000-7e33f000       Deferred        libgl.so.1
ELF     7e33f000-7e344000       Deferred        libxdmcp.so.6
ELF     7e344000-7e347000       Deferred        libxau.so.6
ELF     7e347000-7e438000       Deferred        libx11.so.6
ELF     7e438000-7e446000       Deferred        libxext.so.6
ELF     7e446000-7e44b000       Deferred        libxxf86vm.so.1
ELF     7e44b000-7e463000       Deferred        libice.so.6
ELF     7e463000-7e46b000       Deferred        libsm.so.6
ELF     7e46b000-7e474000       Deferred        libxcursor.so.1
ELF     7e474000-7e47a000       Deferred        libxrandr.so.2
ELF     7e47a000-7e505000       Deferred        winex11<elf>
  \-PE  7e490000-7e505000       \               winex11
ELF     7e55b000-7e57b000       Deferred        libexpat.so.1
ELF     7e57b000-7e5a6000       Deferred        libfontconfig.so.1
ELF     7e5a6000-7e5bb000       Deferred        libz.so.1
ELF     7e5bb000-7e62b000       Deferred        libfreetype.so.6
ELF     7e62b000-7e651000       Deferred        odbc32<elf>
  \-PE  7e630000-7e651000       \               odbc32
ELF     7e651000-7e6df000       Deferred        winmm<elf>
  \-PE  7e660000-7e6df000       \               winmm
ELF     7e6df000-7e701000       Deferred        oledlg<elf>
  \-PE  7e6f0000-7e701000       \               oledlg
ELF     7e701000-7e72e000       Deferred        ws2_32<elf>
  \-PE  7e710000-7e72e000       \               ws2_32
ELF     7e72e000-7e748000       Deferred        wsock32<elf>
  \-PE  7e730000-7e748000       \               wsock32
ELF     7e748000-7e77d000       Deferred        winspool<elf>
  \-PE  7e750000-7e77d000       \               winspool
ELF     7e77d000-7e7d6000       Deferred        shlwapi<elf>
  \-PE  7e790000-7e7d6000       \               shlwapi
ELF     7e7d6000-7e8d9000       Deferred        shell32<elf>
  \-PE  7e7f0000-7e8d9000       \               shell32
ELF     7e8d9000-7e97a000       Deferred        comdlg32<elf>
  \-PE  7e8e0000-7e97a000       \               comdlg32
ELF     7e97a000-7ea38000       Deferred        comctl32<elf>
  \-PE  7e980000-7ea38000       \               comctl32
ELF     7ea38000-7ea4c000       Deferred        lz32<elf>
  \-PE  7ea40000-7ea4c000       \               lz32
ELF     7ea4c000-7ea66000       Deferred        version<elf>
  \-PE  7ea50000-7ea66000       \               version
ELF     7ea66000-7ea86000       Deferred        mpr<elf>
  \-PE  7ea70000-7ea86000       \               mpr
ELF     7ea86000-7ea99000       Deferred        libresolv.so.2
ELF     7eaa8000-7eac6000       Deferred        iphlpapi<elf>
  \-PE  7eab0000-7eac6000       \               iphlpapi
ELF     7eac6000-7eb1f000       Deferred        rpcrt4<elf>
  \-PE  7ead0000-7eb1f000       \               rpcrt4
ELF     7eb1f000-7ebc0000       Deferred        ole32<elf>
  \-PE  7eb30000-7ebc0000       \               ole32
ELF     7ebc0000-7ec5e000       Deferred        oleaut32<elf>
  \-PE  7ebd0000-7ec5e000       \               oleaut32
ELF     7ec5e000-7eca7000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca7000       \               advapi32
ELF     7eca7000-7ed42000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed42000       \               gdi32
ELF     7ed42000-7ee80000       Deferred        user32<elf>
  \-PE  7ed60000-7ee80000       \               user32
ELF     7ef9f000-7efaa000       Deferred        libnss_files.so.2
ELF     7efaa000-7efb4000       Deferred        libnss_nis.so.2
ELF     7efb4000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c83000-b7c87000       Deferred        libdl.so.2
ELF     b7c87000-b7dd1000       Deferred        libc.so.6
ELF     b7dd2000-b7dea000       Deferred        libpthread.so.0
ELF     b7df9000-b7f0d000       Dwarf           libwine.so.1
ELF     b7f0f000-b7f2b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Design Explorer 99 SE\Client99SE.exe
        00000009    0 <==
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.
raub@monaco:~$ 
```

Knowing this is the first time I am running wine, what is it trying to tell me besides it will seem to start and then burps?

---

### Post by cogadh on 2008-05-14
Protel does not work fully in Wine, but according to the AppDB page for it, you need to install Windows ODBC driver to get it to work as much as it does:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4910](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4910)
Before you do that, I would recommend you update to the latest Wine version available for Gutsy, 0.9.59. It works significantly better than 0.9.46 did. There are instructions for updating stickied at the top of the forums.

---

### Post by supremedalek on 2008-05-14
After posting, I did upgrade the version of wine using the instructions on [http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644). About the Windows ODBC driver, where can I find it? google gives me specific database-related drivers.

---

### Post by cogadh on 2008-05-14
The easiest thing to do would be to use WineTricks to install it:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
You can use it to automatically install MDAC 2.5, 2.7 or 2.8 (MDAC is the MS ODBC driver).

---

### Post by sarang on 2009-05-21
Protel 99 SE SP6 seems to work with wine 1.1.21 on Ubuntu 9.04 Jaunty after installing overrides for (all / some of) odbc32, odbccp32, ole32, oleaut32, rpcrt4 libraries. Installed selecting win 95 as the OS and being run on win 98.

---

### Post by albinootje on 2009-05-21
[irrelevant comment removed]

---

### Post by cogadh on 2009-05-21
> **albinootje said:**
> Ubuntu Gutsy has reached end of life (you won't get security updates anymore), think about upgrading to the LTS release Hardy :
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

That'll also give you Wine 1.0 :
[http://packages.ubuntu.com/search?keywords=wine](http://packages.ubuntu.com/search?keywords=wine)
Dude, check the date of the original post, it's from last year, before Gutsy EOL'd.

---

### Post by albinootje on 2009-05-21
> **cogadh said:**
> Dude, check the date of the original post, it's from last year, before Gutsy EOL'd.

Thanks for that correction, I'll edit my comment.

---

