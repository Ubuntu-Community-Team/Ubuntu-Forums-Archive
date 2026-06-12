---
title: "Call of Duty 4 Error"
date: 2012-07-06
forum: Wine
---

### Post by HeavyHDx on 2012-07-06
Hi,

i've installed Ubuntu 10.04 64 Bit and wanted to install CoD4 wich i played already on another installation before a couple of months.
I installed the game with wine and downloaded a non-cd .exe for the game to run, but if i start iw3sp.exe the splash-screen shows and there is this error:

[http://gyazo.com/758e8c62b10c2c8dcc10cd4cab09d8b4.png?1341593334](http://gyazo.com/758e8c62b10c2c8dcc10cd4cab09d8b4.png?1341593334)

(yea i'm german)

so if i go on details and save this error, i get this:

```


Unhandled exception: page fault on read access to 0x0000003c in 32-bit code (0x005d9819).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:005d9819 ESP:0033f838 EBP:0033f870 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:00000001 ECX:00000000 EDX:01330c9c
 ESI:0033f848 EDI:00698964
Stack dump:
0x0033f838:  013dde2c 005d99ab 01337150 00002300
0x0033f848:  00698964 0033fcb8 005d9a01 01621e00
0x0033f858:  00000000 00002180 01626c90 00000000
0x0033f868:  005d9b1f 00698964 0033fcb8 005d9bce
0x0033f878:  01337c98 004453ce 7b845a40 01337150
0x0033f888:  00000001 00535137 7b86ff40 7b845a40
Backtrace:
=>0 0x005d9819 in iw3sp (+0x1d9819) (0x0033f870)
  1 0x005d9bce in iw3sp (+0x1d9bcd) (0x0033fcb8)
  2 0x00535285 in iw3sp (+0x135284) (0x0033fcc8)
  3 0x00595da2 in iw3sp (+0x195da1) (0x0033fe70)
  4 0x7b85b3ec call_process_entry+0xb() in kernel32 (0x0033fe88)
  5 0x7b85ea7b start_process+0x5a(peb=0x33f848) [/home/marcel/Downloads/wine-1.4/dlls/kernel32/process.c:1083] in kernel32 (0x0033fec8)
  6 0x7bc71f80 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  7 0x7bc721bd call_thread_func+0x7c(entry=0x7b85ea20, arg=0x7ffdf000, frame=0x33ffc8) [/home/marcel/Downloads/wine-1.4/dlls/ntdll/signal_i386.c:2532] in ntdll (0x0033ffa8)
  8 0x7bc71f5e call_thread_entry_point+0x11() in ntdll (0x0033ffc8)
  9 0x7bc4c8ce start_process+0x1d(kernel_start=0x7b85ea20) [/home/marcel/Downloads/wine-1.4/dlls/ntdll/loader.c:2612] in ntdll (0x0033ffe8)
  10 0xf767ddbd wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  11 0xf767ddfb wine_switch_to_stack+0x2a(func=0x7bc4c8b0, arg=0x7b85ea20, stack=0x340000) [/home/marcel/Downloads/wine-1.4/libs/wine/port.c:59] in libwine.so.1 (0xffb85668)
  12 0x7bc50d9f LdrInitializeThunk+0x32e(kernel_start=0x7b85ea20, unknown2=0, unknown3=0, unknown4=0) [/home/marcel/Downloads/wine-1.4/dlls/ntdll/loader.c:2668] in ntdll (0xffb856d8)
  13 0x7b86331e __wine_kernel_init+0xa0d() [/home/marcel/Downloads/wine-1.4/dlls/kernel32/process.c:1255] in kernel32 (0xffb86878)
  14 0x7bc512c3 __wine_process_init+0x262() [/home/marcel/Downloads/wine-1.4/dlls/ntdll/loader.c:2877] in ntdll (0xffb868f8)
  15 0xf767b942 wine_init+0x281(argc=0x2, argv=0xffb86e54, error="", error_size=0x400) [/home/marcel/Downloads/wine-1.4/libs/wine/loader.c:831] in libwine.so.1 (0xffb86958)
  16 0x7bf00fbb main+0x8a(argc=0x2, argv=0xffb86e54) [/home/marcel/Downloads/wine-1.4/loader/main.c:230] in <wine-loader> (0xffb86da8)
  17 0xf74fcbd6 __libc_start_main+0xe5() in libc.so.6 (0xffb86e28)
0x005d9819: cmpl	$0,0x3c(%eax)
Modules:
Module	Address			Debug info	Name (108 modules)
PE	  400000- 2100ec2	Export          iw3sp
PE	 2110000- 247f000	Deferred        d3dx9_34
PE	 c5f0000- c601000	Deferred        msseax.flt
PE	10000000-10016000	Deferred        mileseq.flt
PE	18000000-18033000	Deferred        binkw32
PE	21100000-21197000	Deferred        mss32
PE	22300000-22306000	Deferred        mssds3d.flt
PE	24100000-24112000	Deferred        mssdsp.flt
PE	26400000-2642a000	Deferred        mssvoice.asi
PE	26f00000-26f20000	Deferred        mssmp3.asi
ELF	7b800000-7b8f8000	Dwarf           kernel32<elf>
  \-PE	7b810000-7b8f8000	\               kernel32
ELF	7bc00000-7bcc2000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcc2000	\               ntdll
ELF	7bf00000-7bf04000	Dwarf           <wine-loader>
ELF	7ce66000-7ce85000	Deferred        libgcc_s.so.1
ELF	7d6a2000-7d6a9000	Deferred        libogg.so.0
ELF	7d6a9000-7d6d2000	Deferred        libvorbis.so.0
ELF	7d6d2000-7d7ce000	Deferred        libvorbisenc.so.2
ELF	7d7ce000-7d81b000	Deferred        libflac.so.8
ELF	7d81b000-7d854000	Deferred        libdbus-1.so.3
ELF	7d854000-7d8bc000	Deferred        libsndfile.so.1
ELF	7d8bc000-7d8c5000	Deferred        libwrap.so.0
ELF	7d8c5000-7d910000	Deferred        libpulsecommon-0.9.21.so
ELF	7d910000-7d952000	Deferred        libpulse.so.0
ELF	7d952000-7da1a000	Deferred        libasound.so.2
ELF	7da1a000-7da46000	Deferred        winealsa<elf>
  \-PE	7da20000-7da46000	\               winealsa
ELF	7da46000-7dc71000	Deferred        swrast_dri.so
ELF	7dd50000-7dd56000	Deferred        libxtst.so.6
ELF	7dd56000-7de49000	Deferred        oleaut32<elf>
  \-PE	7dd70000-7de49000	\               oleaut32
ELF	7de49000-7de6c000	Deferred        mmdevapi<elf>
  \-PE	7de50000-7de6c000	\               mmdevapi
ELF	7de6c000-7deaf000	Deferred        dsound<elf>
  \-PE	7de70000-7deaf000	\               dsound
ELF	7deaf000-7deb8000	Deferred        librt.so.1
ELF	7deb8000-7dec3000	Deferred        libdrm.so.2
ELF	7dec3000-7dec7000	Deferred        libxdamage.so.1
ELF	7dec7000-7df2c000	Deferred        libgl.so.1
ELF	7df36000-7df3d000	Deferred        libasound_module_pcm_pulse.so
ELF	7df48000-7df7c000	Deferred        uxtheme<elf>
  \-PE	7df50000-7df7c000	\               uxtheme
ELF	7df92000-7df9c000	Deferred        libxcursor.so.1
ELF	7e01a000-7e041000	Deferred        libexpat.so.1
ELF	7e041000-7e071000	Deferred        libfontconfig.so.1
ELF	7e071000-7e07f000	Deferred        libxi.so.6
ELF	7e07f000-7e085000	Deferred        libxfixes.so.3
ELF	7e085000-7e089000	Deferred        libxcomposite.so.1
ELF	7e089000-7e091000	Deferred        libxrandr.so.2
ELF	7e091000-7e09b000	Deferred        libxrender.so.1
ELF	7e09b000-7e0a1000	Deferred        libxxf86vm.so.1
ELF	7e0a1000-7e0a5000	Deferred        libxinerama.so.1
ELF	7e0a5000-7e0c7000	Deferred        imm32<elf>
  \-PE	7e0b0000-7e0c7000	\               imm32
ELF	7e0c7000-7e0cd000	Deferred        libxdmcp.so.6
ELF	7e0cd000-7e0d1000	Deferred        libxau.so.6
ELF	7e0d1000-7e0eb000	Deferred        libxcb.so.1
ELF	7e0eb000-7e0f0000	Deferred        libuuid.so.1
ELF	7e0f0000-7e20d000	Deferred        libx11.so.6
ELF	7e20d000-7e21d000	Deferred        libxext.so.6
ELF	7e21d000-7e236000	Deferred        libice.so.6
ELF	7e236000-7e23f000	Deferred        libsm.so.6
ELF	7e23f000-7e2d3000	Deferred        winex11<elf>
  \-PE	7e250000-7e2d3000	\               winex11
ELF	7e2d3000-7e2e8000	Deferred        libz.so.1
ELF	7e2e8000-7e35e000	Deferred        libfreetype.so.6
ELF	7e37a000-7e408000	Deferred        msvcrt<elf>
  \-PE	7e390000-7e408000	\               msvcrt
ELF	7e408000-7e440000	Deferred        d3d9<elf>
  \-PE	7e410000-7e440000	\               d3d9
ELF	7e463000-7e48b000	Deferred        msacm32<elf>
  \-PE	7e470000-7e48b000	\               msacm32
ELF	7e48b000-7e502000	Deferred        rpcrt4<elf>
  \-PE	7e4a0000-7e502000	\               rpcrt4
ELF	7e502000-7e60a000	Deferred        ole32<elf>
  \-PE	7e520000-7e60a000	\               ole32
ELF	7e60a000-7e6b7000	Deferred        winmm<elf>
  \-PE	7e610000-7e6b7000	\               winmm
ELF	7e6b7000-7e7ac000	Deferred        comctl32<elf>
  \-PE	7e6c0000-7e7ac000	\               comctl32
ELF	7e7ac000-7e817000	Deferred        shlwapi<elf>
  \-PE	7e7c0000-7e817000	\               shlwapi
ELF	7e817000-7ea28000	Deferred        shell32<elf>
  \-PE	7e820000-7ea28000	\               shell32
ELF	7ea28000-7ea89000	Deferred        advapi32<elf>
  \-PE	7ea30000-7ea89000	\               advapi32
ELF	7ea89000-7eb47000	Deferred        gdi32<elf>
  \-PE	7eaa0000-7eb47000	\               gdi32
ELF	7eb47000-7ec87000	Deferred        user32<elf>
  \-PE	7eb60000-7ec87000	\               user32
ELF	7ec87000-7edc0000	Deferred        wined3d<elf>
  \-PE	7ec90000-7edc0000	\               wined3d
ELF	7edc0000-7ee27000	Deferred        ddraw<elf>
  \-PE	7edd0000-7ee27000	\               ddraw
ELF	7ee27000-7ee33000	Deferred        libnss_files.so.2
ELF	7ee33000-7ee3d000	Deferred        libnss_nis.so.2
ELF	7ee3d000-7ee45000	Deferred        libnss_compat.so.2
ELF	7ee48000-7ee61000	Deferred        version<elf>
  \-PE	7ee50000-7ee61000	\               version
ELF	7efbe000-7efe4000	Deferred        libm.so.6
ELF	7efe5000-7effc000	Deferred        libnsl.so.1
ELF	f74e2000-f74e6000	Deferred        libdl.so.2
ELF	f74e6000-f763f000	Dwarf           libc.so.6
ELF	f7640000-f7659000	Deferred        libpthread.so.0
ELF	f7675000-f77b6000	Dwarf           libwine.so.1
ELF	f77b8000-f77d6000	Deferred        ld-linux.so.2
ELF	f77d6000-f77d7000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000002d    0
	0000002c    0
	00000026    0
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
00000021 PnkBstrA.exe
	00000028    0
	00000025    0
	00000022    0
00000023 explorer.exe
	00000024    0
00000029 PnkBstrB.exe
	0000002e    0
	0000002b    0
	0000002a    0
0000002f (D) Z:\media\Spiele\Spiele\Call of Duty 4 - Modern Warfare\iw3sp.exe
	0000003a    0
	00000039    0
	00000038    0
	00000037   15
	00000036   15
	00000032    0
	00000031    1
	00000030    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 2.6.32-41-generic


```

I Know that it works anyhow because i already got it installed, but i can't find a solution for this error!

My PC:

Intel Core 2 Duo E7300 @2.66GHz
2x1024MB DDR2-667
Sapphire Radeon HD 3870 (latest catalyst driver from the AMD-Website installed)
Western Digital Caviar green 640GB

I have 2 1280x1024 screens here and in the catalyst i set "Extend displays" so i got one big desktop with Compiz-effects like Wobbly windows, but i already had that when i played it the last time so i don't think it's compiz wich makes problems!

also if i ran Portal2.exe the game started without problems, but now when i start it now nothing happens!

I hope you can help me, if i get CoD, portal 2 and skyrim to run i will delete my crappy windows 7 and use ubuntu as only OS, but only if this games run!

greets from germany :)

---

### Post by Cavsfan on 2012-07-06
My son plays COD Black Ops, GTA4, Crysis, etc. and he could never get it to work with wine. 
That is why I left windows 7 on here.
COD Black Ops requires Directx 11 and I don't think wine will work for that.
Just my 2 cents. :)

---

### Post by HeavyHDx on 2012-07-06
> **Cavsfan said:**
> My son plays COD Black Ops, GTA4, Crysis, etc. and he could never get it to work with wine. 
That is why I left windows 7 on here.
COD Black Ops requires Directx 11 and I don't think wine will work for that.
Just my 2 cents. :)

Black Ops uses DirectX9 (like all CoDs until BO2) and CoD4 definetly to!

there are a lot of gameplay-videos just like this:

[http://www.youtube.com/watch?v=7t9sZEdeMuI](http://www.youtube.com/watch?v=7t9sZEdeMuI)

It has to work anyhow :/

btw:

Black ops:

[http://www.youtube.com/watch?v=cVWY7v4HqBs](http://www.youtube.com/watch?v=cVWY7v4HqBs)

GTA4:
[http://youtu.be/KVTLOaNGt2I](http://youtu.be/KVTLOaNGt2I)

Crysis 2:

[http://youtu.be/pd8EFBa9knU](http://youtu.be/pd8EFBa9knU)

---

### Post by Dlambert on 2012-07-06
I ran Black Ops on my Linux rig.

---

### Post by Dlambert on 2012-07-06
Anyway Use the installer from PlayOnLinux. :popcorn:

---

### Post by HeavyHDx on 2012-07-06
Well, how do do that? I don't get it run with Playonlinux :/

---

