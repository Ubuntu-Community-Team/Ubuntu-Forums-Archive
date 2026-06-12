---
title: "Diablo 1"
date: 2008-01-26
forum: Wine
---

### Post by Mizutsuki on 2008-01-26
I'm trying to get Diablo 1 to run using Wine.  according to appdb it should be mostly possible:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498&iTestingId=17792](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498&iTestingId=17792)

I tried it using the ubuntu default package 0.9.46, I believe, but after the initial cutscene (sans sound) it would go to a black screen, and no amount of clicking or keypresses would do anything other than dump me back to the desktop.  So I upgraded to 0.9.54, and now I don't even get the initial cutscene.
I followed the instructions in the appdb and placed the appropriate ddraw.dll in the diablo directory for 9.46, unfortunately I can't find one for anything newer than 9.52, so I don't know if that's causing a problem.  Below is the console output:
```
stephen@Vervet:~/.wine/drive_c/Diablo$ wine Diablo.exe 
fixme:spoolsv:serv_main (0 (nil))
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
stephen@Vervet:~/.wine/drive_c/Diablo$ fixme:win:EnumDisplayDevicesW ((null),0,0x34f840,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel This is a hacked ddraw drawing to the desktop window instead of the window the app requested!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8


























fixme:msg:pack_message WM_NCPAINT hdc packing not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
stephen@Vervet:~/.wine/drive_c/Diablo$ wine: Unhandled page fault on write access to 0x000001e0 at address 0x7ce3a944 (thread 0011), starting debugger...
Unhandled exception: page fault on write access to 0x000001e0 in 32-bit code (0x7ce3a944).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ce3a944 ESP:0034f8a4 EBP:0034f8fc EFLAGS:00010a02(   - 00      - ROI1)
 EAX:80004002 EBX:7cef98bc ECX:0000000f EDX:000001e0
 ESI:0034fa49 EDI:7cef437d
Stack dump:
0x0034f8a4:  04030006 7cefa35c 7ce96d6b 7cef98bc
0x0034f8b4:  00000000 00110000 7ce9803c 7cef98bc
0x0034f8c4:  00132670 0004b000 0034f8fc 7ceabe89
0x0034f8d4:  00132670 00000000 001752e8 7cef438c
0x0034f8e4:  00000000 00110000 0034fa48 7cef98bc
0x0034f8f4:  00134d80 0034fa48 0034f94c 7ce96e27
Backtrace:
=>1 0x7ce3a944 in wined3d (+0x1a944) (0x0034f8fc)
  2 0x7ce96e27 IWineD3DBaseSurfaceImpl_GetContainer+0xc7() in wined3d (0x0034f94c)
  3 0x7cf14b67 in ddraw (+0x18b67) (0x0034fa9c)
  4 0x7cf157a9 in ddraw (+0x197a9) (0x0034fc3c)
  5 0x7cf18324 in ddraw (+0x1c324) (0x0034fc7c)
  6 0x00415603 in diablo (+0x15603) (0x0034fd00)
  7 0x00415479 in diablo (+0x15479) (0x004862f4)
  8 0x445c6372 (0x535c3a43)
  9 0x00000000 (0x00000000)
0x7ce3a944: movl        $0x0,0x0(%edx)
Modules:
Module  Address                 Debug info      Name (89 modules)
PE        400000-  6b2000       Export          diablo
PE      10000000-1004b000       Deferred        diabloui
PE      15000000-15045000       Deferred        storm
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ce0c000-7cefc000       Export          wined3d<elf>
  \-PE  7ce20000-7cefc000       \               wined3d
PE      7cefc000-7cf52000       Export          ddraw
ELF     7cf52000-7cfa3000       Deferred        libgcrypt.so.11
ELF     7cfa3000-7cfb3000       Deferred        libtasn1.so.3
ELF     7cfb3000-7cfbb000       Deferred        libkrb5support.so.0
ELF     7cfbb000-7cfe9000       Deferred        libcrypt.so.1
ELF     7cfe9000-7d059000       Deferred        libgnutls.so.13
ELF     7d059000-7d07e000       Deferred        libk5crypto.so.3
ELF     7d07e000-7d106000       Deferred        libkrb5.so.3
ELF     7d106000-7d12f000       Deferred        libgssapi_krb5.so.2
ELF     7d12f000-7d164000       Deferred        libcups.so.2
ELF     7d188000-7d19b000       Deferred        libresolv.so.2
ELF     7d1aa000-7d1c8000       Deferred        iphlpapi<elf>
  \-PE  7d1b0000-7d1c8000       \               iphlpapi
ELF     7d1c8000-7d226000       Deferred        rpcrt4<elf>
  \-PE  7d1d0000-7d226000       \               rpcrt4
ELF     7d226000-7d2c5000       Deferred        ole32<elf>
  \-PE  7d230000-7d2c5000       \               ole32
ELF     7d56e000-7d572000       Deferred        libgpg-error.so.0
ELF     7d592000-7d5c4000       Deferred        uxtheme<elf>
  \-PE  7d5a0000-7d5c4000       \               uxtheme
ELF     7d5c4000-7d5cd000       Deferred        libxcursor.so.1
ELF     7d5cd000-7d5ea000       Deferred        imm32<elf>
  \-PE  7d5d0000-7d5ea000       \               imm32
ELF     7d5ea000-7d5ef000       Deferred        libxfixes.so.3
ELF     7d5ef000-7d5f2000       Deferred        libxcomposite.so.1
ELF     7d5f2000-7d5fa000       Deferred        libxrender.so.1
ELF     7d604000-7d606000       Deferred        libkeyutils.so.1
ELF     7d606000-7d609000       Deferred        libcom_err.so.2
ELF     7dba4000-7dba6000       Deferred        libnvidia-tls.so.1
ELF     7dba6000-7e53e000       Deferred        libglcore.so.1
ELF     7e53e000-7e5d4000       Deferred        libgl.so.1
ELF     7e5d4000-7e5d9000       Deferred        libxdmcp.so.6
ELF     7e5d9000-7e6ca000       Deferred        libx11.so.6
ELF     7e6ca000-7e6d8000       Deferred        libxext.so.6
ELF     7e6d8000-7e6dd000       Deferred        libxxf86vm.so.1
ELF     7e6dd000-7e6f5000       Deferred        libice.so.6
ELF     7e6f5000-7e6fd000       Deferred        libsm.so.6
ELF     7e6ff000-7e705000       Deferred        libxrandr.so.2
ELF     7e70c000-7e79b000       Deferred        winex11<elf>
  \-PE  7e720000-7e79b000       \               winex11
ELF     7e7ed000-7e80d000       Deferred        libexpat.so.1
ELF     7e80d000-7e838000       Deferred        libfontconfig.so.1
ELF     7e847000-7e85c000       Deferred        libz.so.1
ELF     7e85c000-7e8cc000       Deferred        libfreetype.so.6
ELF     7e8cc000-7e8e0000       Deferred        lz32<elf>
  \-PE  7e8d0000-7e8e0000       \               lz32
ELF     7e8e0000-7e8f9000       Deferred        version<elf>
  \-PE  7e8f0000-7e8f9000       \               version
ELF     7e8f9000-7e92e000       Deferred        winspool<elf>
  \-PE  7e900000-7e92e000       \               winspool
ELF     7e92e000-7e9cd000       Deferred        comdlg32<elf>
  \-PE  7e930000-7e9cd000       \               comdlg32
ELF     7e9cd000-7ea32000       Deferred        msvcrt<elf>
  \-PE  7e9e0000-7ea32000       \               msvcrt
ELF     7ea32000-7ea4b000       Deferred        crtdll<elf>
  \-PE  7ea40000-7ea4b000       \               crtdll
ELF     7ea4b000-7eb0a000       Deferred        comctl32<elf>
  \-PE  7ea50000-7eb0a000       \               comctl32
ELF     7eb0a000-7eb61000       Deferred        shlwapi<elf>
  \-PE  7eb20000-7eb61000       \               shlwapi
ELF     7eb61000-7ec65000       Deferred        shell32<elf>
  \-PE  7eb70000-7ec65000       \               shell32
ELF     7ec65000-7ecaf000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecaf000       \               advapi32
ELF     7ecaf000-7ed46000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed46000       \               gdi32
ELF     7ed46000-7ee7d000       Deferred        user32<elf>
  \-PE  7ed60000-7ee7d000       \               user32
ELF     7ee7d000-7ee95000       Deferred        libnsl.so.1
ELF     7ee95000-7ee9e000       Deferred        libnss_compat.so.2
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff2000-7eff5000       Deferred        libxau.so.6
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     b7d33000-b7d3d000       Deferred        libnss_nis.so.2
ELF     b7d40000-b7d44000       Deferred        libdl.so.2
ELF     b7d44000-b7e8e000       Deferred        libc.so.6
ELF     b7e8f000-b7ea7000       Deferred        libpthread.so.0
ELF     b7eb6000-b7fca000       Deferred        libwine.so.1
ELF     b7fcc000-b7fe8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000010 (D) C:\Diablo\Diablo.exe
        00000011    0 <==
00000012 
        00000014    0
        00000013    0
Backtrace:
=>1 0x7ce3a944 in wined3d (+0x1a944) (0x0034f8fc)
  2 0x7ce96e27 IWineD3DBaseSurfaceImpl_GetContainer+0xc7() in wined3d (0x0034f94c)
  3 0x7cf14b67 in ddraw (+0x18b67) (0x0034fa9c)
  4 0x7cf157a9 in ddraw (+0x197a9) (0x0034fc3c)
  5 0x7cf18324 in ddraw (+0x1c324) (0x0034fc7c)
  6 0x00415603 in diablo (+0x15603) (0x0034fd00)
  7 0x00415479 in diablo (+0x15479) (0x004862f4)
  8 0x445c6372 (0x535c3a43)
  9 0x00000000 (0x00000000)
err:ddraw:DllMain DDraw 0x131a60 still has 1 surfaces attached
stephen@Vervet:~/.wine/drive_c/Diablo$ fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:d3d:IWineD3DDeviceImpl_Release (0x134d80) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x132670 with type 1,WINED3DRTYPE_SURFACE
```
Thanks so much for your time,
Stephen

---

### Post by Mizutsuki on 2008-01-26
Ack.  Sorry, forgot to try easy things.  I removed the improperly versioned hacked ddraw.dll from the directory and the intro showed up again, this time with sound (horrah!)  Unfortunately, the game crashed out just as soon as it was supposed to show the menu (doh!)  Here's the console dump:
```
stephen@Vervet:~/.wine/drive_c/Diablo$ wine Diablo.exe 
fixme:spoolsv:serv_main (0 (nil))
stephen@Vervet:~/.wine/drive_c/Diablo$ fixme:win:EnumDisplayDevicesW ((null),0,0x34f850,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:msg:pack_message WM_NCPAINT hdc packing not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
stephen@Vervet:~/.wine/drive_c/Diablo$ fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x131970)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x131970)->(1,(nil)): Stub
wine: Unhandled page fault on read access to 0x0180c000 at address 0x7e4e1c (thread 0011), starting debugger...
Unhandled exception: page fault on read access to 0x0180c000 in 32-bit code (0x007e4e1c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:007e4e1c ESP:0034f278 EBP:7edf4fb8 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:00000000 ECX:00020026 EDX:0034f388
 ESI:0180bfff EDI:01721b43
Stack dump:
0x0034f278:  007d013c 00000013 0034f35c 00000023
0x0034f288:  00000000 0034f2d8 016801a4 7edf4eb5
0x0034f298:  7edf4eb5 016801a4 0168008c 44444353
0x0034f2a8:  44444444 1500c6c0 00010020 3d442023
0x0034f2b8:  00000097 1500c6e0 00000000 1500c6c0
0x0034f2c8:  00000001 00000974 0000025d 003c1630
Backtrace:
=>1 0x007e4e1c (0x7edf4fb8)
0x007e4e1c: movl        0x0(%esi),%eax
Modules:
Module  Address                 Debug info      Name (104 modules)
PE        400000-  6b2000       Deferred        diablo
PE       13f0000- 140a000       Deferred        smackw32
PE      10000000-1004b000       Deferred        diabloui
PE      15000000-15045000       Deferred        storm
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7caab000-7cabf000       Deferred        midimap<elf>
  \-PE  7cab0000-7cabf000       \               midimap
ELF     7cabf000-7cae5000       Deferred        msacm32<elf>
  \-PE  7cad0000-7cae5000       \               msacm32
ELF     7cae5000-7cafc000       Deferred        msacm32<elf>
  \-PE  7caf0000-7cafc000       \               msacm32
ELF     7cafc000-7cbc2000       Deferred        libasound.so.2
ELF     7cbd1000-7cc06000       Deferred        winealsa<elf>
  \-PE  7cbe0000-7cc06000       \               winealsa
ELF     7cc06000-7cc92000       Deferred        winmm<elf>
  \-PE  7cc10000-7cc92000       \               winmm
ELF     7cc92000-7ccdc000       Deferred        dsound<elf>
  \-PE  7cca0000-7ccdc000       \               dsound
ELF     7ce09000-7cef9000       Deferred        wined3d<elf>
  \-PE  7ce20000-7cef9000       \               wined3d
ELF     7cef9000-7cf4d000       Deferred        ddraw<elf>
  \-PE  7cf00000-7cf4d000       \               ddraw
ELF     7cf4d000-7cf9e000       Deferred        libgcrypt.so.11
ELF     7cf9e000-7cfa2000       Deferred        libgpg-error.so.0
ELF     7cfa2000-7cfb2000       Deferred        libtasn1.so.3
ELF     7cfb2000-7cfba000       Deferred        libkrb5support.so.0
ELF     7cfba000-7cfe8000       Deferred        libcrypt.so.1
ELF     7cfe8000-7d058000       Deferred        libgnutls.so.13
ELF     7d058000-7d07d000       Deferred        libk5crypto.so.3
ELF     7d07d000-7d105000       Deferred        libkrb5.so.3
ELF     7d105000-7d12e000       Deferred        libgssapi_krb5.so.2
ELF     7d12e000-7d163000       Deferred        libcups.so.2
ELF     7d187000-7d19a000       Deferred        libresolv.so.2
ELF     7d1a9000-7d1c7000       Deferred        iphlpapi<elf>
  \-PE  7d1b0000-7d1c7000       \               iphlpapi
ELF     7d1c7000-7d225000       Deferred        rpcrt4<elf>
  \-PE  7d1d0000-7d225000       \               rpcrt4
ELF     7d225000-7d2c4000       Deferred        ole32<elf>
  \-PE  7d230000-7d2c4000       \               ole32
ELF     7d56c000-7d56e000       Deferred        libkeyutils.so.1
ELF     7d58e000-7d5c0000       Deferred        uxtheme<elf>
  \-PE  7d590000-7d5c0000       \               uxtheme
ELF     7d5c0000-7d5c9000       Deferred        libxcursor.so.1
ELF     7d5c9000-7d5e6000       Deferred        imm32<elf>
  \-PE  7d5d0000-7d5e6000       \               imm32
ELF     7d5e6000-7d5eb000       Deferred        libxfixes.so.3
ELF     7d5eb000-7d5f1000       Deferred        libxrandr.so.2
ELF     7d5f1000-7d5f9000       Deferred        libxrender.so.1
ELF     7d603000-7d606000       Deferred        libcom_err.so.2
ELF     7dba3000-7dba5000       Deferred        libnvidia-tls.so.1
ELF     7dba5000-7e53d000       Deferred        libglcore.so.1
ELF     7e53d000-7e5d3000       Deferred        libgl.so.1
ELF     7e5d3000-7e5d8000       Deferred        libxdmcp.so.6
ELF     7e5d8000-7e5db000       Deferred        libxau.so.6
ELF     7e5db000-7e6cc000       Deferred        libx11.so.6
ELF     7e6cc000-7e6da000       Deferred        libxext.so.6
ELF     7e6da000-7e6df000       Deferred        libxxf86vm.so.1
ELF     7e6df000-7e6f7000       Deferred        libice.so.6
ELF     7e6f7000-7e6ff000       Deferred        libsm.so.6
ELF     7e700000-7e703000       Deferred        libxcomposite.so.1
ELF     7e70e000-7e79d000       Deferred        winex11<elf>
  \-PE  7e720000-7e79d000       \               winex11
ELF     7e7e2000-7e802000       Deferred        libexpat.so.1
ELF     7e802000-7e82d000       Deferred        libfontconfig.so.1
ELF     7e83c000-7e851000       Deferred        libz.so.1
ELF     7e851000-7e8c1000       Deferred        libfreetype.so.6
ELF     7e8c1000-7e8d5000       Deferred        lz32<elf>
  \-PE  7e8d0000-7e8d5000       \               lz32
ELF     7e8d5000-7e8ee000       Deferred        version<elf>
  \-PE  7e8e0000-7e8ee000       \               version
ELF     7e8ee000-7e923000       Deferred        winspool<elf>
  \-PE  7e900000-7e923000       \               winspool
ELF     7e923000-7e9c2000       Deferred        comdlg32<elf>
  \-PE  7e930000-7e9c2000       \               comdlg32
ELF     7e9c2000-7ea27000       Deferred        msvcrt<elf>
  \-PE  7e9d0000-7ea27000       \               msvcrt
ELF     7ea27000-7ea40000       Deferred        crtdll<elf>
  \-PE  7ea30000-7ea40000       \               crtdll
ELF     7ea40000-7eaff000       Deferred        comctl32<elf>
  \-PE  7ea50000-7eaff000       \               comctl32
ELF     7eaff000-7eb56000       Deferred        shlwapi<elf>
  \-PE  7eb10000-7eb56000       \               shlwapi
ELF     7eb56000-7ec5a000       Deferred        shell32<elf>
  \-PE  7eb70000-7ec5a000       \               shell32
ELF     7ec5a000-7eca4000       Deferred        advapi32<elf>
  \-PE  7ec60000-7eca4000       \               advapi32
ELF     7eca4000-7ed3b000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed3b000       \               gdi32
ELF     7ed3b000-7ee72000       Deferred        user32<elf>
  \-PE  7ed50000-7ee72000       \               user32
ELF     7ee72000-7ee7d000       Deferred        libnss_files.so.2
ELF     7ee7d000-7ee95000       Deferred        libnsl.so.1
ELF     7ee95000-7ee9e000       Deferred        libnss_compat.so.2
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ccb000-b7ccf000       Deferred        libdl.so.2
ELF     b7ccf000-b7e19000       Deferred        libc.so.6
ELF     b7e1a000-b7e32000       Deferred        libpthread.so.0
ELF     b7e41000-b7f55000       Deferred        libwine.so.1
ELF     b7f57000-b7f73000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000010 (D) C:\Diablo\Diablo.exe
        00000016    1
        00000015   15
        00000011    0 <==
00000012 
        00000014    0
        00000013    0
Backtrace:
=>1 0x007e4e1c (0x7edf4fb8)
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
```

---

### Post by Mizutsuki on 2008-01-26
So, I downgraded to the ubuntu default 0.9.46, and put the appropriate ddraw.dll in the directory.  I'm able to play but the menus act as described in the appdb (they are invisible until clicked, and then they improperly refresh.)  What is that hacked ddraw.dll, anyway?  Will one be released for 0.9.54 soon?
Thanks,
Stephen

---

