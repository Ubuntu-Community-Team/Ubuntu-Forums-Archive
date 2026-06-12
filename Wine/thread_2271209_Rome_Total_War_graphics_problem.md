---
title: "Rome Total War graphics problem"
date: 2015-03-28
forum: Wine
---

### Post by soma094 on 2015-03-28
Hi! i just downloaded and installed Rome Total War using Steam and i would like to play it,

but when it launches the screen is divided up into squares and its unplayable.

the sound is perfect though and can see that it loads and it wont crash. 

Any ideas on what this can be and how to fix it?

[ATTACH=CONFIG]260943[/ATTACH] here is a screen shot of it.

my graphics card: 

```
sudo lshw -C video

  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)


```

---

### Post by soma094 on 2015-03-29
I researched this topic before posting here, and ive found an article in which the user had exactly the same problem as mine.

But there wasnt really a solution for my case because he just switched from the integrated card to a dedicated and it solved his problems.

I also know from my search that the integrated gpu is the worst option for gaming in linux...

This forum is my last resort. I just would like to know if anyone has any ideas on how to solve it.

right now im downloading the game again and will try to launch it with an older version of wine (1.6.2) The problem occured using 1.7.33

---

### Post by mastablasta on 2015-03-31
well a similar problem is here along with solution: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=22972](https://appdb.winehq.org/objectManager.php?sClass=version&iId=22972)

game has platinum rating otherwise.

it's not integrated card. it's certain version of them that are bad. new intel chips are good, as are AMD. old ones are really bad for gaming in Linux or Windows.

---

### Post by soma094 on 2015-03-31
I tried out the solution mentioned in the forum, that enable wine to emulate another window for the game but did not work for me...

Also installing another version of wine doesnt seem to solve the problem.

---

### Post by mastablasta on 2015-04-01
do oyu have all other things installed such as direct x libraries and similar to make the game work? does the game itself crash? can you run it from terminal -do you get any errors in it?

this did not work?:

> If you must use the intel graphics chip: Start PlayOnLinux. Select Rome Total war. Left-click the configure button. Press the wine-tab. Left-click on the configure-wine-button. After about 2 seconds the wine-configure program starts. Press the Graphics-tab. Check Emulate virtual screen (Note that the resolution can be adjusted to your desktop screen resolution. But first time around, leave it alone). Left-click ok. Close PlayOnLinux configuration. 
Start the game. 
The splash screen appears: "Rome Total war". 
Then the screen that you posted. 
Then: "Sega" screen. 
Then: "The creative assembly" screen- 
Now a blank screen appears and nothing happens. 
Just press once the Esc-button. 
Now, the video-intro should start. 
Then the start menu appears and all is well. 
I hope it works. 
(My descriptions are based on german language versions and I translated it to English. The exact wording may be different from the English versions that you are using.)


---

### Post by soma094 on 2015-04-01
Yes i have the direct x and no it doesnt crash and also the sound works perfectly. I installed it through steam so in this way i couldnt try it out,

but i added an emulated window to steam and i launched the game through it and it opened inside the emulated window but still didnt work.

i couldnt launch it through the terminal :(

---

### Post by soma094 on 2015-04-01
Weel now it crashes and i get this error:

```
 Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x7d0d2ea5).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d0d2ea5 ESP:00332e80 EBP:7d354be8 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7d349000 ECX:7c6b7188 EDX:00000003
 ESI:7c72ba6c EDI:7c963268
Stack dump:
0x00332e80:  000080e1 000080e1 00008367 00000000
0x00332e90:  000080e1 7c7442f8 00000300 7cea1690
0x00332ea0:  000080e1 00008367 7c72ba6c 7ceda81e
0x00332eb0:  7c72ba6c 3d57c90f 7c542830 00000000
0x00332ec0:  00000000 00000000 00000004 7c6b7188
0x00332ed0:  3ff00000 e0000000 416fffff 7d349000
Backtrace:
=>0 0x7d0d2ea5 in i965_dri.so (+0x2bbea5) (0x7d354be8)
  1 0x7ced1705 in i965_dri.so (+0xba704) (0x00000400)
  2 0x7ced18c7 in i965_dri.so (+0xba8c6) (0x003330d8)
  3 0x7eb061b2 in wined3d (+0xc61b1) (0x003330d8)
  4 0x7eb0928a wined3d_surface_map+0x289() in wined3d (0x00333158)
  5 0x7eb09954 in wined3d (+0xc9953) (0x00333258)
  6 0x7eb0b844 wined3d_surface_blt+0x2e3() in wined3d (0x00333348)
  7 0x7eb0f0e4 wined3d_swapchain_get_front_buffer_data+0xd3() in wined3d (0x003333b8)
  8 0x7ea8b9de wined3d_device_get_front_buffer_data+0x4d() in wined3d (0x00333408)
  9 0x7e195930 in d3d8 (+0x1592f) (0x0033343c)
  10 0x00f55b3b in rometw (+0xb55b3a) (0x0033347c)
  11 0x0098a8a3 in rometw (+0x58a8a2) (0x00333498)
  12 0x0040f8c3 in rometw (+0xf8c2) (0x00333540)
  13 0x00404fd5 in rometw (+0x4fd4) (0x0033e4d4)
  14 0x004033c3 in rometw (+0x33c2) (0x0033fdd4)
  15 0x00fc9760 in rometw (+0xbc975f) (0x0033fe60)
  16 0x7b86275c call_process_entry+0xb() in kernel32 (0x0033fe78)
  17 0x7b86398b in kernel32 (+0x4398a) (0x0033feb8)
  18 0x7bc80710 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  19 0x7bc8385d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  20 0x7bc806ee RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  21 0x7bc5448e call_dll_entry_point+0x36d() in ntdll (0x0033ffe8)
  22 0xf75aa75d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  23 0xf75aa81b wine_switch_to_stack+0x2a() in libwine.so.1 (0xff8a0e28)
  24 0x7bc5a0b1 LdrInitializeThunk+0x240() in ntdll (0xff8a0e78)
  25 0x7b86a240 __wine_kernel_init+0xbbf() in kernel32 (0xff8a1d98)
  26 0x7bc5afe3 __wine_process_init+0x182() in ntdll (0xff8a1e28)
  27 0xf75a83aa wine_init+0x2b9() in libwine.so.1 (0xff8a1e88)
  28 0x7bf00ebb main+0x7a() in <wine-loader> (0xff8a22c8)
  29 0xf73d0a83 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x7d0d2ea5: movl    0x4(%eax),%eax
Modules:
Module    Address            Debug info    Name (162 modules)
PE      400000- 2b56000    Export          rometw
PE     55d0000- 55e8000    Deferred        mssds3d.m3d
PE     5fc0000- 5fdb000    Deferred        mssdsp.flt
PE    10000000-100d5000    Deferred        steam
PE    21100000-21160000    Deferred        mss32
PE    22300000-2232b000    Deferred        msseax.m3d
PE    22400000-22415000    Deferred        msssoft.m3d
PE    26f00000-26f29000    Deferred        mssmp3.asi
PE    30000000-302c1000    Deferred        steam2
PE    38000000-38973000    Deferred        steamclient
PE    3b400000-3b41d000    Deferred        steam_api
PE    3f000000-3f0b1000    Deferred        tier0_s
PE    3f600000-3f653000    Deferred        vstdlib_s
PE    60000000-60021000    Deferred        cserhelper
ELF    7a800000-7a91b000    Deferred        opengl32<elf>
  \-PE    7a820000-7a91b000    \               opengl32
ELF    7b800000-7ba61000    Dwarf           kernel32<elf>
  \-PE    7b820000-7ba61000    \               kernel32
ELF    7bc00000-7bce2000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bce2000    \               ntdll
ELF    7bf00000-7bf03000    Dwarf           <wine-loader>
ELF    7c03b000-7c067000    Deferred        libvorbis.so.0
ELF    7c173000-7c2eb000    Deferred        libvorbisenc.so.2
ELF    7c2eb000-7c31f000    Deferred        libflac.so.8
ELF    7c31f000-7c391000    Deferred        libsndfile.so.1
ELF    7c391000-7c400000    Deferred        libpulsecommon-4.0.so
ELF    7ca04000-7ca0d000    Deferred        libogg.so.0
ELF    7ca0d000-7ca5c000    Deferred        libpulse.so.0
ELF    7ca6d000-7ca74000    Deferred        libasound_module_pcm_pulse.so
ELF    7ca7b000-7cb71000    Deferred        libasound.so.2
ELF    7cb71000-7cb78000    Deferred        libasyncns.so.0
ELF    7cb78000-7cb82000    Deferred        libwrap.so.0
ELF    7cb82000-7cb8d000    Deferred        libjson-c.so.2
ELF    7cb90000-7cbc0000    Deferred        winealsa<elf>
  \-PE    7cba0000-7cbc0000    \               winealsa
ELF    7cbc0000-7cbe2000    Deferred        mmdevapi<elf>
  \-PE    7cbd0000-7cbe2000    \               mmdevapi
ELF    7cbe2000-7cc2b000    Deferred        dsound<elf>
  \-PE    7cbf0000-7cc2b000    \               dsound
ELF    7cc2b000-7cc76000    Deferred        dinput<elf>
  \-PE    7cc30000-7cc76000    \               dinput
ELF    7cceb000-7ccf6000    Deferred        libpciaccess.so.0
ELF    7cddf000-7cded000    Deferred        libdrm_radeon.so.1
ELF    7cded000-7cdf5000    Deferred        libdrm_nouveau.so.2
ELF    7cdf5000-7ce17000    Deferred        libdrm_intel.so.1
ELF    7ce17000-7d38a000    Dwarf           i965_dri.so
ELF    7d38a000-7d3d5000    Deferred        libdbus-1.so.3
ELF    7d3d5000-7d3df000    Deferred        libnih-dbus.so.1
ELF    7d3df000-7d3f8000    Deferred        libnih.so.1
ELF    7d3f8000-7d416000    Deferred        libcgmanager.so.0
ELF    7d416000-7d429000    Deferred        libudev.so.1
ELF    7d429000-7d436000    Deferred        libdrm.so.2
ELF    7d436000-7d439000    Deferred        libxshmfence.so.1
ELF    7d439000-7d499000    Deferred        libgl.so.1
ELF    7d499000-7d500000    Deferred        dbghelp<elf>
  \-PE    7d4a0000-7d500000    \               dbghelp
ELF    7d602000-7d609000    Deferred        libxcb-sync.so.1
ELF    7d609000-7d60d000    Deferred        libxcb-present.so.0
ELF    7d60d000-7d611000    Deferred        libxcb-dri3.so.0
ELF    7d611000-7d617000    Deferred        libxcb-dri2.so.0
ELF    7d617000-7d62f000    Deferred        libxcb-glx.so.0
ELF    7d62f000-7d632000    Deferred        libx11-xcb.so.1
ELF    7d632000-7d64a000    Deferred        libglapi.so.0
ELF    7d64a000-7d667000    Deferred        libgcc_s.so.1
ELF    7d667000-7d66e000    Deferred        libffi.so.6
ELF    7d66e000-7d673000    Deferred        libgpg-error.so.0
ELF    7d673000-7d6af000    Deferred        libp11-kit.so.0
ELF    7d6ce000-7d753000    Deferred        libgcrypt.so.11
ELF    7d753000-7d765000    Deferred        libtasn1.so.3
ELF    7d765000-7d82e000    Deferred        libgnutls.so.26
ELF    7d82e000-7d85c000    Deferred        netapi32<elf>
  \-PE    7d830000-7d85c000    \               netapi32
ELF    7d85c000-7d88e000    Deferred        secur32<elf>
  \-PE    7d860000-7d88e000    \               secur32
ELF    7d88e000-7d8fe000    Deferred        setupapi<elf>
  \-PE    7d8a0000-7d8fe000    \               setupapi
ELF    7d8fe000-7da41000    Deferred        oleaut32<elf>
  \-PE    7d920000-7da41000    \               oleaut32
ELF    7da41000-7da54000    Deferred        psapi<elf>
  \-PE    7da50000-7da54000    \               psapi
ELF    7da54000-7db25000    Deferred        crypt32<elf>
  \-PE    7da60000-7db25000    \               crypt32
ELF    7db25000-7db5b000    Deferred        uxtheme<elf>
  \-PE    7db30000-7db5b000    \               uxtheme
ELF    7db5b000-7db61000    Deferred        libxfixes.so.3
ELF    7db61000-7db6c000    Deferred        libxcursor.so.1
ELF    7db6c000-7db7d000    Deferred        libxi.so.6
ELF    7db7d000-7db81000    Deferred        libxcomposite.so.1
ELF    7db81000-7db8c000    Deferred        libxrandr.so.2
ELF    7db8c000-7db97000    Deferred        libxrender.so.1
ELF    7db97000-7db9d000    Deferred        libxxf86vm.so.1
ELF    7db9d000-7dba1000    Deferred        libxinerama.so.1
ELF    7dba1000-7dba8000    Deferred        libxdmcp.so.6
ELF    7dba8000-7dbac000    Deferred        libxau.so.6
ELF    7dbac000-7dbce000    Deferred        libxcb.so.1
ELF    7dbce000-7dd02000    Deferred        libx11.so.6
ELF    7dd02000-7dd15000    Deferred        libxext.so.6
ELF    7dd15000-7dd19000    Deferred        libxdamage.so.1
ELF    7dd19000-7dd32000    Deferred        imagehlp<elf>
  \-PE    7dd20000-7dd32000    \               imagehlp
ELF    7dd34000-7ddc7000    Deferred        winex11<elf>
  \-PE    7dd40000-7ddc7000    \               winex11
ELF    7ddc7000-7ddeb000    Deferred        imm32<elf>
  \-PE    7ddd0000-7ddeb000    \               imm32
ELF    7de38000-7de61000    Deferred        libexpat.so.1
ELF    7de61000-7de9c000    Deferred        libfontconfig.so.1
ELF    7de9c000-7dec4000    Deferred        libpng12.so.0
ELF    7dec4000-7dedd000    Deferred        libz.so.1
ELF    7dedd000-7df7d000    Deferred        libfreetype.so.6
ELF    7df7d000-7df95000    Deferred        libresolv.so.2
ELF    7dfb4000-7dfda000    Deferred        iphlpapi<elf>
  \-PE    7dfc0000-7dfda000    \               iphlpapi
ELF    7dfda000-7e011000    Deferred        ws2_32<elf>
  \-PE    7dfe0000-7e011000    \               ws2_32
ELF    7e011000-7e02c000    Deferred        wsock32<elf>
  \-PE    7e020000-7e02c000    \               wsock32
ELF    7e02c000-7e134000    Deferred        comctl32<elf>
  \-PE    7e030000-7e134000    \               comctl32
ELF    7e134000-7e15f000    Deferred        msvfw32<elf>
  \-PE    7e140000-7e15f000    \               msvfw32
ELF    7e15f000-7e17a000    Deferred        dinput8<elf>
  \-PE    7e160000-7e17a000    \               dinput8
ELF    7e17a000-7e1af000    Dwarf           d3d8<elf>
  \-PE    7e180000-7e1af000    \               d3d8
ELF    7e1af000-7e229000    Deferred        shlwapi<elf>
  \-PE    7e1c0000-7e229000    \               shlwapi
ELF    7e229000-7e461000    Deferred        shell32<elf>
  \-PE    7e240000-7e461000    \               shell32
ELF    7e461000-7e49f000    Deferred        d3d9<elf>
  \-PE    7e470000-7e49f000    \               d3d9
ELF    7e49f000-7e4c9000    Deferred        msacm32<elf>
  \-PE    7e4b0000-7e4c9000    \               msacm32
ELF    7e4c9000-7e54e000    Deferred        rpcrt4<elf>
  \-PE    7e4d0000-7e54e000    \               rpcrt4
ELF    7e54e000-7e690000    Deferred        ole32<elf>
  \-PE    7e570000-7e690000    \               ole32
ELF    7e690000-7e748000    Deferred        winmm<elf>
  \-PE    7e6a0000-7e748000    \               winmm
ELF    7e748000-7e8a5000    Deferred        user32<elf>
  \-PE    7e760000-7e8a5000    \               user32
ELF    7e8a5000-7e916000    Deferred        advapi32<elf>
  \-PE    7e8b0000-7e916000    \               advapi32
ELF    7e916000-7ea35000    Deferred        gdi32<elf>
  \-PE    7e920000-7ea35000    \               gdi32
ELF    7ea35000-7eb7b000    Dwarf           wined3d<elf>
  \-PE    7ea40000-7eb7b000    \               wined3d
ELF    7eb7b000-7ebf0000    Deferred        ddraw<elf>
  \-PE    7eb80000-7ebf0000    \               ddraw
ELF    7ebf0000-7ebfd000    Deferred        libnss_files.so.2
ELF    7ebfd000-7ec09000    Deferred        libnss_nis.so.2
ELF    7ec09000-7ec22000    Deferred        libnsl.so.1
ELF    7ec22000-7ec2b000    Deferred        libnss_compat.so.2
ELF    7ef9b000-7efe1000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f73b2000-f73b7000    Deferred        libdl.so.2
ELF    f73b7000-f7565000    Dwarf           libc.so.6
ELF    f7565000-f7581000    Deferred        libpthread.so.0
ELF    f7587000-f7590000    Deferred        librt.so.1
ELF    f75a1000-f7757000    Dwarf           libwine.so.1
ELF    f7759000-f777b000    Deferred        ld-linux.so.2
ELF    f777b000-f777c000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 Steam.exe
    0000007c    0
    0000005a    0
    00000057    0
    00000056    0
    00000053    0
    00000052    0
    00000051    0
    00000050    0
    0000004f    0
    0000004e    0
    0000004d    0
    0000004c    0
    0000004b    0
    0000004a    0
    00000049    0
    00000048    0
    0000000c    0
    00000040    0
    0000002e    0
    0000002d    0
    0000002c    0
    00000029    0
    00000028    0
    00000009    0
0000000e services.exe
    0000001d    0
    0000001c    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000017    0
    00000013    0
00000019 plugplay.exe
    0000001f    0
    0000001e    0
    0000001a    0
00000020 explorer.exe
    00000022    0
    00000021    0
0000002a steamwebhelper.exe
    0000006f    0
    0000006e    0
    0000006d    0
    0000006c    0
    0000006b    0
    00000069    0
    00000068    0
    0000005e    0
    0000005b    0
    00000045    0
    00000042    0
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
    00000035    0
    00000034    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0
    0000002f    0
    0000002b    0
00000058 steamwebhelper.exe
    00000026    0
    00000025    0
    00000054    0
    00000047    0
    00000046    0
    00000067    0
    00000066    0
    00000065    0
    00000059    0
00000070 (D) C:\Program Files\Steam\steamapps\common\Rome Total War Gold\RomeTW.exe
    00000079   15
    00000078   15
    00000076    0
    00000075    0
    00000074    0
    00000071    0 <==
System information:
    Wine build: wine-1.7.33
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-37-generic 
```

so this is the error in detials

---

### Post by soma094 on 2015-04-03
So i would like to give an update on my problem...

if anyone in the future would have the same issue then he/she could find the solution here.

So what i did:

I had the idea that maybe the driver for my integrated intel graphic card can be the problem so i wanted to upgrade the driver just to see

if that was the problem.

I found out that the program that could update this driver is now only available for the Utopic Unicorn version of ubuntu. ( is there another way to upgrade an intel driver? )

So i installed that version. Then again playonlinux then steam through it then downloaded the game again and i came to the problem that was mentioned before [https://appdb.winehq.org/objectManag...sion&iId=22972]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=22972") so no divided screen just the resolution issue and that could be solved easily with the mentioned solution.

> If you must use the intel graphics chip: Start PlayOnLinux. Select Rome  Total war. Left-click the configure button. Press the wine-tab.  Left-click on the configure-wine-button. After about 2 seconds the  wine-configure program starts. Press the Graphics-tab. Check Emulate  virtual screen (Note that the resolution can be adjusted to your desktop  screen resolution. But first time around, leave it alone). Left-click  ok. Close PlayOnLinux configuration. 
Start the game. 
The splash screen appears: "Rome Total war". 
Then the screen that you posted. 
Then: "Sega" screen. 
Then: "The creative assembly" screen- 
Now a blank screen appears and nothing happens. 
Just press once the Esc-button. 
Now, the video-intro should start. 
Then the start menu appears and all is well. 
I hope it works. 
(My descriptions are based on german language versions and I translated  it to English. The exact wording may be different from the English  versions that you are using.)

---

### Post by soma094 on 2015-04-03
I actually found a better solution for the resolution issue.

So if you open the game in an emulated window ( at least i had this problem ) then because of the menu bar you cannot see the lower part of the game where the buttons are so you basically cant play.

What i did instead is that i loaded the game without an emulated window and didnt care about the resolution problem.

Then at the main menu i go to options/video options/ and then play with the screen resolution until it gets fine.

It was a better solution for me, but anyone can add to it if anyone has a better solution both for the intel graphics driver or for the lower part of the screen problem with the menu bar.

---

