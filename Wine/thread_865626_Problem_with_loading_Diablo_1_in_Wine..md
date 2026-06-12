---
title: "Problem with loading Diablo 1 in Wine."
date: 2008-07-20
forum: Wine
---

### Post by Caeliferum on 2008-07-20
Well, I've installed the game under Wine. When loading it, the Blizzard intro movie will play fine. But after that, it just exits back to the Ubuntu desktop.

Any suggestions? I have a Windows parition with the game installed as well, but I don't want to resort to booting it off the Windows partition because I plan to be using an Ubuntu-only system come this September, and I would rather be able to use games I install under Wine.

---

### Post by poofyhairguy on 2008-07-20
> **Caeliferum said:**
> Well, I've installed the game under Wine. When loading it, the Blizzard intro movie will play fine. But after that, it just exits back to the Ubuntu desktop.

Any suggestions? I have a Windows parition with the game installed as well, but I don't want to resort to booting it off the Windows partition because I plan to be using an Ubuntu-only system come this September, and I would rather be able to use games I install under Wine.

Are you using the newest version of wine possible?

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Caeliferum on 2008-07-21
Yes, I'm using 1.0.

---

### Post by Caeliferum on 2008-07-21
Here's the terminal output, from starting the game to it crashing to the desktop:



```
caeliferum@CalcuLORD-Rebirth:~/.wine/drive_c/Diablo$ wine diablo.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f8ec,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x12b910)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x12b910)->(1,(nil)): Stub
wine: Unhandled page fault on read access to 0xc7810789 at address 0xc7810789 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xc7810789 in 32-bit code (0xc7810789).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:c7810789 ESP:0032f3c8 EBP:7ee25548 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00959858 EBX:00000000 ECX:00959c30 EDX:00000001
 ESI:01c62d13 EDI:019633b8
Stack dump:
0x0032f3c8:  00959858 00000018 0032f464 ffffffe7
0x0032f3d8:  00000000 0032f408 0195e998 00959840
0x0032f3e8:  00000013 00000cc0 00000299 7edfa308
0x0032f3f8:  00010020 15004d60 15004d40 0195e6c0
0x0032f408:  0032f4b8 15001745 0195e6c0 0032f464
0x0032f418:  00000013 00959c30 01c12800 0032f444
Backtrace:
=>1 0xc7810789 (0x7ee25548)
  2 0x00000000 (0x000ed430)
0xc7810789: -- no code accessible --
Modules:
Module	Address			Debug info	Name (103 modules)
PE	  400000-  6c2000	Deferred        diablo
PE	15000000-1503d000	Deferred        storm
PE	20000000-20046000	Deferred        diabloui
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d3e1000-7d3f5000	Deferred        midimap<elf>
  \-PE	7d3f0000-7d3f5000	\               midimap
ELF	7d3f5000-7d41b000	Deferred        msacm32<elf>
  \-PE	7d400000-7d41b000	\               msacm32
ELF	7d41b000-7d432000	Deferred        msacm32<elf>
  \-PE	7d420000-7d432000	\               msacm32
ELF	7d432000-7d4f5000	Deferred        libasound.so.2
ELF	7d4f5000-7d52b000	Deferred        winealsa<elf>
  \-PE	7d500000-7d52b000	\               winealsa
ELF	7d52b000-7d5bd000	Deferred        winmm<elf>
  \-PE	7d540000-7d5bd000	\               winmm
ELF	7d5bd000-7d607000	Deferred        dsound<elf>
  \-PE	7d5c0000-7d607000	\               dsound
ELF	7de25000-7e03b000	Deferred        r300_dri.so
ELF	7e03b000-7e045000	Deferred        libdrm.so.2
ELF	7e045000-7e0a7000	Deferred        libgl.so.1
ELF	7e0a7000-7e1aa000	Deferred        wined3d<elf>
  \-PE	7e0c0000-7e1aa000	\               wined3d
ELF	7e1aa000-7e201000	Deferred        ddraw<elf>
  \-PE	7e1b0000-7e201000	\               ddraw
ELF	7e201000-7e205000	Deferred        libgpg-error.so.0
ELF	7e205000-7e252000	Deferred        libgcrypt.so.11
ELF	7e252000-7e262000	Deferred        libtasn1.so.3
ELF	7e262000-7e294000	Deferred        libcrypt.so.1
ELF	7e294000-7e30a000	Deferred        libgnutls.so.13
ELF	7e30a000-7e32d000	Deferred        libk5crypto.so.3
ELF	7e32d000-7e3ba000	Deferred        libkrb5.so.3
ELF	7e3ba000-7e3e3000	Deferred        libgssapi_krb5.so.2
ELF	7e3e3000-7e416000	Deferred        libcups.so.2
ELF	7e449000-7e45c000	Deferred        libresolv.so.2
ELF	7e45c000-7e45f000	Deferred        libxdamage.so.1
ELF	7e45f000-7e462000	Deferred        libkeyutils.so.1
ELF	7e46b000-7e489000	Deferred        iphlpapi<elf>
  \-PE	7e470000-7e489000	\               iphlpapi
ELF	7e489000-7e4ea000	Deferred        rpcrt4<elf>
  \-PE	7e4a0000-7e4ea000	\               rpcrt4
ELF	7e4ea000-7e58e000	Deferred        ole32<elf>
  \-PE	7e500000-7e58e000	\               ole32
ELF	7e5b6000-7e5e9000	Deferred        uxtheme<elf>
  \-PE	7e5c0000-7e5e9000	\               uxtheme
ELF	7e5e9000-7e5f2000	Deferred        libxcursor.so.1
ELF	7e5f2000-7e5f7000	Deferred        libxfixes.so.3
ELF	7e5f7000-7e5fa000	Deferred        libxcomposite.so.1
ELF	7e5fa000-7e600000	Deferred        libxrandr.so.2
ELF	7e600000-7e608000	Deferred        libxrender.so.1
ELF	7e608000-7e60b000	Deferred        libxinerama.so.1
ELF	7e60b000-7e62b000	Deferred        imm32<elf>
  \-PE	7e610000-7e62b000	\               imm32
ELF	7e62b000-7e630000	Deferred        libxdmcp.so.6
ELF	7e630000-7e648000	Deferred        libxcb.so.1
ELF	7e648000-7e64b000	Deferred        libxau.so.6
ELF	7e64b000-7e732000	Deferred        libx11.so.6
ELF	7e732000-7e740000	Deferred        libxext.so.6
ELF	7e740000-7e745000	Deferred        libxxf86vm.so.1
ELF	7e745000-7e75d000	Deferred        libice.so.6
ELF	7e75d000-7e765000	Deferred        libsm.so.6
ELF	7e767000-7e76f000	Deferred        libkrb5support.so.0
ELF	7e76f000-7e772000	Deferred        libcom_err.so.2
ELF	7e774000-7e80b000	Deferred        winex11<elf>
  \-PE	7e780000-7e80b000	\               winex11
ELF	7e833000-7e854000	Deferred        libexpat.so.1
ELF	7e854000-7e87e000	Deferred        libfontconfig.so.1
ELF	7e87e000-7e893000	Deferred        libz.so.1
ELF	7e893000-7e903000	Deferred        libfreetype.so.6
ELF	7e903000-7e905000	Deferred        libxcb-xlib.so.0
ELF	7e912000-7e948000	Deferred        winspool<elf>
  \-PE	7e920000-7e948000	\               winspool
ELF	7e948000-7e9f3000	Deferred        comdlg32<elf>
  \-PE	7e950000-7e9f3000	\               comdlg32
ELF	7e9f3000-7ea07000	Deferred        lz32<elf>
  \-PE	7ea00000-7ea07000	\               lz32
ELF	7ea07000-7ea20000	Deferred        version<elf>
  \-PE	7ea10000-7ea20000	\               version
ELF	7ea20000-7eadf000	Deferred        comctl32<elf>
  \-PE	7ea30000-7eadf000	\               comctl32
ELF	7eadf000-7eb38000	Deferred        shlwapi<elf>
  \-PE	7eaf0000-7eb38000	\               shlwapi
ELF	7eb38000-7ec4b000	Deferred        shell32<elf>
  \-PE	7eb50000-7ec4b000	\               shell32
ELF	7ec4b000-7ec9d000	Deferred        advapi32<elf>
  \-PE	7ec60000-7ec9d000	\               advapi32
ELF	7ec9d000-7ed38000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed38000	\               gdi32
ELF	7ed38000-7ee7f000	Deferred        user32<elf>
  \-PE	7ed50000-7ee7f000	\               user32
ELF	7ef9f000-7efaa000	Deferred        libnss_files.so.2
ELF	7efaa000-7efb4000	Deferred        libnss_nis.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c33000-b7c37000	Deferred        libdl.so.2
ELF	b7c37000-b7d86000	Deferred        libc.so.6
ELF	b7d87000-b7d9f000	Deferred        libpthread.so.0
ELF	b7dae000-b7ee4000	Deferred        libwine.so.1
ELF	b7ee6000-b7f02000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Diablo\diablo.exe
	00000019    1
	00000018   15
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
00000016 
	00000017    0
Backtrace:
=>1 0xc7810789 (0x7ee25548)
  2 0x00000000 (0x000ed430)

```

---

### Post by das letzte einhorn on 2008-07-22
I believe you will find some answers to your problems here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498&iTestingId=20919](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498&iTestingId=20919)

---

