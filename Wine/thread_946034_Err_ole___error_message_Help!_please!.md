---
title: "Err: ole   error message Help! please!"
date: 2008-10-12
forum: Wine
---

### Post by thefishki345 on 2008-10-12
wine.1.1.5

Hi,

I recently created a thread 5 days ago:

[http://ubuntuforums.org/showthread.php?p=5921957#post5921957](http://ubuntuforums.org/showthread.php?p=5921957#post5921957)

but got no replies. So basically if you read through that it  says when I try and run Assassins creed, which worked fine before, I get an err:ole error.

Terminal output:

```

 err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
wine: Unhandled page fault on read access to 0x00000020 at address 0x79ea30 (thread 0019), starting debugger...
Unhandled exception: page fault on read access to 0x00000020 in 32-bit code (0x0079ea30).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0079ea30 ESP:7ddac648 EBP:00000000 EFLAGS:00010216(   - 00      -RIAP1)
 EAX:0282fe30 EBX:00000000 ECX:00000000 EDX:00000001
 ESI:00362d28 EDI:00004a17
Stack dump:
0x7ddac648:  009a58b4 00004a17 00362d28 00000000
0x7ddac658:  00004a17 00362dc8 0282fe30 00362dcc
0x7ddac668:  7bc33e7f 00362d28 00362dc4 00000000
0x7ddac678:  007a2f09 00362dc8 009a4e39 7ddac6f0
0x7ddac688:  01564168 ffffffff 009a5e64 0282c230
0x7ddac698:  00000000 00000000 00004a17 00000008
Backtrace:
0x0079ea30: movl	0x20(%ecx),%eax
Modules:
Module	Address			Debug info	Name (100 modules)
PE	  340000-  354000	Deferred        xinput1_3
PE	  400000- 1bbf000	Export          assassinscreed_dx9
PE	10000000-10031000	Deferred        eax
PE	18000000-18038000	Deferred        binkw32
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7df14000-7df47000	Deferred        uxtheme<elf>
  \-PE	7df20000-7df47000	\               uxtheme
ELF	7df47000-7df6e000	Deferred        msacm32<elf>
  \-PE	7df50000-7df6e000	\               msacm32
ELF	7df6e000-7e031000	Deferred        libasound.so.2
ELF	7e038000-7e04c000	Deferred        midimap<elf>
  \-PE	7e040000-7e04c000	\               midimap
ELF	7e04c000-7e081000	Deferred        winealsa<elf>
  \-PE	7e060000-7e081000	\               winealsa
ELF	7e081000-7e08a000	Deferred        libxcursor.so.1
ELF	7e08a000-7e08f000	Deferred        libxfixes.so.3
ELF	7e08f000-7e092000	Deferred        libxcomposite.so.1
ELF	7e092000-7e098000	Deferred        libxrandr.so.2
ELF	7e098000-7e0a0000	Deferred        libxrender.so.1
ELF	7e0a0000-7e0a5000	Deferred        libxxf86vm.so.1
ELF	7e0a5000-7e0a8000	Deferred        libxinerama.so.1
ELF	7e0a8000-7e0c8000	Deferred        imm32<elf>
  \-PE	7e0b0000-7e0c8000	\               imm32
ELF	7e0c8000-7e0cd000	Deferred        libxdmcp.so.6
ELF	7e0cd000-7e0e5000	Deferred        libxcb.so.1
ELF	7e0e5000-7e0e7000	Deferred        libxcb-xlib.so.0
ELF	7e0e7000-7e0ea000	Deferred        libxau.so.6
ELF	7e0ea000-7e1d1000	Deferred        libx11.so.6
ELF	7e1d1000-7e1df000	Deferred        libxext.so.6
ELF	7e1e1000-7e1f8000	Deferred        msacm32<elf>
  \-PE	7e1f0000-7e1f8000	\               msacm32
ELF	7e1fa000-7e292000	Deferred        winex11<elf>
  \-PE	7e210000-7e292000	\               winex11
ELF	7e2cc000-7e2ed000	Deferred        libexpat.so.1
ELF	7e2ed000-7e317000	Deferred        libfontconfig.so.1
ELF	7e317000-7e32c000	Deferred        libz.so.1
ELF	7e32c000-7e39c000	Deferred        libfreetype.so.6
ELF	7e3b7000-7e3d6000	Deferred        d3dx8<elf>
  \-PE	7e3c0000-7e3d6000	\               d3dx8
ELF	7e3d6000-7e3f5000	Deferred        d3dx9_36<elf>
  \-PE	7e3e0000-7e3f5000	\               d3dx9_36
ELF	7e3f5000-7e505000	Deferred        wined3d<elf>
  \-PE	7e410000-7e505000	\               wined3d
ELF	7e505000-7e535000	Deferred        d3d9<elf>
  \-PE	7e510000-7e535000	\               d3d9
ELF	7e535000-7e549000	Deferred        lz32<elf>
  \-PE	7e540000-7e549000	\               lz32
ELF	7e549000-7e5b0000	Deferred        setupapi<elf>
  \-PE	7e550000-7e5b0000	\               setupapi
ELF	7e5b0000-7e5dc000	Deferred        ws2_32<elf>
  \-PE	7e5c0000-7e5dc000	\               ws2_32
ELF	7e5dc000-7e5fe000	Deferred        mpr<elf>
  \-PE	7e5e0000-7e5fe000	\               mpr
ELF	7e5fe000-7e64d000	Deferred        wininet<elf>
  \-PE	7e610000-7e64d000	\               wininet
ELF	7e64d000-7e70e000	Deferred        comctl32<elf>
  \-PE	7e660000-7e70e000	\               comctl32
ELF	7e70e000-7e768000	Deferred        shlwapi<elf>
  \-PE	7e720000-7e768000	\               shlwapi
ELF	7e768000-7e882000	Deferred        shell32<elf>
  \-PE	7e780000-7e882000	\               shell32
ELF	7e882000-7e969000	Deferred        oleaut32<elf>
  \-PE	7e8a0000-7e969000	\               oleaut32
ELF	7e969000-7e9fb000	Deferred        winmm<elf>
  \-PE	7e970000-7e9fb000	\               winmm
ELF	7e9fb000-7ea45000	Deferred        dsound<elf>
  \-PE	7ea00000-7ea45000	\               dsound
ELF	7ea45000-7ea58000	Deferred        libresolv.so.2
ELF	7ea5a000-7ea73000	Deferred        version<elf>
  \-PE	7ea60000-7ea73000	\               version
ELF	7ea73000-7ea92000	Deferred        iphlpapi<elf>
  \-PE	7ea80000-7ea92000	\               iphlpapi
ELF	7ea92000-7eaf7000	Deferred        rpcrt4<elf>
  \-PE	7eaa0000-7eaf7000	\               rpcrt4
ELF	7eaf7000-7eb95000	Deferred        gdi32<elf>
  \-PE	7eb10000-7eb95000	\               gdi32
ELF	7eb95000-7ecde000	Deferred        user32<elf>
  \-PE	7ebb0000-7ecde000	\               user32
ELF	7ecde000-7ede7000	Deferred        ole32<elf>
  \-PE	7ed00000-7ede7000	\               ole32
ELF	7ede7000-7ee1f000	Deferred        dinput<elf>
  \-PE	7edf0000-7ee1f000	\               dinput
ELF	7ee1f000-7ee73000	Deferred        advapi32<elf>
  \-PE	7ee30000-7ee73000	\               advapi32
ELF	7ef93000-7ef9e000	Deferred        libnss_files.so.2
ELF	7ef9e000-7efa8000	Deferred        libnss_nis.so.2
ELF	7efa8000-7efc0000	Deferred        libnsl.so.1
ELF	7efc0000-7efe5000	Deferred        libm.so.6
ELF	7efe8000-7f000000	Deferred        dinput8<elf>
  \-PE	7eff0000-7f000000	\               dinput8
ELF	f7c55000-f7c5e000	Deferred        libnss_compat.so.2
ELF	f7c5f000-f7c63000	Deferred        libdl.so.2
ELF	f7c63000-f7db2000	Deferred        libc.so.6
ELF	f7db3000-f7dcb000	Deferred        libpthread.so.0
ELF	f7de6000-f7f1c000	Deferred        libwine.so.1
ELF	f7f1e000-f7f3d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Ubisoft\Assassin's Creed\AssassinsCreed_Dx9.exe
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b   15
	0000001a    0
	00000019    1 <==
	00000018    1
	00000009    0
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

```


Please help me. If anyone has any idea how to fix this etc please tell me. I am running wine 1.1.5

---

### Post by jamesrl on 2008-10-13
[Page faults]("http://en.wikipedia.org/wiki/Page_fault") (basically are memory errors) that are notoriously difficult to track down.  Something within wine is not acting as windows would do, and that cause the program to want to access memory that isn't loaded.
Debugging is a complicated process:
[http://wiki.jswindle.com/index.php/Debugging_Wine](http://wiki.jswindle.com/index.php/Debugging_Wine)
and can't really be done through the forums.
You can possibly try seeing if anything changed, since before you started to crash and now.  I'd also recommend maybe trying windows running from VirtualBox as opposed to wine.

Also you could read the Assassin's Creed page at wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=11069&iTestingId=27000](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11069&iTestingId=27000)

---

### Post by david_kt on 2008-10-13
> **thefishki345 said:**
> wine.1.1.5

Hi,

I recently created a thread 5 days ago:

[http://ubuntuforums.org/showthread.php?p=5921957#post5921957](http://ubuntuforums.org/showthread.php?p=5921957#post5921957)

but got no replies. So basically if you read through that it  says when I try and run Assassins creed, **_which worked fine before_**,

When did it work fine? Do you remember which wine version? Try to downgrade wine to that version, or just try older wines if you do not remember which one. It could solve your problem much faster than troubleshooting latest wine. Please see my other post explaining this case more clearly:

[http://ubuntuforums.org/showthread.php?t=944949](http://ubuntuforums.org/showthread.php?t=944949)

DK

---

### Post by thefishki345 on 2008-10-14
Hi all, thankyou for your replies.
jamesrl I will have a look at those pages and ask someone I know who has more knowledge of linux etc than me. and I have already seen the wine page, even commented in it :)

david_kt, when I say it worked ¨fine¨ I mean it just launched, it still gave me unplayable results, I am probably going to go back to wine 1.0 (the wine which launched) but all my other games run better on 1.1.5 (Guild wars runs faster, call of duty4 doesnt need a patch). I am thinking of doing a multiple wine install hmm...

thanks for all your help guys

---

### Post by thefishki345 on 2008-10-15
Argh, tried wine 1.0 and it still gave me the same errors, tried 1.1.6 and even reinstalled the game, same errors :(

---

### Post by thefishki345 on 2008-10-18
BUMP

please

---

