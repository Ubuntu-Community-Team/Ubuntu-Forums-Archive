---
title: "Black screen on Half life 2"
date: 2007-08-04
forum: Wine
---

### Post by toontastic on 2007-08-04
I'm pretty new to Ubuntu but really want the likes of CSS to work. I think I have installed it correctly through wine and I've managed to load up steam. It has done whatever updates it has to and I am able to launch the game. I get the screen with the loading image in the bottom right then I just get a black screen.

Before that screen I get an error saying Video Driver Outdated.

Your video drivers appear to be out of date and could cause problems if you choose to continue and run the game. We strongly recommend that you follow the link below and update your video drivers to the latest version available from your driver vendor.

Your dirver details:

Windows verson: Windows XP
Description Direct3D HAL
version 6.14.0.9

I'm using ATI 8500XT graphics card.

---

### Post by mr. Twitch on 2007-08-17
im getting the exact same problem

im using an ATi X1900CF Graphics card.

---

### Post by muted1 on 2008-02-26
I seem to have the same problem. I'm thinking that it is something to do with the video drivers. I'm not sure at all though.

---

### Post by diobrando on 2008-05-09
Same issue here, and with a geforce 7950 gx2 SLI.

---

### Post by ale55andro on 2008-05-14
same problem: ATI Mobility Radeon X300

---

### Post by SuperNapalm on 2008-05-14
One thing you can try is this:

Right click the game and select properties and then game launch options. Type in the following

```
-dxlevel 70 -window
```

Loading up the game with that and the defult settings seem to work, but of course this is my PC.

Specs:
3.4ghz Duel Core Intel
1gb ram
Sapphire Radeon x1650 PRO

Bottom line, you will not get HL2 or CSS working as well as it does in Windows, not until Valve finish porting the source engine to Linux (can't confirm that for sure but i've seen reports they are in fact doing it).

---

### Post by aoanla on 2008-05-14
Hrm. Steam used to do that to me ages ago, with a much-older-than-current version of Wine, and a much-older-than-current version of the ATI fglrx drivers.

I assume you all are using the newest video drivers for your cards, and the newest release of Wine?

---

### Post by Zypher on 2008-05-14
I was having this issue, turn your graphic settings all the way down.

---

### Post by Sleaka J on 2008-05-15
It's caused by AA. If you use a -window Launch Option and turn off AA, you shouldn't get any more black screens on startup.

---

### Post by ExRarne on 2008-05-15
What is AA, and how do I disable it?

---

### Post by noerrorsfound on 2008-05-15
> **ExRarne said:**
> What is AA, and how do I disable it?
AA stands for [anti-aliasing]("http://en.wikipedia.org/wiki/Anti-aliasing"). It smooths the jagged edges of graphics. You can disable it from the ingame video options menu, or with the command **mat_antialias 0** which goes in the game's console (accessed ingame with tilde [~] but I remember you sometimes having to enable "developer console" in the controls menu before the key works). You can also make an **autoexec.cfg** file in **Program Files\Valve\Steam\SteamApps\yourusername\Half-Life\hl2\cfg** (not so sure about the directory) and include the command.

---

### Post by evil_urna on 2008-06-20
I am haveing this same problem. I am running wine version 1.0 on ubuntu version 8.04. I can boot the game. I get the valve movie and it is VERY choppy. Sometimes I get sound sometimes I dont. Then it goes fullscreen for a time, then it goes black. I get cursor but no picture. This is very frustrating. I have tried everything I could find on the net and it did not help. 

I am really close to just giving up on linux all together. I have nothing but problems. Sometimes I can find help but for the most part not. And whenever I ask for help on here I get no response or very little of one.

Please someone out there have any idea on what it could be.

---

### Post by evil_urna on 2008-06-23
Bumping dis 

also I tried a fresh install of ubuntu 8.04 and wine 1.0. Just in case of any conflicts. And I am still stuck in black screen hell

Edit: When I try to run HL2 with the -window -dxlevel 81 -novid -heapsize 512000 settings it will go to the loading screen for the main menu with the blurry background and whatnot and after about 2 min there it will crash out with this error.

```
wine: Unhandled page fault on write access to 0x00000022 at address 0xe058a37 (thread 0023), starting debugger...
Unhandled exception: page fault on write access to 0x00000022 in 32-bit code (0x0e058a37).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0e058a37 ESP:0033e574 EBP:00000004 EFLAGS:00210216(   - 00      -RIAP1)
 EAX:00000000 EBX:07ed0070 ECX:0e06a9d0 EDX:0e0667b8
 ESI:00000700 EDI:0e06a9d0
Stack dump:
0x0033e574:  00000090 0e06a9d0 00000004 0121fff4
0x0033e584:  0e059d32 07ed0070 00000730 161b0074
0x0033e594:  0e06a9d0 0121fff4 0e05a084 161b0074
0x0033e5a4:  00000730 161b0074 0e06a9f0 0e06a9d0
0x0033e5b4:  0e0586ca 161b0074 ffffffff 0033e60c
0x0033e5c4:  00000008 0033ff08 00000000 003c70bb
Backtrace:
0x0e058a37: addw	$0xffff,0x22(%eax)
Modules:
Module	Address			Debug info	Name (142 modules)
PE	  3c0000-  3ee000	Deferred        launcher
PE	  3f0000-  400000	Deferred        steam_api
PE	  400000-  41c000	Deferred        hl2
PE	 1160000- 1194000	Deferred        tier0
PE	 11a0000- 11c0000	Deferred        vstdlib
PE	 dad0000- db06000	Deferred        filesystem_steam
PE	 db10000- db1e000	Deferred        unicode
PE	 dd80000- de58000	Deferred        datamodel
PE	 df70000- df99000	Deferred        dmserializers
PE	 dfa0000- e045000	Deferred        materialsystem
PE	 e050000- e071000	Export          datacache
PE	 e080000- e095000	Deferred        valve_avi
PE	 e1b0000- e274000	Deferred        vguimatsurface
PE	 e280000- e2e7000	Deferred        vgui2
PE	 e2f0000- e31f000	Deferred        soundemittersystem
PE	 e650000- e678000	Deferred        stdshader_dbg
PE	 e680000- e6b3000	Deferred        stdshader_dx6
PE	 e6c0000- e6e7000	Deferred        stdshader_dx7
PE	 e6f0000- e72f000	Deferred        stdshader_dx8
PE	 e730000- e76f000	Deferred        stdshader_dx9
PE	 ef80000- f13d000	Deferred        gameui
PE	 ff10000- ff20000	Deferred        vaudio_miles
PE	10000000-1003a000	Deferred        gameoverlayrenderer
PE	117a0000-118b4000	Deferred        serverbrowser
PE	20000000-2064b000	Deferred        engine
PE	21100000-21164000	Deferred        mss32
PE	22000000-2263d000	Deferred        server
PE	24000000-24388000	Deferred        client
PE	26000000-26126000	Deferred        vphysics
PE	26400000-26439000	Deferred        mssvoice.asi
PE	26f00000-26f2e000	Deferred        mssmp3.asi
PE	2a000000-2a09f000	Deferred        shaderapidx9
PE	2c000000-2c2d8000	Deferred        studiorender
PE	30000000-302e6000	Deferred        steam
PE	60000000-60021000	Deferred        cserhelper
PE	628c0000-628d9000	Deferred        parsifal
ELF	7ab27000-7ab71000	Deferred        dbghelp<elf>
  \-PE	7ab30000-7ab71000	\               dbghelp
ELF	7ad71000-7ad7c000	Deferred        libgcc_s.so.1
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7b94b000-7b960000	Deferred        psapi<elf>
  \-PE	7b950000-7b960000	\               psapi
ELF	7b9e1000-7ba2b000	Deferred        dsound<elf>
  \-PE	7b9f0000-7ba2b000	\               dsound
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bca8000-7bcbc000	Deferred        winejoystick<elf>
  \-PE	7bcb0000-7bcbc000	\               winejoystick
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7cd4a000-7cd61000	Deferred        mcicda<elf>
  \-PE	7cd50000-7cd61000	\               mcicda
ELF	7d10a000-7dc1f000	Deferred        libglcore.so.1
ELF	7dc1f000-7dcc3000	Deferred        libgl.so.1
ELF	7dee5000-7dfe8000	Deferred        wined3d<elf>
  \-PE	7df00000-7dfe8000	\               wined3d
ELF	7dfe8000-7e018000	Deferred        d3d9<elf>
  \-PE	7dff0000-7e018000	\               d3d9
ELF	7e018000-7e039000	Deferred        mpr<elf>
  \-PE	7e020000-7e039000	\               mpr
ELF	7e039000-7e087000	Deferred        wininet<elf>
  \-PE	7e040000-7e087000	\               wininet
ELF	7e087000-7e129000	Deferred        oleaut32<elf>
  \-PE	7e0a0000-7e129000	\               oleaut32
ELF	7e129000-7e13d000	Deferred        midimap<elf>
  \-PE	7e130000-7e13d000	\               midimap
ELF	7e13d000-7e154000	Deferred        msacm32<elf>
  \-PE	7e140000-7e154000	\               msacm32
ELF	7e154000-7e217000	Deferred        libasound.so.2
ELF	7e223000-7e259000	Deferred        winealsa<elf>
  \-PE	7e230000-7e259000	\               winealsa
ELF	7e259000-7e281000	Deferred        msvfw32<elf>
  \-PE	7e260000-7e281000	\               msvfw32
ELF	7e281000-7e313000	Deferred        winmm<elf>
  \-PE	7e290000-7e313000	\               winmm
ELF	7e313000-7e339000	Deferred        msacm32<elf>
  \-PE	7e320000-7e339000	\               msacm32
ELF	7e339000-7e374000	Deferred        avifil32<elf>
  \-PE	7e340000-7e374000	\               avifil32
ELF	7e4a9000-7e50a000	Deferred        rpcrt4<elf>
  \-PE	7e4c0000-7e50a000	\               rpcrt4
ELF	7e50a000-7e5ae000	Deferred        ole32<elf>
  \-PE	7e520000-7e5ae000	\               ole32
ELF	7e60d000-7e640000	Deferred        uxtheme<elf>
  \-PE	7e610000-7e640000	\               uxtheme
ELF	7e640000-7e6ff000	Deferred        comctl32<elf>
  \-PE	7e650000-7e6ff000	\               comctl32
ELF	7e6ff000-7e812000	Deferred        shell32<elf>
  \-PE	7e710000-7e812000	\               shell32
ELF	7e812000-7e86b000	Deferred        shlwapi<elf>
  \-PE	7e820000-7e86b000	\               shlwapi
ELF	7e86b000-7e87f000	Deferred        lz32<elf>
  \-PE	7e870000-7e87f000	\               lz32
ELF	7e87f000-7e898000	Deferred        version<elf>
  \-PE	7e880000-7e898000	\               version
ELF	7e898000-7e8ab000	Deferred        libresolv.so.2
ELF	7e8b7000-7e8d5000	Deferred        iphlpapi<elf>
  \-PE	7e8c0000-7e8d5000	\               iphlpapi
ELF	7e8d5000-7e901000	Deferred        ws2_32<elf>
  \-PE	7e8e0000-7e901000	\               ws2_32
ELF	7e901000-7e91b000	Deferred        wsock32<elf>
  \-PE	7e910000-7e91b000	\               wsock32
ELF	7e91b000-7e924000	Deferred        libxcursor.so.1
ELF	7e924000-7e929000	Deferred        libxfixes.so.3
ELF	7e929000-7e92c000	Deferred        libxcomposite.so.1
ELF	7e92c000-7e932000	Deferred        libxrandr.so.2
ELF	7e932000-7e93a000	Deferred        libxrender.so.1
ELF	7e93a000-7e93d000	Deferred        libxinerama.so.1
ELF	7e93d000-7e95d000	Deferred        imm32<elf>
  \-PE	7e940000-7e95d000	\               imm32
ELF	7e95d000-7e962000	Deferred        libxdmcp.so.6
ELF	7e962000-7e97a000	Deferred        libxcb.so.1
ELF	7e97a000-7ea61000	Deferred        libx11.so.6
ELF	7ea61000-7ea6f000	Deferred        libxext.so.6
ELF	7ea6f000-7ea74000	Deferred        libxxf86vm.so.1
ELF	7ea74000-7ea8c000	Deferred        libice.so.6
ELF	7ea8c000-7ea94000	Deferred        libsm.so.6
ELF	7ea9c000-7ea9e000	Deferred        libnvidia-tls.so.1
ELF	7eaa0000-7eb37000	Deferred        winex11<elf>
  \-PE	7eab0000-7eb37000	\               winex11
ELF	7eb51000-7eb72000	Deferred        libexpat.so.1
ELF	7eb72000-7eb9c000	Deferred        libfontconfig.so.1
ELF	7eba8000-7ebbd000	Deferred        libz.so.1
ELF	7ebbd000-7ec2d000	Deferred        libfreetype.so.6
ELF	7ec2e000-7ec31000	Deferred        libxau.so.6
ELF	7ec39000-7ec8b000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec8b000	\               advapi32
ELF	7ec8b000-7ed26000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed26000	\               gdi32
ELF	7ed26000-7ee6d000	Deferred        user32<elf>
  \-PE	7ed40000-7ee6d000	\               user32
ELF	7ee6d000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee82000	Deferred        libnss_nis.so.2
ELF	7ee82000-7ee9a000	Deferred        libnsl.so.1
ELF	7ee9a000-7eea3000	Deferred        libnss_compat.so.2
ELF	7eea3000-7eea5000	Deferred        libxcb-xlib.so.0
ELF	7efcf000-7eff4000	Deferred        libm.so.6
ELF	b7cb3000-b7cb7000	Deferred        libdl.so.2
ELF	b7cb7000-b7e06000	Deferred        libc.so.6
ELF	b7e06000-b7e1e000	Deferred        libpthread.so.0
ELF	b7e2a000-b7f60000	Deferred        libwine.so.1
ELF	b7f62000-b7f7e000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000050    1
	00000048    1
	00000041    0
	0000003b    0
	00000036    1
	00000031    0
	00000032    1
	00000033    0
	00000030    1
	0000002f    0
	00000027    1
	00000022    0
	0000000b    1
	00000047    0
	00000046    1
	00000040    0
	0000003f    0
	0000003e    0
	0000003d    0
	0000003a    0
	00000039    1
	00000038    0
	00000037    0
	00000035    0
	00000034    1
	0000002e    0
	0000002d   15
	0000002b    0
	0000002a   15
	00000029   15
	00000028    0
	00000026    0
	00000025    0
	00000024    0
	00000021    0
	00000020    1
	0000001f    0
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b    0
	0000001a    0
	00000019    0
	00000018    0
	00000009    0
0000000c 
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
00000013 (D) C:\Program Files\Steam\SteamApps\evil_urna\half-life 2\hl2.exe
	00000051    0
	0000004c    0
	0000004b   15
	0000004a    0
	00000049    0
	0000003c    0
	00000045    2
	00000023    0 <==
Backtrace:

```

Not a single clue what it means.

---

### Post by kevin11951 on 2008-06-23
[SIZE="4"]-dxlevel **81**[/SIZE]

---

### Post by evil_urna on 2008-06-23
> **kevin11951 said:**
> [SIZE="4"]-dxlevel **81**[/SIZE]

Thanks brohiem for the bolded large tag there bit it changes nothing for me.

---

### Post by evil_urna on 2008-06-23
I don't know if this was a good idea or not but I used this guide
[http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html](http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html)
to install DX9 into wine. I read elsewhere that this was a bad move but I did it anyway. 

I am seeming to have some success. It will load in fullscreen but it runs very slow, Even at low settings. I am going to **** around a bit more and see if I can achieve success

This is with the -dxlevel 70 tag.

---

### Post by evil_urna on 2008-06-23
I tried it with no -dxlevel modifier and it will go to the loading screen then crash out. If I use -dxlevel 81 it will crash out and give me that error I posted before. If I use 70 it will load but run like crap. This is starting to get old. 

Anyone have any idea where to go next

---

### Post by evil_urna on 2008-06-23
Still no success. There has to be someone here that has had this same problem and resolved it.

---

### Post by mister_k81 on 2008-07-10
Sorry for bumping this old thread, but I was having the exact same issue as evil_urna. The game would give me a black screen after the Valve logo and run really slowly. 

But after messing around with the game options for a while, I think I found a solution. Unchecking the "Enable Steam Community In-Game" box in the *File > Settings > In-Game* menu in the steam client seemed to have solved my problem. The game runs great now that I disabled this option, and no extra launch options are necessary.

---

