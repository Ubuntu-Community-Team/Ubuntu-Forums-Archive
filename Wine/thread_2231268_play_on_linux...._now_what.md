---
title: "play on linux.... now what :|"
date: 2014-06-24
forum: Wine
---

### Post by deezdrama on 2014-06-24
sorry guys im a complete linux noob.

so far ive installed latest ubuntu

installed steam...

Played rust and it ran like crap so got help here and changed video driver to a nvidia one....

rust ran great...

then- I seen terraria on sale for $1.99 and had to get it on steam, so now im trying to figure out how to play it.

I cant find any info or tutorials except for old ones from several years ago that just deal with wine.

Anyway... I installed play on linux, it gave me a message that a nvidia driver had to be deleted (will this affect my gaming now?) I clicked continue, It installed and the about 3/4 of the way my software center turned grey and hung up, I exited and re opened it and it finished installing so I assume that went ok.
Now I have playon linux installed but no idea what to do now?

do i have to install steam again from POL? or run it from POL somehow?

any help or tutorials out there?

thanks

---

### Post by sandyd on 2014-06-24
Try running this in the terminal (fix from [AskUbuntu]("http://askubuntu.com/questions/449507/nvidia-libopencl1-331-has-to-be-removed-before-installing-wine"))
```

sudo apt-get remove wine
sudo apt-get install nvidia-libopencl1-331
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install nvidia-cuda-toolkit
sudo apt-get install ocl-icd-opencl-dev
sudo apt-get install wine1.6 winetricks
```
That should give you back your nvidia drivers, install WINE and winetricks

Then, we can install steam (taken from [WineHQ Page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=29123"))
Just go through the installs as if it was on Windows
```

winetricks dotnet40 
winetricks xna40
winetricks --no-isolate steam
```

Open steam, login, and install terraria

---

### Post by deezdrama on 2014-06-24
so i still need to install wine? I thought POL was a frontend that handled all the wine installs and settings?
Whats winetricks? 

Also... will I end up with 2 installs of steam? one for linux and one that i run with wine to handle the window based games?

This is all overwhelming... im a 20 year windows user but just tired of windows crap and vulnerability so vowed to stay with linux this time.

I just wish there was more (and easier to find) tutorials for stuff like this

thanks

---

### Post by sandyd on 2014-06-24
> **deezdrama said:**
> so i still need to install wine? I thought POL was a frontend that handled all the wine installs and settings?
Whats winetricks? 

Also... will I end up with 2 installs of steam? one for linux and one that i run with wine to handle the window based games?

This is all overwhelming... im a 20 year windows user but just tired of windows crap and vulnerability so vowed to stay with linux this time.

I just wish there was more (and easier to find) tutorials for stuff like this

thanksYou need to reinstall it in that order to get the nvidia drivers back - its an apparent bug. This install process still causes steam to run on WINE, so there wont be two versions of Steam unless you installed steam for Linux (which will only play native linux games)

Winetricks allows us to install some windows libraries and required programs in WINE easily.

Play On Linux is a frontend to WINE - though I dont use POL, so I just referenced the instructions from the WINE page. You can just use the instructions in the first code block if you want to use POL instead of using WINE directly

---

### Post by deezdrama on 2014-06-24
I installed POL
Installed steam thru POL
i let steam update then signed in
Installed terraria
it then installed that xna 4
clicked play and a wine message popped up saying terraria exe encountered an error and closed

arggggg ](*,)

---

### Post by deezdrama on 2014-06-24
details of the error......


```

Unhandled exception: page fault on write access to 0xa3e3e822 in 32-bit code (0x02bbe600).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:02bbe600 ESP:0033f6c0 EBP:0033f6e4 EFLAGS:00010202(  R- --  I   - - - )
 EAX:02bbe568 EBX:00000000 ECX:02baa088 EDX:02bbe600
 ESI:036bb270 EDI:0eb43a20
Stack dump:
0x0033f6c0:  0272d752 02bbe568 070f98bb 024c4f00
0x0033f6d0:  036bb270 036bb270 0033fef0 0275f6b8
0x0033f6e0:  ffffffff 0033f724 0246210c 02bbe568
0x0033f6f0:  036bb270 00000200 00000200 024619b8
0x0033f700:  00192370 00192260 01cadaa0 024620ec
0x0033f710:  01cadaa0 0eb43a20 024c4f00 0033f724
Backtrace:
=>0 0x02bbe600 (0x0033f6e4)
  1 0x0246210c (0x0033f724)
  2 0x024619b8 (0x0033f7e8)
  3 0x0246155c (0x0033f828)
  4 0x02460ca4 (0x0033f8a8)
  5 0x02458c94 (0x0033f978)
  6 0x024589b4 (0x0033f998)
  7 0x024585d9 (0x0033fa18)
  8 0x024584ec (0x0033fa38)
  9 0x023c4d90 (0x0033fad8)
  10 0x023c50ef (0x0033fb08)
  11 0x6d50bc26 mono_jit_runtime_invoke+0xb5(method=0x1e91f8, obj=0x0(nil), params=0x33fbbc, exc=(nil)) [/home/meh/work/wine-mono-0.0.8/build-cross-x86/mono/mini/../../../mono/mono/mini/mini.c:5957] in libmono-2.0-x86 (0x00000000)
  12 0x6d65549f mono_runtime_invoke+0x3e(method=0x1e91f8, obj=0x0(nil), params=0x33fbbc, exc=(nil)) [/home/meh/work/wine-mono-0.0.8/build-cross-x86/mono/metadata/../../../mono/mono/metadata/object.c:2823] in libmono-2.0-x86 (0x024c6f20)
  13 0x6d657256 mono_runtime_exec_main+0xd5(method=0x1e91f8, args=0x1ca9e20, exc=(nil)) [/home/meh/work/wine-mono-0.0.8/build-cross-x86/mono/metadata/../../../mono/mono/metadata/object.c:4027] in libmono-2.0-x86 (0x024c6f20)
  14 0x7ebdb066 _CorExeMain+0x3b5() in mscoree (0x0033fe58)
  15 0x7b8610fc call_process_entry+0xb() in kernel32 (0x0033fe78)
  16 0x7b864c0b in kernel32 (+0x54c0a) (0x0033feb8)
  17 0x7bc756b0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  18 0x7bc7590d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  19 0x7bc7568e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  20 0x7bc4d99e in ntdll (+0x3d99d) (0x0033ffe8)
0x02bbe600: movb    %ah,0xa12802ba(%eax)
Modules:
Module    Address            Debug info    Name (143 modules)
PE      400000-  7d0000    Deferred        terraria
PE     20b0000- 2382000    Deferred        mscorlib
PE     2630000- 2648000    Deferred        microsoft.xna.framework.game
PE     2650000- 271c000    Deferred        system.core
PE     2720000- 278c000    Deferred        microsoft.xna.framework.graphicsC:\windows\Microsoft.NET\assembly\GAC_32\Microsoft.Xna.Framework.Graphics\v4.0_4.0.0.0__842cf8be1de50553\Microsoft.Xna.Framework.Graphics.dll
PE     2790000- 2baa000    Deferred        d3dx9_41
PE     2ce0000- 2d8a000    Deferred        microsoft.xna.framework
PE     2d90000- 2d97000    Deferred        x3daudio1_7
PE     2da0000- 2f68000    Deferred        system
PE     2f70000- 2f86000    Deferred        microsoft.xna.framework.xact
PE     30c0000- 30e4000    Deferred        system.configuration
PE     30f0000- 3236000    Deferred        system.xml
PE     32d0000- 35ba000    Deferred        system.windows.forms
PE     35c0000- 3634000    Deferred        system.drawing
PE     3640000- 364a000    Deferred        accessibility
PE     dad0000- dadc000    Deferred        microsoft.xna.framework.input.toC:\windows\Microsoft.NET\assembly\GAC_MSIL\Microsoft.Xna.Framework.Input.Touch\v4.0_4.0.0.0__842cf8be1de50553\Microsoft.Xna.Framework.Input.Touch.dll
PE     dae0000- db16000    Deferred        mono.posix
PE     dd90000- de64000    Deferred        steam
PE    10000000-100bc000    Deferred        gameoverlayrenderer
PE    30000000-302c1000    Deferred        steam2
PE    38000000-38896000    Deferred        steamclient
PE    3b400000-3b41f000    Deferred        steam_api
PE    3f000000-3f0b2000    Deferred        tier0_s
PE    3f600000-3f64f000    Deferred        vstdlib_s
PE    60000000-60021000    Deferred        cserhelper
PE    6d500000-6df26000    Dwarf           libmono-2.0-x86
PE    78050000-780b9000    Deferred        msvcp100
PE    78aa0000-78b5e000    Deferred        msvcr100
ELF    795bc000-7b800000    Deferred        libnvidia-glcore.so.331.38
ELF    7b800000-7b904000    Dwarf           kernel32<elf>
  \-PE    7b810000-7b904000    \               kernel32
ELF    7bc00000-7bcc7000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc7000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7d2fc000-7d400000    Deferred        libgl.so.1
ELF    7d54a000-7d54e000    Deferred        libnvidia-tls.so.331.38
ELF    7d54e000-7d56b000    Deferred        libgcc_s.so.1
ELF    7d588000-7d5fc000    Deferred        libgcrypt.so.11
ELF    7d5fc000-7d60c000    Deferred        libtasn1.so.3
ELF    7d60c000-7d6a4000    Deferred        libgnutls.so.26
ELF    7d6a4000-7d6ce000    Deferred        netapi32<elf>
  \-PE    7d6b0000-7d6ce000    \               netapi32
ELF    7d6ce000-7d6fc000    Deferred        secur32<elf>
  \-PE    7d6d0000-7d6fc000    \               secur32
ELF    7d6fc000-7d739000    Deferred        winspool<elf>
  \-PE    7d700000-7d739000    \               winspool
ELF    7d739000-7d7a2000    Deferred        setupapi<elf>
  \-PE    7d740000-7d7a2000    \               setupapi
ELF    7d7a2000-7d7ba000    Deferred        libresolv.so.2
ELF    7d7ba000-7d7be000    Deferred        libgpg-error.so.0
ELF    7d7be000-7d7d7000    Deferred        imagehlp<elf>
  \-PE    7d7c0000-7d7d7000    \               imagehlp
ELF    7d7d7000-7d7fa000    Deferred        iphlpapi<elf>
  \-PE    7d7e0000-7d7fa000    \               iphlpapi
ELF    7d7fa000-7d8b7000    Deferred        crypt32<elf>
  \-PE    7d800000-7d8b7000    \               crypt32
ELF    7d8b7000-7d938000    Deferred        gdiplus<elf>
  \-PE    7d8d0000-7d938000    \               gdiplus
ELF    7d938000-7d9de000    Deferred        windowscodecs<elf>
  \-PE    7d950000-7d9de000    \               windowscodecs
ELF    7d9de000-7dab4000    Deferred        opengl32<elf>
  \-PE    7da00000-7dab4000    \               opengl32
ELF    7dab4000-7dbe1000    Deferred        wined3d<elf>
  \-PE    7dac0000-7dbe1000    \               wined3d
ELF    7dbe1000-7dc17000    Deferred        d3d9<elf>
  \-PE    7dbf0000-7dc17000    \               d3d9
ELF    7dc17000-7dc33000    Deferred        fusion<elf>
  \-PE    7dc20000-7dc33000    \               fusion
ELF    7dc33000-7dd4e000    Deferred        oleaut32<elf>
  \-PE    7dc50000-7dd4e000    \               oleaut32
ELF    7dd4e000-7dd7e000    Deferred        ws2_32<elf>
  \-PE    7dd60000-7dd7e000    \               ws2_32
ELF    7dd7e000-7dd92000    Deferred        mswsock<elf>
  \-PE    7dd80000-7dd92000    \               mswsock
ELF    7dd92000-7de2a000    Deferred        msvcrt<elf>
  \-PE    7ddb0000-7de2a000    \               msvcrt
ELF    7de41000-7de74000    Deferred        uxtheme<elf>
  \-PE    7de50000-7de74000    \               uxtheme
ELF    7de74000-7de7a000    Deferred        libxfixes.so.3
ELF    7de7a000-7de85000    Deferred        libxcursor.so.1
ELF    7de85000-7de96000    Deferred        libxi.so.6
ELF    7de96000-7de9a000    Deferred        libxcomposite.so.1
ELF    7de9a000-7dea5000    Deferred        libxrandr.so.2
ELF    7dea5000-7deb0000    Deferred        libxrender.so.1
ELF    7deb0000-7deb6000    Deferred        libxxf86vm.so.1
ELF    7deb6000-7deba000    Deferred        libxinerama.so.1
ELF    7deba000-7dec1000    Deferred        libxdmcp.so.6
ELF    7dec1000-7dec5000    Deferred        libxau.so.6
ELF    7dec5000-7dee7000    Deferred        libxcb.so.1
ELF    7dee7000-7deed000    Deferred        libuuid.so.1
ELF    7deed000-7e021000    Deferred        libx11.so.6
ELF    7e021000-7e034000    Deferred        libxext.so.6
ELF    7e034000-7e04e000    Deferred        libice.so.6
ELF    7e04e000-7e057000    Deferred        libsm.so.6
ELF    7e074000-7e0ff000    Deferred        winex11<elf>
  \-PE    7e080000-7e0ff000    \               winex11
ELF    7e13c000-7e165000    Deferred        libexpat.so.1
ELF    7e165000-7e1a0000    Deferred        libfontconfig.so.1
ELF    7e1a0000-7e1c8000    Deferred        libpng12.so.0
ELF    7e1c8000-7e268000    Deferred        libfreetype.so.6
ELF    7e285000-7e2a7000    Deferred        imm32<elf>
  \-PE    7e290000-7e2a7000    \               imm32
ELF    7e2a7000-7e2cf000    Deferred        msacm32<elf>
  \-PE    7e2b0000-7e2cf000    \               msacm32
ELF    7e2cf000-7e37f000    Deferred        winmm<elf>
  \-PE    7e2e0000-7e37f000    \               winmm
ELF    7e37f000-7e3f7000    Deferred        rpcrt4<elf>
  \-PE    7e390000-7e3f7000    \               rpcrt4
ELF    7e3f7000-7e50b000    Deferred        ole32<elf>
  \-PE    7e410000-7e50b000    \               ole32
ELF    7e50b000-7e601000    Deferred        comctl32<elf>
  \-PE    7e510000-7e601000    \               comctl32
ELF    7e601000-7e619000    Deferred        version<elf>
  \-PE    7e610000-7e619000    \               version
ELF    7e619000-7e67f000    Deferred        advapi32<elf>
  \-PE    7e630000-7e67f000    \               advapi32
ELF    7e67f000-7e785000    Deferred        gdi32<elf>
  \-PE    7e690000-7e785000    \               gdi32
ELF    7e785000-7e8ca000    Deferred        user32<elf>
  \-PE    7e7a0000-7e8ca000    \               user32
ELF    7e8ca000-7e939000    Deferred        shlwapi<elf>
  \-PE    7e8e0000-7e939000    \               shlwapi
ELF    7e939000-7eb50000    Deferred        shell32<elf>
  \-PE    7e950000-7eb50000    \               shell32
ELF    7eb50000-7eb63000    Deferred        psapi<elf>
  \-PE    7eb60000-7eb63000    \               psapi
ELF    7eb63000-7ebc1000    Deferred        dbghelp<elf>
  \-PE    7eb70000-7ebc1000    \               dbghelp
ELF    7ebc1000-7ebf2000    Dwarf           mscoree<elf>
  \-PE    7ebd0000-7ebf2000    \               mscoree
ELF    7ebf2000-7ebff000    Deferred        libnss_files.so.2
ELF    7ebff000-7ec0b000    Deferred        libnss_nis.so.2
ELF    7ec0b000-7ec24000    Deferred        libnsl.so.1
ELF    7ec24000-7ec2d000    Deferred        libnss_compat.so.2
ELF    7ef9d000-7efe3000    Deferred        libm.so.6
ELF    7efec000-7f000000    Deferred        libz.so.1
ELF    f7424000-f7429000    Deferred        libdl.so.2
ELF    f7429000-f75d8000    Deferred        libc.so.6
ELF    f75d8000-f75f4000    Deferred        libpthread.so.0
ELF    f75f7000-f7600000    Deferred        librt.so.1
ELF    f7612000-f7753000    Dwarf           libwine.so.1
ELF    f7755000-f7777000    Deferred        ld-linux.so.2
ELF    f7777000-f7778000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001e    0
    0000001d    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    00000020    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    0000001f    0
    0000001c    0
    0000001b    0
00000022 explorer.exe
    00000023    0
00000031 Steam.exe
    0000004b    0
    0000002c    0
    00000017    0
    00000045    0
    00000028    0
    00000030    0
    0000002f    0
    0000002e    0
    00000029    0
    0000002a    0
    0000002b    0
    00000018    0
    00000009    0
    00000021    0
    00000025    0
    0000000b    0
    0000000d    0
    0000000c    0
    00000047    0
    00000046    0
    00000044    0
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003f    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
    00000036    0
    00000032    0
00000064 (D) C:\Program Files\Steam\SteamApps\common\Terraria\Terraria.exe
    00000063    0
    0000004a    0
    00000049    0 <==
System information:
    Wine build: wine-1.5.25
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-29-generic
```

---

### Post by deezdrama on 2014-06-24
i went back and from POL i installed net framework 4 and xinput like i seen on a youtube vid...

terraria opened fine and i made my character, when i went to name it as soon as i pressed a key, the system froze and had to power down the pc.

I remember reading someone else had this same exact issue but cant remember what he did to fix it, i think it was something to do with disabling the steam overlay or something... anyone know?

---

### Post by deezdrama on 2014-06-24
I disabled steam overlay and WOW... its running great!

yay lol Im getting closer and closer to never going back to Windows again!


So.... do other games just install the same way?
like dayz? do i just install and play or will there be other needed files?

---

### Post by bapoumba on 2014-06-24
*Thread moved to **Wine**.*

---

