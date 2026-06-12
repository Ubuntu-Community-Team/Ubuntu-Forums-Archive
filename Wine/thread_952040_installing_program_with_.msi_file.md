---
title: "installing program with .msi file"
date: 2008-10-18
forum: Wine
---

### Post by le_vainqueur on 2008-10-18
I would like to install a program called [Informatik]("http://www.download.com/Informatik-PDF-Markup/3000-10743_4-10801483.html") in wine.  The installer is a .msi file, however, so I am not sure how to go about this.  The program requires .net framework 2 which I already have up and running in wine.  What should I do to try to install this program.

---

### Post by Kareeser on 2008-10-19
[http://wiki.jswindle.com/index.php/Wine_MSI](http://wiki.jswindle.com/index.php/Wine_MSI)

wine msiexec /i xyz.msi

---

### Post by TikiKai on 2008-11-04
Hey everyone, I'm trying to install a windows msi file as well, and using the msiexec -i fails with the following...any thoughts on where I should turn next? (except a virtual machine?)

I tried sudo ... as well, but couldn't because:
scott@Ennio:/home$ sudo msiexec /i  ~/SiteSpinnerV270f.msi
[sudo] password for scott: 
wine: /home/scott/.wine is not owned by you


Thanks in advance!


scott@Ennio:/home$ msiexec /i  ~/SiteSpinnerV270f.msi
fixme:advapi:LookupAccountNameW (null) L"scott" (nil) 0x32f87c (nil) 0x32f880 0x32f874 - stub
fixme:advapi:LookupAccountNameW (null) L"scott" 0x12ef00 0x32f87c 0x12bb78 0x32f880 0x32f874 - stub
wine: Unhandled page fault on read access to 0xffffffff at address 0x330036 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x00330036).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00330036 ESP:0032f54c EBP:00660069 EFLAGS:00210296(   - 00      RISAP1)
 EAX:ffffffff EBX:0073006e ECX:0032f4c4 EDX:00000001
 ESI:0053005f EDI:00720065
Stack dump:
0x0032f54c:  00660069 0030002e 0030005f 0030005f
0x0032f55c:  00320000 0020eb50 0020d338 7edfa76d
0x0032f56c:  7ee5aff4 00000000 0000000a 0032f5b8
0x0032f57c:  7ee1dff0 00216f88 0020b438 0032f5a8
0x0032f58c:  01e1e515 00000000 00000000 00000000
0x0032f59c:  0032f5cc 000001eb 0032f5cc 00216f88
Backtrace:
=>1 0x00330036 (0x00660069)
  2 0x00000000 (0x00000000)
0x00330036: adcl	%eax,0x0(%eax)
Modules:
Module	Address			Debug info	Name (78 modules)
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e25a000-7e27a000	Deferred        libjpeg.so.62
ELF	7e2dd000-7e310000	Deferred        uxtheme<elf>
  \-PE	7e2e0000-7e310000	\               uxtheme
ELF	7e310000-7e319000	Deferred        libxcursor.so.1
ELF	7e319000-7e31e000	Deferred        libxfixes.so.3
ELF	7e31e000-7e322000	Deferred        libxcomposite.so.1
ELF	7e322000-7e329000	Deferred        libxrandr.so.2
ELF	7e329000-7e333000	Deferred        libxrender.so.1
ELF	7e333000-7e336000	Deferred        libxinerama.so.1
ELF	7e336000-7e357000	Deferred        imm32<elf>
  \-PE	7e340000-7e357000	\               imm32
ELF	7e357000-7e35c000	Deferred        libxdmcp.so.6
ELF	7e35c000-7e375000	Deferred        libxcb.so.1
ELF	7e375000-7e378000	Deferred        libxcb-xlib.so.0
ELF	7e378000-7e467000	Deferred        libx11.so.6
ELF	7e467000-7e476000	Deferred        libxext.so.6
ELF	7e476000-7e47c000	Deferred        libxxf86vm.so.1
ELF	7e47c000-7e494000	Deferred        libice.so.6
ELF	7e494000-7e49d000	Deferred        libsm.so.6
ELF	7e4af000-7e54a000	Deferred        winex11<elf>
  \-PE	7e4c0000-7e54a000	\               winex11
ELF	7e573000-7e59a000	Deferred        libexpat.so.1
ELF	7e59a000-7e5c7000	Deferred        libfontconfig.so.1
ELF	7e5c7000-7e5dd000	Deferred        libz.so.1
ELF	7e5dd000-7e653000	Deferred        libfreetype.so.6
ELF	7e653000-7e668000	Deferred        lz32<elf>
  \-PE	7e660000-7e668000	\               lz32
ELF	7e668000-7e683000	Deferred        version<elf>
  \-PE	7e670000-7e683000	\               version
ELF	7e683000-7e729000	Deferred        oleaut32<elf>
  \-PE	7e690000-7e729000	\               oleaut32
ELF	7e729000-7e74b000	Deferred        cabinet<elf>
  \-PE	7e730000-7e74b000	\               cabinet
ELF	7e74b000-7e810000	Deferred        comctl32<elf>
  \-PE	7e750000-7e810000	\               comctl32
ELF	7e810000-7e924000	Deferred        shell32<elf>
  \-PE	7e820000-7e924000	\               shell32
ELF	7e924000-7e947000	Deferred        mpr<elf>
  \-PE	7e930000-7e947000	\               mpr
ELF	7e947000-7e997000	Deferred        wininet<elf>
  \-PE	7e950000-7e997000	\               wininet
ELF	7e997000-7e9f2000	Deferred        shlwapi<elf>
  \-PE	7e9a0000-7e9f2000	\               shlwapi
ELF	7e9f2000-7ea06000	Deferred        libresolv.so.2
ELF	7ea18000-7ea37000	Deferred        iphlpapi<elf>
  \-PE	7ea20000-7ea37000	\               iphlpapi
ELF	7ea37000-7ea9a000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea9a000	\               rpcrt4
ELF	7ea9a000-7eb39000	Deferred        gdi32<elf>
  \-PE	7eab0000-7eb39000	\               gdi32
ELF	7eb39000-7ec85000	Deferred        user32<elf>
  \-PE	7eb50000-7ec85000	\               user32
ELF	7ec85000-7ecd8000	Deferred        advapi32<elf>
  \-PE	7ec90000-7ecd8000	\               advapi32
ELF	7ecd8000-7ed7e000	Deferred        ole32<elf>
  \-PE	7ecf0000-7ed7e000	\               ole32
ELF	7ed7e000-7edbd000	Deferred        urlmon<elf>
  \-PE	7ed90000-7edbd000	\               urlmon
ELF	7edbd000-7ee68000	Deferred        msi<elf>
  \-PE	7edd0000-7ee68000	\               msi
ELF	7ee68000-7ee83000	Deferred        msiexec<elf>
  \-PE	7ee70000-7ee83000	\               msiexec
ELF	7efa3000-7efaf000	Deferred        libnss_files.so.2
ELF	7efaf000-7efc8000	Deferred        libnsl.so.1
ELF	7efc8000-7efee000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c10000-b7c13000	Deferred        libxau.so.6
ELF	b7c13000-b7c1c000	Deferred        libnss_compat.so.2
ELF	b7c1d000-b7c21000	Deferred        libdl.so.2
ELF	b7c21000-b7d7f000	Deferred        libc.so.6
ELF	b7d80000-b7d99000	Deferred        libpthread.so.0
ELF	b7dab000-b7ee2000	Deferred        libwine.so.1
ELF	b7ee4000-b7f01000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\system32\msiexec.exe
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
=>1 0x00330036 (0x00660069)
  2 0x00000000 (0x00000000)

---

### Post by YokoZar on 2008-11-04
**Do not use sudo to run wine, ever**

msi files can be run by just double clicking them in Ubuntu 8.10

---

### Post by cogadh on 2008-11-04
However, because you have now run wine with sudo, you have probably screwed up your permissions on your .wine directory. You should never run wine using sudo or with a root account. Your best bet for fixing it is to delete your .wine directory and then re-create it without using sudo ever again.

---

### Post by TikiKai on 2008-11-04
Doublelicking on the msi said unrecognizable .exe format. 

As to running anything else, the other apps I have installed in wine work great, and new ones install just fine too. But thanks for the advice, for sure.

Any other ideas? I know that the file is a good one because I just copied it over the network into a windows box and it installed perfectly.

Mahalo!

---

### Post by cogadh on 2008-11-04
You could try "wine start SiteSpinnerV270f.msi", but it will likely produce the same results. That register dump you got was terribly uninformative and the last time Site Spinner was tested and worked in Wine was back at version 0.9.15. Its entirely possible that it just doesn't work in Wine anymore.

---

### Post by TikiKai on 2008-11-05
10-4
I'll run it in a virtual box...The disk space is OK but I'd rather not pollute my RAM and CPU. 

All in all, I've been able to find a replacement (sometimes better, sometimes no so much) for almost everything else I've 'needed' in my migration to linux (Debian server Ubuntu workstations) so I guess I can consider myself lucky!

Thanks for the advice, I appreciate it. I'm really enjoying the learning curve. 

Nevertheless, I sure would like to know what happened between the older Wine/SiteSpinner and this Wine/SiteSpinner to make it stop working. VirtualMechanics is pretty much hands off on the linux thought but I think...if the dump was more informative I would have been at least that much more prepared to research it on my own which is probably where those guys at Virtual Mechanics are sitting. In the installation process it would be nice to know exactly when and which actions try to do to what to where? (Dont get me wrong, I do not think I can intemperate a BSOD on viewing it either...)

Anything even vaguely resembling something I can track down without knowing addressing would be nice.

Thanks again, guys, 
Mahalo to you and yours,
Scott

---

