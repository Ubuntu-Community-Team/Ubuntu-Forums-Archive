---
title: "Wine bug report question"
date: 2008-03-23
forum: Wine
---

### Post by Zeikcied on 2008-03-23
I have a question about reporting a Wine bug.

I found another thread that linked to a Wine Wiki page on bug reports, but I want some clarification.

I have a game, Total Extreme Wrestling 2007.  I got it running in Wine using ies4linux (because it requires ActiveX) and a series of Windows native DLL and OCX files copied to the ies4linux install.  It has worked perfectly fine for over a year, but the three most recent Wine versions (including the newest one) have broken the game.

It starts fine, but then when I hit a button to go to another screen, it crashes shortly after displaying the new screen.  It has a long list of messages when I run it in the console window, and it looks like this:

```
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {7fd52380-4e07-101b-ae2d-08002b2ec713}
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {37d84f60-42cb-11ce-8135-00aa004bb851}
fixme:quartz:MediaControl_RenderFile (0x14c058/0x14c05c)->(L"C:\\Program Files\\GDS\\TEW2007\\music\\reborn.wma" (0x149f54)): stub !!!
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {df0b3d60-548f-101b-8e65-08002b2bd119}
wine: Unhandled page fault on read access to 0x028f2f3c at address 0xb7db5cbc (thread 002c), starting debugger...
Unhandled exception: page fault on read access to 0x028f2f3c in 32-bit code (0xb7db5cbc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7db5cbc ESP:0034f220 EBP:0034f2fc EFLAGS:00010216(   - 00      -RIAP1)
 EAX:00000001 EBX:7ea5dc6c ECX:00000055 EDX:00166510
 ESI:028f2f3c EDI:02fc0000
Stack dump:
0x0034f220:  7ea0840d 02fc0000 028f2f3c 00000154
0x0034f230:  00000000 00000000 00000000 00180000
0x0034f240:  00000000 00000154 028f2f3c 02fc0000
0x0034f250:  00000154 00000154 0000001c 00000071
0x0034f260:  0000001c 00000000 00000071 0000001c
0x0034f270:  00000154 00180001 02fc0000 7ed42be0
Backtrace:
=>1 0xb7db5cbc memcpy+0x1c() in libc.so.6 (0x0034f2fc)
  2 0x7ecec976 SetDIBits+0x190() in gdi32 (0x0034f33c)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file "asycfilt.dbg" ("")
  3 0x003c6e94 in asycfilt (+0x6e94) (0x0034f388)
  4 0x003c6a13 in asycfilt (+0x6a13) (0x0034f3f8)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file "oleaut32.dbg" ("")
  5 0x653a03c7 in oleaut32 (+0x603c7) (0x66054f38)
  6 0x08758b56 (0x53ec8b55)
  7 0x00000000 (0x00000000)
0xb7db5cbc memcpy+0x1c in libc.so.6: repe movsl (%esi),%es:(%edi)
Modules:
Module  Address                 Debug info      Name (104 modules)
PE        3c0000-  3e6000       Export          asycfilt
PE        400000- 1217000       Deferred        tew2007
PE       2480000- 24a8000       Deferred        elicen40
PE      10000000-10047000       Deferred        lcmmfu.cpl
PE      65340000-653d2000       Export          oleaut32
PE      65f00000-65fc2000       Deferred        ole32
PE      66000000-66152000       Deferred        msvbvm60
PE      6b800000-6b825000       Deferred        scrrun
PE      70bd0000-70c35000       Deferred        shlwapi
PE      78000000-78044000       Deferred        msvcrt
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dcc2000-7dccd000       Deferred        libgcc_s.so.1
ELF     7df92000-7dfa6000       Deferred        midimap<elf>
  \-PE  7dfa0000-7dfa6000       \               midimap
ELF     7dfa6000-7e06c000       Deferred        libasound.so.2
ELF     7e06d000-7e084000       Deferred        msacm32<elf>
  \-PE  7e070000-7e084000       \               msacm32
ELF     7e084000-7e0b9000       Deferred        winealsa<elf>
  \-PE  7e090000-7e0b9000       \               winealsa
ELF     7e0b9000-7e0e1000       Deferred        msvfw32<elf>
  \-PE  7e0c0000-7e0e1000       \               msvfw32
ELF     7e0e1000-7e16d000       Deferred        winmm<elf>
  \-PE  7e0f0000-7e16d000       \               winmm
ELF     7e16d000-7e1b7000       Deferred        dsound<elf>
  \-PE  7e170000-7e1b7000       \               dsound
ELF     7e1b7000-7e219000       Deferred        quartz<elf>
  \-PE  7e1c0000-7e219000       \               quartz
ELF     7e241000-7e267000       Deferred        msacm32<elf>
  \-PE  7e250000-7e267000       \               msacm32
ELF     7e2ad000-7e2ca000       Deferred        imm32<elf>
  \-PE  7e2b0000-7e2ca000       \               imm32
ELF     7e2ca000-7e31b000       Deferred        libgcrypt.so.11
ELF     7e31b000-7e31f000       Deferred        libgpg-error.so.0
ELF     7e31f000-7e32f000       Deferred        libtasn1.so.3
ELF     7e32f000-7e337000       Deferred        libkrb5support.so.0
ELF     7e337000-7e365000       Deferred        libcrypt.so.1
ELF     7e365000-7e3d5000       Deferred        libgnutls.so.13
ELF     7e3d5000-7e3fa000       Deferred        libk5crypto.so.3
ELF     7e3fa000-7e482000       Deferred        libkrb5.so.3
ELF     7e482000-7e4ab000       Deferred        libgssapi_krb5.so.2
ELF     7e4ab000-7e4e0000       Deferred        libcups.so.2
ELF     7e583000-7e5b5000       Deferred        uxtheme<elf>
  \-PE  7e590000-7e5b5000       \               uxtheme
ELF     7e5b5000-7e5da000       Deferred        netapi32<elf>
  \-PE  7e5c0000-7e5da000       \               netapi32
ELF     7e5da000-7e60f000       Deferred        winspool<elf>
  \-PE  7e5e0000-7e60f000       \               winspool
ELF     7e60f000-7e6ce000       Deferred        comctl32<elf>
  \-PE  7e620000-7e6ce000       \               comctl32
ELF     7e6ce000-7e7d4000       Deferred        shell32<elf>
  \-PE  7e6e0000-7e7d4000       \               shell32
ELF     7e7d4000-7e874000       Deferred        comdlg32<elf>
  \-PE  7e7e0000-7e874000       \               comdlg32
ELF     7e874000-7e87d000       Deferred        libxcursor.so.1
ELF     7e87d000-7e882000       Deferred        libxfixes.so.3
ELF     7e882000-7e885000       Deferred        libxcomposite.so.1
ELF     7e885000-7e88b000       Deferred        libxrandr.so.2
ELF     7e88b000-7e893000       Deferred        libxrender.so.1
ELF     7e893000-7e898000       Deferred        libxdmcp.so.6
ELF     7e898000-7e89b000       Deferred        libxau.so.6
ELF     7e89b000-7e98c000       Deferred        libx11.so.6
ELF     7e98c000-7e99a000       Deferred        libxext.so.6
ELF     7e99a000-7e99f000       Deferred        libxxf86vm.so.1
ELF     7e99f000-7e9b7000       Deferred        libice.so.6
ELF     7e9b7000-7e9bf000       Deferred        libsm.so.6
ELF     7e9c0000-7e9c2000       Deferred        libkeyutils.so.1
ELF     7e9c2000-7e9c5000       Deferred        libcom_err.so.2
ELF     7e9d7000-7ea65000       Deferred        winex11<elf>
  \-PE  7e9e0000-7ea65000       \               winex11
ELF     7eae7000-7eb07000       Deferred        libexpat.so.1
ELF     7eb07000-7eb32000       Deferred        libfontconfig.so.1
ELF     7eb32000-7eb47000       Deferred        libz.so.1
ELF     7eb47000-7ebb7000       Deferred        libfreetype.so.6
ELF     7ebb7000-7ebca000       Deferred        libresolv.so.2
ELF     7ebe2000-7ec00000       Deferred        iphlpapi<elf>
  \-PE  7ebf0000-7ec00000       \               iphlpapi
ELF     7ec00000-7ec2b000       Deferred        ws2_32<elf>
  \-PE  7ec10000-7ec2b000       \               ws2_32
ELF     7ec2b000-7ec44000       Deferred        wsock32<elf>
  \-PE  7ec30000-7ec44000       \               wsock32
ELF     7ec44000-7ec58000       Deferred        lz32<elf>
  \-PE  7ec50000-7ec58000       \               lz32
ELF     7ec58000-7ec71000       Deferred        version<elf>
  \-PE  7ec60000-7ec71000       \               version
ELF     7ec71000-7ecbb000       Deferred        advapi32<elf>
  \-PE  7ec80000-7ecbb000       \               advapi32
ELF     7ecbb000-7ed53000       Export          gdi32<elf>
  \-PE  7ecd0000-7ed53000       \               gdi32
ELF     7ed53000-7ee8f000       Deferred        user32<elf>
  \-PE  7ed70000-7ee8f000       \               user32
ELF     7efae000-7efb9000       Deferred        libnss_files.so.2
ELF     7efb9000-7efc3000       Deferred        libnss_nis.so.2
ELF     7efc3000-7efe8000       Deferred        libm.so.6
ELF     7efe8000-7f000000       Deferred        libnsl.so.1
ELF     b7d36000-b7d3f000       Deferred        libnss_compat.so.2
ELF     b7d40000-b7d44000       Deferred        libdl.so.2
ELF     b7d44000-b7e8e000       Export          libc.so.6
ELF     b7e8f000-b7ea7000       Deferred        libpthread.so.0
ELF     b7ebf000-b7fd3000       Deferred        libwine.so.1
ELF     b7fd5000-b7ff1000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
0000000c
        00000014   15
        0000000d   -1
0000000e
        00000011    0
        00000010    0
        0000000f    0
00000015
        00000017    0
        00000016    0
0000002b (D) C:\Program Files\GDS\TEW2007\TEW2007.exe
        0000002c    0 <==
Backtrace:
=>1 0xb7db5cbc memcpy+0x1c() in libc.so.6 (0x0034f2fc)
  2 0x7ecec976 SetDIBits+0x190() in gdi32 (0x0034f33c)
  3 0x003c6e94 in asycfilt (+0x6e94) (0x0034f388)
  4 0x003c6a13 in asycfilt (+0x6a13) (0x0034f3f8)
  5 0x653a03c7 in oleaut32 (+0x603c7) (0x66054f38)
  6 0x08758b56 (0x53ec8b55)
  7 0x00000000 (0x00000000)
err:syslevel:_CheckNotSysLevel Holding lock 0x7ed42be0 level 3
err:syslevel:_CheckNotSysLevel Holding lock 0x7ed42be0 level 3
err:syslevel:_CheckNotSysLevel Holding lock 0x7ed42be0 level 3
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee54e80, level 2): Holding 0x7ed42be0, level 3. Expect deadlock!

```

Now, because I'm using ies4linux, and not a default Wine install, and because I'm using some native Windows system files (or at least I think I still am), I don't think I can make a bug report, according to the Wine Wiki.  But it's still bothersome, because it used to work perfectly, but the new Wine versions broke it.

I don't know if I should make a bug report or not.

---

### Post by tkiesel on 2008-03-23
Your best bet is to follow the Wine project's guidelines for posting bug reports.  It's sad I know, but you might be in a spot where you have to hope for future Wine updates to fix it back up.

Another possibility is:  Try installing the Windows version of Firefox 1.5 in Wine and see if you can get the [ActiveX firefox plugin]("http://support.mozilla.com/en-US/kb/ActiveX") to work.

---

### Post by Zeikcied on 2008-04-30
> **tkiesel said:**
> Your best bet is to follow the Wine project's guidelines for posting bug reports.  It's sad I know, but you might be in a spot where you have to hope for future Wine updates to fix it back up.

Another possibility is:  Try installing the Windows version of Firefox 1.5 in Wine and see if you can get the [ActiveX firefox plugin]("http://support.mozilla.com/en-US/kb/ActiveX") to work.
I finally got around to doing this, because my problem still isn't fixed with Wine 0.9.60.

I got Firefox 1.5.12, and I installed the "Plug-in for ActiveX controls," and the "Mozilla ActiveX control," and it doesn't work as an ies4linux substitute.

Is there any special directory I have to install the Mozilla ActiveX Control?  The directory that came up in the installer was c:\Program Files\Mozilla ActiveX Control v1.7.12.  I just assumed that was the right place.

Oh, the error I get from the game is:

```
Run-time error '429':

ActiveX component can't create object
```

It gets past that part in ies4linux, but then it still crashes like described in my original post.

---

### Post by Zeikcied on 2008-05-23
Wine 1.0-RC1 hasn't fixed anything yet.

So I have a couple questions.

Should I just delete and reinstall ies4linux?  I installed a newer version on top of of an older one, but I don't know what all it overwrote.  Would a fresh install help?

Second, I recall reading that you should delete your .wine directory every so often, so that newer versions of the files are generated.  Is that true?  I haven't done that in a while.

Third, I'm not sure if I installed that Mozilla ActiveX plug-in properly.  But I'm not entirely sure if that would help, anyway.  I don't think the program uses a web browser at all.  It just initializes an ActiveX control, and I don't know what or how it does it.  Now, it can create the control just fine in ies4linux, but it won't work with Firefox 1.5 and the Mozilla ActiveX plug-in, assuming I have it installed properly.

---

### Post by Zeikcied on 2008-06-01
Still broken in Wine 1.0-RC3.  I'm starting to lose hope that this will be fixed, and I'm annoyed that I can't submit a bug report about it because I have to use ies4linux to make it work.

However, the demo of Total Extreme Wrestling 2008 runs using the ies4linux method.  Although it does experience random crashes (with the same Konsole output as the 2007 version), it can actually navigate through the menus.

In both versions, the crash only happens when navigating through menus.  (But since the games are menu-based, that renders them unusable.)  With the 2007 version, it happens every time you try to navigate.  In 2008, it happens with less frequency, but it still crashes.

Is there any hope, whatsoever?

---

