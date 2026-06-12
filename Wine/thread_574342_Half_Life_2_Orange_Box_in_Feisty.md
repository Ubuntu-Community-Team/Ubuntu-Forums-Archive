---
title: "Half Life 2 Orange Box in Feisty"
date: 2007-10-12
forum: Wine
---

### Post by Ghola28 on 2007-10-12
Picked up The Orange Box (Half Life 2, Half Life 2: Episode One, Half Life 2: Episode Two, Portal AND Team Fortress 2 included for $50!) last night and installed everything today.

I used WINE 0.9.41, Ubuntu 32-bit 7.04.  Had to copy all the data from the DVDs onto my harddrive before installing, but everything went smoothly, including installing Steam.

Two hiccups: Steam cut out sound from my machine initially.  I found that playing an .ogg file while Steam loads up made sure sound came through okay.  Also, I changed the audio settings in winecfg to make sure the Alsa driver was selected, with driver emulation turned off.

Portal, Half Life 2, and Team Fortress 2 all play well at 1024 x 768.  

Go WINE!

EDIT: Realized I used an older version of WINE (0.9.41), the one that Automatix installs.

---

### Post by Sockerdrickan on 2007-10-12
That's GREAT to hear thanks

---

### Post by beeldings on 2007-10-12
What are your system details and what kind of performance are you getting? I ask simply because the HL2 demo didn't run that well on my system. I don't know if this can be attributed to the fact that I am not running the game in a native Windows environment or if it is a hardware limitation.

---

### Post by duncan_nz on 2007-10-12
I'm running orange box games just fine on my computer, I get 60 fps average.

8600gts 256
athlon64 3700 cpu
2gig 400mhz ram

---

### Post by beeldings on 2007-10-13
Looks like my performance issues are hardware related.

Running a GeForce 7800 GS AGP, AMD Athlon 64 3200+ with 2 Gb RAM.

---

### Post by Sockerdrickan on 2007-10-13
Why would that hardware be an issue? Maybe the CPU in that case

---

### Post by quadomatic on 2007-10-13
> **beeldings said:**
> Looks like my performance issues are hardware related.

Running a GeForce 7800 GS AGP, AMD Athlon 64 3200+ with 2 Gb RAM.

Really? How fast are you able to play it?

I'm guessing I won't be playing HL2 games in WINE as good as I did in Windows anytime soon, considering my processor is the same as yours (possibly worse, as I have socket 754) and I only have 768 MB of Ram. And of course, my video card :(

---

### Post by oedipuss on 2007-10-13
Really ? I've tried to run portal with wine 0.9.46 and while it does start, the graphics are all garbled up. 
Tried disabling hdr and bloom too, but with no success. 

Any special things you did with wine?

---

### Post by Sockerdrickan on 2007-10-13
I'd like to see screenshots of success!! :popcorn:

---

### Post by quadomatic on 2007-10-13
> **Tux0r said:**
> I'd like to see screenshots of success!! :popcorn:

ditto

What settings are you running it with?

BTW: If it works for you, add test data to WINE AppDB!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9421)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5823](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5823)
Portal needs to be added

---

### Post by kimbrel on 2007-10-15
I can’t get Portal working on Gutsy.
Steam installed fine and downloaded Portal for me, but when I tell it to launch portal, my system changes to 1024x768 and then the Valve logo movie plays in the upper right corner, followed by the Source logo, and then it hangs, and disappears, taking Steam with it. 
Hardware: Thinkpad T60, Core Duo 1.83GHz, 1.5GB RAM, Radeon Mobility X1400 128MB (fglrx is enabled). 
I don’t have any other Steam/Source games to try running, so I’m kind of in the dark here. 
Any ideas?

---

### Post by Ghola28 on 2007-10-16
Here's my hardware:

Intel Core 2 Duo 2.0 GHz
2.0 GB RAM
Nvidia Quadro FX 360M video card

I'm running WINE 0.9.41 (see edit of earlier post) with WinXP as the default.  I've changed the Audio Tab in winecfg to use the Alsa drivers, with Hardware Accleration set to Emulation, the Sample Rate set to 44100, Bits per sample set to 16, and Driver Emulation checked.

I *did* have to copy the Tacoma fonts from a windows install to the windows -> fonts folder in my wine install (so I could see the text in Steam).

I'll post screenshots soon.

---

### Post by Ghola28 on 2007-10-16
> **kimbrel said:**
> I can’t get Portal working on Gutsy.
Steam installed fine and downloaded Portal for me, but when I tell it to launch portal, my system changes to 1024x768 and then the Valve logo movie plays in the upper right corner, followed by the Source logo, and then it hangs, and disappears, taking Steam with it. 
Hardware: Thinkpad T60, Core Duo 1.83GHz, 1.5GB RAM, Radeon Mobility X1400 128MB (fglrx is enabled). 
I don’t have any other Steam/Source games to try running, so I’m kind of in the dark here. 
Any ideas?

What version of Wine are you running?  I think the "official" Ubuntu version is 0.9.41.  If you're running a different version, you might try installing 0.9.41 (from Synaptic, do a search for Wine) and running Steam with that (or re-install Steam in Wine 0.9.41, then run it).

---

### Post by YokoZar on 2007-10-16
> **Ghola28 said:**
> What version of Wine are you running?  I think the "official" Ubuntu version is 0.9.41.  If you're running a different version, you might try installing 0.9.41 (from Synaptic, do a search for Wine) and running Steam with that (or re-install Steam in Wine 0.9.41, then run it).
Automatix is not official.

The Wine package in the Gutsy repository is 0.9.46.  The latest available in the repository at winehq.org is 0.9.47.

---

### Post by etherealmachine on 2007-10-16
I'm finding it impossible to install Half-Life 2 Episode one in Feisty due to DirectX 9.0c. The installer runs fine, but tells me I need to upgrade DirectX. It installs is, then fails. Very annoying since I know it doesn't need DirectX 9 to play. Any way to force it not to install DX9?

---

### Post by superxero044 on 2007-10-16
Yeah when i run the hl2 games they say i have directx 8.1 but I have a 7800 gt.

Any reason why this should be happening? Thanks.

---

### Post by shad0w_walker on 2007-10-16
I have managed to Portal and Team fortress 2 working beautifully here. No noticeable performance issues either. To my knowledge I'm using the stock wine provided with the Gutsy repos. 

I do however have some serious texture issues with HL2: Episode 2 which i find to be weird. Alot of items appear to be showing only one colour channel. So the texture is present but only the red or blue or <insert colour of choice> part of the texture. It also seems to change when i move around or look at it from a different angle.

---

### Post by YokoZar on 2007-10-17
> **etherealmachine said:**
> I'm finding it impossible to install Half-Life 2 Episode one in Feisty due to DirectX 9.0c. The installer runs fine, but tells me I need to upgrade DirectX. It installs is, then fails. Very annoying since I know it doesn't need DirectX 9 to play. Any way to force it not to install DX9?Just tell it not to install DirectX.

---

### Post by pt123 on 2007-10-18
screenshots or it didn't happen

---

### Post by SanCo.ac on 2007-10-19
Could use some help with portal, runs all fine until I start first map and when the countdown reach 00.00.00 the game just freeze, using wine 0.9.47 on Ubuntu Feisty.

Any ideas?

Tried all with and without -gl, dxlevel 81, -window and so on. still happens.

---

### Post by shad0w_walker on 2007-10-19
Have you tried running Portal/Steam from a terminal so you can see any error messages it generates?

---

### Post by SanCo.ac on 2007-10-19
This is spammed all the time

> err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x13b5f8) : Only 1 render targets are supported.

When it freeze I get this

> fixme:d3d:state_clipping Clipping not supported with vertex shaders

and then this

> fixme:font:WineEngRemoveFontResourceEx :stub
wine: Unhandled page fault on read access to 0x6322ba50 at address 0x1d001c (thread 0040), starting debugger...
Unhandled exception: page fault on read access to 0x6322ba50 in 32-bit code (0x001d001c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:001d001c ESP:0034e6f4 EBP:00000000 EFLAGS:00210206(   - 00      - RIP1)
 EAX:001d001c EBX:0dbb5e80 ECX:09b702c0 EDX:09b7d100
 ESI:0dbb5b50 EDI:00000000
Stack dump:
0x0034e6f4:  0db214a8 00000001 0000000a 0034e7c0
0x0034e704:  00400000 ffffffff ffffffff 0dbfebe1
0x0034e714:  0000000f 003d84be 00000003 0034e7c0
0x0034e724:  003d8747 00111000 0034e764 003d873e
0x0034e734:  00111000 01161a40 003d4f45 00000001
0x0034e744:  01051d6d 00000002 00000000 7bc3eb73
Backtrace:
=>1 0x001d001c (0x00000000)
0x001d001c: imull       $0,0xe78c6b00(%esi,%ebx,8),%ecx
Modules:
Module  Address                 Debug info      Name (153 modules)
PE        3d0000-  3fd000       Deferred        launcher
PE        400000-  41a000       Deferred        hl2
PE       1160000- 119b000       Deferred        tier0
PE       11a0000- 11f5000       Deferred        vstdlib
PE       1200000- 1214000       Deferred        steam_api
PE       bf70000- bfb9000       Deferred        filesystem_steam
PE       c1e0000- c7c3000       Deferred        engine
PE       ce60000- ce80000       Deferred        inputsystem
PE       ce80000- cfa1000       Deferred        materialsystem
PE       d3b0000- d3ec000       Deferred        datacache
PE       d3f0000- d7dc000       Deferred        studiorender
PE       da00000- daf0000       Deferred        vphysics
PE       daf0000- db0f000       Deferred        valve_avi
PE       db10000- dbd8000       Deferred        vguimatsurface
PE       dbe0000- dc3d000       Deferred        vgui2
PE       dc40000- ddc8000       Deferred        shaderapidx9
PE       dee0000- def4000       Deferred        xinput1_3
PE       e010000- e041000       Deferred        stdshader_dbg
PE       e050000- e096000       Deferred        stdshader_dx6
PE       e0a0000- e0d5000       Deferred        stdshader_dx7
PE       e0e0000- e144000       Deferred        stdshader_dx8
PE       e150000- e165000       Deferred        unicode
PE       f080000- f0a3000       Deferred        soundemittersystem
PE       f0b0000- f0c7000       Deferred        scenefilecache
PE       f0d0000- f10f000       Deferred        tier0_s
PE       f120000- f14e000       Deferred        nattypeprobe
PE       f6b0000- fbe9000       Deferred        client
PE      10000000-10031000       Deferred        gameoverlayrenderer
PE      10040000-107da000       Deferred        server
PE      15c00000-15dbc000       Deferred        steamclient
PE      15dc0000-15e32000       Deferred        vstdlib_s
PE      15f50000-161eb000       Deferred        p2pcore
PE      161f0000-1634a000       Deferred        p2pvoice
PE      16350000-163fd000       Deferred        mss32_s
PE      16510000-166d9000       Deferred        gameui
PE      172d0000-172e5000       Deferred        vaudio_miles
PE      172f0000-17354000       Deferred        mss32
PE      18000000-18033000       Deferred        binkw32
PE      24950000-24a0b000       Deferred        serverbrowser
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      30000000-30320000       Deferred        steam
PE      60000000-60021000       Deferred        cserhelper
ELF     79e77000-79ec1000       Deferred        dbghelp<elf>
  \-PE  79e80000-79ec1000       \               dbghelp
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b965000-7b99f000       Deferred        shdocvw<elf>
  \-PE  7b970000-7b99f000       \               shdocvw
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c63b000-7c660000       Deferred        netapi32<elf>
  \-PE  7c640000-7c660000       \               netapi32
ELF     7c660000-7c687000       Deferred        secur32<elf>
  \-PE  7c670000-7c687000       \               secur32
ELF     7ca5f000-7caa8000       Deferred        dsound<elf>
  \-PE  7ca70000-7caa8000       \               dsound
ELF     7cccf000-7ccdb000       Deferred        libgcc_s.so.1
ELF     7cce6000-7ccfb000       Deferred        psapi<elf>
  \-PE  7ccf0000-7ccfb000       \               psapi
ELF     7ccfb000-7cd0f000       Deferred        winejoystick<elf>
  \-PE  7cd00000-7cd0f000       \               winejoystick
ELF     7cd0f000-7cd73000       Deferred        setupapi<elf>
  \-PE  7cd20000-7cd73000       \               setupapi
ELF     7cd73000-7ce54000       Deferred        wined3d<elf>
  \-PE  7cd90000-7ce54000       \               wined3d
ELF     7ce54000-7ce83000       Deferred        d3d9<elf>
  \-PE  7ce60000-7ce83000       \               d3d9
ELF     7ce83000-7cf21000       Deferred        oleaut32<elf>
  \-PE  7cea0000-7cf21000       \               oleaut32
ELF     7cf21000-7cf48000       Deferred        msvfw32<elf>
  \-PE  7cf30000-7cf48000       \               msvfw32
ELF     7cf48000-7cf82000       Deferred        avifil32<elf>
  \-PE  7cf50000-7cf82000       \               avifil32
ELF     7cf82000-7cf97000       Deferred        midimap<elf>
  \-PE  7cf90000-7cf97000       \               midimap
ELF     7cf97000-7cfbd000       Deferred        msacm32<elf>
  \-PE  7cfa0000-7cfbd000       \               msacm32
ELF     7cfbd000-7cfd5000       Deferred        msacm32<elf>
  \-PE  7cfc0000-7cfd5000       \               msacm32
ELF     7cfd5000-7d09a000       Deferred        libasound.so.2
ELF     7d09a000-7d0d0000       Deferred        winealsa<elf>
  \-PE  7d0b0000-7d0d0000       \               winealsa
ELF     7d0d0000-7d0f0000       Deferred        mpr<elf>
  \-PE  7d0e0000-7d0f0000       \               mpr
ELF     7d0f0000-7d13a000       Deferred        wininet<elf>
  \-PE  7d100000-7d13a000       \               wininet
ELF     7d13a000-7d1c8000       Deferred        winmm<elf>
  \-PE  7d150000-7d1c8000       \               winmm
ELF     7d3ea000-7d3fe000       Deferred        mswsock<elf>
  \-PE  7d3f0000-7d3fe000       \               mswsock
ELF     7d3fe000-7d412000       Deferred        lz32<elf>
  \-PE  7d400000-7d412000       \               lz32
ELF     7d412000-7d42c000       Deferred        version<elf>
  \-PE  7d420000-7d42c000       \               version
ELF     7d4ba000-7d4ec000       Deferred        uxtheme<elf>
  \-PE  7d4c0000-7d4ec000       \               uxtheme
ELF     7d4ec000-7d545000       Deferred        rpcrt4<elf>
  \-PE  7d500000-7d545000       \               rpcrt4
ELF     7d545000-7d5e6000       Deferred        ole32<elf>
  \-PE  7d550000-7d5e6000       \               ole32
ELF     7d5e6000-7d6a4000       Deferred        comctl32<elf>
  \-PE  7d5f0000-7d6a4000       \               comctl32
ELF     7d6a4000-7d6fd000       Deferred        shlwapi<elf>
  \-PE  7d6b0000-7d6fd000       \               shlwapi
ELF     7d6fd000-7d800000       Deferred        shell32<elf>
  \-PE  7d710000-7d800000       \               shell32
ELF     7d800000-7d813000       Deferred        libresolv.so.2
ELF     7d813000-7d831000       Deferred        iphlpapi<elf>
  \-PE  7d820000-7d831000       \               iphlpapi
ELF     7d831000-7d85e000       Deferred        ws2_32<elf>
  \-PE  7d840000-7d85e000       \               ws2_32
ELF     7daa9000-7dac3000       Deferred        wsock32<elf>
  \-PE  7dab0000-7dac3000       \               wsock32
ELF     7dac3000-7dac8000       Deferred        libxfixes.so.3
ELF     7dac8000-7dad1000       Deferred        libxcursor.so.1
ELF     7dad1000-7daee000       Deferred        imm32<elf>
  \-PE  7dae0000-7daee000       \               imm32
ELF     7daee000-7daf4000       Deferred        libxrandr.so.2
ELF     7daf4000-7dafc000       Deferred        libxrender.so.1
ELF     7e030000-7e032000       Deferred        libnvidia-tls.so.1
ELF     7e032000-7e8b8000       Deferred        libglcore.so.1
ELF     7e8b8000-7e944000       Deferred        libgl.so.1
ELF     7e944000-7e949000       Deferred        libxdmcp.so.6
ELF     7e949000-7e94c000       Deferred        libxau.so.6
ELF     7e94c000-7ea3d000       Deferred        libx11.so.6
ELF     7ea3d000-7ea4b000       Deferred        libxext.so.6
ELF     7ea4b000-7ea50000       Deferred        libxxf86vm.so.1
ELF     7ea50000-7ea68000       Deferred        libice.so.6
ELF     7ea68000-7ea71000       Deferred        libsm.so.6
ELF     7ea7f000-7eb0a000       Deferred        winex11<elf>
  \-PE  7ea90000-7eb0a000       \               winex11
ELF     7eb67000-7eb87000       Deferred        libexpat.so.1
ELF     7eb87000-7ebb2000       Deferred        libfontconfig.so.1
ELF     7ebc0000-7ebd4000       Deferred        libz.so.1
ELF     7ebd4000-7ec3f000       Deferred        libfreetype.so.6
ELF     7ec3f000-7ec88000       Deferred        advapi32<elf>
  \-PE  7ec50000-7ec88000       \               advapi32
ELF     7ec88000-7ed23000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed23000       \               gdi32
ELF     7ed23000-7ee61000       Deferred        user32<elf>
  \-PE  7ed40000-7ee61000       \               user32
ELF     7ee80000-7ee8b000       Deferred        libnss_files.so.2
ELF     7ee8b000-7eea2000       Deferred        libnsl.so.1
ELF     7eea2000-7eeab000       Deferred        libnss_compat.so.2
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d4a000-b7d4e000       Deferred        libdl.so.2
ELF     b7d4e000-b7e8f000       Deferred        libc.so.6
ELF     b7e90000-b7ea7000       Deferred        libpthread.so.0
ELF     b7eb5000-b7fc9000       Deferred        libwine.so.1
ELF     b7fcb000-b7fe6000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000003f (D) Z:\home\adam\Spel\Steam\steamapps\<username>\portal\hl2.exe
        00000047    0
        0000002a    0
        00000028    0
        00000024    2
        00000021    0
        00000046   15
        00000045    0
        00000043    0
        00000042    0
        00000041    0
        00000040    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        0000001f    1
        00000029    1
        00000044    1
        0000003d    0
        0000003c    0
        0000003b    1
        0000003a    0
        00000039    1
        00000038    0
        00000037    1
        00000036    0
        00000035    1
        00000034    0
        00000033    1
        00000032    0
        00000031    1
        00000030    0
        0000002f    1
        0000002e    0
        0000002d    1
        0000002c    0
        0000002b    1
        00000026    0
        00000025    0
        00000023    0
        00000022    1
        00000020    0
        0000001e    0
        0000001d    0
        0000001c   15
        0000001b   15
        0000001a    0
        00000019    0
        00000018    0
        00000017    0
        00000016    0
        00000015    1
        00000014    0
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0

any ideas?

---

### Post by aldenhg on 2007-10-20
I get the same thing. As soon as the portal is supposed to open when the timer hits 0 it freezes, neccesitating a restart on Wine. I'm currently trying it with different emulated versions of Windows.

---

### Post by SanCo.ac on 2007-10-20
Post any updates if you find anything that works, please.

---

### Post by aldenhg on 2007-10-20
I downgraded Wine to the previous version and it works now.

---

### Post by Ubermouser on 2007-10-21
Has anyone using an ATI card been able to get Half life 2's orange box to work? From what I've seen on this thread, only those with Nvidia cards even have half a chance in hell. :mad:

---

### Post by aoanla on 2007-10-21
I have an ATI X1950 Pro, and I've managed to get Portal to work for reasonable periods of time (that is, play times on the order of half an hour between crashes) by downgrading to wine 0.9.42
None of the newer versions work (you can run Steam itself, but games crash fairly instantly, sometimes managing to play the intro video depending on the precise Wine version).

So, my advice is to try 0.9.42 (remembering not to play with the settings Portal chooses for your video card - altering them seems to increase the risk of a crash, even if you downgrade settings...)

---

### Post by Sockerdrickan on 2007-10-21
We want screenshots!

---

### Post by SanCo.ac on 2007-10-21
> **aoanla said:**
> I have an ATI X1950 Pro, and I've managed to get Portal to work for reasonable periods of time (that is, play times on the order of half an hour between crashes) by downgrading to wine 0.9.42
None of the newer versions work (you can run Steam itself, but games crash fairly instantly, sometimes managing to play the intro video depending on the precise Wine version).

So, my advice is to try 0.9.42 (remembering not to play with the settings Portal chooses for your video card - altering them seems to increase the risk of a crash, even if you downgrade settings...)

Works excellent, thank you Aoanla :)

And I use Nvidia for that mather.

---

### Post by eljoeb on 2007-10-21
Orange box/any source engine game works fine on my computer with the newest version of wine.  Performance is substantially worse than windows, but at a lower resolution and detail it is playable.

---

### Post by Curlydave on 2007-10-21
> **pt123 said:**
> screenshots or it didn't happen

[img]http://mysite.verizon.net/vze1q71c/tf1.jpg[/img]

[img]http://mysite.verizon.net/vze1q71c/tf2.jpg[/img]

I'm pretty surprised it worked as well as it did. I've tried getting Source games to work on wine in the past and could never get them to launch. The only hoops I had to jump through were getting the Tahoma font into Wine's /windows/fonts directory, and having it crash a few times while trying to download the gecko engine, which it did automatically.

The performance seems to be unhindered - I'm getting +100 fps, but that could be because it wouldn't let me enable HDR, motion blur, AA, high quality shadows, and I think it's running in DX8 mode based on how bad the water looks in the shot above.

The sound is also broken. In the menu it stutters constantly, in-game it feels empty, like most of the audio quality is missing, and the sounds are a shell of their former self. I had the same problem with UT2k4 on linux a while back, and that ran natively.

As far as running games through Wine goes, this has been my best experience. It's still broken to the point where I'd never bother playing it on Linux when I have a working copy on Windows, but getting it running was a pleasant surprise.

---

### Post by Sockerdrickan on 2007-10-21
Dude! Awesome! HL2 EP2 pictures please!

---

### Post by Ubermouser on 2007-10-21
> **aoanla said:**
> I have an ATI X1950 Pro, and I've managed to get Portal to work for reasonable periods of time (that is, play times on the order of half an hour between crashes) by downgrading to wine 0.9.42
None of the newer versions work (you can run Steam itself, but games crash fairly instantly, sometimes managing to play the intro video depending on the precise Wine version).

So, my advice is to try 0.9.42 (remembering not to play with the settings Portal chooses for your video card - altering them seems to increase the risk of a crash, even if you downgrade settings...)

Running Team Fortress 2 in WINE version 0.9.42 gets me as far as the main screen where I'm greeted with the introduction music and a black screen. Could anyone tell me what graphics drivers they're using with their ATI graphics card, and what if any registry changes you had to make in order to get TF2 to run? Thanks in advance!

---

### Post by aoanla on 2007-10-21
> **Ubermouser said:**
> Running Team Fortress 2 in WINE version 0.9.42 gets me as far as the main screen where I'm greeted with the introduction music and a black screen. Could anyone tell me what graphics drivers they're using with their ATI graphics card, and what if any registry changes you had to make in order to get TF2 to run? Thanks in advance!

I'm using fglrx 8.41.7, with no changes to the registry defaults. That said, I've not tried playing TF2 for more than a brief period, so I can't claim that I know it's stable under those settings - Portal certainly isn't, although it plays long enough for me to complete a couple of test zones each time...

---

### Post by Ubermouser on 2007-10-21
Thanks, aoanla, this got Team fortress 2 and Portal to work, albeit far from the experience CurlyDave had. I get closer to 10fps, and the game looks downright hideous compared to Windows.

[[IMG]http://img84.imageshack.us/img84/381/horribletf2rb3.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=horribletf2rb3.jpg)

also: Installing the latest fglrx (8.41.7) drivers from ATI's site cut my glxgears fps in half. I've an ATI x1900xtx. :mad:

---

### Post by justin whitaker on 2007-10-21
I'm using Crossover on Gutsy...game looks as good as XP, but no sound. I'm working on it.

---

### Post by silverh20 on 2007-10-22
Here are some screens I took while running half life episode 2. i havent gotten sound working yet with wine despite having alsa selected and emulation enabled. also its running in directx8.1 mode for some reason. i set wine to be in winxp mode so im not sure whats going on. also, i got my version of wine from the synaptic package manager. had to install the gecko mozilla browser for wine by running a command. also i copied the tahoma font to my wine c drive from my windows partition. i get great frames per second tho running at 1680X1050 with 16 anisotropic, bloom, high detail textures, medium shadows, and the rest. 

7800gtx 
amd 4400 x2
2 gb ddr
Gutsy 32 bit 7.10 release

---

### Post by Sockerdrickan on 2007-10-22
wowomg @ second pic

---

### Post by Curlydave on 2007-10-22
> **silverh20 said:**
> Here are some screens I took while running half life episode 2. i havent gotten sound working yet with wine despite having alsa selected and emulation enabled. also its running in directx8.1 mode for some reason. i set wine to be in winxp mode so im not sure whats going on. also, i got my version of wine from the synaptic package manager. had to install the gecko mozilla browser for wine by running a command. also i copied the tahoma font to my wine c drive from my windows partition. i get great frames per second tho running at 1680X1050 with 16 anisotropic, bloom, high detail textures, medium shadows, and the rest. 

7800gtx 
amd 4400 x2
2 gb ddr
Gutsy 32 bit 7.10 release

You'll get better performance if you turn off compiz-fusion.

---

### Post by silverh20 on 2007-10-22
Just tried CSS and it worked and even had sound, for about 30 sec, then it froze. Haven't gotten sound in HL2:EP2 still yet but that hasn't crashed either so something might be up with my sound.

---

### Post by aoanla on 2007-10-22
> **Ubermouser said:**
> Thanks, aoanla, this got Team fortress 2 and Portal to work, albeit far from the experience CurlyDave had. I get closer to 10fps, and the game looks downright hideous compared to Windows.

[[IMG]http://img84.imageshack.us/img84/381/horribletf2rb3.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=horribletf2rb3.jpg)

also: Installing the latest fglrx (8.41.7) drivers from ATI's site cut my glxgears fps in half. I've an ATI x1900xtx. :mad:

Well, 8.42.x is due out by the end of this week (maybe even today), so hopefully that will improve matters for you...

---

### Post by JamesNeko on 2007-10-22
> **Ghola28 said:**
> I'm running WINE 0.9.41 (see edit of earlier post) with WinXP as the default.  I've changed the Audio Tab in winecfg to use the Alsa drivers, with Hardware Accleration set to Emulation, the Sample Rate set to 44100, Bits per sample set to 16, and Driver Emulation checked.

I *did* have to copy the Tacoma fonts from a windows install to the windows -> fonts folder in my wine install (so I could see the text in Steam).

I'll post screenshots soon.

Thanks for this! The sound problem was driving me nuts - couldn't use ol' reliable OSS, since Steam grabs the sound first. This is the first time I've gotten non-stuttery sound using Wine's ALSA output.

Also, anyone using 0.9.47 should downgrade - it's fixed the Steam font thing, but broken the viewing of Portals. If you just upgraded today before installing the Orange Box (like me), you may be able to downgrade by poking around in your /var/cache/apt/archives directory. See if the old wine .46 .deb is in there, and if it is, use dpkg -i to install it. You might lose the Steam fonts, but I'm sure there's a fix for that somewhere..

---

### Post by JamesNeko on 2007-10-23
By the way, I noticed here: [http://developer.valvesoftware.com/wiki/Command_line](http://developer.valvesoftware.com/wiki/Command_line)
that there's a -gl command line switch. I tried it, but I'm not certain it listened to me- does it work? Or should I be using -dxlevel 81, etc?
I get great performance with WoW in GL mode, so I'm hoping I can get a similar effect with HL2.

---

### Post by DDuong on 2007-10-24
> **justin whitaker said:**
> I'm using Crossover on Gutsy...game looks as good as XP, but no sound. I'm working on it.

Hello,

I also use Crossover on Gutsy and had the same problem until I found this link and it worked fine for me.

> [http://www.codeweavers.com/support/docs/crossover-standard/faq#sound-faqs](http://www.codeweavers.com/support/docs/crossover-standard/faq#sound-faqs)

What I did was the following (which is also in that link I gave you):

> ~/cxoffice/bin/wine --bottle bottlename --wl-app winecfg

Replace the usual info there and then choose the "Audio" tab, then select ALSA again, click Apply, and try the game again.  Should work.  Also, play around with the hard acceleration etc options.

---

### Post by aoanla on 2007-10-24
> **JamesNeko said:**
> By the way, I noticed here: [http://developer.valvesoftware.com/wiki/Command_line](http://developer.valvesoftware.com/wiki/Command_line)
that there's a -gl command line switch. I tried it, but I'm not certain it listened to me- does it work? Or should I be using -dxlevel 81, etc?
I get great performance with WoW in GL mode, so I'm hoping I can get a similar effect with HL2.

You should use the -dxlevel switches - HL2 currently, as far as I know, doesn't have an OpenGL renderer for anything other than the PS3.

---

### Post by JamesNeko on 2007-10-24
> **aoanla said:**
> You should use the -dxlevel switches - HL2 currently, as far as I know, doesn't have an OpenGL renderer for anything other than the PS3.

mumblegrumble, if they have the renderer, why not release it? Same deal with Oblivion getting a PS3 port.

Well, thanks for the info anyway.

---

### Post by Sockerdrickan on 2007-10-24
I played EP2 through tonight (01:00-05:40 lol) and missed the first lesson in school
one word
**WOW**
best Half-Life game yet!!

Screens with my rig coming today. :popcorn:

---

### Post by Prometheus7 on 2007-10-29
Has anyone been able to tone up the graphics (the water looks very two dimensional) with their working version in wine?

---

### Post by Crafty Kisses on 2007-10-29
Nice, I have The Orange Box for Xbox 360, but it's good to hear that it works with Linux. :)

---

### Post by Prometheus7 on 2007-10-29
OK, so I kind of found the answer to my question...

In steam if you right click on a game and select "Properties", then in the "General" tab you can "Set Launch Options...".

Here you can set the dxlevel, force use of gl, and enable the console by typing...

"-dxlevel 90 -gl -console"

Haven't tried with directx 9 yet but plan on trying that tonight when I get home. Will let you all know the results.

Steam seems to run better in Gutsy than XP and its great that I can play the game, but I'd like to tweak it so that I can see the water effects in their full glory. This is especially because I plan to eventually get Bioshock through steam and I know there are incredible water effects in that game.

---

### Post by jekinney on 2007-12-21
I havn't messed with Wine in a year or so, when steam would get stuck at 26%(or so). But I was able to run IE and download DX9c updates and GPU drivers and install them in WINE. 

The people with the FPS and low quality tried that yet?

And some of your systems are below the min. requirements. EP2 has a updated engine, so the requirements went up over EP1.

Just a thought,my linux box is for media and internet, my Gameing PC is only for gaming, using a striped down Windows XP(uses same resorces as Linux at idel).

---

