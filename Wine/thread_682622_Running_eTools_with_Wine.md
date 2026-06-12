---
title: "Running eTools with Wine"
date: 2008-01-30
forum: Wine
---

### Post by Nameless_one on 2008-01-30
I am trying to run eTools (the D&D tool suite) in Wine. The AppDB has [this (link)](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8975&iTestingId=20495) page about it, and as you can see it is supposed to run perfectly. 

I encounter the following problem. I install the program and try to run it, but I get a popup error message which reads:
```
Failed to connect to datasource: [Microsoft][ODBC Driver Manager] Data source name not found and no default driver specified
```

and the command line output is:
```
$ ./eTools.exe 
fixme:spoolsv:serv_main (0 (nil))
fixme:imm:ImmReleaseContext (0x10020, 0x124690): stub
wine: Unhandled page fault on read access to 0x00000014 at address 0x10006818 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000014 in 32-bit code (0x10006818).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:10006818 ESP:0034f4d4 EBP:0034f568 EFLAGS:00010206(   - 00      - RIP1)
 EAX:0034f4d8 EBX:0034fbb8 ECX:00000000 EDX:0011004c
 ESI:00000000 EDI:0034fbb8
Stack dump:
0x0034f4d4:  00000000 00000000 1000686f 0034fbb8
0x0034f4e4:  0034fa30 00000000 0034f55c 1001ea6b
0x0034f4f4:  ffffffff 10006849 00000000 00000000
0x0034f504:  0040f3b0 0034fbb8 0034fa30 0034fbb8
0x0034f514:  00000000 00110000 00193a88 7ee6e8bc
0x0034f524:  00193a90 0034fbb8 0034f55c 7ee52db4
Backtrace:
=>1 0x10006818 in odbc++ (+0x6818) (0x0034f568)
  2 0x0040e7ea in etools (+0xe7ea) (0x0034fa28)
  3 0x00403574 in etools (+0x3574) (0x0034fa68)
  4 0x004030f6 in etools (+0x30f6) (0x0034facc)
  5 0x004b634f in core (+0x5634f) (0x0034fb68)
  6 0x004b6130 in core (+0x56130) (0x0034fbc4)
  7 0x00403e12 in etools (+0x3e12) (0x0034fe3c)
  8 0x0042538a in etools (+0x2538a) (0x0034fe7c)
  9 0x0041d6fc in etools (+0x1d6fc) (0x0034ff08)
  10 0x7b86e6d5 in kernel32 (+0x4e6d5) (0x0034ffe8)
  11 0xb7dfc1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x10006818: movl        0x14(%esi),%ecx
Modules:
Module  Address                 Debug info      Name (101 modules)
PE        350000-  3ad000       Deferred        etools
PE        3b0000-  3ff000       Deferred        generator
PE        400000-  45c000       Export          etools
PE        460000-  614000       Export          core
PE        620000-  809000       Deferred        editor
PE        810000-  927000       Deferred        customize
PE      10000000-1003a000       Export          odbc++
PE      1f7a0000-1f7d6000       Deferred        odbc32
PE      1f840000-1f857000       Deferred        odbcint
PE      39d00000-3a083000       Deferred        qt-mt307
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bd25000-7bd39000       Deferred        midimap<elf>
  \-PE  7bd30000-7bd39000       \               midimap
ELF     7bd39000-7bd5f000       Deferred        msacm32<elf>
  \-PE  7bd40000-7bd5f000       \               msacm32
ELF     7bd5f000-7bd76000       Deferred        msacm32<elf>
  \-PE  7bd60000-7bd76000       \               msacm32
ELF     7bd76000-7be3c000       Deferred        libasound.so.2
ELF     7be3c000-7be71000       Deferred        winealsa<elf>
  \-PE  7be50000-7be71000       \               winealsa
ELF     7be71000-7bec2000       Deferred        libgcrypt.so.11
ELF     7bec2000-7bed2000       Deferred        libtasn1.so.3
ELF     7bed2000-7bf00000       Deferred        libcrypt.so.1
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf08000-7bf78000       Deferred        libgnutls.so.13
ELF     7bf78000-7c000000       Deferred        libkrb5.so.3
ELF     7c376000-7c39b000       Deferred        libk5crypto.so.3
ELF     7c39b000-7c3c4000       Deferred        libgssapi_krb5.so.2
ELF     7c3c4000-7c3f9000       Deferred        libcups.so.2
ELF     7c481000-7c4b3000       Deferred        uxtheme<elf>
  \-PE  7c490000-7c4b3000       \               uxtheme
ELF     7c5b6000-7c5ba000       Deferred        libgpg-error.so.0
ELF     7cfe8000-7cfed000       Deferred        libxfixes.so.3
ELF     7cfed000-7cff6000       Deferred        libxcursor.so.1
ELF     7cff6000-7cffe000       Deferred        libxrender.so.1
ELF     7cffe000-7d000000       Deferred        libkeyutils.so.1
ELF     7d000000-7d008000       Deferred        libkrb5support.so.0
ELF     7d008000-7d00b000       Deferred        libcom_err.so.2
ELF     7d89e000-7d8a9000       Deferred        libgcc_s.so.1
ELF     7d8a9000-7d8b2000       Deferred        librt.so.1
ELF     7d96c000-7e2cf000       Deferred        fglrx_dri.so
ELF     7e2cf000-7e36f000       Deferred        libgl.so.1
ELF     7e36f000-7e374000       Deferred        libxdmcp.so.6
ELF     7e374000-7e377000       Deferred        libxau.so.6
ELF     7e377000-7e468000       Deferred        libx11.so.6
ELF     7e468000-7e476000       Deferred        libxext.so.6
ELF     7e476000-7e47b000       Deferred        libxxf86vm.so.1
ELF     7e47b000-7e493000       Deferred        libice.so.6
ELF     7e493000-7e49b000       Deferred        libsm.so.6
ELF     7e49b000-7e4a1000       Deferred        libxrandr.so.2
ELF     7e4aa000-7e539000       Deferred        winex11<elf>
  \-PE  7e4c0000-7e539000       \               winex11
ELF     7e5c9000-7e5e9000       Deferred        libexpat.so.1
ELF     7e5e9000-7e614000       Deferred        libfontconfig.so.1
ELF     7e614000-7e629000       Deferred        libz.so.1
ELF     7e629000-7e699000       Deferred        libfreetype.so.6
ELF     7e699000-7e725000       Deferred        winmm<elf>
  \-PE  7e6a0000-7e725000       \               winmm
ELF     7e725000-7e7c5000       Deferred        oleaut32<elf>
  \-PE  7e730000-7e7c5000       \               oleaut32
ELF     7e7c5000-7e7e2000       Deferred        imm32<elf>
  \-PE  7e7d0000-7e7e2000       \               imm32
ELF     7e7e2000-7e7f5000       Deferred        libresolv.so.2
ELF     7e804000-7e822000       Deferred        iphlpapi<elf>
  \-PE  7e810000-7e822000       \               iphlpapi
ELF     7e822000-7e880000       Deferred        rpcrt4<elf>
  \-PE  7e830000-7e880000       \               rpcrt4
ELF     7e880000-7e91f000       Deferred        ole32<elf>
  \-PE  7e890000-7e91f000       \               ole32
ELF     7e91f000-7e954000       Deferred        winspool<elf>
  \-PE  7e930000-7e954000       \               winspool
ELF     7e954000-7e9f3000       Deferred        comdlg32<elf>
  \-PE  7e960000-7e9f3000       \               comdlg32
ELF     7e9f3000-7ea4a000       Deferred        shlwapi<elf>
  \-PE  7ea00000-7ea4a000       \               shlwapi
ELF     7ea4a000-7eb4e000       Deferred        shell32<elf>
  \-PE  7ea60000-7eb4e000       \               shell32
ELF     7eb4e000-7eb98000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb98000       \               advapi32
ELF     7eb98000-7ec2f000       Deferred        gdi32<elf>
  \-PE  7ebb0000-7ec2f000       \               gdi32
ELF     7ec2f000-7ed66000       Deferred        user32<elf>
  \-PE  7ec50000-7ed66000       \               user32
ELF     7ed66000-7ee25000       Deferred        comctl32<elf>
  \-PE  7ed70000-7ee25000       \               comctl32
ELF     7ee25000-7ee8a000       Deferred        msvcrt<elf>
  \-PE  7ee30000-7ee8a000       \               msvcrt
ELF     7efa9000-7efb4000       Deferred        libnss_files.so.2
ELF     7efb4000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c75000-b7c7e000       Deferred        libnss_compat.so.2
ELF     b7c7f000-b7c83000       Deferred        libdl.so.2
ELF     b7c83000-b7dcd000       Deferred        libc.so.6
ELF     b7dce000-b7de6000       Deferred        libpthread.so.0
ELF     b7df5000-b7f09000       Export          libwine.so.1
ELF     b7f0b000-b7f27000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Wizards of the Coast\eTools\eTools.exe
        00000009    0 <==
0000000a 
        0000000b    0
00000010 
        00000012    0
        00000011    0
Backtrace:
=>1 0x10006818 in odbc++ (+0x6818) (0x0034f568)
  2 0x0040e7ea in etools (+0xe7ea) (0x0034fa28)
  3 0x00403574 in etools (+0x3574) (0x0034fa68)
  4 0x004030f6 in etools (+0x30f6) (0x0034facc)
  5 0x004b634f in core (+0x5634f) (0x0034fb68)
  6 0x004b6130 in core (+0x56130) (0x0034fbc4)
  7 0x00403e12 in etools (+0x3e12) (0x0034fe3c)
  8 0x0042538a in etools (+0x2538a) (0x0034fe7c)
  9 0x0041d6fc in etools (+0x1d6fc) (0x0034ff08)
  10 0x7b86e6d5 in kernel32 (+0x4e6d5) (0x0034ffe8)
  11 0xb7dfc1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

I have followed the advice of the people on AppDB (btw, I am Mikey there, the person who commented last), and I still got this. I tried several Windows versions, but the problem remains. 

Any ideas?

---

### Post by Nameless_one on 2008-01-31
Bump.

---

### Post by Nameless_one on 2008-02-20
By the way, I solved this by installing the MySql driver for ODBC as intructed somewhere in the WineHQ page.

---

### Post by radionausea on 2011-06-10
I realise that this is thread necromancy of an appalling kind and I do apologise

I swapped over to Ubuntu yesterday and I have the same problem described above.

I've downloaded unixODBC, and followed the instructions.

I also followed the instructions here:
[http://howtoforge.com/adding-an-odbc-driver-for-mysql-on-ubuntu](http://howtoforge.com/adding-an-odbc-driver-for-mysql-on-ubuntu)

but I cannot find the drivers anywhere.

I am an absolute novice.  I've only just figured out how to navigate using the terminal.

Could somebody please help, preferably with instructions suitable for a 107 year old dealing with a pc for the first time?  

Thanks in advance

---

