---
title: "Directplay problems"
date: 2008-06-02
forum: Wine
---

### Post by VinisLentoje on 2008-06-02
Hello, I wanted to play some games in multiplayer that works through DirectPlay. I have folowed the instractions in this site: [http://wiki.winehq.org/DirectPlayGames]("http://wiki.winehq.org/DirectPlayGames") but it didn't help, I still got the same reaction when trying create/join a game. First game (Knights and Merchants) dies, while other (Age of Empires II) fails creating/joining and kicks me back to the main menu,
Any ideas?

---

### Post by cogadh on 2008-06-02
Post the terminal output from one of the failing games.

---

### Post by VinisLentoje on 2008-06-02
From Knights and Merchants:

```
fixme:advapi:SetEntriesInAclA 1 0x33c788 (nil) 0x33c7c0
fixme:advapi:SetSecurityInfo stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dc2aa08, overlapped 0x7dc2a9ec): stub
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": /usr/lib32/libxml2.so.2: undefined symbol: gzopen64
fixme:shell:DllCanUnloadNow stub
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": /usr/lib32/libxml2.so.2: undefined symbol: gzopen64
wine: configuration in '/home/vinis/.wine' has been updated.
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
fixme:win:EnumDisplayDevicesW ((null),0,0x32f278,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(800,600)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x496dab (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00496dab).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00496dab ESP:0032f9ac EBP:0032f9d0 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:7b8b3884 ECX:00000000 EDX:00ffaaa8
 ESI:00000000 EDI:0049a1a3
Stack dump:
0x0032f9ac:  0032f9c8 0032f9c4 00000002 00000000
0x0032f9bc:  0032f9cc 00ffaaa8 ffffffff 00000000
0x0032f9cc:  0032fa1c 0032f9ec 0049683e 0032f9e4
0x0032f9dc:  0032f9e8 00ffaaa8 00000000 00000000
0x0032f9ec:  0032fe18 00465712 00401d93 00000000
0x0032f9fc:  00000000 7bc3377f 00127120 7bc88444
Backtrace:
=>1 0x00496dab in km_tpr (+0x96dab) (0x0032f9d0)
  2 0x0049683e in km_tpr (+0x9683e) (0x0032f9ec)
  3 0x00465712 in km_tpr (+0x65712) (0x0032fe18)
  4 0x00460754 in km_tpr (+0x60754) (0x0032fe24)
  5 0x004844b3 in km_tpr (+0x844b3) (0x0032fe7c)
  6 0x0049a283 in km_tpr (+0x9a283) (0x0032ff08)
  7 0x7b877b27 in kernel32 (+0x57b27) (0x0032ffe8)
0x00496dab: movl	0x0(%ecx),%ecx
Modules:
Module	Address			Debug info	Name (102 modules)
PE	  330000-  389000	Deferred        binkw32
PE	  390000-  3de000	Deferred        fsgs
PE	  400000-  573000	Export          km_tpr
PE	10000000-1006f000	Deferred        fmod
PE	5e080000-5e0bb000	Deferred        dplayx
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c339000-7c383000	Deferred        dsound<elf>
  \-PE	7c340000-7c383000	\               dsound
ELF	7d2a7000-7dfe6000	Deferred        libglcore.so.1
ELF	7dfe6000-7e08b000	Deferred        libgl.so.1
ELF	7e08b000-7e18d000	Deferred        wined3d<elf>
  \-PE	7e0a0000-7e18d000	\               wined3d
ELF	7e2c7000-7e2fa000	Deferred        uxtheme<elf>
  \-PE	7e2d0000-7e2fa000	\               uxtheme
ELF	7e2fa000-7e311000	Deferred        msacm32<elf>
  \-PE	7e300000-7e311000	\               msacm32
ELF	7e311000-7e3d4000	Deferred        libasound.so.2
ELF	7e3d5000-7e3e9000	Deferred        midimap<elf>
  \-PE	7e3e0000-7e3e9000	\               midimap
ELF	7e3e9000-7e41f000	Deferred        winealsa<elf>
  \-PE	7e3f0000-7e41f000	\               winealsa
ELF	7e41f000-7e428000	Deferred        libxcursor.so.1
ELF	7e428000-7e42d000	Deferred        libxfixes.so.3
ELF	7e42d000-7e430000	Deferred        libxcomposite.so.1
ELF	7e430000-7e436000	Deferred        libxrandr.so.2
ELF	7e436000-7e43e000	Deferred        libxrender.so.1
ELF	7e43e000-7e441000	Deferred        libxinerama.so.1
ELF	7e441000-7e461000	Deferred        imm32<elf>
  \-PE	7e450000-7e461000	\               imm32
ELF	7e461000-7e466000	Deferred        libxdmcp.so.6
ELF	7e466000-7e47e000	Deferred        libxcb.so.1
ELF	7e47e000-7e481000	Deferred        libxau.so.6
ELF	7e481000-7e568000	Deferred        libx11.so.6
ELF	7e568000-7e576000	Deferred        libxext.so.6
ELF	7e576000-7e57b000	Deferred        libxxf86vm.so.1
ELF	7e58c000-7e58e000	Deferred        libnvidia-tls.so.1
ELF	7e590000-7e627000	Deferred        winex11<elf>
  \-PE	7e5a0000-7e627000	\               winex11
ELF	7e665000-7e686000	Deferred        libexpat.so.1
ELF	7e686000-7e6b0000	Deferred        libfontconfig.so.1
ELF	7e6b0000-7e6c1000	Deferred        libz.so.1
ELF	7e6c1000-7e731000	Deferred        libfreetype.so.6
ELF	7e746000-7e77d000	Deferred        dinput<elf>
  \-PE	7e750000-7e77d000	\               dinput
ELF	7e77d000-7e795000	Deferred        dinput8<elf>
  \-PE	7e780000-7e795000	\               dinput8
ELF	7e795000-7e7ec000	Deferred        ddraw<elf>
  \-PE	7e7a0000-7e7ec000	\               ddraw
ELF	7e7ec000-7e8ab000	Deferred        comctl32<elf>
  \-PE	7e7f0000-7e8ab000	\               comctl32
ELF	7e8ab000-7e8bf000	Deferred        lz32<elf>
  \-PE	7e8b0000-7e8bf000	\               lz32
ELF	7e8bf000-7e8d8000	Deferred        version<elf>
  \-PE	7e8c0000-7e8d8000	\               version
ELF	7e8d8000-7e900000	Deferred        msvfw32<elf>
  \-PE	7e8e0000-7e900000	\               msvfw32
ELF	7e900000-7e93b000	Deferred        avifil32<elf>
  \-PE	7e910000-7e93b000	\               avifil32
ELF	7e93b000-7e985000	Deferred        dbghelp<elf>
  \-PE	7e940000-7e985000	\               dbghelp
ELF	7e985000-7e99c000	Deferred        imagehlp<elf>
  \-PE	7e990000-7e99c000	\               imagehlp
ELF	7e99c000-7e9c8000	Deferred        ws2_32<elf>
  \-PE	7e9a0000-7e9c8000	\               ws2_32
ELF	7e9c8000-7e9e2000	Deferred        wsock32<elf>
  \-PE	7e9d0000-7e9e2000	\               wsock32
ELF	7e9e2000-7e9f5000	Deferred        libresolv.so.2
ELF	7e9f5000-7ea0a000	Deferred        psapi<elf>
  \-PE	7ea00000-7ea0a000	\               psapi
ELF	7ea0a000-7ea28000	Deferred        iphlpapi<elf>
  \-PE	7ea10000-7ea28000	\               iphlpapi
ELF	7ea28000-7ea89000	Deferred        rpcrt4<elf>
  \-PE	7ea30000-7ea89000	\               rpcrt4
ELF	7ea89000-7eb2d000	Deferred        ole32<elf>
  \-PE	7eaa0000-7eb2d000	\               ole32
ELF	7eb2d000-7eb97000	Deferred        msvcrt<elf>
  \-PE	7eb40000-7eb97000	\               msvcrt
ELF	7eb97000-7ec32000	Deferred        gdi32<elf>
  \-PE	7ebb0000-7ec32000	\               gdi32
ELF	7ec32000-7ed79000	Deferred        user32<elf>
  \-PE	7ec50000-7ed79000	\               user32
ELF	7ed79000-7ee0b000	Deferred        winmm<elf>
  \-PE	7ed80000-7ee0b000	\               winmm
ELF	7ee0b000-7ee31000	Deferred        msacm32<elf>
  \-PE	7ee10000-7ee31000	\               msacm32
ELF	7ee31000-7ee83000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee83000	\               advapi32
ELF	7efa3000-7efae000	Deferred        libnss_files.so.2
ELF	7efae000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efeb000	Deferred        libm.so.6
ELF	7efeb000-7efed000	Deferred        libxcb-xlib.so.0
ELF	7efed000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7d06000-f7d0a000	Deferred        libdl.so.2
ELF	f7d0a000-f7e59000	Deferred        libc.so.6
ELF	f7e59000-f7e71000	Deferred        libpthread.so.0
ELF	f7e87000-f7fbd000	Deferred        libwine.so.1
ELF	f7fbf000-f7fde000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) E:\bambizas\rts\KnM_TPR\Knights & Merchants The Peasants Rebellion\KM_TPR.exe
	00000040    2
	0000003f   15
	0000003e   15
	0000003d    0
	00000009    0 <==
0000000c 
	0000001a    0
	00000019    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	0000001b    0
	00000018    0
	00000017    0
0000003b 
	0000003c    0
Backtrace:
=>1 0x00496dab in km_tpr (+0x96dab) (0x0032f9d0)
  2 0x0049683e in km_tpr (+0x9683e) (0x0032f9ec)
  3 0x00465712 in km_tpr (+0x65712) (0x0032fe18)
  4 0x00460754 in km_tpr (+0x60754) (0x0032fe24)
  5 0x004844b3 in km_tpr (+0x844b3) (0x0032fe7c)
  6 0x0049a283 in km_tpr (+0x9a283) (0x0032ff08)
  7 0x7b877b27 in kernel32 (+0x57b27) (0x0032ffe8)

```

---

### Post by cogadh on 2008-06-02
It looks like you have a problem long before you get to the DirectPlay issue:
```
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": /usr/lib32/libxml2.so.2: undefined symbol: gzopen64
```
It looks like your 64 bit system and 32 bit Wine libraries aren't cooperating. You might try using [winetricks](http://wiki.winehq.org/winetricks) to install the real MSXML3 and see if that corrects the issue.
Additionally, it appears to be looking for a DLL you do not have:
```
err:rundll32:main Unable to load L"streamci"
```
You just need to get the streamci.dll from an existing Windows machine or search online for it and place it in the ~/.wine/drive_c/windows/system32 folder.
After those two items are fixed, try running the game again and lets see if you still have issues.

---

### Post by VinisLentoje on 2008-06-02
Knights and Merchants still dies with this terminal output:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f278,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(800,600)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x127398)->(1,(nil)): Stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x496dab (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00496dab).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00496dab ESP:0032f9ac EBP:0032f9d0 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:7b8b3884 ECX:00000000 EDX:0110d208
 ESI:00000000 EDI:0049a1a3
Stack dump:
0x0032f9ac:  0032f9c8 0032f9c4 00000002 00000000
0x0032f9bc:  0032f9cc 0110d208 ffffffff 00000000
0x0032f9cc:  0032fa1c 0032f9ec 0049683e 0032f9e4
0x0032f9dc:  0032f9e8 0110d208 00000000 00000000
0x0032f9ec:  0032fe18 00465712 00401d93 00000000
0x0032f9fc:  00000000 7bc3377f 00127120 7bc88444
Backtrace:
=>1 0x00496dab in km_tpr (+0x96dab) (0x0032f9d0)
  2 0x0049683e in km_tpr (+0x9683e) (0x0032f9ec)
  3 0x00465712 in km_tpr (+0x65712) (0x0032fe18)
  4 0x00460754 in km_tpr (+0x60754) (0x0032fe24)
  5 0x004844b3 in km_tpr (+0x844b3) (0x0032fe7c)
  6 0x0049a283 in km_tpr (+0x9a283) (0x0032ff08)
  7 0x7b877b27 in kernel32 (+0x57b27) (0x0032ffe8)
0x00496dab: movl	0x0(%ecx),%ecx
Modules:
Module	Address			Debug info	Name (102 modules)
PE	  330000-  389000	Deferred        binkw32
PE	  390000-  3de000	Deferred        fsgs
PE	  400000-  573000	Export          km_tpr
PE	10000000-1006f000	Deferred        fmod
PE	5e080000-5e0bb000	Deferred        dplayx
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c332000-7c37c000	Deferred        dsound<elf>
  \-PE	7c340000-7c37c000	\               dsound
ELF	7d2a1000-7dfe0000	Deferred        libglcore.so.1
ELF	7dfe0000-7e085000	Deferred        libgl.so.1
ELF	7e085000-7e187000	Deferred        wined3d<elf>
  \-PE	7e0a0000-7e187000	\               wined3d
ELF	7e2c1000-7e2f4000	Deferred        uxtheme<elf>
  \-PE	7e2d0000-7e2f4000	\               uxtheme
ELF	7e2f4000-7e30b000	Deferred        msacm32<elf>
  \-PE	7e300000-7e30b000	\               msacm32
ELF	7e30b000-7e3ce000	Deferred        libasound.so.2
ELF	7e3cf000-7e3e3000	Deferred        midimap<elf>
  \-PE	7e3d0000-7e3e3000	\               midimap
ELF	7e3e3000-7e419000	Deferred        winealsa<elf>
  \-PE	7e3f0000-7e419000	\               winealsa
ELF	7e419000-7e422000	Deferred        libxcursor.so.1
ELF	7e422000-7e427000	Deferred        libxfixes.so.3
ELF	7e427000-7e42a000	Deferred        libxcomposite.so.1
ELF	7e42a000-7e430000	Deferred        libxrandr.so.2
ELF	7e430000-7e438000	Deferred        libxrender.so.1
ELF	7e438000-7e43b000	Deferred        libxinerama.so.1
ELF	7e43b000-7e45b000	Deferred        imm32<elf>
  \-PE	7e440000-7e45b000	\               imm32
ELF	7e45b000-7e460000	Deferred        libxdmcp.so.6
ELF	7e460000-7e478000	Deferred        libxcb.so.1
ELF	7e478000-7e47b000	Deferred        libxau.so.6
ELF	7e47b000-7e562000	Deferred        libx11.so.6
ELF	7e562000-7e570000	Deferred        libxext.so.6
ELF	7e570000-7e575000	Deferred        libxxf86vm.so.1
ELF	7e586000-7e588000	Deferred        libnvidia-tls.so.1
ELF	7e58a000-7e621000	Deferred        winex11<elf>
  \-PE	7e5a0000-7e621000	\               winex11
ELF	7e670000-7e691000	Deferred        libexpat.so.1
ELF	7e691000-7e6bb000	Deferred        libfontconfig.so.1
ELF	7e6bb000-7e6cc000	Deferred        libz.so.1
ELF	7e6cc000-7e73c000	Deferred        libfreetype.so.6
ELF	7e73c000-7e73e000	Deferred        libxcb-xlib.so.0
ELF	7e751000-7e788000	Deferred        dinput<elf>
  \-PE	7e760000-7e788000	\               dinput
ELF	7e788000-7e7a0000	Deferred        dinput8<elf>
  \-PE	7e790000-7e7a0000	\               dinput8
ELF	7e7a0000-7e7f7000	Deferred        ddraw<elf>
  \-PE	7e7b0000-7e7f7000	\               ddraw
ELF	7e7f7000-7e8b6000	Deferred        comctl32<elf>
  \-PE	7e800000-7e8b6000	\               comctl32
ELF	7e8b6000-7e8ca000	Deferred        lz32<elf>
  \-PE	7e8c0000-7e8ca000	\               lz32
ELF	7e8ca000-7e8e3000	Deferred        version<elf>
  \-PE	7e8d0000-7e8e3000	\               version
ELF	7e8e3000-7e90b000	Deferred        msvfw32<elf>
  \-PE	7e8f0000-7e90b000	\               msvfw32
ELF	7e90b000-7e946000	Deferred        avifil32<elf>
  \-PE	7e910000-7e946000	\               avifil32
ELF	7e946000-7e990000	Deferred        dbghelp<elf>
  \-PE	7e950000-7e990000	\               dbghelp
ELF	7e990000-7e9a7000	Deferred        imagehlp<elf>
  \-PE	7e9a0000-7e9a7000	\               imagehlp
ELF	7e9a7000-7e9d3000	Deferred        ws2_32<elf>
  \-PE	7e9b0000-7e9d3000	\               ws2_32
ELF	7e9d3000-7e9ed000	Deferred        wsock32<elf>
  \-PE	7e9e0000-7e9ed000	\               wsock32
ELF	7e9ed000-7ea00000	Deferred        libresolv.so.2
ELF	7ea00000-7ea1e000	Deferred        iphlpapi<elf>
  \-PE	7ea10000-7ea1e000	\               iphlpapi
ELF	7ea1e000-7ea7f000	Deferred        rpcrt4<elf>
  \-PE	7ea30000-7ea7f000	\               rpcrt4
ELF	7ea7f000-7eb23000	Deferred        ole32<elf>
  \-PE	7ea90000-7eb23000	\               ole32
ELF	7eb23000-7eb8d000	Deferred        msvcrt<elf>
  \-PE	7eb30000-7eb8d000	\               msvcrt
ELF	7eb8d000-7ec28000	Deferred        gdi32<elf>
  \-PE	7eba0000-7ec28000	\               gdi32
ELF	7ec28000-7ed6f000	Deferred        user32<elf>
  \-PE	7ec40000-7ed6f000	\               user32
ELF	7ed6f000-7ee01000	Deferred        winmm<elf>
  \-PE	7ed80000-7ee01000	\               winmm
ELF	7ee01000-7ee27000	Deferred        msacm32<elf>
  \-PE	7ee10000-7ee27000	\               msacm32
ELF	7ee27000-7ee79000	Deferred        advapi32<elf>
  \-PE	7ee30000-7ee79000	\               advapi32
ELF	7ef99000-7efa4000	Deferred        libnss_files.so.2
ELF	7efa4000-7efae000	Deferred        libnss_nis.so.2
ELF	7efae000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efeb000	Deferred        libm.so.6
ELF	7efeb000-7f000000	Deferred        psapi<elf>
  \-PE	7eff0000-7f000000	\               psapi
ELF	f7c95000-f7c9e000	Deferred        libnss_compat.so.2
ELF	f7c9f000-f7ca3000	Deferred        libdl.so.2
ELF	f7ca3000-f7df2000	Deferred        libc.so.6
ELF	f7df2000-f7e0a000	Deferred        libpthread.so.0
ELF	f7e20000-f7f56000	Deferred        libwine.so.1
ELF	f7f58000-f7f77000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) E:\bambizas\rts\KnM_TPR\Knights & Merchants The Peasants Rebellion\KM_TPR.exe
	00000021    2
	00000020   15
	0000001f   15
	0000001e    0
	00000009    0 <==
0000000c 
	0000001a    0
	00000019    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	0000001b    0
	00000018    0
	00000017    0
0000001c 
	0000001d    0
Backtrace:
=>1 0x00496dab in km_tpr (+0x96dab) (0x0032f9d0)
  2 0x0049683e in km_tpr (+0x9683e) (0x0032f9ec)
  3 0x00465712 in km_tpr (+0x65712) (0x0032fe18)
  4 0x00460754 in km_tpr (+0x60754) (0x0032fe24)
  5 0x004844b3 in km_tpr (+0x844b3) (0x0032fe7c)
  6 0x0049a283 in km_tpr (+0x9a283) (0x0032ff08)
  7 0x7b877b27 in kernel32 (+0x57b27) (0x0032ffe8)

```

---

