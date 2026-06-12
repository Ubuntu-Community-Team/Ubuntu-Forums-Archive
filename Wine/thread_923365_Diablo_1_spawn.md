---
title: "Diablo 1 spawn"
date: 2008-09-18
forum: Wine
---

### Post by toastytoast on 2008-09-18
I install the diablo spawn version from my friends cd i would like to play it i have tryed 95 through vista wine settings none work diablo 2 works well though when i try to run it it will start but then crash before the menu screen wine reports
cesW ((null),0,0x33f7e8,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x131ea0)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x131ea0)->(1,(nil)): Stub
wine: Unhandled page fault on read access to 0x017ac000 at address 0x7b4df8 (thread 0017), starting debugger...
Unhandled exception: page fault on read access to 0x017ac000 in 32-bit code (0x007b4df8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:007b4df8 ESP:0033f2a4 EBP:7edec409 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:00000000 ECX:0033f400 EDX:00000001
 ESI:017abfff EDI:016d1b43
Stack dump:
0x0033f2a4:  003f0118 00000013 0033f388 00000023
0x0033f2b4:  00000000 0033f304 016301a4 7edec450
0x0033f2c4:  7edec450 016301a4 0163008c 44444353
0x0033f2d4:  44444444 1500b5d0 7ee36e40 3d442023
0x0033f2e4:  00000097 1500b5f0 00000000 1500b5d0
0x0033f2f4:  00000001 00000974 0000025d 003b1630
Backtrace:
=>1 0x007b4df8 (0x7edec409)
  2 0x3110558b (0x3674ff85)
0x007b4df8: movl	0x0(%esi),%eax
Modules:
Module	Address			Debug info	Name (108 modules)
PE	  400000-  692000	Deferred        diablo_s
PE	 13c0000- 13da000	Deferred        smackw32
PE	10000000-10048000	Deferred        diabloui
PE	15000000-15041000	Deferred        storm
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7be03000-7be17000	Deferred        midimap<elf>
  \-PE	7be10000-7be17000	\               midimap
ELF	7be17000-7be3d000	Deferred        msacm32<elf>
  \-PE	7be20000-7be3d000	\               msacm32
ELF	7be3d000-7bf00000	Deferred        libasound.so.2
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7bf0d000-7bf24000	Deferred        msacm32<elf>
  \-PE	7bf10000-7bf24000	\               msacm32
ELF	7bf24000-7bfb6000	Deferred        winmm<elf>
  \-PE	7bf30000-7bfb6000	\               winmm
ELF	7bfb6000-7c000000	Deferred        dsound<elf>
  \-PE	7bfc0000-7c000000	\               dsound
ELF	7c5aa000-7c5e0000	Deferred        winealsa<elf>
  \-PE	7c5b0000-7c5e0000	\               winealsa
ELF	7dd8d000-7dfbf000	Deferred        i915_dri.so
ELF	7dfbf000-7dfc9000	Deferred        libdrm.so.2
ELF	7dfc9000-7dfcc000	Deferred        libxdamage.so.1
ELF	7dfcc000-7e02e000	Deferred        libgl.so.1
ELF	7e02e000-7e131000	Deferred        wined3d<elf>
  \-PE	7e040000-7e131000	\               wined3d
ELF	7e131000-7e188000	Deferred        ddraw<elf>
  \-PE	7e140000-7e188000	\               ddraw
ELF	7e188000-7e18c000	Deferred        libgpg-error.so.0
ELF	7e18c000-7e1d9000	Deferred        libgcrypt.so.11
ELF	7e1d9000-7e1e9000	Deferred        libtasn1.so.3
ELF	7e1e9000-7e1ec000	Deferred        libkeyutils.so.1
ELF	7e1ec000-7e1f4000	Deferred        libkrb5support.so.0
ELF	7e1f4000-7e226000	Deferred        libcrypt.so.1
ELF	7e226000-7e29c000	Deferred        libgnutls.so.13
ELF	7e29c000-7e2bf000	Deferred        libk5crypto.so.3
ELF	7e2bf000-7e34c000	Deferred        libkrb5.so.3
ELF	7e34c000-7e375000	Deferred        libgssapi_krb5.so.2
ELF	7e375000-7e3a8000	Deferred        libcups.so.2
ELF	7e3cc000-7e3df000	Deferred        libresolv.so.2
ELF	7e3ee000-7e40c000	Deferred        iphlpapi<elf>
  \-PE	7e3f0000-7e40c000	\               iphlpapi
ELF	7e40c000-7e46d000	Deferred        rpcrt4<elf>
  \-PE	7e420000-7e46d000	\               rpcrt4
ELF	7e46d000-7e511000	Deferred        ole32<elf>
  \-PE	7e480000-7e511000	\               ole32
ELF	7e539000-7e56c000	Deferred        uxtheme<elf>
  \-PE	7e540000-7e56c000	\               uxtheme
ELF	7e56c000-7e575000	Deferred        libxcursor.so.1
ELF	7e575000-7e57a000	Deferred        libxfixes.so.3
ELF	7e57a000-7e57d000	Deferred        libxcomposite.so.1
ELF	7e57d000-7e583000	Deferred        libxrandr.so.2
ELF	7e583000-7e58b000	Deferred        libxrender.so.1
ELF	7e58b000-7e58e000	Deferred        libxinerama.so.1
ELF	7e58e000-7e5ae000	Deferred        imm32<elf>
  \-PE	7e590000-7e5ae000	\               imm32
ELF	7e5ae000-7e5c6000	Deferred        libxcb.so.1
ELF	7e5c6000-7e6ad000	Deferred        libx11.so.6
ELF	7e6ad000-7e6bb000	Deferred        libxext.so.6
ELF	7e6bb000-7e6d3000	Deferred        libice.so.6
ELF	7e6d3000-7e6db000	Deferred        libsm.so.6
ELF	7e6e5000-7e6e8000	Deferred        libcom_err.so.2
ELF	7e6ea000-7e781000	Deferred        winex11<elf>
  \-PE	7e700000-7e781000	\               winex11
ELF	7e7a5000-7e7c6000	Deferred        libexpat.so.1
ELF	7e7c6000-7e7f0000	Deferred        libfontconfig.so.1
ELF	7e7ff000-7e814000	Deferred        libz.so.1
ELF	7e814000-7e881000	Deferred        libfreetype.so.6
ELF	7e881000-7e8eb000	Deferred        msvcrt<elf>
  \-PE	7e890000-7e8eb000	\               msvcrt
ELF	7e8eb000-7e904000	Deferred        crtdll<elf>
  \-PE	7e8f0000-7e904000	\               crtdll
ELF	7e904000-7e918000	Deferred        lz32<elf>
  \-PE	7e910000-7e918000	\               lz32
ELF	7e918000-7e931000	Deferred        version<elf>
  \-PE	7e920000-7e931000	\               version
ELF	7e931000-7e967000	Deferred        winspool<elf>
  \-PE	7e940000-7e967000	\               winspool
ELF	7e967000-7ea12000	Deferred        comdlg32<elf>
  \-PE	7e970000-7ea12000	\               comdlg32
ELF	7ea12000-7ead1000	Deferred        comctl32<elf>
  \-PE	7ea20000-7ead1000	\               comctl32
ELF	7ead1000-7eb2a000	Deferred        shlwapi<elf>
  \-PE	7eae0000-7eb2a000	\               shlwapi
ELF	7eb2a000-7ec3d000	Deferred        shell32<elf>
  \-PE	7eb40000-7ec3d000	\               shell32
ELF	7ec3d000-7ec8f000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec8f000	\               advapi32
ELF	7ec8f000-7ed2a000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed2a000	\               gdi32
ELF	7ed2a000-7ee71000	Deferred        user32<elf>
  \-PE	7ed40000-7ee71000	\               user32
ELF	7ee71000-7ee7c000	Deferred        libnss_files.so.2
ELF	7ee7c000-7ee94000	Deferred        libnsl.so.1
ELF	7ee94000-7ee9d000	Deferred        libnss_compat.so.2
ELF	7ee9d000-7eea2000	Deferred        libxdmcp.so.6
ELF	7eea2000-7eea4000	Deferred        libxcb-xlib.so.0
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff1000-7eff6000	Deferred        libxxf86vm.so.1
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cd1000-b7cd4000	Deferred        libxau.so.6
ELF	b7cdb000-b7cdf000	Deferred        libdl.so.2
ELF	b7cdf000-b7e2e000	Deferred        libc.so.6
ELF	b7e2f000-b7e47000	Deferred        libpthread.so.0
ELF	b7e56000-b7f8c000	Deferred        libwine.so.1
ELF	b7f8e000-b7faa000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
00000016 (D) C:\Program Files\Spawn\Diablo_S.exe
	0000001a   15
	00000017    0 <==
00000018 
	00000019    0
Backtrace:
=>1 0x007b4df8 (0x7edec409)
  2 0x3110558b (0x3674ff85)


please help diablo 1 is a really good game

---

### Post by asdfoo on 2008-09-18
The AppDB [http://appdb.winehq.org](http://appdb.winehq.org) has instructions for Diablo, did you follow them?

---

