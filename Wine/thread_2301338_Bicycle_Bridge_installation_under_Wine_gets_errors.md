---
title: "Bicycle Bridge installation under Wine gets errors"
date: 2015-11-01
forum: Wine
---

### Post by Ralph L on 2015-11-01
I posted this message in Wine Forums, but have gotten no response.  Because participants in this forum are usually very helpful and have a great deal of experience with all facets of Linux (including Wine), I am taking the liberty of posting it here.  I hope I am not violating any rule.  I don't understand enough about linux (and/or windows) to solve my problem.

I have installed Wine 1.7.5.0, which I believe is the latest version (unstable). I am trying to install Bicycle Bridge using Wine, under Terminal, so I can get error messages. Listed below are the error messages. The important one is probably the unhandled page fault. In spite of the installation errors the game does get installed and the installed game does mostly work. The only parts that don't seem to work is that the game freezes (and must be xkilled at times), and the Help features only partially work.

I am trying to understand the error messages from the installation, and what can be done to fix them.  It may require only another Windows .dll, or something else.  NOTE:  I can also post the error messages I get, when I actually run Bicycle Bridge, but I thought the installation errors should be resolved first.   Any help is much appreciated........
```
ralph@lat1:/media/ralph/BBRIDGE$ wine setup.exe
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err:ntdll:RtlpWaitForCriticalSection section 0x7ea04780 "syslevel.c: Win16Mutex" wait timed out in thread 0028, blocked by 0029, retrying (60 sec)
fixme:shell:Dde_OnRequest returning fake program groups list
fixme:shell:Dde_OnExecute stub: L"Progman" L"[CreateGroup(Expert Software,1)][AddItem(\"C:\\Program Files\\Expert Software\\Bicycle\00ae Bridge\\Bbridge.exe\",Bicycle\00ae Bridge,\"C:\\Program Files\\Expert Software\\Bicycle\00ae Bridge\\Bbridge.exe\",0,-1,-1,\"C:\\Program Files\\Expert Software\\Bicycle\00ae Bridge\\\",,0,0)]"
fixme:shell:Dde_OnRequest returning fake program groups list
fixme:shell:Dde_OnExecute stub: L"Progman" L"[CreateGroup(Expert Software,1)][AddItem(NOTEPAD.EXE C:\\Program Files\\Expert Software\\Bicycle\00ae Bridge\\README.TXT,Bicycle\00ae Bridge Readme,,0,-1,-1,\"C:\\Program Files\\Expert Software\\Bicycle\00ae Bridge\\\",,0,0)]"
fixme:shell:Dde_OnRequest returning fake program groups list
fixme:shell:Dde_OnExecute stub: L"Progman" L"[CreateGroup(Expert Software,1)][AddItem(D:\\Bridge.pdf,Bicycle\00ae Bridge Online Manual,\"C:\\Program Files\\Expert Software\\Bicycle\00ae Bridge\\pdf.ico\",0,-1,-1,D:\\,,0,0)]"
fixme:shell:Dde_OnRequest returning fake program groups list
fixme:shell:Dde_OnExecute stub: L"Progman" L"[CreateGroup(Expert Software,1)][AddItem(D:\\catalog\\excatv2.exe,Online Catalog,,0,-1,-1,D:\\catalog\\,,0,0)]"
fixme:toolhelp:InterruptRegister16 (0000, 0x11cf00ba), stub.
wine: Unhandled page fault on read access to 0x00001428 at address 0x1267:0x00000cdb (thread 002f), starting debugger...
Unhandled exception: page fault on read access to 0x00001428 in 16-bit code (1267:0cdb).
fixme:dbghelp:addr_to_linear Failed to linearize address 5011:ef02 (mode 0)
fixme:dbghelp:addr_to_linear Failed to linearize address 4412:1f2f (mode 0)
In 16 bit mode.
Register dump:
 CS:1267 SS:123f DS:12bf ES:139f FS:0033 GS:003b
 IP:0cdb SP:4fe2 BP:4fe4 FLAGS:0202(  R- --  I   - - - )
 AX:142f BX:116c CX:0000 DX:142f SI:129c DI:1044
Stack dump:
0x123f:0x4fe2:  12bf 4ff5 0e25 1267 0050 142e 139f 4ffc
0x123f:0x4ff2:  123f 4fff 0202 11ef 0050 142e 5010 2f2f
0x123f:0x5002:  121f 1044 139f 0001 1044 139f 0001 501c
0257: sel=12bf base=003e1b28 limit=0000355f 16-bit rw-
0273: sel=139f base=003eec50 limit=00001fff 16-bit rw-
Backtrace:
=>0 0x1267:0x0cdb (0x123f:0x4fe4)
  1 0x1267:0x0e25 (0x123f:0x4ff4)
  2 0x5011:0xef02 (0x123f:0x4ffe)
  3 0x4412:0x1f2f (0x123f:0x5010)
  4 0x1227:0x1f89 (0x123f:0x501c)
  5 0x1227:0x2856 (0x123f:0x5028)
  6 0x122f:0x4bc1 (0x123f:0x5038)
  7 0x1227:0x0e1e (0x123f:0x5046)
  8 0x1237:0x0496 (0x123f:0x5054)
  9 0x1237:0x251a (0x123f:0x0000)
0x1267:0x0cdb: lesw   0x6(%bp),%bx
Modules:
Module   Address         Debug info   Name (113 modules)
PE   71590000-71617000   Deferred        comctl32
ELF   7b800000-7ba68000   Deferred        kernel32<elf>
  \-PE   7b810000-7ba68000   \               kernel32
ELF   7bc00000-7bcf0000   Deferred        ntdll<elf>
  \-PE   7bc10000-7bcf0000   \               ntdll
ELF   7bf00000-7bf04000   Deferred        <wine-loader>
ELF   7d72f000-7d773000   Deferred        usp10<elf>
  \-PE   7d740000-7d773000   \               usp10
ELF   7d7b7000-7d7ce000   Deferred        toolhelp.dll16.so
PE   7d7c0000-7d7ce000   Deferred        toolhelp.dll16
ELF   7d7ce000-7d7d7000   Deferred        librt.so.1
ELF   7d7d7000-7d7de000   Deferred        libffi.so.6
ELF   7d7de000-7d7e3000   Deferred        libgpg-error.so.0
ELF   7d7e3000-7d7fb000   Deferred        libresolv.so.2
ELF   7d7fb000-7d7ff000   Deferred        libkeyutils.so.1
ELF   7d7ff000-7d84a000   Deferred        libdbus-1.so.3
ELF   7d84a000-7d886000   Deferred        libp11-kit.so.0
ELF   7d886000-7d89a000   Deferred        libtasn1.so.6
ELF   7d89a000-7d920000   Deferred        libgcrypt.so.11
ELF   7d920000-7d92c000   Deferred        libkrb5support.so.0
ELF   7d92c000-7d95c000   Deferred        libk5crypto.so.3
ELF   7d95c000-7da1a000   Deferred        libkrb5.so.3
ELF   7da1a000-7da2c000   Deferred        libavahi-client.so.3
ELF   7da2c000-7daf2000   Deferred        libgnutls.so.26
ELF   7daf2000-7db37000   Deferred        libgssapi_krb5.so.2
ELF   7db37000-7dba4000   Deferred        libcups.so.2
ELF   7dba5000-7dbba000   Deferred        win87em.dll16.so
PE   7dbb0000-7dbba000   Deferred        win87em.dll16
ELF   7dc00000-7dc06000   Deferred        libxfixes.so.3
ELF   7dc06000-7dc11000   Deferred        libxcursor.so.1
ELF   7dc11000-7dc21000   Deferred        libxi.so.6
ELF   7dc21000-7dc25000   Deferred        libxcomposite.so.1
ELF   7dc25000-7dc30000   Deferred        libxrandr.so.2
ELF   7dc30000-7dc3b000   Deferred        libxrender.so.1
ELF   7dc3b000-7dc41000   Deferred        libxxf86vm.so.1
ELF   7dc41000-7dc45000   Deferred        libxinerama.so.1
ELF   7dc45000-7dc4c000   Deferred        libxdmcp.so.6
ELF   7dc4c000-7dc50000   Deferred        libxau.so.6
ELF   7dc50000-7dc72000   Deferred        libxcb.so.1
ELF   7dc72000-7dda6000   Deferred        libx11.so.6
ELF   7dda6000-7ddb9000   Deferred        libxext.so.6
ELF   7ddb9000-7de4d000   Deferred        winex11<elf>
  \-PE   7ddc0000-7de4d000   \               winex11
ELF   7de4d000-7dec8000   Deferred        shlwapi<elf>
  \-PE   7de60000-7dec8000   \               shlwapi
ELF   7dec8000-7e112000   Deferred        shell32<elf>
  \-PE   7dee0000-7e112000   \               shell32
ELF   7e112000-7e200000   Deferred        comdlg32<elf>
  \-PE   7e120000-7e200000   \               comdlg32
ELF   7e301000-7e306000   Deferred        libcom_err.so.2
ELF   7e306000-7e314000   Deferred        libavahi-common.so.3
ELF   7e316000-7e359000   Deferred        winspool<elf>
  \-PE   7e320000-7e359000   \               winspool
ELF   7e359000-7e370000   Deferred        commdlg.dll16.so
PE   7e360000-7e370000   Deferred        commdlg.dll16
ELF   7e370000-7e385000   Deferred        sound.drv16.so
PE   7e380000-7e385000   Deferred        sound.drv16
ELF   7e385000-7e3b0000   Deferred        msacm32<elf>
  \-PE   7e390000-7e3b0000   \               msacm32
ELF   7e3b0000-7e434000   Deferred        rpcrt4<elf>
  \-PE   7e3c0000-7e434000   \               rpcrt4
ELF   7e434000-7e577000   Deferred        ole32<elf>
  \-PE   7e450000-7e577000   \               ole32
ELF   7e577000-7e631000   Deferred        winmm<elf>
  \-PE   7e580000-7e631000   \               winmm
ELF   7e631000-7e65d000   Deferred        mmsystem.dll16.so
PE   7e640000-7e65d000   Deferred        mmsystem.dll16
ELF   7e65d000-7e671000   Deferred        mouse.drv16.so
PE   7e660000-7e671000   Deferred        mouse.drv16
ELF   7e671000-7e686000   Deferred        keyboard.drv16.so
PE   7e680000-7e686000   Deferred        keyboard.drv16
ELF   7e686000-7e69b000   Deferred        display.drv16.so
PE   7e690000-7e69b000   Deferred        display.drv16
ELF   7e69b000-7e6c3000   Deferred        mpr<elf>
  \-PE   7e6a0000-7e6c3000   \               mpr
ELF   7e6c3000-7e713000   Deferred        user.exe16.so
PE   7e6d0000-7e713000   Deferred        user.exe16
ELF   7e713000-7e746000   Deferred        gdi.exe16.so
PE   7e720000-7e746000   Deferred        gdi.exe16
ELF   7e746000-7e75b000   Deferred        comm.drv16.so
PE   7e750000-7e75b000   Deferred        comm.drv16
ELF   7e75b000-7e770000   Deferred        system.drv16.so
PE   7e760000-7e770000   Deferred        system.drv16
ELF   7e770000-7e795000   Deferred        imm32<elf>
  \-PE   7e780000-7e795000   \               imm32
ELF   7e81c000-7e845000   Deferred        libexpat.so.1
ELF   7e845000-7e880000   Deferred        libfontconfig.so.1
ELF   7e880000-7e8a8000   Deferred        libpng12.so.0
ELF   7e8a8000-7e8c2000   Deferred        libz.so.1
ELF   7e8c2000-7e962000   Deferred        libfreetype.so.6
ELF   7e962000-7ea0c000   Deferred        krnl386.exe16.so
PE   7e970000-7ea0c000   Deferred        krnl386.exe16
ELF   7ea0c000-7ea26000   Deferred        version<elf>
  \-PE   7ea10000-7ea26000   \               version
ELF   7ea26000-7eaa1000   Deferred        advapi32<elf>
  \-PE   7ea30000-7eaa1000   \               advapi32
ELF   7eaa1000-7ebc0000   Deferred        gdi32<elf>
  \-PE   7eab0000-7ebc0000   \               gdi32
ELF   7ebc0000-7ed1c000   Deferred        user32<elf>
  \-PE   7ebd0000-7ed1c000   \               user32
ELF   7ed1c000-7ed33000   Deferred        winevdm<elf>
  \-PE   7ed20000-7ed33000   \               winevdm
ELF   7ed33000-7ed40000   Deferred        libnss_files.so.2
ELF   7ed40000-7ed4c000   Deferred        libnss_nis.so.2
ELF   7ed4c000-7ed65000   Deferred        libnsl.so.1
ELF   7efa4000-7efea000   Deferred        libm.so.6
ELF   b73f4000-b73fd000   Deferred        libnss_compat.so.2
ELF   b73fe000-b75ac000   Deferred        libc.so.6
ELF   b75ac000-b75b1000   Deferred        libdl.so.2
ELF   b75b2000-b75ce000   Deferred        libpthread.so.0
ELF   b75e4000-b779a000   Dwarf           libwine.so.1
ELF   b779c000-b77be000   Deferred        ld-linux.so.2
ELF   b77c0000-b77c1000   Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
   0000001e    0
   0000001d    0
   00000014    0
   00000010    0
   0000000f    0
00000012 winedevice.exe
   0000001c    0
   00000019    0
   00000018    0
   00000013    0
0000001a plugplay.exe
   00000020    0
   0000001f    0
   0000001b    0
00000021 explorer.exe
   00000025    0
   00000024    0
   00000023    0
   00000022    0
00000026 winevdm.exe
   0000002c    0
   00000029    0
   00000027    0
0000002a _ins0432._mp
   0000002b    0
0000002d (D) C:\windows\system32\winevdm.exe
   0000002f    0 <==
   0000002e    0
System information:
    Wine build: wine-1.7.50
    Platform: i386
    Host system: Linux
    Host version: 3.19.8-992-generi
```

---

### Post by howefield on 2015-11-01
Thread moved to the "*Wine*" sub forum.

---

### Post by Ralph L on 2015-12-03
I posted this question about 4 weeks ago and have gotten no responses.  If anybody knows why I got the unhandled page fault and other errors, I would appreciate a response.  My guess is that I am missing some required .dll or other standard Windows program.

Thank you very much in advance.

Ralph

---

