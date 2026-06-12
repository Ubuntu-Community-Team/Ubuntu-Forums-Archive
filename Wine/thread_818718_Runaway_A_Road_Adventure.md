---
title: "Runaway: A Road Adventure"
date: 2008-06-04
forum: Wine
---

### Post by phildaman46 on 2008-06-04
Has anyone gotten the game Runaway: A Road Adventure running in Ubuntu 8.04 with Wine 1.0-rc3? I get a "Resource\Resource.000" error when trying to load the game. I can get the sequel to run flawlessly. Since the second game runs, I figured the first one would run too.

---

### Post by LeonZerleg on 2008-06-05
Hi! I have Runaway running in my laptop, just did

apt-get install wine -y

Then I launched wincfg but touched nothing.

wine # For the config to be created.

wine Instalar.exe (My version is the Spanish remastered one).

It installed fine and had no problem to run it from the command line either.

Remove your .wine copying it to other location, try wine without arguments and then wine Runaway.exe

Try to avoid calling wine like "wine path/to/the/game/Runaway.exe".

---

### Post by phildaman46 on 2008-06-05
Where do you have your game installed? I have the English version of the game. Wine needs a path where the Runaway.exe is. If I just put "wine Runaway.exe" I get this message "wine: could not load L"c:\\windows\\system32\\Runaway.exe": Module not found".

---

### Post by LeonZerleg on 2008-06-05
My Path is:

/home/user/.wine/Drive_C/Archivos de programa/Runaway/Runaway.exe

In English, "Archivos de Programa" is "Program Files".

It depends in where you installed it.

---

### Post by phildaman46 on 2008-06-05
My path is:

/home/user/.wine/drive_c/Program Files/PENDULO Studios/RUNAWAY - A road adventure/Runaway.exe

Still no luck on running the game.

---

### Post by LeonZerleg on 2008-06-05
And how do you execute it? You cannot place spaces after the "wine" command. make a cd before launching wine.

How did you do the installation? I did a full install (about 2 gigs) to don't need the dvd mounted to play.

If it's possible, copy and paste the messages which wine gives when  you launch it.

---

### Post by phildaman46 on 2008-06-05
I type this in the terminal, "wine '/home/phildaman46/Wine/drive_c/Program Files/PENDULO Studios/RUNAWAY - A road adventure/Runaway.exe'". Without the quotes of course. I did a Medium install, The Maximum install doesn't work either when trying to run the game. When I try to run the game, I get this in the terminal along with a RESOURCE\RESOURCE.000 not found error:

fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:win:EnumDisplayDevicesW ((null),0,0x32efb0,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_Release (0x1483c8) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x148a40 with type 1,WINED3DRTYPE_SURFACE
wine: Unhandled page fault on read access to 0x00000034 at address 0x7bc33ddd (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000034 in 32-bit code (0x7bc33ddd).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc33ddd ESP:0032f508 EBP:0032f520 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000024 EBX:7bc88444 ECX:00000020 EDX:7e891bc4
 ESI:00000000 EDI:00000020
Stack dump:
0x0032f508:  7e891bc4 00000000 00000024 00000000
0x0032f518:  00000000 7ec35eb0 0032f52c 005917db
0x0032f528:  00000020 0032f53c 0058eb5d 00000000
0x0032f538:  7e891bc0 0032f60c 0040bcf1 00a0b8c7
0x0032f548:  00000001 00000001 00000000 005c21bc
0x0032f558:  005c2230 7ec34ee0 0040c41c 00000800
Backtrace:
=>1 0x7bc33ddd RtlEnterCriticalSection+0x1d() in ntdll (0x0032f520)
  2 0x005917db in runaway (+0x1917db) (0x0032f52c)
  3 0x0058eb5d in runaway (+0x18eb5d) (0x0032f53c)
  4 0x0040bcf1 in runaway (+0xbcf1) (0x0032f60c)
  5 0x0032fef8 (0x0032fe7c)
  6 0x00b77148 in runaway (+0x777148) (0x0032ff08)
  7 0x7b877b27 in kernel32 (+0x57b27) (0x0032ffe8)
0x7bc33ddd RtlEnterCriticalSection+0x1d in ntdll: movl	0x14(%edi),%eax
Modules:
Module	Address			Debug info	Name (86 modules)
PE	  400000-  c0a000	Export          runaway
PE	10000000-10016000	Deferred        cmdlineext02
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d222000-7d248000	Deferred        dmusic<elf>
  \-PE	7d230000-7d248000	\               dmusic
ELF	7d5f1000-7e106000	Deferred        libglcore.so.1
ELF	7e106000-7e1aa000	Deferred        libgl.so.1
ELF	7e1bb000-7e2bd000	Deferred        wined3d<elf>
  \-PE	7e1d0000-7e2bd000	\               wined3d
ELF	7e309000-7e33c000	Deferred        uxtheme<elf>
  \-PE	7e310000-7e33c000	\               uxtheme
ELF	7e33c000-7e3de000	Deferred        oleaut32<elf>
  \-PE	7e350000-7e3de000	\               oleaut32
ELF	7e3de000-7e49d000	Deferred        comctl32<elf>
  \-PE	7e3f0000-7e49d000	\               comctl32
ELF	7e49d000-7e4f6000	Deferred        shlwapi<elf>
  \-PE	7e4b0000-7e4f6000	\               shlwapi
ELF	7e4f6000-7e606000	Deferred        shell32<elf>
  \-PE	7e510000-7e606000	\               shell32
ELF	7e606000-7e61a000	Deferred        midimap<elf>
  \-PE	7e610000-7e61a000	\               midimap
ELF	7e61a000-7e640000	Deferred        msacm32<elf>
  \-PE	7e620000-7e640000	\               msacm32
ELF	7e640000-7e657000	Deferred        msacm32<elf>
  \-PE	7e650000-7e657000	\               msacm32
ELF	7e657000-7e692000	Deferred        wineoss<elf>
  \-PE	7e660000-7e692000	\               wineoss
ELF	7e692000-7e69b000	Deferred        libxcursor.so.1
ELF	7e69b000-7e6a0000	Deferred        libxfixes.so.3
ELF	7e6a0000-7e6a3000	Deferred        libxcomposite.so.1
ELF	7e6a3000-7e6a9000	Deferred        libxrandr.so.2
ELF	7e6a9000-7e6b1000	Deferred        libxrender.so.1
ELF	7e6b1000-7e6b4000	Deferred        libxinerama.so.1
ELF	7e6b4000-7e6d4000	Deferred        imm32<elf>
  \-PE	7e6c0000-7e6d4000	\               imm32
ELF	7e6d4000-7e6d9000	Deferred        libxdmcp.so.6
ELF	7e6d9000-7e6f1000	Deferred        libxcb.so.1
ELF	7e6f1000-7e6f4000	Deferred        libxau.so.6
ELF	7e6f4000-7e7db000	Deferred        libx11.so.6
ELF	7e7db000-7e7e9000	Deferred        libxext.so.6
ELF	7e7e9000-7e7ee000	Deferred        libxxf86vm.so.1
ELF	7e7fb000-7e7fd000	Deferred        libnvidia-tls.so.1
ELF	7e7ff000-7e896000	Deferred        winex11<elf>
  \-PE	7e810000-7e896000	\               winex11
ELF	7e8c1000-7e8e2000	Deferred        libexpat.so.1
ELF	7e8e2000-7e90c000	Deferred        libfontconfig.so.1
ELF	7e91d000-7e932000	Deferred        libz.so.1
ELF	7e932000-7e9a2000	Deferred        libfreetype.so.6
ELF	7e9a2000-7e9b6000	Deferred        lz32<elf>
  \-PE	7e9b0000-7e9b6000	\               lz32
ELF	7e9b6000-7e9cf000	Deferred        version<elf>
  \-PE	7e9c0000-7e9cf000	\               version
ELF	7e9cf000-7ea61000	Deferred        winmm<elf>
  \-PE	7e9e0000-7ea61000	\               winmm
ELF	7ea61000-7eaab000	Deferred        dsound<elf>
  \-PE	7ea70000-7eaab000	\               dsound
ELF	7eaab000-7eabe000	Deferred        libresolv.so.2
ELF	7eacf000-7eaed000	Deferred        iphlpapi<elf>
  \-PE	7eae0000-7eaed000	\               iphlpapi
ELF	7eaed000-7eb4e000	Deferred        rpcrt4<elf>
  \-PE	7eb00000-7eb4e000	\               rpcrt4
ELF	7eb4e000-7ebe9000	Deferred        gdi32<elf>
  \-PE	7eb60000-7ebe9000	\               gdi32
ELF	7ebe9000-7ed30000	Deferred        user32<elf>
  \-PE	7ec00000-7ed30000	\               user32
ELF	7ed30000-7ed82000	Deferred        advapi32<elf>
  \-PE	7ed40000-7ed82000	\               advapi32
ELF	7ed82000-7ee26000	Deferred        ole32<elf>
  \-PE	7ed90000-7ee26000	\               ole32
ELF	7ee26000-7ee7d000	Deferred        ddraw<elf>
  \-PE	7ee30000-7ee7d000	\               ddraw
ELF	7ef9d000-7efa8000	Deferred        libnss_files.so.2
ELF	7efa8000-7efb2000	Deferred        libnss_nis.so.2
ELF	7efb2000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7efef000-7eff1000	Deferred        libxcb-xlib.so.0
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7ca2000-f7ca6000	Deferred        libdl.so.2
ELF	f7ca6000-f7df5000	Deferred        libc.so.6
ELF	f7df6000-f7e0e000	Deferred        libpthread.so.0
ELF	f7e1f000-f7f55000	Deferred        libwine.so.1
ELF	f7f57000-f7f76000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\PENDULO Studios\RUNAWAY - A road adventure\Runaway.exe
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
=>1 0x7bc33ddd RtlEnterCriticalSection+0x1d() in ntdll (0x0032f520)
  2 0x005917db in runaway (+0x1917db) (0x0032f52c)
  3 0x0058eb5d in runaway (+0x18eb5d) (0x0032f53c)
  4 0x0040bcf1 in runaway (+0xbcf1) (0x0032f60c)
  5 0x0032fef8 (0x0032fe7c)
  6 0x00b77148 in runaway (+0x777148) (0x0032ff08)
  7 0x7b877b27 in kernel32 (+0x57b27) (0x0032ffe8)

---

### Post by phildaman46 on 2008-06-05
Those "Cool" signs aren't suppose to be there, ignore them.

---

### Post by LeonZerleg on 2008-06-05
:S Bad luck guy, when i have one of this traces i usually try to search for a crack or something because, as far as I know, it's a problem with a library or with the exe. You'll have to try searching form methods to install _your version_ of Runaway, is obvius that the remastered spanish one differs from that one.

Sorry.

---

### Post by phildaman46 on 2008-06-05
The no-cd cracks don't help. I get the same error. Oh well, I'll just run the game in Windows until a new version of Wine comes out.

---

### Post by cogadh on 2008-06-05
You need to change directories to the game's install directory before running it and probably turn off any Desktop Effects you have enabled. At least one of those errors indicates that the game executable cannot find some needed files, which usually indicates that it needs to be run from within its install directory. Another one of those errors would seem to indicate that some of your video card's resources are being occupied by something else at the time of game launch, which is usually an indication that Desktop Effects are enabled (Wine and Desktop Effects do not like to cooperate). Try making those two changes and see of the game will run then.

---

