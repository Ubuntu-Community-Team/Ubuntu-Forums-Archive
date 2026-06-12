---
title: "Garena 3"
date: 2008-09-16
forum: Wine
---

### Post by /////// on 2008-09-16
How do I run Garena 3 in WINE. I've managed to install it fine but when I load it, I get this terminal error:

fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
wine: Unhandled division by zero at address 0x7e9450c8 (thread 0021), starting debugger...
Unhandled exception: divide by zero in 32-bit code (0x7e9450c8).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e9450c8 ESP:0032bc8c EBP:0032bd24 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:843cc181 EBX:7e9b773c ECX:7ede9480 EDX:00000000
 ESI:001564d0 EDI:0032bd08
Stack dump:
0x0032bc8c:  00010074 00000000 0032bcec 00000001
0x0032bc9c:  00010074 7bc33e7f 7e495541 7e9b773c
0x0032bcac:  00156520 001564d0 0032bd08 7e944b76
0x0032bcbc:  0032bcec 00000001 00000000 00000004
0x0032bccc:  00010074 0000001c 00000000 00000000
0x0032bcdc:  00000000 843cc181 00000000 00000000
Backtrace:
=>1 0x7e9450c8 in comctl32 (+0x350c8) (0x0032bd24)
  2 0x7e953bce in comctl32 (+0x43bce) (0x0032bda4)
  3 0x7e956761 in comctl32 (+0x46761) (0x0032c6d4)
  4 0x7eda5dba WINPROC_wrapper+0x1a() in user32 (0x0032c704)
  5 0x7eda649e WINPROC_wrapper+0x6fe() in user32 (0x0032c744)
  6 0x7edac672 CallWindowProcW+0x52() in user32 (0x0032c784)
  7 0x00450595 in garena (+0x50595) (0x0032cb20)
  8 0x44200041 (0x40200041)
0x7e9450c8: divl	0x34(%esi),%eax
Modules:
Module	Address			Debug info	Name (119 modules)
PE	  330000-  347000	Deferred        pluginkernel
PE	  350000-  3ba000	Deferred        garenaskin
PE	  400000-  70d000	Export          garena
PE	  da0000-  dcb000	Deferred        networklayer
PE	  ee0000-  ef4000	Deferred        webcache
PE	 1010000- 102b000	Deferred        garenatvrecorder
PE	 1140000- 115d000	Deferred        wc3ladder
PE	 1270000- 1286000	Deferred        wc3vc
PE	10000000-1000e000	Deferred        inject
PE	48000000-4806c000	Deferred        riched20
PE	60900000-6095f000	Deferred        sqlite3
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d551000-7d56b000	Deferred        wsock32<elf>
  \-PE	7d560000-7d56b000	\               wsock32
ELF	7d56b000-7d592000	Deferred        msacm32<elf>
  \-PE	7d570000-7d592000	\               msacm32
ELF	7d592000-7d5a9000	Deferred        msacm32<elf>
  \-PE	7d5a0000-7d5a9000	\               msacm32
ELF	7ddaa000-7ddb3000	Deferred        librt.so.1
ELF	7ddb3000-7ddcb000	Deferred        libice.so.6
ELF	7ddcb000-7de19000	Deferred        libpulse.so.0
ELF	7de1a000-7de2e000	Deferred        midimap<elf>
  \-PE	7de20000-7de2e000	\               midimap
ELF	7de2e000-7def1000	Deferred        libasound.so.2
ELF	7def1000-7df26000	Deferred        winealsa<elf>
  \-PE	7df00000-7df26000	\               winealsa
ELF	7df26000-7df2a000	Deferred        libgpg-error.so.0
ELF	7df2a000-7df77000	Deferred        libgcrypt.so.11
ELF	7df77000-7df87000	Deferred        libtasn1.so.3
ELF	7df87000-7df8f000	Deferred        libkrb5support.so.0
ELF	7df8f000-7dfc1000	Deferred        libcrypt.so.1
ELF	7dfc1000-7e036000	Deferred        libgnutls.so.13
ELF	7e036000-7e059000	Deferred        libk5crypto.so.3
ELF	7e059000-7e0e6000	Deferred        libkrb5.so.3
ELF	7e0e6000-7e10f000	Deferred        libgssapi_krb5.so.2
ELF	7e10f000-7e142000	Deferred        libcups.so.2
ELF	7e145000-7e149000	Deferred        libcap.so.1
ELF	7e149000-7e151000	Deferred        libsm.so.6
ELF	7e151000-7e157000	Deferred        libasound_module_pcm_pulse.so
ELF	7e1a8000-7e1db000	Deferred        uxtheme<elf>
  \-PE	7e1b0000-7e1db000	\               uxtheme
ELF	7e1db000-7e1e4000	Deferred        libxcursor.so.1
ELF	7e1e4000-7e1e9000	Deferred        libxfixes.so.3
ELF	7e1e9000-7e1ec000	Deferred        libxcomposite.so.1
ELF	7e1ec000-7e1f2000	Deferred        libxrandr.so.2
ELF	7e1f2000-7e1fa000	Deferred        libxrender.so.1
ELF	7e1fa000-7e1ff000	Deferred        libxxf86vm.so.1
ELF	7e1ff000-7e202000	Deferred        libxinerama.so.1
ELF	7e202000-7e222000	Deferred        imm32<elf>
  \-PE	7e210000-7e222000	\               imm32
ELF	7e222000-7e227000	Deferred        libxdmcp.so.6
ELF	7e227000-7e23f000	Deferred        libxcb.so.1
ELF	7e23f000-7e241000	Deferred        libxcb-xlib.so.0
ELF	7e241000-7e244000	Deferred        libxau.so.6
ELF	7e244000-7e32b000	Deferred        libx11.so.6
ELF	7e32b000-7e339000	Deferred        libxext.so.6
ELF	7e33c000-7e33f000	Deferred        libkeyutils.so.1
ELF	7e349000-7e34c000	Deferred        libcom_err.so.2
ELF	7e34e000-7e3e6000	Deferred        winex11<elf>
  \-PE	7e360000-7e3e6000	\               winex11
ELF	7e425000-7e446000	Deferred        libexpat.so.1
ELF	7e446000-7e470000	Deferred        libfontconfig.so.1
ELF	7e470000-7e485000	Deferred        libz.so.1
ELF	7e485000-7e4f5000	Deferred        libfreetype.so.6
ELF	7e50a000-7e51e000	Deferred        lz32<elf>
  \-PE	7e510000-7e51e000	\               lz32
ELF	7e51e000-7e537000	Deferred        version<elf>
  \-PE	7e520000-7e537000	\               version
ELF	7e537000-7e5c9000	Deferred        winmm<elf>
  \-PE	7e540000-7e5c9000	\               winmm
ELF	7e5c9000-7e5eb000	Deferred        mpr<elf>
  \-PE	7e5d0000-7e5eb000	\               mpr
ELF	7e5eb000-7e63a000	Deferred        wininet<elf>
  \-PE	7e5f0000-7e63a000	\               wininet
ELF	7e63a000-7e666000	Deferred        ws2_32<elf>
  \-PE	7e640000-7e666000	\               ws2_32
ELF	7e666000-7e738000	Deferred        oleaut32<elf>
  \-PE	7e680000-7e738000	\               oleaut32
ELF	7e738000-7e74b000	Deferred        libresolv.so.2
ELF	7e74d000-7e760000	Deferred        msimg32<elf>
  \-PE	7e750000-7e760000	\               msimg32
ELF	7e760000-7e77f000	Deferred        iphlpapi<elf>
  \-PE	7e770000-7e77f000	\               iphlpapi
ELF	7e77f000-7e7e3000	Deferred        rpcrt4<elf>
  \-PE	7e790000-7e7e3000	\               rpcrt4
ELF	7e7e3000-7e8d5000	Deferred        ole32<elf>
  \-PE	7e800000-7e8d5000	\               ole32
ELF	7e8d5000-7e90a000	Deferred        winspool<elf>
  \-PE	7e8e0000-7e90a000	\               winspool
ELF	7e90a000-7e9cb000	Export          comctl32<elf>
  \-PE	7e910000-7e9cb000	\               comctl32
ELF	7e9cb000-7ea25000	Deferred        shlwapi<elf>
  \-PE	7e9e0000-7ea25000	\               shlwapi
ELF	7ea25000-7eb3f000	Deferred        shell32<elf>
  \-PE	7ea40000-7eb3f000	\               shell32
ELF	7eb3f000-7ebeb000	Deferred        comdlg32<elf>
  \-PE	7eb50000-7ebeb000	\               comdlg32
ELF	7ebeb000-7ec3d000	Deferred        advapi32<elf>
  \-PE	7ec00000-7ec3d000	\               advapi32
ELF	7ec3d000-7ecdb000	Deferred        gdi32<elf>
  \-PE	7ec50000-7ecdb000	\               gdi32
ELF	7ecdb000-7ee24000	Export          user32<elf>
  \-PE	7ed00000-7ee24000	\               user32
ELF	7ee24000-7ee8e000	Deferred        msvcrt<elf>
  \-PE	7ee30000-7ee8e000	\               msvcrt
ELF	7efae000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efeb000	Deferred        libm.so.6
ELF	7efeb000-7eff6000	Deferred        libnss_files.so.2
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	f7d00000-f7d09000	Deferred        libnss_compat.so.2
ELF	f7d0a000-f7d0e000	Deferred        libdl.so.2
ELF	f7d0e000-f7e5d000	Deferred        libc.so.6
ELF	f7e5e000-f7e76000	Deferred        libpthread.so.0
ELF	f7e8b000-f7fc1000	Deferred        libwine.so.1
ELF	f7fc3000-f7fe2000	Deferred        ld-linux.so.2
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
00000016 
	0000001b    0
	00000017    0
00000018 
	00000019    0
00000020 (D) C:\Program Files\Garena\Garena.exe
	00000023   15
	00000022    0
	00000021    0 <==
Backtrace:
=>1 0x7e9450c8 in comctl32 (+0x350c8) (0x0032bd24)
  2 0x7e953bce in comctl32 (+0x43bce) (0x0032bda4)
  3 0x7e956761 in comctl32 (+0x46761) (0x0032c6d4)
  4 0x7eda5dba WINPROC_wrapper+0x1a() in user32 (0x0032c704)
  5 0x7eda649e WINPROC_wrapper+0x6fe() in user32 (0x0032c744)
  6 0x7edac672 CallWindowProcW+0x52() in user32 (0x0032c784)
  7 0x00450595 in garena (+0x50595) (0x0032cb20)
  8 0x44200041 (0x40200041)

---

### Post by cocoyriv on 2008-10-01
I followed the howto [[COLOR="Red"]here[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13086"). I used the latest wine version from git and used the basic try2 patch. 
Garena3 works for me. :D It loads. I am able to join rooms. People can see my chat messages. I can load Frozen Throne, Starcraft and CS 1.6 but I don't see any games either from the games list in Garena or from within the games themselves. :( 
I hope this helps.

---

### Post by micdhack on 2008-10-27
so its still not fully working..
with the default wine i am getting the exact same errors
lets hope that in the near future the will manage to make it work. I saw that already in fedora works so i think its just a matter of time.

---

