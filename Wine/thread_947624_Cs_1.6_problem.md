---
title: "Cs 1.6 problem"
date: 2008-10-14
forum: Wine
---

### Post by qbox on 2008-10-14
Hi
I play counter strike for a long time with wine and until now I didn't have any problems.

Now when I start the game I receive this output in the console.

```
qbox@qbox:~$ wine .wine/drive_c/xtcs\ counter-strike\ 1.6\ final\ release/cstrike.exe 
fixme:ntoskrnl:KeInitializeTimerEx 0x111110 0
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5e0,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise (0x18d078)->(1 00000002 0x66a290)
fixme:shdocvw:PersistStreamInit_InitNew (0x18d078)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x18d078)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x18d078)->(ffffffff)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x18d588,0x18da18): stub
fixme:shdocvw:ViewObject_SetAdvise (0x68a66d0)->(1 00000002 0xf8b8e0)
fixme:shdocvw:PersistStreamInit_InitNew (0x68a66d0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x68a66d0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x68a66d0)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x68a66d0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x68a66d0)
fixme:shdocvw:OleObject_Close (0x68a66d0)->(1)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
err:mshtml:check_version Could not open VERSION file
err:mshtml:check_version Could not open VERSION file
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x18d114)->((null) 1 0x32d9c8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->((null) 25 2 0x32d9dc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->((null) 26 2 0x32d9dc (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 000000f0
fixme:shdocvw:ClientSite_GetContainer (0x18d114)->(0x32da18)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32dadc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32db6c)
fixme:shdocvw:ViewObject_Draw (0x18d078)->(1 -1 (nil) (nil) 0xc14 0xc2c 0x32f9b0 (nil) (nil) 00000000)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->((null) 29 2 0x32f548 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x18d114)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f470)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f470)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->((null) 26 2 0x32f528 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->((null) 29 2 0x32f538 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->((null) 28 2 0x32f470 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x18d114)->(0x32f3d4)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x18d114)->(0xf7e8d735)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->((null) 25 2 0x32f308 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18d114)->((null) 26 2 0x32f308 (nil))
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:winmm:MMDRV_Exit Closing while ll-driver open
File h:\.wine\drive_c\xtcs counter-strike 1.6 final release\cstrike\demoheader.dmf was never closed
qbox@qbox:~$ 


```

---

### Post by qbox on 2008-10-14
Or this error:

```
qbox@qbox:~$ wine .wine/drive_c/xtcs\ counter-strike\ 1.6\ final\ release/cstrike.exe 
fixme:ntoskrnl:KeInitializeTimerEx 0x111110 0
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5e0,0x00000000), stub!
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  1269728
  Current serial number in output stream:  1269728
qbox@qbox:~$ 

```

---

### Post by Rocket2DMn on 2008-10-14
Moved to the Wine forum area.

Are you using wine from the Ubuntu repos or direct from winehq?  Have you tried reinstalling steam inside wine?

---

### Post by qbox on 2008-12-07
ANY HELP?
wine 1.1.10
ubuntu 8.04

```
qbox@qbox:~$ wine .wine/drive_c/xtcs\ counter-strike\ 1.6\ final\ release/cstrike.exe 
wine: Unhandled page fault on read access to 0x00000000 at address 0x14014f9 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x014014f9).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:014014f9 ESP:0032fa94 EBP:0032fbac EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:00000005
 ESI:014113a0 EDI:00000104
Stack dump:
0x0032fa94:  014113a0 0000005c 10015298 014114a8
0x0032faa4:  00000000 685c3a5a 5c656d6f 786f6271
0x0032fab4:  69772e5c 645c656e 65766972 785c635f
0x0032fac4:  20736374 6e756f63 2d726574 69727473
0x0032fad4:  3120656b 6620362e 6c616e69 6c657220
0x0032fae4:  65736165 7473635c 656b6972 6578652e
Backtrace:
=>1 0x014014f9 in cstrike (+0x14f9) (0x0032fbac)
  2 0x01401aa3 in cstrike (+0x1aa3) (0x0032fe7c)
  3 0x014038f1 in cstrike (+0x38f1) (0x0032ff08)
  4 0x7b878357 in kernel32 (+0x58357) (0x0032ffe8)
  5 0xf7dfca17 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x014014f9: cmpb	%bl,0x0(%eax)
Modules:
Module	Address			Debug info	Name (51 modules)
PE	 1400000- 351f000	Export          cstrike
PE	10000000-1001f000	Deferred        filesystem_stdio
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca9000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e89d000-7e8a6000	Deferred        libxcursor.so.1
ELF	7e8a6000-7e8ab000	Deferred        libxfixes.so.3
ELF	7e8ab000-7e8ae000	Deferred        libxcomposite.so.1
ELF	7e8ae000-7e8b4000	Deferred        libxrandr.so.2
ELF	7e8b4000-7e8bc000	Deferred        libxrender.so.1
ELF	7e8bc000-7e8c1000	Deferred        libxxf86vm.so.1
ELF	7e8c1000-7e8c4000	Deferred        libxinerama.so.1
ELF	7e8c4000-7e8e4000	Deferred        imm32<elf>
  \-PE	7e8d0000-7e8e4000	\               imm32
ELF	7e8e4000-7e8e9000	Deferred        libxdmcp.so.6
ELF	7e8e9000-7e901000	Deferred        libxcb.so.1
ELF	7e901000-7e903000	Deferred        libxcb-xlib.so.0
ELF	7e903000-7e906000	Deferred        libxau.so.6
ELF	7e906000-7e9ed000	Deferred        libx11.so.6
ELF	7e9ed000-7e9fb000	Deferred        libxext.so.6
ELF	7ea19000-7eab1000	Deferred        winex11<elf>
  \-PE	7ea30000-7eab1000	\               winex11
ELF	7eaeb000-7eb0c000	Deferred        libexpat.so.1
ELF	7eb0c000-7eb36000	Deferred        libfontconfig.so.1
ELF	7eb36000-7eb4b000	Deferred        libz.so.1
ELF	7eb4b000-7ebbb000	Deferred        libfreetype.so.6
ELF	7ebbb000-7ec59000	Deferred        gdi32<elf>
  \-PE	7ebd0000-7ec59000	\               gdi32
ELF	7ec59000-7eda3000	Deferred        user32<elf>
  \-PE	7ec70000-7eda3000	\               user32
ELF	7eda3000-7edf7000	Deferred        advapi32<elf>
  \-PE	7edb0000-7edf7000	\               advapi32
ELF	7ee15000-7ee34000	Deferred        iphlpapi<elf>
  \-PE	7ee20000-7ee34000	\               iphlpapi
ELF	7ee34000-7ee60000	Deferred        ws2_32<elf>
  \-PE	7ee40000-7ee60000	\               ws2_32
ELF	7ee60000-7ee7a000	Deferred        wsock32<elf>
  \-PE	7ee70000-7ee7a000	\               wsock32
ELF	7ef9a000-7efa5000	Deferred        libnss_files.so.2
ELF	7efa5000-7efbd000	Deferred        libnsl.so.1
ELF	7efbd000-7efe2000	Deferred        libm.so.6
ELF	7efe8000-7effb000	Deferred        libresolv.so.2
ELF	f7c60000-f7c6a000	Deferred        libnss_nis.so.2
ELF	f7c6b000-f7c6f000	Deferred        libdl.so.2
ELF	f7c6f000-f7dbe000	Deferred        libc.so.6
ELF	f7dbe000-f7dd6000	Deferred        libpthread.so.0
ELF	f7dd7000-f7de0000	Deferred        libnss_compat.so.2
ELF	f7df5000-f7f2b000	Export          libwine.so.1
ELF	f7f2d000-f7f4c000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\qbox\.wine\drive_c\xtcs counter-strike 1.6 final release\cstrike.exe
	00000009    0 <==
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
Backtrace:
=>1 0x014014f9 in cstrike (+0x14f9) (0x0032fbac)
  2 0x01401aa3 in cstrike (+0x1aa3) (0x0032fe7c)
  3 0x014038f1 in cstrike (+0x38f1) (0x0032ff08)
  4 0x7b878357 in kernel32 (+0x58357) (0x0032ffe8)
  5 0xf7dfca17 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
qbox@qbox:~$ 


```

---

### Post by qbox on 2009-01-02
still wont work.

---

### Post by matteojg on 2009-01-02
I've read that certain software that performed fine on older versions of wine will crash on newer versions, this is referred to as a 'regression' ([http://wiki.winehq.org/Regression](http://wiki.winehq.org/Regression)).

So if it had been working for a long time and then all of a sudden stopped, perhaps your Wine program was updated, either automatically or manually, and the new version no longer works with your game.

Do you know what version of Wine you initially used to play the game, and is it the same one you are using now?

---

