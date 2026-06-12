---
title: "Graphical Design-Programme (Frontplatten Designer)"
date: 2008-12-01
forum: Wine
---

### Post by osterchrisi on 2008-12-01
Hey guys,

I'm having trouble with a front panel designer (see [here]("http://www.schaeffer-ag.de/en/download/front-panel-designer.html")). I've ran this programme unter WinXP without having trouble, it's not too complex and it's not 3D as far as i remember.

I'm using a GeForce4 MX 420 graphic card with the original nvidia-drivers. The panel says the following:

```
chrisi@station:~/Desktop/Frontplatten Designer$ wine frontdesign.exe
wine: Unhandled page fault on read access to 0x00000000 at address 0x42ef7c (thread 0009), starting debugger...
First chance exception: page fault on read access to 0x00000000 in 32-bit code (0x0042ef7c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0042ef7c ESP:0099fc34 EBP:0099fc48 EFLAGS:00210286(   - 00      -RISP1)
 EAX:00000000 EBX:00a35990 ECX:ffffffff EDX:00000000
 ESI:00a359f4 EDI:00000000
Stack dump:
0x0099fc34:  00000000 009d12a8 00a35a35 00a35874
0x0099fc44:  00a35990 0099fc60 0042d447 00a35990
0x0099fc54:  00a2ef2c 0099fcb0 00a357d0 0099fca8
0x0099fc64:  0042d2aa 00a35990 00a357d0 00a2ef2c
0x0099fc74:  00a357d0 00a2ef2c 00a2ef2c 00a357d0
0x0099fc84:  0099fcc8 005d253f 00647c98 0099fc70
Backtrace:
=>1 0x0042ef7c in frontdesign (+0x2ef7c) (0x0099fc48)
  2 0x0042d447 in frontdesign (+0x2d447) (0x0099fc60)
  3 0x0042d2aa in frontdesign (+0x2d2aa) (0x0099fca8)
  4 0x00452b82 in frontdesign (+0x52b82) (0x0099fd68)
  5 0x00453299 in frontdesign (+0x53299) (0x0099fdf4)
  6 0x00440261 in frontdesign (+0x40261) (0x0099fe50)
  7 0x00569368 in frontdesign (+0x169368) (0x0099fe74)
  8 0x00401cdc in frontdesign (+0x1cdc) (0x0099fed0)
  9 0x005da1fb in frontdesign (+0x1da1fb) (0x0099ff00)
  10 0x00000000 (0x0099ffe8)
  11 0xb7eead37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0042ef7c: repne scasb	%es:(%edi)
Modules:
Module	Address			Debug info	Name (86 modules)
PE	  400000-  797000	Export          frontdesign
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e063000-7e0ae000	Deferred        riched20<elf>
  \-PE	7e070000-7e0ae000	\               riched20
ELF	7e0fa000-7e12d000	Deferred        uxtheme<elf>
  \-PE	7e100000-7e12d000	\               uxtheme
ELF	7e12d000-7e196000	Deferred        libgcrypt.so.11
ELF	7e196000-7e1a8000	Deferred        libtasn1.so.3
ELF	7e1a8000-7e1b1000	Deferred        libkrb5support.so.0
ELF	7e1b1000-7e1e3000	Deferred        libcrypt.so.1
ELF	7e1e3000-7e280000	Deferred        libgnutls.so.26
ELF	7e280000-7e2a4000	Deferred        libk5crypto.so.3
ELF	7e2a4000-7e336000	Deferred        libkrb5.so.3
ELF	7e336000-7e360000	Deferred        libgssapi_krb5.so.2
ELF	7e360000-7e396000	Deferred        libcups.so.2
ELF	7e3a4000-7e3ad000	Deferred        libxcursor.so.1
ELF	7e3ad000-7e3b2000	Deferred        libxfixes.so.3
ELF	7e3b2000-7e3b6000	Deferred        libxcomposite.so.1
ELF	7e3b6000-7e3bd000	Deferred        libxrandr.so.2
ELF	7e3bd000-7e3c7000	Deferred        libxrender.so.1
ELF	7e3c7000-7e3ca000	Deferred        libxinerama.so.1
ELF	7e3ca000-7e3eb000	Deferred        imm32<elf>
  \-PE	7e3d0000-7e3eb000	\               imm32
ELF	7e3eb000-7e3f0000	Deferred        libxdmcp.so.6
ELF	7e3f0000-7e409000	Deferred        libxcb.so.1
ELF	7e409000-7e40c000	Deferred        libxcb-xlib.so.0
ELF	7e40c000-7e40f000	Deferred        libxau.so.6
ELF	7e40f000-7e4fe000	Deferred        libx11.so.6
ELF	7e4fe000-7e50d000	Deferred        libxext.so.6
ELF	7e50d000-7e513000	Deferred        libxxf86vm.so.1
ELF	7e513000-7e52b000	Deferred        libice.so.6
ELF	7e52b000-7e534000	Deferred        libsm.so.6
ELF	7e534000-7e538000	Deferred        libgpg-error.so.0
ELF	7e538000-7e53c000	Deferred        libkeyutils.so.1
ELF	7e53c000-7e540000	Deferred        libcom_err.so.2
ELF	7e542000-7e5dd000	Deferred        winex11<elf>
  \-PE	7e550000-7e5dd000	\               winex11
ELF	7e602000-7e629000	Deferred        libexpat.so.1
ELF	7e629000-7e656000	Deferred        libfontconfig.so.1
ELF	7e656000-7e66c000	Deferred        libz.so.1
ELF	7e66c000-7e6e2000	Deferred        libfreetype.so.6
ELF	7e6e2000-7e788000	Deferred        oleaut32<elf>
  \-PE	7e6f0000-7e788000	\               oleaut32
ELF	7e788000-7e79c000	Deferred        libresolv.so.2
ELF	7e7aa000-7e7c9000	Deferred        iphlpapi<elf>
  \-PE	7e7b0000-7e7c9000	\               iphlpapi
ELF	7e7c9000-7e82c000	Deferred        rpcrt4<elf>
  \-PE	7e7e0000-7e82c000	\               rpcrt4
ELF	7e82c000-7e8d2000	Deferred        ole32<elf>
  \-PE	7e840000-7e8d2000	\               ole32
ELF	7e8d2000-7e92d000	Deferred        shlwapi<elf>
  \-PE	7e8e0000-7e92d000	\               shlwapi
ELF	7e92d000-7ea41000	Deferred        shell32<elf>
  \-PE	7e940000-7ea41000	\               shell32
ELF	7ea41000-7eaef000	Deferred        comdlg32<elf>
  \-PE	7ea50000-7eaef000	\               comdlg32
ELF	7eaef000-7ebb4000	Deferred        comctl32<elf>
  \-PE	7eb00000-7ebb4000	\               comctl32
ELF	7ebb4000-7ebeb000	Deferred        winspool<elf>
  \-PE	7ebc0000-7ebeb000	\               winspool
ELF	7ebeb000-7ec00000	Deferred        lz32<elf>
  \-PE	7ebf0000-7ec00000	\               lz32
ELF	7ec00000-7ec1b000	Deferred        version<elf>
  \-PE	7ec10000-7ec1b000	\               version
ELF	7ec1b000-7ecba000	Deferred        gdi32<elf>
  \-PE	7ec30000-7ecba000	\               gdi32
ELF	7ecba000-7ee06000	Deferred        user32<elf>
  \-PE	7ecd0000-7ee06000	\               user32
ELF	7ee06000-7ee29000	Deferred        mpr<elf>
  \-PE	7ee10000-7ee29000	\               mpr
ELF	7ee29000-7ee7c000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee7c000	\               advapi32
ELF	7ef9c000-7efa8000	Deferred        libnss_files.so.2
ELF	7efa8000-7efb3000	Deferred        libnss_nis.so.2
ELF	7efb3000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff2000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7d59000-b7d5d000	Deferred        libdl.so.2
ELF	b7d5d000-b7ebb000	Deferred        libc.so.6
ELF	b7ebc000-b7ed5000	Deferred        libpthread.so.0
ELF	b7ee3000-b801a000	Export          libwine.so.1
ELF	b801c000-b8039000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\chrisi\Desktop\Frontplatten Designer\frontdesign.exe
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
=>1 0x0042ef7c in frontdesign (+0x2ef7c) (0x0099fc48)
  2 0x0042d447 in frontdesign (+0x2d447) (0x0099fc60)
  3 0x0042d2aa in frontdesign (+0x2d2aa) (0x0099fca8)
  4 0x00452b82 in frontdesign (+0x52b82) (0x0099fd68)
  5 0x00453299 in frontdesign (+0x53299) (0x0099fdf4)
  6 0x00440261 in frontdesign (+0x40261) (0x0099fe50)
  7 0x00569368 in frontdesign (+0x169368) (0x0099fe74)
  8 0x00401cdc in frontdesign (+0x1cdc) (0x0099fed0)
  9 0x005da1fb in frontdesign (+0x1da1fb) (0x0099ff00)
  10 0x00000000 (0x0099ffe8)
  11 0xb7eead37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

I have absolutely no idea what that should mean, I use WINE 1.0.1 and copied five dlls from the programme folder to the "Windows\system32" folder. Any suggestions?

Thank you!

---

### Post by qwertymn on 2008-12-02
Hi, i tried this app, and it starts fine for me in virtual desktop mode. Maybe you could try on a new fresh ~/.wine, and set wine to run in virtual desktop

---

