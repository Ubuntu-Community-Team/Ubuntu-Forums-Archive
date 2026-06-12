---
title: "Wine 1.7.7 photoshop + picasa"
date: 2014-02-01
forum: Wine
---

### Post by kdesrosiers-2 on 2014-02-01
Hi, 

I'm quite new with ubuntu. I'm on Xubuntu 12.04


I manage to install photoshop with a "special" wine 1.7 compile by me but as recommended on Alejandro Fanjul web site. 

Now my photoshop is working perfectly (better/faster than in windows).

But... with this wine version I cannot install picasa 3.9 (my GF want it because it is easy to send picture (with redimensionning) via gmail).

Now that my photoshop is install... can I install another version of wine that will allow me to install picasa ?

Here are the error messages in the wine windows :

Unhandled exception: page fault on read access to 0x00406c21 in 32-bit code (0x00406c21).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00406c21 ESP:0032fe64 EBP:0032fe78 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:00000000 EBX:7b8b3ff4 ECX:0032fef0 EDX:00400000
 ESI:7ffdf000 EDI:00406c21
Stack dump:
0x0032fe64:  7b85fb0c 7ffdf000 7bc56efa 7b8b3ff4
0x0032fe74:  7ffdf000 0032feb8 7b860d8b 7ffdf000
0x0032fe84:  00406c21 00000000 00000000 00000000
0x0032fe94:  00000000 00000000 00000000 00000000
0x0032fea4:  00000000 0032fed0 7bcc5ff4 ffe174a4
0x0032feb4:  001107a0 0032fed8 7bc81210 00000000
Backtrace:
=>0 0x00406c21 EntryPoint() in picasa39-setup (0x0032fe78)
  1 0x7b860d8b start_process+0x6a(peb=0xffffffff) [/home/kevin/TÃ©lÃ©chargements/wine-1.7.7/dlls/kernel32/process.c:1097] in kernel32 (0x0032feb8)
  2 0x7bc81210 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  3 0x7bc841ed call_thread_func+0x7c(entry=0x7b860d20, arg=0x7ffdf000, frame=0x32ffc8) [/home/kevin/TÃ©lÃ©chargements/wine-1.7.7/dlls/ntdll/signal_i386.c:2602] in ntdll (0x0032ffa8)
  4 0x7bc811ee call_thread_entry_point+0x11() in ntdll (0x0032ffc8)
  5 0x7bc54bce start_process+0x1d(kernel_start=0x7b860d20) [/home/kevin/TÃ©lÃ©chargements/wine-1.7.7/dlls/ntdll/loader.c:2762] in ntdll (0x0032ffe8)
  6 0xf75b298d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  7 0xf75b2a4b wine_switch_to_stack+0x2a(func=0x7bc54bb0, arg=0x7b860d20, stack=0x330000) [/home/kevin/TÃ©lÃ©chargements/wine-1.7.7/libs/wine/port.c:59] in libwine.so.1 (0xffe174c8)
  8 0x7bc5aa98 LdrInitializeThunk+0x3a7(kernel_start=0xffffffff, unknown2=0x7bc98750, unknown3=0x7b83b910, unknown4=0x7bcc5ff4) [/home/kevin/TÃ©lÃ©chargements/wine-1.7.7/dlls/ntdll/loader.c:2818] in ntdll (0xffe17538)
  9 0x7b8675a8 __wine_kernel_init+0xa27() [/home/kevin/TÃ©lÃ©chargements/wine-1.7.7/dlls/kernel32/process.c:1269] in kernel32 (0xffe186e8)
  10 0x7bc5b4cb __wine_process_init+0x25a() [/home/kevin/TÃ©lÃ©chargements/wine-1.7.7/dlls/ntdll/loader.c:3027] in ntdll (0xffe18778)
  11 0xf75afec0 wine_init+0x29f(argc=0x2, argv=0xffe18cc4, error="", error_size=0x400) [/home/kevin/TÃ©lÃ©chargements/wine-1.7.7/libs/wine/loader.c:952] in libwine.so.1 (0xffe187d8)
  12 0x7bf00cfb main+0x8a(argc=<is not available>, argv=<is not available>) [/home/kevin/TÃ©lÃ©chargements/wine-1.7.7/loader/main.c:237] in <wine-loader> (0xffe18c28)
  13 0xf73dc4d3 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x00406c21 EntryPoint in picasa39-setup: call	0x0040b756
Modules:
Module	Address			Debug info	Name (66 modules)
PE	  400000- 14d8000	Export          picasa39-setup
PE	1a400000-1a532000	Deferred        urlmon
PE	5dca0000-5de88000	Deferred        iertutil
PE	77f60000-77fd6000	Deferred        shlwapi
ELF	7b800000-7ba5a000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba5a000	\               kernel32
ELF	7bc00000-7bce3000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bce3000	\               ntdll
ELF	7bf00000-7bf04000	Dwarf           <wine-loader>
ELF	7de7d000-7deb4000	Deferred        uxtheme<elf>
  \-PE	7de80000-7deb4000	\               uxtheme
ELF	7deb4000-7deba000	Deferred        libxfixes.so.3
ELF	7deba000-7dec5000	Deferred        libxcursor.so.1
ELF	7dec5000-7ded6000	Deferred        libxi.so.6
ELF	7ded6000-7deda000	Deferred        libxcomposite.so.1
ELF	7deda000-7dee3000	Deferred        libxrandr.so.2
ELF	7dee3000-7deed000	Deferred        libxrender.so.1
ELF	7deed000-7def3000	Deferred        libxxf86vm.so.1
ELF	7def3000-7def7000	Deferred        libxinerama.so.1
ELF	7def7000-7defe000	Deferred        libxdmcp.so.6
ELF	7defe000-7df02000	Deferred        libxau.so.6
ELF	7df02000-7df23000	Deferred        libxcb.so.1
ELF	7df23000-7e057000	Deferred        libx11.so.6
ELF	7e057000-7e069000	Deferred        libxext.so.6
ELF	7e089000-7e11d000	Deferred        winex11<elf>
  \-PE	7e090000-7e11d000	\               winex11
ELF	7e11d000-7e225000	Deferred        comctl32<elf>
  \-PE	7e120000-7e225000	\               comctl32
ELF	7e271000-7e29b000	Deferred        libexpat.so.1
ELF	7e29b000-7e2cf000	Deferred        libfontconfig.so.1
ELF	7e2cf000-7e369000	Deferred        libfreetype.so.6
ELF	7e389000-7e5be000	Deferred        shell32<elf>
  \-PE	7e3a0000-7e5be000	\               shell32
ELF	7e5be000-7e68d000	Deferred        crypt32<elf>
  \-PE	7e5d0000-7e68d000	\               crypt32
ELF	7e68d000-7e6c3000	Deferred        wintrust<elf>
  \-PE	7e690000-7e6c3000	\               wintrust
ELF	7e6e8000-7e81c000	Deferred        oleaut32<elf>
  \-PE	7e700000-7e81c000	\               oleaut32
ELF	7e81c000-7e8a0000	Deferred        rpcrt4<elf>
  \-PE	7e830000-7e8a0000	\               rpcrt4
ELF	7e8a0000-7e9de000	Deferred        ole32<elf>
  \-PE	7e8c0000-7e9de000	\               ole32
ELF	7e9de000-7e9f8000	Deferred        version<elf>
  \-PE	7e9e0000-7e9f8000	\               version
ELF	7e9f8000-7eb53000	Deferred        user32<elf>
  \-PE	7ea10000-7eb53000	\               user32
ELF	7eb53000-7ebfe000	Deferred        msvcrt<elf>
  \-PE	7eb70000-7ebfe000	\               msvcrt
ELF	7ebfe000-7ed15000	Deferred        gdi32<elf>
  \-PE	7ec10000-7ed15000	\               gdi32
ELF	7ed15000-7ed84000	Deferred        advapi32<elf>
  \-PE	7ed20000-7ed84000	\               advapi32
ELF	7ef84000-7ef91000	Deferred        libnss_files.so.2
ELF	7ef91000-7efab000	Deferred        libnsl.so.1
ELF	7efab000-7efd7000	Deferred        libm.so.6
ELF	7efd7000-7efe0000	Deferred        librt.so.1
ELF	7efe3000-7eff9000	Deferred        libz.so.1
ELF	f73b1000-f73bd000	Deferred        libnss_nis.so.2
ELF	f73be000-f73c3000	Deferred        libdl.so.2
ELF	f73c3000-f756d000	Dwarf           libc.so.6
ELF	f756e000-f7589000	Deferred        libpthread.so.0
ELF	f75a0000-f75a9000	Deferred        libnss_compat.so.2
ELF	f75a9000-f775f000	Dwarf           libwine.so.1
ELF	f7761000-f7783000	Deferred        ld-linux.so.2
ELF	f7783000-f7784000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\HyperBig\tempo\picasa39-setup.exe
	00000009    0 <==
0000000e services.exe
	0000001f    0
	0000001e    0
	00000019    0
	00000018    0
	00000016    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001d    0
	0000001a    0
	00000017    0
	00000013    0
0000001b plugplay.exe
	00000021    0
	00000020    0
	0000001c    0
00000022 explorer.exe
	00000023    0
System information:
    Wine build: wine-1.7.7
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-58-generic

Thanks

---

### Post by ubase133 on 2014-02-05
Try Playonlinux [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
It creates an environment with a specific wine version - actually, the most compatible - for each program/game you install.
Even if picasa is not in its database, you can create a wine bottle and put picasa in it. The other one with photoshop won't be touched

---

### Post by oldfred on 2014-02-05
My wife liked Picasa from when we ran XP, and the old Linux beta never was as good.
But I have installed the Windows version for the last couple of years without any issues (ok a couple of minor ones).

But I do not think you can have two versions of wine.

[http://askubuntu.com/questions/86452/how-would-i-install-picasa-3-9](http://askubuntu.com/questions/86452/how-would-i-install-picasa-3-9)
[http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html](http://www.webupd8.org/2012/01/install-picasa-39-in-linux-and-fix.html)

basically
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine winetricks

Configure Wine to set up directory,  Applications, Wine, Configure

Then download picasa for windows
 ([http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe))
cd && wget [http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe)
Move it into .wine/drive_c/Program Files
wine picasa39-setup.exe

---

### Post by kdesrosiers-2 on 2014-02-05
Thanks guys, I managed to install it with your help.

But, I also have some minor issues (to me but my GF says its a no go). I cannot import photos from my flash card inserted in my media bay (I can import them with gthumb), and I cannot use the direct gmail connection to send e-mail with picture (the workaround is to use thunderbird with an IMAP link to gmail).

---

