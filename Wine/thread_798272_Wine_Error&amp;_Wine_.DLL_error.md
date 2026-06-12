---
title: "Wine Error&amp; Wine .DLL error"
date: 2008-05-18
forum: Wine
---

### Post by ggsherma on 2008-05-18
Hello all,

I've been having some problems installing Ragnarok Online for quite a while and I checked -everywhere- on the internet and could not find a solution to my problem (there are a lot of people having this same problem).

First of all, if I try to run winecfg from the terminal, it will open, but before it opens I get this error:

```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
```

So now, if I try to run the setup for Ragnarok, it will come up, but before it does I get this error:

```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f018,0x00000000), stub!

```

Now, if I try to run the .exe that should update the game (the patch file), I get this error, and it does not come up - It just closes the wine window:

```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x402052 (thread 0009), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x7bc4530c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc4530c ESP:7f21e6a4 EBP:7f21e708 EFLAGS:00000202(   - 00      - - I1)
 EAX:0000194e EBX:7bc89704 ECX:7f020700 EDX:7f00004c
 ESI:7f21e6b0 EDI:00000001
Stack dump:
0x7f21e6a4:  00010028 00000000 00000000 80000100
0x7f21e6b4:  00000001 00000000 00402052 00000002
0x7f21e6c4:  0041ca2e 0000194e 00000002 7ed8d5a0
0x7f21e6d4:  84000040 00000000 7f000014 7e9ab044
0x7f21e6e4:  ffffffff 00000001 7f21e70c 7e98d7a7
0x7f21e6f4:  7f000000 00000000 000004c8 7ec6c080
Backtrace:
=>1 0x7bc4530c in ntdll (+0x3530c) (0x7f21e708)
0x7bc4530c: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (68 modules)
PE	  400000-  424000	Deferred        sakray
PE	5f400000-5f4ed000	Deferred        mfc42
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Export          ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e47c000-7e49b000	Deferred        imm32<elf>
  \-PE	7e480000-7e49b000	\               imm32
ELF	7e4bf000-7e4d2000	Deferred        libresolv.so.2
ELF	7e4e1000-7e4ff000	Deferred        iphlpapi<elf>
  \-PE	7e4f0000-7e4ff000	\               iphlpapi
ELF	7e4ff000-7e55f000	Deferred        rpcrt4<elf>
  \-PE	7e510000-7e55f000	\               rpcrt4
ELF	7e55f000-7e603000	Deferred        ole32<elf>
  \-PE	7e570000-7e603000	\               ole32
ELF	7e628000-7e65a000	Deferred        uxtheme<elf>
  \-PE	7e630000-7e65a000	\               uxtheme
ELF	7e65a000-7e663000	Deferred        libxcursor.so.1
ELF	7e663000-7e668000	Deferred        libxfixes.so.3
ELF	7e668000-7e66b000	Deferred        libxcomposite.so.1
ELF	7e66b000-7e671000	Deferred        libxrandr.so.2
ELF	7e671000-7e679000	Deferred        libxrender.so.1
ELF	7e679000-7e67c000	Deferred        libxinerama.so.1
ELF	7e67c000-7e681000	Deferred        libxdmcp.so.6
ELF	7e681000-7e699000	Deferred        libxcb.so.1
ELF	7e699000-7e69c000	Deferred        libxau.so.6
ELF	7e69c000-7e783000	Deferred        libx11.so.6
ELF	7e783000-7e791000	Deferred        libxext.so.6
ELF	7e791000-7e796000	Deferred        libxxf86vm.so.1
ELF	7e796000-7e7ae000	Deferred        libice.so.6
ELF	7e7ae000-7e7b6000	Deferred        libsm.so.6
ELF	7e7c5000-7e856000	Deferred        winex11<elf>
  \-PE	7e7d0000-7e856000	\               winex11
ELF	7e86f000-7e890000	Deferred        libexpat.so.1
ELF	7e890000-7e8ba000	Deferred        libfontconfig.so.1
ELF	7e8c9000-7e8de000	Deferred        libz.so.1
ELF	7e8de000-7e94e000	Deferred        libfreetype.so.6
ELF	7e94e000-7e950000	Deferred        libxcb-xlib.so.0
ELF	7e95d000-7e9c6000	Deferred        msvcrt<elf>
  \-PE	7e970000-7e9c6000	\               msvcrt
ELF	7e9c6000-7ea85000	Deferred        comctl32<elf>
  \-PE	7e9d0000-7ea85000	\               comctl32
ELF	7ea85000-7eb8f000	Deferred        shell32<elf>
  \-PE	7eaa0000-7eb8f000	\               shell32
ELF	7eb8f000-7ebe8000	Deferred        shlwapi<elf>
  \-PE	7eba0000-7ebe8000	\               shlwapi
ELF	7ebe8000-7ec39000	Deferred        advapi32<elf>
  \-PE	7ebf0000-7ec39000	\               advapi32
ELF	7ec39000-7ecd4000	Deferred        gdi32<elf>
  \-PE	7ec50000-7ecd4000	\               gdi32
ELF	7ecd4000-7ee1a000	Deferred        user32<elf>
  \-PE	7ecf0000-7ee1a000	\               user32
ELF	7ee1a000-7ee3b000	Deferred        mpr<elf>
  \-PE	7ee20000-7ee3b000	\               mpr
ELF	7ee3b000-7ee89000	Deferred        wininet<elf>
  \-PE	7ee40000-7ee89000	\               wininet
ELF	7efa9000-7efb4000	Deferred        libnss_files.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cc1000-b7cca000	Deferred        libnss_compat.so.2
ELF	b7ccb000-b7ccf000	Deferred        libdl.so.2
ELF	b7ccf000-b7e1e000	Deferred        libc.so.6
ELF	b7e1f000-b7e37000	Deferred        libpthread.so.0
ELF	b7e46000-b7f5b000	Deferred        libwine.so.1
ELF	b7f5d000-b7f79000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Gravity\RO\sakray.exe
	00000009    0 <==
0000000c 
	00000017    0
	00000016    0
	00000011    0
	00000010    0
	0000000e    0
	0000000d    0
00000012 
	00000015    0
	00000014    0
	00000013    0
00000018 
	0000001a    0
	00000019    0
Backtrace:
=>1 0x7bc4530c in ntdll (+0x3530c) (0x7f21e708)
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting

```

Now what I have done already:

I have downloaded MFC42.DLL from a website and put it in my system32, system and RO folder (actually I downloaded 2 mfc42 and put them both in all three of those folders.

I have also edited the default mmap_min_addr to 0 like some websites said to do.

I also read a few things about Ragnarok needing to run in full window mode etc.. so I followed those instructions and had no such luck.

I am running the most current wine available and my Ubuntu is version 8.04 - the Hardy Heron.

Any help is appreciated.

Thankyou,

Geoff

---

### Post by isparkes on 2008-05-18
Hi Geoff,

I've got this error as well, so just to let you know you are not alone. I don't have any solutions yet, but then again I've only just moved over to Hardy...

---

### Post by evilviper77 on 2008-05-18
Well crap, I remember getting that "failed to reserve range error" from wine and I can't remember what caused it or what I did to fix it. I think it happened to me when I set the wine setting of "Allow DirectX apps to stop the mouse leaving their window". See if you have that check and if you do turn it off and try again.

Then again I also had a sound error that messed up wine, but it ended up being my own fault messing with the sound groups and whatnot and I just had to reinstall linux to get it to work, I'm guessing this isn't your problem.

The last thing I could think of might have to be about DirectX in wine, I know the post here says not to install windows DirectX but I found this guide at [http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html](http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html) that has a guide that works perfectly. If the DirectX check thing doesn't work you can try going through that guide and seeing if that helps. Not going to guarantee anything but I figured I'd pass it along just in case.

---

### Post by ggsherma on 2008-05-18
> **evilviper77 said:**
> Well crap, I remember getting that "failed to reserve range error" from wine and I can't remember what caused it or what I did to fix it. I think it happened to me when I set the wine setting of "Allow DirectX apps to stop the mouse leaving their window". See if you have that check and if you do turn it off and try again.
I tried that and still didn't work.

> 
Then again I also had a sound error that messed up wine, but it ended up being my own fault messing with the sound groups and whatnot and I just had to reinstall linux to get it to work, I'm guessing this isn't your problem.
I turned off sounds and still didn't work.

> The last thing I could think of might have to be about DirectX in wine, I know the post here says not to install windows DirectX but I found this guide at [http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html](http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html) that has a guide that works perfectly. If the DirectX check thing doesn't work you can try going through that guide and seeing if that helps. Not going to guarantee anything but I figured I'd pass it along just in case.

I will try this and let you know!

> **isparkes said:**
> Hi Geoff,

I've got this error as well, so just to let you know you are not alone. I don't have any solutions yet, but then again I've only just moved over to Hardy...


Thanks for the replies. Hope we can get this working. :)

---

### Post by ggsherma on 2008-05-18
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x402052 (thread 0009), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x7bc4530c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc4530c ESP:7f21e6a4 EBP:7f21e708 EFLAGS:00200202(   - 00      - - I1)
 EAX:0000194e EBX:7bc89704 ECX:7f020700 EDX:7f00004c
 ESI:7f21e6b0 EDI:00000001
Stack dump:
0x7f21e6a4:  00010028 00000000 00000000 80000100
0x7f21e6b4:  00000001 00000000 00402052 00000002
0x7f21e6c4:  0041ca2e 0000194e 00000002 7ed835a0
0x7f21e6d4:  84000040 00000000 7f000014 7e9a1044
0x7f21e6e4:  ffffffff 00000001 7f21e70c 7e9837a7
0x7f21e6f4:  7f000000 00000000 000004c8 7ec62080
Backtrace:
=>1 0x7bc4530c in ntdll (+0x3530c) (0x7f21e708)
0x7bc4530c: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (68 modules)
PE	  400000-  424000	Deferred        sakray
PE	5f400000-5f4ed000	Deferred        mfc42
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Export          ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e479000-7e498000	Deferred        imm32<elf>
  \-PE	7e480000-7e498000	\               imm32
ELF	7e4bc000-7e4cf000	Deferred        libresolv.so.2
ELF	7e4de000-7e4fc000	Deferred        iphlpapi<elf>
  \-PE	7e4e0000-7e4fc000	\               iphlpapi
ELF	7e4fc000-7e55c000	Deferred        rpcrt4<elf>
  \-PE	7e510000-7e55c000	\               rpcrt4
ELF	7e55c000-7e600000	Deferred        ole32<elf>
  \-PE	7e570000-7e600000	\               ole32
ELF	7e625000-7e657000	Deferred        uxtheme<elf>
  \-PE	7e630000-7e657000	\               uxtheme
ELF	7e657000-7e660000	Deferred        libxcursor.so.1
ELF	7e660000-7e665000	Deferred        libxfixes.so.3
ELF	7e665000-7e668000	Deferred        libxcomposite.so.1
ELF	7e668000-7e66e000	Deferred        libxrandr.so.2
ELF	7e66e000-7e676000	Deferred        libxrender.so.1
ELF	7e676000-7e679000	Deferred        libxinerama.so.1
ELF	7e679000-7e67e000	Deferred        libxdmcp.so.6
ELF	7e67e000-7e696000	Deferred        libxcb.so.1
ELF	7e696000-7e698000	Deferred        libxcb-xlib.so.0
ELF	7e698000-7e69b000	Deferred        libxau.so.6
ELF	7e69b000-7e782000	Deferred        libx11.so.6
ELF	7e782000-7e790000	Deferred        libxext.so.6
ELF	7e790000-7e7a8000	Deferred        libice.so.6
ELF	7e7a8000-7e7b0000	Deferred        libsm.so.6
ELF	7e7bf000-7e850000	Deferred        winex11<elf>
  \-PE	7e7d0000-7e850000	\               winex11
ELF	7e874000-7e895000	Deferred        libexpat.so.1
ELF	7e895000-7e8bf000	Deferred        libfontconfig.so.1
ELF	7e8bf000-7e8d4000	Deferred        libz.so.1
ELF	7e8d4000-7e944000	Deferred        libfreetype.so.6
ELF	7e944000-7e949000	Deferred        libxxf86vm.so.1
ELF	7e953000-7e9bc000	Deferred        msvcrt<elf>
  \-PE	7e960000-7e9bc000	\               msvcrt
ELF	7e9bc000-7ea7b000	Deferred        comctl32<elf>
  \-PE	7e9c0000-7ea7b000	\               comctl32
ELF	7ea7b000-7eb85000	Deferred        shell32<elf>
  \-PE	7ea90000-7eb85000	\               shell32
ELF	7eb85000-7ebde000	Deferred        shlwapi<elf>
  \-PE	7eb90000-7ebde000	\               shlwapi
ELF	7ebde000-7ec2f000	Deferred        advapi32<elf>
  \-PE	7ebf0000-7ec2f000	\               advapi32
ELF	7ec2f000-7ecca000	Deferred        gdi32<elf>
  \-PE	7ec40000-7ecca000	\               gdi32
ELF	7ecca000-7ee10000	Deferred        user32<elf>
  \-PE	7ece0000-7ee10000	\               user32
ELF	7ee10000-7ee31000	Deferred        mpr<elf>
  \-PE	7ee20000-7ee31000	\               mpr
ELF	7ee31000-7ee7f000	Deferred        wininet<elf>
  \-PE	7ee40000-7ee7f000	\               wininet
ELF	7ef9f000-7efaa000	Deferred        libnss_files.so.2
ELF	7efaa000-7efb4000	Deferred        libnss_nis.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c97000-b7c9b000	Deferred        libdl.so.2
ELF	b7c9b000-b7dea000	Deferred        libc.so.6
ELF	b7deb000-b7e03000	Deferred        libpthread.so.0
ELF	b7e12000-b7f27000	Deferred        libwine.so.1
ELF	b7f29000-b7f45000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Gravity\RO\sakray.exe
	00000009    0 <==
0000000c 
	00000017    0
	00000016    0
	00000013    0
	00000010    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000014    0
	00000012    0
00000018 
	0000001a    0
	00000019    0
Backtrace:
=>1 0x7bc4530c in ntdll (+0x3530c) (0x7f21e708)
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting

```

I followed all those steps and I could not run the dxdiag as it said it wasn't there. I tried to rerun the entire setup and still, the dxdiag wasn't there.

After doing all of the steps (except the dxdiag part) I ran my patch to see if it works and I still get the error above (wine opens then closes literally 2-3 seconds after it opens).

---

### Post by ggsherma on 2008-05-18
Ok as I was typing the above message, apparently wine came out with an update. So I updated and ran my patch program again and I got this:

```
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dd79a08, overlapped 0x7dd799ec): stub
wine: configuration in '/home/geoff/.wine' has been updated.
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x402052 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x7bc451ec).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc451ec ESP:0032e6a4 EBP:0032e708 EFLAGS:00000206(   - 00      - -IP1)
 EAX:0000194e EBX:7bc88444 ECX:001306e0 EDX:0011004c
 ESI:0032e6b0 EDI:00000001
Stack dump:
0x0032e6a4:  00060028 00000000 00000000 80000100
0x0032e6b4:  00000001 00000000 00402052 00000002
0x0032e6c4:  0041ca2e 0000194e 00000002 00000001
0x0032e6d4:  7edd6080 7edb68e8 00110014 7e9995a0
0x0032e6e4:  ffffffff 00000001 0032e70c 7e97c8d7
0x0032e6f4:  00110000 00000000 000004c8 7ec610a0
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0032e708)
0x7bc451ec: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (68 modules)
PE	  400000-  424000	Deferred        sakray
PE	5f400000-5f4ed000	Deferred        mfc42
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e489000-7e49c000	Deferred        libresolv.so.2
ELF	7e4ab000-7e4c9000	Deferred        iphlpapi<elf>
  \-PE	7e4b0000-7e4c9000	\               iphlpapi
ELF	7e4c9000-7e52a000	Deferred        rpcrt4<elf>
  \-PE	7e4e0000-7e52a000	\               rpcrt4
ELF	7e52a000-7e5ce000	Deferred        ole32<elf>
  \-PE	7e540000-7e5ce000	\               ole32
ELF	7e5f3000-7e626000	Deferred        uxtheme<elf>
  \-PE	7e600000-7e626000	\               uxtheme
ELF	7e626000-7e62f000	Deferred        libxcursor.so.1
ELF	7e62f000-7e634000	Deferred        libxfixes.so.3
ELF	7e634000-7e637000	Deferred        libxcomposite.so.1
ELF	7e637000-7e63d000	Deferred        libxrandr.so.2
ELF	7e63d000-7e645000	Deferred        libxrender.so.1
ELF	7e645000-7e648000	Deferred        libxinerama.so.1
ELF	7e648000-7e668000	Deferred        imm32<elf>
  \-PE	7e650000-7e668000	\               imm32
ELF	7e668000-7e66d000	Deferred        libxdmcp.so.6
ELF	7e66d000-7e685000	Deferred        libxcb.so.1
ELF	7e685000-7e688000	Deferred        libxau.so.6
ELF	7e688000-7e76f000	Deferred        libx11.so.6
ELF	7e76f000-7e77d000	Deferred        libxext.so.6
ELF	7e77d000-7e795000	Deferred        libice.so.6
ELF	7e795000-7e79d000	Deferred        libsm.so.6
ELF	7e7ac000-7e842000	Deferred        winex11<elf>
  \-PE	7e7c0000-7e842000	\               winex11
ELF	7e85e000-7e87f000	Deferred        libexpat.so.1
ELF	7e87f000-7e8a9000	Deferred        libfontconfig.so.1
ELF	7e8a9000-7e8ab000	Deferred        libxcb-xlib.so.0
ELF	7e8ab000-7e8b0000	Deferred        libxxf86vm.so.1
ELF	7e8b8000-7e8cd000	Deferred        libz.so.1
ELF	7e8cd000-7e93d000	Deferred        libfreetype.so.6
ELF	7e94c000-7e9b5000	Deferred        msvcrt<elf>
  \-PE	7e960000-7e9b5000	\               msvcrt
ELF	7e9b5000-7ea74000	Deferred        comctl32<elf>
  \-PE	7e9c0000-7ea74000	\               comctl32
ELF	7ea74000-7eb83000	Deferred        shell32<elf>
  \-PE	7ea80000-7eb83000	\               shell32
ELF	7eb83000-7ebdc000	Deferred        shlwapi<elf>
  \-PE	7eb90000-7ebdc000	\               shlwapi
ELF	7ebdc000-7ec2e000	Deferred        advapi32<elf>
  \-PE	7ebf0000-7ec2e000	\               advapi32
ELF	7ec2e000-7ecc9000	Deferred        gdi32<elf>
  \-PE	7ec40000-7ecc9000	\               gdi32
ELF	7ecc9000-7ee10000	Deferred        user32<elf>
  \-PE	7ece0000-7ee10000	\               user32
ELF	7ee10000-7ee31000	Deferred        mpr<elf>
  \-PE	7ee20000-7ee31000	\               mpr
ELF	7ee31000-7ee7f000	Deferred        wininet<elf>
  \-PE	7ee40000-7ee7f000	\               wininet
ELF	7ef9f000-7efaa000	Deferred        libnss_files.so.2
ELF	7efaa000-7efb4000	Deferred        libnss_nis.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c92000-b7c96000	Deferred        libdl.so.2
ELF	b7c96000-b7de5000	Deferred        libc.so.6
ELF	b7de6000-b7dfe000	Deferred        libpthread.so.0
ELF	b7e0d000-b7f43000	Deferred        libwine.so.1
ELF	b7f45000-b7f61000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Gravity\RO\sakray.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
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
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0032e708)
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting

```

It still does not stay open longer than a few seconds. MFC42.DLL seems to be the problem but I made sure I copied it into the System32, system and RO folder (RO is the folder of the game).

---

### Post by evilviper77 on 2008-05-18
> **ggsherma said:**
> Ok as I was typing the above message, apparently wine came out with an update. So I updated and ran my patch program again and I got this:

It still does not stay open longer than a few seconds. MFC42.DLL seems to be the problem but I made sure I copied it into the System32, system and RO folder (RO is the folder of the game).

If it took you a lot of time to install wine you might want to rename the .wine folder to .wineold or something and reinstall wine then running the directX update to get it to work. If it still doesn't work you can just delete the wine folder and rename the old one to wine and be back at square one.

Plus you really need to read everything he writes on that page, I skipped over the part I had to copy mscoree.dll and streamci.dll from a windows PC system folder into the wine system folder and it screwed up my install of it. If you still can't get it to work tell me where it's screwing up and i'll see if I can help get it to work.

One other question is how did you install wine? Did you just use the apt-get manager to install it? I say this cause I also remember installing wine from a tar and silly me did the configure, the make, and the make install under root so it threw some awful errors (can't remember which ones specifically) and I had to reinstall it.

---

### Post by ggsherma on 2008-05-18
> **evilviper77 said:**
> If it took you a lot of time to install wine you might want to rename the .wine folder to .wineold or something and reinstall wine then running the directX update to get it to work. If it still doesn't work you can just delete the wine folder and rename the old one to wine and be back at square one.


I actually formatted the the PC and reinstalled everything again and it did not work. So there's something I am doing wrong :-)

> Plus you really need to read everything he writes on that page, I skipped over the part I had to copy mscoree.dll and streamci.dll from a windows PC system folder into the wine system folder and it screwed up my install of it. If you still can't get it to work tell me where it's screwing up and i'll see if I can help get it to work.
I am only using linux. I do not dual boot so I only have a .wine system32 folder.

> One other question is how did you install wine? Did you just use the apt-get manager to install it? I say this cause I also remember installing wine from a tar and silly me did the configure, the make, and the make install under root so it threw some awful errors (can't remember which ones specifically) and I had to reinstall it.

I got it from the website. 

The .wine is located [email]geoff@geoff-laptop:~/.wine[/email]$ 

I am pretty new to linux. So, sorry for my incoherence :)

Edit: If you could give me the steps to uninstall .wine, then re-install the correct way I am more than willing to do that. Because I cannot get my office 2k7 or Photoshop to install either. :) (Im sure there are things you have to do special for those two, which I can google later).

Thanks!

---

### Post by evilviper77 on 2008-05-18
> **ggsherma said:**
> I actually formatted the the PC and reinstalled everything again and it did not work. So there's something I am doing wrong :-)


I am only using linux. I do not dual boot so I only have a .wine system32 folder.



I got it from the website. 

The .wine is located [email]geoff@geoff-laptop:~/.wine[/email]$ 

I am pretty new to linux. So, sorry for my incoherence :)

Edit: If you could give me the steps to uninstall .wine, then re-install the correct way I am more than willing to do that. Because I cannot get my office 2k7 or Photoshop to install either. :) (Im sure there are things you have to do special for those two, which I can google later).

Thanks!

Well to get those two dlls just search the web for them. Should get a hit on the first 3 webpages for downloads for them then you can just copy them over to the system32 folder.

edit: There should be a guide around here for getting office 2k7 to work in wine; but supposedly it's a real pain. I'll see if I can post a link to it.
edit: Here it is: [http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/](http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/)

---

### Post by ggsherma on 2008-05-18
> **evilviper77 said:**
> Well to get those two dlls just search the web for them. Should get a hit on the first 3 webpages for downloads for them then you can just copy them over to the system32 folder.

edit: There should be a guide around here for getting office 2k7 to work in wine; but supposedly it's a real pain. I'll see if I can post a link to it.
edit: Here it is: [http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/](http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/)

Yeah, I've seen the tutorial.I get stuck at this part:

> Install msxml3.msi file from the Terminal window by issuing msiexec /i msxml3.msi

It won't let me run it in the terminal window. It's located on my desktop at this point.

Any idea how I can fix the error I'm getting with the first problem I have?

Thanks for your patience.

Geoff

---

### Post by evilviper77 on 2008-05-19
> **ggsherma said:**
> Yeah, I've seen the tutorial.I get stuck at this part:



It won't let me run it in the terminal window. It's located on my desktop at this point.

Any idea how I can fix the error I'm getting with the first problem I have?

Thanks for your patience.

Geoff
Here are the links to the dll files for directX

[http://www.dll-files.com/dllindex/dll-files.shtml?mscoree](http://www.dll-files.com/dllindex/dll-files.shtml?mscoree)
[http://www.dlldump.com/download-dll-files_new.php/dllfiles/S/streamci.dll/5.1.2600.0/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/S/streamci.dll/5.1.2600.0/download.html)

---

### Post by ggsherma on 2008-05-19
Yeah I have those. I put them into the folder he said -- However, the part I quoted before is the part I'm having a problem with. I guess I'm typing in something wrong when I do it (I quoted the part I was having problems with, it's after the part with the dlls).

---

### Post by ScorpKing on 2008-05-19
To fix your first error take a look at this [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by rickyrockrat on 2008-05-19
Thanks! that fixed it for me.

---

### Post by ggsherma on 2008-05-20
Thank you. That fixed the first error, but I still get this when trying to run Ragnorak's Patch:

```
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x402052 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x7bc451ec).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc451ec ESP:0032e6a4 EBP:0032e708 EFLAGS:00200206(   - 00      - -IP1)
 EAX:0000194e EBX:7bc88444 ECX:00130908 EDX:0011004c
 ESI:0032e6b0 EDI:00000001
Stack dump:
0x0032e6a4:  00010028 00000000 00000000 80000100
0x0032e6b4:  00000001 00000000 00402052 00000002
0x0032e6c4:  0041ca2e 0000194e 00000002 00000001
0x0032e6d4:  7ede0080 7edc08e8 00110014 7e9a35a0
0x0032e6e4:  ffffffff 00000001 0032e70c 7e9868d7
0x0032e6f4:  00110000 00000000 000004c8 7ec6b0a0
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0032e708)
  2 0x00402052 in sakray (+0x2052) (0x00000390)
  3 0x00000000 (0x00000000)
0x7bc451ec: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (67 modules)
PE	  400000-  424000	Export          sakray
PE	5f400000-5f4ed000	Deferred        mfc42
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e48a000-7e49d000	Deferred        libresolv.so.2
ELF	7e4ac000-7e4ca000	Deferred        iphlpapi<elf>
  \-PE	7e4b0000-7e4ca000	\               iphlpapi
PE	7e4ca000-7e532000	Deferred        rpcrt4
ELF	7e532000-7e5d6000	Deferred        ole32<elf>
  \-PE	7e540000-7e5d6000	\               ole32
ELF	7e5fb000-7e62e000	Deferred        uxtheme<elf>
  \-PE	7e600000-7e62e000	\               uxtheme
ELF	7e62e000-7e637000	Deferred        libxcursor.so.1
ELF	7e637000-7e63c000	Deferred        libxfixes.so.3
ELF	7e63c000-7e63f000	Deferred        libxcomposite.so.1
ELF	7e63f000-7e645000	Deferred        libxrandr.so.2
ELF	7e645000-7e64d000	Deferred        libxrender.so.1
ELF	7e64d000-7e650000	Deferred        libxinerama.so.1
ELF	7e650000-7e670000	Deferred        imm32<elf>
  \-PE	7e660000-7e670000	\               imm32
ELF	7e670000-7e675000	Deferred        libxdmcp.so.6
ELF	7e675000-7e68d000	Deferred        libxcb.so.1
ELF	7e68d000-7e774000	Deferred        libx11.so.6
ELF	7e774000-7e782000	Deferred        libxext.so.6
ELF	7e782000-7e787000	Deferred        libxxf86vm.so.1
ELF	7e787000-7e79f000	Deferred        libice.so.6
ELF	7e79f000-7e7a7000	Deferred        libsm.so.6
ELF	7e7b6000-7e84c000	Deferred        winex11<elf>
  \-PE	7e7c0000-7e84c000	\               winex11
ELF	7e868000-7e889000	Deferred        libexpat.so.1
ELF	7e889000-7e8b3000	Deferred        libfontconfig.so.1
ELF	7e8b3000-7e8b6000	Deferred        libxau.so.6
ELF	7e8c2000-7e8d7000	Deferred        libz.so.1
ELF	7e8d7000-7e947000	Deferred        libfreetype.so.6
ELF	7e947000-7e949000	Deferred        libxcb-xlib.so.0
ELF	7e956000-7e9bf000	Deferred        msvcrt<elf>
  \-PE	7e970000-7e9bf000	\               msvcrt
ELF	7e9bf000-7ea7e000	Deferred        comctl32<elf>
  \-PE	7e9d0000-7ea7e000	\               comctl32
ELF	7ea7e000-7eb8d000	Deferred        shell32<elf>
  \-PE	7ea90000-7eb8d000	\               shell32
ELF	7eb8d000-7ebe6000	Deferred        shlwapi<elf>
  \-PE	7eba0000-7ebe6000	\               shlwapi
ELF	7ebe6000-7ec38000	Deferred        advapi32<elf>
  \-PE	7ebf0000-7ec38000	\               advapi32
ELF	7ec38000-7ecd3000	Deferred        gdi32<elf>
  \-PE	7ec50000-7ecd3000	\               gdi32
ELF	7ecd3000-7ee1a000	Deferred        user32<elf>
  \-PE	7ecf0000-7ee1a000	\               user32
ELF	7ee1a000-7ee3b000	Deferred        mpr<elf>
  \-PE	7ee20000-7ee3b000	\               mpr
ELF	7ee3b000-7ee89000	Deferred        wininet<elf>
  \-PE	7ee40000-7ee89000	\               wininet
ELF	7efa9000-7efb4000	Deferred        libnss_files.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c80000-b7c89000	Deferred        libnss_compat.so.2
ELF	b7c8a000-b7c8e000	Deferred        libdl.so.2
ELF	b7c8e000-b7ddd000	Deferred        libc.so.6
ELF	b7dde000-b7df6000	Deferred        libpthread.so.0
ELF	b7e05000-b7f3b000	Deferred        libwine.so.1
ELF	b7f3d000-b7f59000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Gravity\RO\sakray.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0032e708)
  2 0x00402052 in sakray (+0x2052) (0x00000390)
  3 0x00000000 (0x00000000)
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting
geoff@geoff-laptop:~/.wine/drive_c/Program Files/Gravity/RO$ wine: Call from 0x7b8446d0 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting

```

Could you tell me what I have to do to fix the MFC42.DLL error? It seems that's the only thing keeping me from running this program.

What I've tried to do was download MFC42.DLL and put it into my RO folder, System32 folder and in the .wine folder. I also put it on the override menu in wine (through the library).

Thank you again for your help,

Geoff

---

### Post by ggsherma on 2008-05-20
Ok I solved the office 2k7 problem by installing winetricks. Worked like a charm. If anyone is having problems getting that to work I can explain the steps if they'd like.

I am, however, still having a problem with the patch I want to run. The above post has the error I am getting.

Thanks

---

### Post by ggsherma on 2008-05-20
Ok. I didn't get Office 2k7 installed. It failed 3/4ths of the way through and now I cannot uninstall it or re-install it. Everytime I try to re-run the setup.exe, it'll ask for my product key, I'll put it in, it'll began to install then say "..have encountered a problem and cannot install"

I tried to uninstall it by going to "Applications, Wine then uninstall Wine software (as it's under there)" and that didn't work. It won't disappear when I click uninstall.

I did get a little further with the Ragnorak file. I took the dll file from my XP computer and it seems to read that one better than the downloaded one I had. But it's still not working. I'll post what it does in the morning (the error).

---

### Post by evilviper77 on 2008-05-20
> **ggsherma said:**
> Ok. I didn't get Office 2k7 installed. It failed 3/4ths of the way through and now I cannot uninstall it or re-install it. Everytime I try to re-run the setup.exe, it'll ask for my product key, I'll put it in, it'll began to install then say "..have encountered a problem and cannot install"

I tried to uninstall it by going to "Applications, Wine then uninstall Wine software (as it's under there)" and that didn't work. It won't disappear when I click uninstall.

I did get a little further with the Ragnorak file. I took the dll file from my XP computer and it seems to read that one better than the downloaded one I had. But it's still not working. I'll post what it does in the morning (the error).

For the dll problem you are having, you could try going into the overrides section in 'winecfg' (like you did for the directX install) and override MFC42.dll to builtin, then to native if that doesn't work. Can also try using different "operating systems" in wine when you run it along with those different overrides to see if that changes anything.

---

### Post by ggsherma on 2008-05-21
I fixed the DLL problem. The game will still not patch. No errors, but it'll just hang and keep the window open with the beginning of the patch screen open. No clue what to do.

---

