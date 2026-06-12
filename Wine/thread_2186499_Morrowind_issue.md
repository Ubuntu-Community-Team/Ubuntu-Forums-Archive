---
title: "Morrowind issue"
date: 2013-11-07
forum: Wine
---

### Post by steve8 on 2013-11-07
Anyone got the elderscrolls 3 morrowind working I have an extract and play copy with mods. I had this game on here before and it never gave me any problems.
Everytime i try to start it crashes and gives me an error:

```
Unhandled exception: unimplemented function msvcp60.dll.??0Init@ios_base@std@@QAE@XZ called in 32-bit code (0x7b83ac5f).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b83ac5f ESP:0033fc98 EBP:0033fcfc EFLAGS:00000287(   - --  I S - -P-C)
 EAX:7b826419 EBX:7b8af000 ECX:00000008 EDX:0033fcb8
 ESI:ffcb7824 EDI:00000000
Stack dump:
0x0033fc98:  0033fd1c 00000008 7e400810 80000100
0x0033fca8:  00000001 00000000 7b83ac5f 00000002
0x0033fcb8:  7e43d4c0 7e4421bb 7ffdf000 0033fce4
0x0033fcc8:  7e3f8000 0033fd1c 7e39340f 7e3f8000
0x0033fcd8:  0033fd28 7e39340f 0000000d 00694540
0x0033fce8:  00000000 0033fd2c 006946c1 0033fd0c
000c: sel=0067 base=00000000 limit=00000000 32-bit --x
Backtrace:
=>0 0x7b83ac5f in kernel32 (+0x2ac5f) (0x0033fcfc)
  1 0x7e43d498 in msvcp60 (+0x2d497) (0x0033fd2c)
  2 0x7e421e85 in msvcp60 (+0x11e84) (0x0033fd90)
  3 0x004012eb in morrowind.original (+0x12ea) (0x0033fd90)
  4 0x00727948 in morrowind.original (+0x327947) (0x0033fe40)
  5 0x7b861d48 call_process_entry+0xb() in kernel32 (0x0033fe58)
  6 0x7b861e8d call_process_entry+0x150() in kernel32 (0x0033fea8)
  7 0x7bc7edfc call_thread_func_wrapper+0xb() in ntdll (0x0033feb8)
  8 0x7bc7ee4b call_thread_func+0x44() in ntdll (0x0033ff98)
  9 0x7bc7edda in ntdll (+0x6edd9) (0x0033ffb8)
  10 0x7bc545bf in ntdll (+0x445be) (0x0033ffe8)
  11 0xf768ab5d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  12 0xf768ab3b wine_switch_to_stack+0x2a() in libwine.so.1 (0xffcb7848)
  13 0x7bc54901 LdrInitializeThunk+0x341() in ntdll (0xffcb78c8)
  14 0x7b862766 __wine_kernel_init+0x719() in kernel32 (0xffcb8758)
  15 0x7bc5507b __wine_process_init+0x156() in ntdll (0xffcb87a8)
  16 0xf76893ce wine_init+0x140() in libwine.so.1 (0xffcb87e8)
  17 0x7bf011c6 main+0x13d() in <wine-loader> (0xffcb8c28)
  18 0xf74ad905 __libc_start_main+0xf4() in libc.so.6 (0x00000000)
0x7b83ac5f: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (74 modules)
PE	  400000-  7e4000	Export          morrowind.original
PE	30000000-3006e000	Deferred        binkw32
ELF	7b800000-7ba43000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba43000	\               kernel32
ELF	7bc00000-7bce3000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bce3000	\               ntdll
ELF	7bf00000-7bf04000	Dwarf           <wine-loader>
ELF	7dd8f000-7ddc6000	Deferred        uxtheme<elf>
  \-PE	7dda0000-7ddc6000	\               uxtheme
ELF	7dddc000-7dde2000	Deferred        libxfixes.so.3
ELF	7dde2000-7dded000	Deferred        libxcursor.so.1
ELF	7de5f000-7de88000	Deferred        libexpat.so.1
ELF	7de88000-7dec2000	Deferred        libfontconfig.so.1
ELF	7dec2000-7ded3000	Deferred        libxi.so.6
ELF	7ded3000-7ded7000	Deferred        libxcomposite.so.1
ELF	7ded7000-7dee2000	Deferred        libxrandr.so.2
ELF	7dee2000-7deed000	Deferred        libxrender.so.1
ELF	7deed000-7def3000	Deferred        libxxf86vm.so.1
ELF	7def3000-7def7000	Deferred        libxinerama.so.1
ELF	7def7000-7df1b000	Deferred        imm32<elf>
  \-PE	7df00000-7df1b000	\               imm32
ELF	7df1b000-7df22000	Deferred        libxdmcp.so.6
ELF	7df22000-7df26000	Deferred        libxau.so.6
ELF	7df26000-7df47000	Deferred        libxcb.so.1
ELF	7df47000-7df4d000	Deferred        libuuid.so.1
ELF	7df4d000-7df67000	Deferred        libice.so.6
ELF	7df67000-7e09c000	Deferred        libx11.so.6
ELF	7e09c000-7e0af000	Deferred        libxext.so.6
ELF	7e0af000-7e0b8000	Deferred        libsm.so.6
ELF	7e0b8000-7e169000	Deferred        winex11<elf>
  \-PE	7e0c0000-7e169000	\               winex11
ELF	7e169000-7e183000	Deferred        libz.so.1
ELF	7e183000-7e222000	Deferred        libfreetype.so.6
ELF	7e240000-7e35f000	Deferred        comctl32<elf>
  \-PE	7e250000-7e35f000	\               comctl32
ELF	7e35f000-7e401000	Deferred        msvcrt<elf>
  \-PE	7e370000-7e401000	\               msvcrt
ELF	7e401000-7e49e000	Dwarf           msvcp60<elf>
  \-PE	7e410000-7e49e000	\               msvcp60
ELF	7e49e000-7e61b000	Deferred        wined3d<elf>
  \-PE	7e4b0000-7e61b000	\               wined3d
ELF	7e61b000-7e653000	Deferred        d3d8<elf>
  \-PE	7e620000-7e653000	\               d3d8
ELF	7e653000-7e6a0000	Deferred        dsound<elf>
  \-PE	7e660000-7e6a0000	\               dsound
ELF	7e6a0000-7e6bc000	Deferred        dinput8<elf>
  \-PE	7e6b0000-7e6bc000	\               dinput8
ELF	7e6bc000-7e6e9000	Deferred        msacm32<elf>
  \-PE	7e6c0000-7e6e9000	\               msacm32
ELF	7e6e9000-7e79f000	Deferred        winmm<elf>
  \-PE	7e6f0000-7e79f000	\               winmm
ELF	7e79f000-7e828000	Deferred        rpcrt4<elf>
  \-PE	7e7b0000-7e828000	\               rpcrt4
ELF	7e828000-7e989000	Deferred        ole32<elf>
  \-PE	7e840000-7e989000	\               ole32
ELF	7e989000-7e9fa000	Deferred        advapi32<elf>
  \-PE	7e9a0000-7e9fa000	\               advapi32
ELF	7e9fa000-7ead9000	Deferred        gdi32<elf>
  \-PE	7ea10000-7ead9000	\               gdi32
ELF	7ead9000-7ec48000	Deferred        user32<elf>
  \-PE	7eaf0000-7ec48000	\               user32
ELF	7ec48000-7ec55000	Deferred        libnss_files.so.2
ELF	7ec55000-7ec6e000	Deferred        libnsl.so.1
ELF	7ef9f000-7efe2000	Deferred        libm.so.6
ELF	7efe5000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f7482000-f748e000	Deferred        libnss_nis.so.2
ELF	f748f000-f7494000	Deferred        libdl.so.2
ELF	f7494000-f7648000	Dwarf           libc.so.6
ELF	f7649000-f7664000	Deferred        libpthread.so.0
ELF	f7667000-f7670000	Deferred        libnss_compat.so.2
ELF	f7682000-f77c6000	Dwarf           libwine.so.1
ELF	f77c8000-f77ea000	Deferred        ld-linux.so.2
ELF	f77ea000-f77eb000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001f    0
	0000001e    0
	00000018    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000019    0
	00000014    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001d    0
	0000001b    0
00000021 explorer.exe
	00000022    0
00000023 (D) Z:\home\paul\Downloads\Morrowind GOTY\Morrowind GOTY\Morrowind.Original.exe
	00000024    0 <==
System information:
    Wine build: wine-1.4.1
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.11.0-13-generic
```

---

### Post by Toz on 2013-11-07
*Added code tags and moved to the **Wine** subforum.*

---

### Post by King Dude on 2013-11-08
You may want to check out [OpenMW]("https://openmw.org/en/"), a reimplementation of the Morrowind engine that makes TES: Morrowind run natively on Linux and fixes numerous bugs. It also adds some features, such as better graphics, AI, and physics.

---

### Post by steve8 on 2013-11-08
well i guess that won't even run on my system it gives me errors when i try to install the deb packages tried a couple of em and no luck

---

### Post by steve8 on 2013-11-08
i dont understand why the game doesnt work anymore it worked fine before

---

