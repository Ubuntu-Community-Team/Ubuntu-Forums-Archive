---
title: "Starcraft B.net"
date: 2008-08-26
forum: Wine
---

### Post by h_howee on 2008-08-26
I tried running Starcraft BW using PlayOnLinux and got the following error messages:
```

fixme:win:EnumDisplayDevicesW ((null),0,0x33f410,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
howard@howard-desktop:~$
(python:2762): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'

(python:2878): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
CDROM mount point : /media/cdrom0

(python:2944): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
fixme:ras:RasEnumConnectionsA (0x1ff0094,0x33f7cc,0x33f7e0),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
wine: Unhandled page fault on write access to 0x011bc000 at address 0x1da0148 (thread 001c), starting debugger...
Unhandled exception: **page fault on write access to 0x011bc000 in 32-bit code (0x01da0148)**.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:01da0148 ESP:0033e434 EBP:0033e540 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00cff200 EBX:00000000 ECX:00000001 EDX:00000000
 ESI:025f796f EDI:011bc000
Stack dump:
0x0033e434:  003e01cc 00000003 0033e50c 00000000
0x0033e444:  000001d8 0033e494 0000005a 1505ed34
0x0033e454:  1505ed34 0000005a 025f5fd8 00000004
0x0033e464:  00000000 150291c0 7e01dabb 7e086c84
0x0033e474:  00000002 150291c0 150291e0 00000029
0x0033e484:  00000002 000002a2 000000a6 003a1be0
Backtrace:
=>1 0x01da0148 (0x0033e540)
0x01da0148: movb	%al,0x0(%edi)
Modules:
Module	Address			Debug info	Name (118 modules)
PE	  400000-  6ec000	Deferred        starcraft
PE	 2000000- 2011000	Deferred        local
PE	10000000-1001a000	Deferred        smackw32
PE	15000000-15069000	Deferred        storm
PE	19000000-19089000	Deferred        battle.snp
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7b9dd000-7b9f6000	Deferred        rasapi32<elf>
  \-PE	7b9e0000-7b9f6000	\               rasapi32
ELF	7b9f6000-7ba22000	Deferred        ws2_32<elf>
  \-PE	7ba00000-7ba22000	\               ws2_32
ELF	7ba22000-7ba3c000	Deferred        wsock32<elf>
  \-PE	7ba30000-7ba3c000	\               wsock32
ELF	7ba3c000-7bb00000	Deferred        libasound.so.2
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bca4000-7bcaf000	Deferred        libgcc_s.so.1
ELF	7bcc3000-7bce9000	Deferred        msacm32<elf>
  \-PE	7bcd0000-7bce9000	\               msacm32
ELF	7bce9000-7bd00000	Deferred        msacm32<elf>
  \-PE	7bcf0000-7bd00000	\               msacm32
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7bf0c000-7bf5a000	Deferred        libpulse.so.0
ELF	7bf5a000-7bf6e000	Deferred        midimap<elf>
  \-PE	7bf60000-7bf6e000	\               midimap
ELF	7bf6e000-7c000000	Deferred        winmm<elf>
  \-PE	7bf80000-7c000000	\               winmm
ELF	7c0f1000-7c0fa000	Deferred        librt.so.1
ELF	7c0fa000-7c130000	Deferred        winealsa<elf>
  \-PE	7c100000-7c130000	\               winealsa
ELF	7c130000-7c17a000	Deferred        dsound<elf>
  \-PE	7c140000-7c17a000	\               dsound
ELF	7dce7000-7df19000	Deferred        i915_dri.so
ELF	7df19000-7df23000	Deferred        libdrm.so.2
ELF	7df23000-7df26000	Deferred        libxdamage.so.1
ELF	7df26000-7df88000	Deferred        libgl.so.1
ELF	7df88000-7e08b000	Deferred        wined3d<elf>
  \-PE	7dfa0000-7e08b000	\               wined3d
ELF	7e08b000-7e0e2000	Deferred        ddraw<elf>
  \-PE	7e090000-7e0e2000	\               ddraw
ELF	7e1f3000-7e1f7000	Deferred        libgpg-error.so.0
ELF	7e1f7000-7e244000	Deferred        libgcrypt.so.11
ELF	7e244000-7e254000	Deferred        libtasn1.so.3
ELF	7e254000-7e25c000	Deferred        libkrb5support.so.0
ELF	7e25c000-7e28e000	Deferred        libcrypt.so.1
ELF	7e28e000-7e304000	Deferred        libgnutls.so.13
ELF	7e304000-7e327000	Deferred        libk5crypto.so.3
ELF	7e327000-7e3b4000	Deferred        libkrb5.so.3
ELF	7e3b4000-7e3dd000	Deferred        libgssapi_krb5.so.2
ELF	7e3dd000-7e410000	Deferred        libcups.so.2
ELF	7e434000-7e447000	Deferred        libresolv.so.2
ELF	7e447000-7e44d000	Deferred        libnss_dns.so.2
ELF	7e44d000-7e450000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e450000-7e454000	Deferred        libcap.so.1
ELF	7e454000-7e45b000	Deferred        libasound_module_pcm_pulse.so
ELF	7e45b000-7e479000	Deferred        iphlpapi<elf>
  \-PE	7e460000-7e479000	\               iphlpapi
ELF	7e479000-7e4da000	Deferred        rpcrt4<elf>
  \-PE	7e490000-7e4da000	\               rpcrt4
ELF	7e4da000-7e57e000	Deferred        ole32<elf>
  \-PE	7e4f0000-7e57e000	\               ole32
ELF	7e5a6000-7e5d9000	Deferred        uxtheme<elf>
  \-PE	7e5b0000-7e5d9000	\               uxtheme
ELF	7e5d9000-7e5e2000	Deferred        libxcursor.so.1
ELF	7e5e2000-7e5e7000	Deferred        libxfixes.so.3
ELF	7e5e7000-7e5ea000	Deferred        libxcomposite.so.1
ELF	7e5ea000-7e5f0000	Deferred        libxrandr.so.2
ELF	7e5f0000-7e5f8000	Deferred        libxrender.so.1
ELF	7e5f8000-7e5fb000	Deferred        libxinerama.so.1
ELF	7e5fb000-7e600000	Deferred        libxdmcp.so.6
ELF	7e600000-7e618000	Deferred        libxcb.so.1
ELF	7e618000-7e61b000	Deferred        libxau.so.6
ELF	7e61b000-7e702000	Deferred        libx11.so.6
ELF	7e702000-7e710000	Deferred        libxext.so.6
ELF	7e710000-7e715000	Deferred        libxxf86vm.so.1
ELF	7e715000-7e72d000	Deferred        libice.so.6
ELF	7e72d000-7e735000	Deferred        libsm.so.6
ELF	7e736000-7e739000	Deferred        libkeyutils.so.1
ELF	7e744000-7e747000	Deferred        libcom_err.so.2
ELF	7e749000-7e7e0000	Deferred        winex11<elf>
  \-PE	7e760000-7e7e0000	\               winex11
ELF	7e80a000-7e82b000	Deferred        libexpat.so.1
ELF	7e82b000-7e855000	Deferred        libfontconfig.so.1
ELF	7e855000-7e86a000	Deferred        libz.so.1
ELF	7e86a000-7e8da000	Deferred        libfreetype.so.6
ELF	7e8da000-7e8dc000	Deferred        libxcb-xlib.so.0
ELF	7e8ee000-7e924000	Deferred        winspool<elf>
  \-PE	7e900000-7e924000	\               winspool
ELF	7e924000-7e9cf000	Deferred        comdlg32<elf>
  \-PE	7e930000-7e9cf000	\               comdlg32
ELF	7e9cf000-7ea8e000	Deferred        comctl32<elf>
  \-PE	7e9e0000-7ea8e000	\               comctl32
ELF	7ea8e000-7eae7000	Deferred        shlwapi<elf>
  \-PE	7eaa0000-7eae7000	\               shlwapi
ELF	7eae7000-7ebfa000	Deferred        shell32<elf>
  \-PE	7eb00000-7ebfa000	\               shell32
ELF	7ebfa000-7ec13000	Deferred        version<elf>
  \-PE	7ec00000-7ec13000	\               version
ELF	7ec13000-7ec33000	Deferred        imm32<elf>
  \-PE	7ec20000-7ec33000	\               imm32
ELF	7ec33000-7ec85000	Deferred        advapi32<elf>
  \-PE	7ec40000-7ec85000	\               advapi32
ELF	7ec85000-7ed20000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed20000	\               gdi32
ELF	7ed20000-7ee67000	Deferred        user32<elf>
  \-PE	7ed40000-7ee67000	\               user32
ELF	7ee67000-7ee72000	Deferred        libnss_files.so.2
ELF	7ee72000-7ee8a000	Deferred        libnsl.so.1
ELF	7ee8a000-7ee93000	Deferred        libnss_compat.so.2
ELF	7ee93000-7eea7000	Deferred        lz32<elf>
  \-PE	7eea0000-7eea7000	\               lz32
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cf0000-b7cf4000	Deferred        libdl.so.2
ELF	b7cf4000-b7e43000	Deferred        libc.so.6
ELF	b7e44000-b7e5c000	Deferred        libpthread.so.0
ELF	b7e70000-b7fa6000	Deferred        libwine.so.1
ELF	b7fa8000-b7fc4000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000019 
	0000001a    0
0000001b (D) C:\Program Files\Starcraft\StarCraft.exe
	0000002c    0
	0000002b    0
	00000029    0
	00000028    2
	00000027    2
	00000022    2
	00000021    0
	00000020   15
	0000001f   15
	0000001d    1
	0000001c    0 <==
Backtrace:
=>1 0x01da0148 (0x0033e540)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
howard@howard-desktop:~$ err:seh:setup_exception_record stack overflow 820 bytes in thread 002c eip 7bc3ab33 esp 76a25ffc stack 0x76a25000-0x76a26000-0x76b36000
err:seh:setup_exception_record stack overflow 828 bytes in thread 002b eip 7bc72c62 esp 76b36ff4 stack 0x76b36000-0x76b37000-0x76c47000
err:seh:setup_exception_record stack overflow 876 bytes in thread 0029 eip b7e4ea1f esp 76c47fc4 stack 0x76c47000-0x76c48000-0x76d58000

```
How do I fix this?

[edit]
[http://ubuntuforums.org/showthread.php?t=868935](http://ubuntuforums.org/showthread.php?t=868935)
I got part of it fixed. I can log onto B.net but the lobby's still messed up. The pictures and buttons don't appear and the text overlaps when I change screens. I remember this problem coming up once in a while on windows too when I minimize the game through means other than alt+tabbing like clicking on a popup.
```

(python:13970): Gtk-WARNING **: /build/buildd/gtk+2.0-2.12.9/gtk/gtkwidget.c:8547: widget class `GtkPizza' has no property named `row-ending-details'

```
That error repeated itself 6 times. I don't think it's relevant to the problem but I'll post it just in case.

---

### Post by MeTylerDurden on 2008-08-27
I haven't been able to get Starcraft to install at all. Been going over and over all the help pages in spare time. When I click install there is no progress on the installation bar just hangs there for eternity.

---

### Post by MeTylerDurden on 2008-08-29
After much intense struggle I was able to install StarCraft, I wouldn't go through the effort though as only plays in small box and other problems that make it unplayable.  The way to do it is install Wubi so you can play in windows, thats the safest easiest way because I tried both ways.

---

### Post by Twitch6000 on 2008-08-29
> **h_howee said:**
> I tried running Starcraft BW using PlayOnLinux and got the following error messages:
```

fixme:win:EnumDisplayDevicesW ((null),0,0x33f410,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
howard@howard-desktop:~$
(python:2762): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'

(python:2878): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
CDROM mount point : /media/cdrom0

(python:2944): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
fixme:ras:RasEnumConnectionsA (0x1ff0094,0x33f7cc,0x33f7e0),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
wine: Unhandled page fault on write access to 0x011bc000 at address 0x1da0148 (thread 001c), starting debugger...
Unhandled exception: **page fault on write access to 0x011bc000 in 32-bit code (0x01da0148)**.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:01da0148 ESP:0033e434 EBP:0033e540 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00cff200 EBX:00000000 ECX:00000001 EDX:00000000
 ESI:025f796f EDI:011bc000
Stack dump:
0x0033e434:  003e01cc 00000003 0033e50c 00000000
0x0033e444:  000001d8 0033e494 0000005a 1505ed34
0x0033e454:  1505ed34 0000005a 025f5fd8 00000004
0x0033e464:  00000000 150291c0 7e01dabb 7e086c84
0x0033e474:  00000002 150291c0 150291e0 00000029
0x0033e484:  00000002 000002a2 000000a6 003a1be0
Backtrace:
=>1 0x01da0148 (0x0033e540)
0x01da0148: movb	%al,0x0(%edi)
Modules:
Module	Address			Debug info	Name (118 modules)
PE	  400000-  6ec000	Deferred        starcraft
PE	 2000000- 2011000	Deferred        local
PE	10000000-1001a000	Deferred        smackw32
PE	15000000-15069000	Deferred        storm
PE	19000000-19089000	Deferred        battle.snp
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7b9dd000-7b9f6000	Deferred        rasapi32<elf>
  \-PE	7b9e0000-7b9f6000	\               rasapi32
ELF	7b9f6000-7ba22000	Deferred        ws2_32<elf>
  \-PE	7ba00000-7ba22000	\               ws2_32
ELF	7ba22000-7ba3c000	Deferred        wsock32<elf>
  \-PE	7ba30000-7ba3c000	\               wsock32
ELF	7ba3c000-7bb00000	Deferred        libasound.so.2
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bca4000-7bcaf000	Deferred        libgcc_s.so.1
ELF	7bcc3000-7bce9000	Deferred        msacm32<elf>
  \-PE	7bcd0000-7bce9000	\               msacm32
ELF	7bce9000-7bd00000	Deferred        msacm32<elf>
  \-PE	7bcf0000-7bd00000	\               msacm32
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7bf0c000-7bf5a000	Deferred        libpulse.so.0
ELF	7bf5a000-7bf6e000	Deferred        midimap<elf>
  \-PE	7bf60000-7bf6e000	\               midimap
ELF	7bf6e000-7c000000	Deferred        winmm<elf>
  \-PE	7bf80000-7c000000	\               winmm
ELF	7c0f1000-7c0fa000	Deferred        librt.so.1
ELF	7c0fa000-7c130000	Deferred        winealsa<elf>
  \-PE	7c100000-7c130000	\               winealsa
ELF	7c130000-7c17a000	Deferred        dsound<elf>
  \-PE	7c140000-7c17a000	\               dsound
ELF	7dce7000-7df19000	Deferred        i915_dri.so
ELF	7df19000-7df23000	Deferred        libdrm.so.2
ELF	7df23000-7df26000	Deferred        libxdamage.so.1
ELF	7df26000-7df88000	Deferred        libgl.so.1
ELF	7df88000-7e08b000	Deferred        wined3d<elf>
  \-PE	7dfa0000-7e08b000	\               wined3d
ELF	7e08b000-7e0e2000	Deferred        ddraw<elf>
  \-PE	7e090000-7e0e2000	\               ddraw
ELF	7e1f3000-7e1f7000	Deferred        libgpg-error.so.0
ELF	7e1f7000-7e244000	Deferred        libgcrypt.so.11
ELF	7e244000-7e254000	Deferred        libtasn1.so.3
ELF	7e254000-7e25c000	Deferred        libkrb5support.so.0
ELF	7e25c000-7e28e000	Deferred        libcrypt.so.1
ELF	7e28e000-7e304000	Deferred        libgnutls.so.13
ELF	7e304000-7e327000	Deferred        libk5crypto.so.3
ELF	7e327000-7e3b4000	Deferred        libkrb5.so.3
ELF	7e3b4000-7e3dd000	Deferred        libgssapi_krb5.so.2
ELF	7e3dd000-7e410000	Deferred        libcups.so.2
ELF	7e434000-7e447000	Deferred        libresolv.so.2
ELF	7e447000-7e44d000	Deferred        libnss_dns.so.2
ELF	7e44d000-7e450000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e450000-7e454000	Deferred        libcap.so.1
ELF	7e454000-7e45b000	Deferred        libasound_module_pcm_pulse.so
ELF	7e45b000-7e479000	Deferred        iphlpapi<elf>
  \-PE	7e460000-7e479000	\               iphlpapi
ELF	7e479000-7e4da000	Deferred        rpcrt4<elf>
  \-PE	7e490000-7e4da000	\               rpcrt4
ELF	7e4da000-7e57e000	Deferred        ole32<elf>
  \-PE	7e4f0000-7e57e000	\               ole32
ELF	7e5a6000-7e5d9000	Deferred        uxtheme<elf>
  \-PE	7e5b0000-7e5d9000	\               uxtheme
ELF	7e5d9000-7e5e2000	Deferred        libxcursor.so.1
ELF	7e5e2000-7e5e7000	Deferred        libxfixes.so.3
ELF	7e5e7000-7e5ea000	Deferred        libxcomposite.so.1
ELF	7e5ea000-7e5f0000	Deferred        libxrandr.so.2
ELF	7e5f0000-7e5f8000	Deferred        libxrender.so.1
ELF	7e5f8000-7e5fb000	Deferred        libxinerama.so.1
ELF	7e5fb000-7e600000	Deferred        libxdmcp.so.6
ELF	7e600000-7e618000	Deferred        libxcb.so.1
ELF	7e618000-7e61b000	Deferred        libxau.so.6
ELF	7e61b000-7e702000	Deferred        libx11.so.6
ELF	7e702000-7e710000	Deferred        libxext.so.6
ELF	7e710000-7e715000	Deferred        libxxf86vm.so.1
ELF	7e715000-7e72d000	Deferred        libice.so.6
ELF	7e72d000-7e735000	Deferred        libsm.so.6
ELF	7e736000-7e739000	Deferred        libkeyutils.so.1
ELF	7e744000-7e747000	Deferred        libcom_err.so.2
ELF	7e749000-7e7e0000	Deferred        winex11<elf>
  \-PE	7e760000-7e7e0000	\               winex11
ELF	7e80a000-7e82b000	Deferred        libexpat.so.1
ELF	7e82b000-7e855000	Deferred        libfontconfig.so.1
ELF	7e855000-7e86a000	Deferred        libz.so.1
ELF	7e86a000-7e8da000	Deferred        libfreetype.so.6
ELF	7e8da000-7e8dc000	Deferred        libxcb-xlib.so.0
ELF	7e8ee000-7e924000	Deferred        winspool<elf>
  \-PE	7e900000-7e924000	\               winspool
ELF	7e924000-7e9cf000	Deferred        comdlg32<elf>
  \-PE	7e930000-7e9cf000	\               comdlg32
ELF	7e9cf000-7ea8e000	Deferred        comctl32<elf>
  \-PE	7e9e0000-7ea8e000	\               comctl32
ELF	7ea8e000-7eae7000	Deferred        shlwapi<elf>
  \-PE	7eaa0000-7eae7000	\               shlwapi
ELF	7eae7000-7ebfa000	Deferred        shell32<elf>
  \-PE	7eb00000-7ebfa000	\               shell32
ELF	7ebfa000-7ec13000	Deferred        version<elf>
  \-PE	7ec00000-7ec13000	\               version
ELF	7ec13000-7ec33000	Deferred        imm32<elf>
  \-PE	7ec20000-7ec33000	\               imm32
ELF	7ec33000-7ec85000	Deferred        advapi32<elf>
  \-PE	7ec40000-7ec85000	\               advapi32
ELF	7ec85000-7ed20000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed20000	\               gdi32
ELF	7ed20000-7ee67000	Deferred        user32<elf>
  \-PE	7ed40000-7ee67000	\               user32
ELF	7ee67000-7ee72000	Deferred        libnss_files.so.2
ELF	7ee72000-7ee8a000	Deferred        libnsl.so.1
ELF	7ee8a000-7ee93000	Deferred        libnss_compat.so.2
ELF	7ee93000-7eea7000	Deferred        lz32<elf>
  \-PE	7eea0000-7eea7000	\               lz32
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cf0000-b7cf4000	Deferred        libdl.so.2
ELF	b7cf4000-b7e43000	Deferred        libc.so.6
ELF	b7e44000-b7e5c000	Deferred        libpthread.so.0
ELF	b7e70000-b7fa6000	Deferred        libwine.so.1
ELF	b7fa8000-b7fc4000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000019 
	0000001a    0
0000001b (D) C:\Program Files\Starcraft\StarCraft.exe
	0000002c    0
	0000002b    0
	00000029    0
	00000028    2
	00000027    2
	00000022    2
	00000021    0
	00000020   15
	0000001f   15
	0000001d    1
	0000001c    0 <==
Backtrace:
=>1 0x01da0148 (0x0033e540)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
howard@howard-desktop:~$ err:seh:setup_exception_record stack overflow 820 bytes in thread 002c eip 7bc3ab33 esp 76a25ffc stack 0x76a25000-0x76a26000-0x76b36000
err:seh:setup_exception_record stack overflow 828 bytes in thread 002b eip 7bc72c62 esp 76b36ff4 stack 0x76b36000-0x76b37000-0x76c47000
err:seh:setup_exception_record stack overflow 876 bytes in thread 0029 eip b7e4ea1f esp 76c47fc4 stack 0x76c47000-0x76c48000-0x76d58000

```
How do I fix this?

[edit]
[http://ubuntuforums.org/showthread.php?t=868935](http://ubuntuforums.org/showthread.php?t=868935)
I got part of it fixed. I can log onto B.net but the lobby's still messed up. The pictures and buttons don't appear and the text overlaps when I change screens. I remember this problem coming up once in a while on windows too when I minimize the game through means other than alt+tabbing like clicking on a popup.
```

(python:13970): Gtk-WARNING **: /build/buildd/gtk+2.0-2.12.9/gtk/gtkwidget.c:8547: widget class `GtkPizza' has no property named `row-ending-details'

```
That error repeated itself 6 times. I don't think it's relevant to the problem but I'll post it just in case.

I still don't see how you people are getting it to work under full screen :(.

I suggest though for it to not have the overlap bug and such.
Either use a virtual machine or get Cedega which fixes Starcraft.

---

### Post by Sephoroth on 2008-08-29
Hmm, I remember I had a "black screen" bug though buttons would work fine after being moused over and after a match actually started everything worked fine.  It's been a while since I've tried it though....

---

