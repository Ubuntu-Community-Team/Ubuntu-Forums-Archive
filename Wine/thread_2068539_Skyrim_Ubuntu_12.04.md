---
title: "Skyrim Ubuntu 12.04"
date: 2012-10-09
forum: Wine
---

### Post by samishal on 2012-10-09
Hi there,

I'm trying to install SKyrim, in steam in wine on Ubuntu 12.04. I've been following this video tutorial from the [Linux Game Cast]("http://linuxgamecast.com/2011/11/l-g-c-how-to-%E2%80%94-the-elder-scrolls-v-skyrim-winetricks/") but my installation fails when I try to add the dotnet20 package. 

The error that I get is that mono is not installed and then it fails to install the dotnet20 package. mono-runtime IS installed on my system so I'm rather confused. dotnet20 also fails to install when I tried to install it using playonlinux.

If there's any info I can provide I will on request as I'm not sure what you might need :)

Sam

---

### Post by samishal on 2012-10-09
Hi there,

I've actually managed to get Skyrim working now here is how I did it : 

Firstly, make sure that your hardware is compatable and that you have the correct drivers. Run the "Additional drivers" program to get the drivers for the graphics card.

After you have installed all of the necasary drivers go to the Software Centre and search for PlayOnLinux. Install it. Don't bother with a WINE manual install.

Run PlayOnLinux then go to Install>>Games and then search Skyrim. It will take a while as it needs to download and install a whole lot of stuff. Eventually once it has installed what it needs to you will be asked how you want to install the game select the Steam way.

After installing and setting up steam you'll be told to fully close steam after it has finished the installtion of the game. Click next.

There should be a skyrim shortcut placed on you desktop (Mine was slightly off screen at the top left had side) If the Steam log in page dosen't appear automatically double click the shortcut. Please give it a minute or two before using the shortcut.

Log into Steam.

If you have the disk like I do then don't bother downloading the game like a toolbox.

Insert the disk then go to Games>>Add non steam game
then browse to /media/<Skyrimdisk> and select setup.exe (shoudl have steam logo). click add and then go to youe games library, you shoudl see setup.exe in there, click it, then click play. Skyrim will now install.

After skyrim has installed Close steam and wait for PlayOnLinux to continue, I had to close PLayOnLinux manually but hey you might get lucky.

If you run skyrim from the desktop shortcut you will probably get something like : "Failed to initialize rendered...etc" to fix this run PlayOnLinux go to Configure>>Wine>>Registry Editor and then navigate to : HKEY_CURRENT_USER/Wine/Direct3D and then set the UseGLSL from disabled to enabled.

close everything.

Run skyrim again. 

It should work.(fingers crossed)

You might need to restart you comp.

Happy Dragon Killing.

Love Sam

---

### Post by ilcontegis on 2012-11-06
Simply use POL (Play On Linux) everything is automatic.

---

### Post by wjcunning on 2012-11-14
POL doesn't work for SKYRIM. I fiddled with it for 2 days, on three different hardware sets,finally tired of it and bailed. Followed about a dozen different threads that offered hints, but in the end only the .Net stuff was installed.  

Play on Linux certainly didn't work, that's for sure.

---

### Post by markackerman8@gmail.com on 2012-12-15
I can't see the cursor !!

I have a torrent version which works perfectly in Windows even with the most recent updates.  I have managed to get it to the play window by running the POL version which makes the bottle with all the needed stuff in it.  But since I can't install thru Steam (the only way POL works) I just copied my Program(x86) folder to wine c drive and it starts.  But no matter what I do I can NEVER see The cursor.  I can in the launcher for settings but as soon as it gets to the sart menu it disappears.

Any help would sure be appreciated 
Kubuntu 12.10
Intel I7 -Intel and amd radeon 6850m cards (dual - muxless) only open source Radeon driver working - though quite well.

Please Help mark -and Thanks :P

---

### Post by f1ndingwalden on 2013-02-01
test

---

### Post by ilcontegis on 2013-02-13
> **wjcunning said:**
> POL doesn't work for SKYRIM. I fiddled with it for 2 days, on three different hardware sets,finally tired of it and bailed. Followed about a dozen different threads that offered hints, but in the end only the .Net stuff was installed.  

Play on Linux certainly didn't work, that's for sure.

Late reply.
I had no issues with Skyrim and POL. The problem is your hardware.
Probably you have an ati card.:popcorn:

---

### Post by Perfect Storm on 2013-02-13
Moved to Gaming ---> Wine section.

---

### Post by markackerman8@gmail.com on 2013-02-14
Yep probably my damn ATI card that cant handle proprietary drivers - only the radeon driver works (which at least gives me 30% functionality).

Cheers, Mark

---

### Post by aarons6 on 2013-02-19
games on linux is best done with nvidia video.
ati can be done but its a lot of work.. 
first off you need 32 bit linux.. 64 will not work. at least not for me.
second you need ati's drivers from the amd website installed.. these are very hard to get working. you need linux headers and source. run them as root out of X.. wheni had my ati video card i just dropped out of shell and ran sudo service lightdm stop or something to kill the X and then sudo the ati.run file


then to install skyrim, i just ran a blank wine prefix with the directx10, the dotnetfx and vcredist the game installs.. 

i use openbox to play games..  dont log into openbox, just run openbox in another x server. 
xinit openbox -- :1

then open the term and run wine skse_loader.exe
if you have the steam version you have to install steam as well.. 
wine msiexec /i steam.msi
it works great in linux with no issues. 

i dont use POL to play games.. i find it causes more problems then its worth. i never could get anything working with POL.. maybe others have more success.. 


make sure you install the game in an EXT partition.. 
do not run wine games on fuse partitions.. this causes problems.

---

### Post by peteremmm on 2013-08-06
Just for the record - I'm running Ubuntu 13.10 beta with an Nvidia card. I use Playonlinux, and I installed Skyrim from Steam. It works without a problem. The dotnet package installs fine. There are performance issues sometimes, but that's because of the emulation.

---

### Post by texaswriter on 2013-08-09
Crossover + NVIDIA GPU + Proprietary drivers --> Worked for me. I think there are instructions, but I just followed the automated process. Works near perfectly, all mods and DLC. Played it over 120 hours so far. Good luck.

There are instructions to install it on vanilla WINE if you don't use Crossover. I haven't tried these instructions, but would still recommend NVIDIA GPU and the proprietary drivers. 

This is the steam version of skyrim: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=24749](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24749)

---

### Post by Wx83kXJ on 2013-08-10
I installed Steam, and updated the game.  Whenever I launch Skyrim from Steam, I get this message (attached).

This is the error information:
```
Unhandled exception: unimplemented function msvcp90.dll.??0?$basic_ifstream@_WU?$char_traits@_W@std@@@std@@QAE@PB_WHH@Z called in 32-bit code (0x7b839cf2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b839cf2 ESP:0033f7a0 EBP:0033f804 EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b826245 EBX:7b894ff4 ECX:7e5ad340 EDX:0033f7c0
 ESI:80000100 EDI:00429ef0
Stack dump:
0x0033f7a0:  0033f824 00000008 0041db3c 80000100
0x0033f7b0:  00000001 00000000 7b839cf2 00000002
0x0033f7c0:  7e5ad340 7e5b0992 00000004 7e5d3550
0x0033f7d0:  0041db3c 0033f8bc 0033f7ec 00403e52
0x0033f7e0:  00000001 00000000 0013c858 0033f81c
0x0033f7f0:  00403059 0033fb18 7b839caa 00000000
Backtrace:
=>0 0x7b839cf2 in kernel32 (+0x29cf2) (0x0033f804)
  1 0x7e5ad2a8 in msvcp90 (+0x3d2a7) (0x0033f834)
  2 0x7e578825 in msvcp90 (+0x8824) (0x0033fd38)
  3 0x0040a040 in skyrimlauncher (+0xa03f) (0x0033fd38)
  4 0x00412633 in skyrimlauncher (+0x12632) (0x0033fde0)
  5 0x00407acf in skyrimlauncher (+0x7ace) (0x0033fe70)
  6 0x7b859cdc call_process_entry+0xb() in kernel32 (0x0033fe88)
  7 0x7b85af4f in kernel32 (+0x4af4e) (0x0033fec8)
  8 0x7bc71db0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  9 0x7bc7486d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  10 0x7bc71d8e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  11 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x7b839cf2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (93 modules)
PE      400000-  5d2000    Export          skyrimlauncher
PE    10000000-100a3000    Deferred        gameoverlayrenderer
PE    3b400000-3b41e000    Deferred        steam_api
ELF    7b800000-7ba15000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d68a000-7d69d000    Deferred        gnome-keyring-pkcs11.so
ELF    7d69d000-7d6a6000    Deferred        librt.so.1
ELF    7d6a6000-7d6ab000    Deferred        libgpg-error.so.0
ELF    7d6ab000-7d6c3000    Deferred        libresolv.so.2
ELF    7d6c3000-7d70c000    Deferred        libdbus-1.so.3
ELF    7d70c000-7d71e000    Deferred        libp11-kit.so.0
ELF    7d71e000-7d7a3000    Deferred        libgcrypt.so.11
ELF    7d7a3000-7d7b5000    Deferred        libtasn1.so.3
ELF    7d7b5000-7d7be000    Deferred        libkrb5support.so.0
ELF    7d7be000-7d7e6000    Deferred        libk5crypto.so.3
ELF    7d7e6000-7d8b5000    Deferred        libkrb5.so.3
ELF    7d8b5000-7d8c7000    Deferred        libavahi-client.so.3
ELF    7d8c7000-7d8d5000    Deferred        libavahi-common.so.3
ELF    7d8d5000-7d999000    Deferred        libgnutls.so.26
ELF    7d999000-7d9d7000    Deferred        libgssapi_krb5.so.2
ELF    7d9d7000-7da2a000    Deferred        libcups.so.2
ELF    7df28000-7df5c000    Deferred        uxtheme<elf>
  \-PE    7df30000-7df5c000    \               uxtheme
ELF    7df5c000-7df62000    Deferred        libxfixes.so.3
ELF    7df62000-7df6d000    Deferred        libxcursor.so.1
ELF    7df71000-7df75000    Deferred        libkeyutils.so.1
ELF    7df75000-7df7a000    Deferred        libcom_err.so.2
ELF    7dfe3000-7e00d000    Deferred        libexpat.so.1
ELF    7e00d000-7e041000    Deferred        libfontconfig.so.1
ELF    7e041000-7e051000    Deferred        libxi.so.6
ELF    7e051000-7e055000    Deferred        libxcomposite.so.1
ELF    7e055000-7e05e000    Deferred        libxrandr.so.2
ELF    7e05e000-7e068000    Deferred        libxrender.so.1
ELF    7e068000-7e06e000    Deferred        libxxf86vm.so.1
ELF    7e06e000-7e075000    Deferred        libxdmcp.so.6
ELF    7e075000-7e096000    Deferred        libxcb.so.1
ELF    7e096000-7e0b0000    Deferred        libice.so.6
ELF    7e0b0000-7e1e4000    Deferred        libx11.so.6
ELF    7e1e4000-7e1f6000    Deferred        libxext.so.6
ELF    7e1f6000-7e1ff000    Deferred        libsm.so.6
ELF    7e20e000-7e2a1000    Deferred        winex11<elf>
  \-PE    7e220000-7e2a1000    \               winex11
ELF    7e2a1000-7e2b7000    Deferred        libz.so.1
ELF    7e2b7000-7e351000    Deferred        libfreetype.so.6
ELF    7e351000-7e373000    Deferred        imm32<elf>
  \-PE    7e360000-7e373000    \               imm32
ELF    7e373000-7e39b000    Deferred        msacm32<elf>
  \-PE    7e380000-7e39b000    \               msacm32
ELF    7e39b000-7e448000    Deferred        winmm<elf>
  \-PE    7e3a0000-7e448000    \               winmm
ELF    7e448000-7e48b000    Deferred        dsound<elf>
  \-PE    7e450000-7e48b000    \               dsound
ELF    7e48b000-7e4ba000    Deferred        msvcr90<elf>
  \-PE    7e490000-7e4ba000    \               msvcr90
ELF    7e4ba000-7e547000    Deferred        msvcrt<elf>
  \-PE    7e4d0000-7e547000    \               msvcrt
ELF    7e547000-7e62c000    Dwarf           msvcp90<elf>
  \-PE    7e570000-7e62c000    \               msvcp90
ELF    7e62c000-7e6a1000    Deferred        rpcrt4<elf>
  \-PE    7e640000-7e6a1000    \               rpcrt4
ELF    7e6a1000-7e7a9000    Deferred        ole32<elf>
  \-PE    7e6c0000-7e7a9000    \               ole32
ELF    7e7a9000-7e8a1000    Deferred        comctl32<elf>
  \-PE    7e7b0000-7e8a1000    \               comctl32
ELF    7e8a1000-7e8ba000    Deferred        version<elf>
  \-PE    7e8b0000-7e8ba000    \               version
ELF    7e8ba000-7e977000    Deferred        gdi32<elf>
  \-PE    7e8d0000-7e977000    \               gdi32
ELF    7e977000-7eab7000    Deferred        user32<elf>
  \-PE    7e990000-7eab7000    \               user32
ELF    7eab7000-7eb21000    Deferred        shlwapi<elf>
  \-PE    7eac0000-7eb21000    \               shlwapi
ELF    7eb21000-7ed32000    Deferred        shell32<elf>
  \-PE    7eb30000-7ed32000    \               shell32
ELF    7ed32000-7ed92000    Deferred        advapi32<elf>
  \-PE    7ed40000-7ed92000    \               advapi32
ELF    7ed92000-7ed9f000    Deferred        libnss_files.so.2
ELF    7ed9f000-7edab000    Deferred        libnss_nis.so.2
ELF    7edab000-7edc5000    Deferred        libnsl.so.1
ELF    7efc5000-7eff1000    Deferred        libm.so.6
ELF    7eff3000-7eff9000    Deferred        libuuid.so.1
ELF    b7490000-b7494000    Deferred        libxinerama.so.1
ELF    b7495000-b749a000    Deferred        libdl.so.2
ELF    b749a000-b7643000    Deferred        libc.so.6
ELF    b7644000-b765f000    Deferred        libpthread.so.0
ELF    b7660000-b7664000    Deferred        libxau.so.6
ELF    b7664000-b766d000    Deferred        libnss_compat.so.2
ELF    b766e000-b77b0000    Dwarf           libwine.so.1
ELF    b77b2000-b77d4000    Deferred        ld-linux.so.2
ELF    b77d4000-b77d5000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000027    0
    0000001e    0
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
00000023 explorer.exe
    00000024    0
00000029 Steam.exe
    00000056    0
    00000055    0
    00000054    0
    00000053    0
    00000052    0
    00000051    0
    00000050    0
    0000004f    0
    0000004e    0
    0000004d    0
    0000004a    0
    00000048    0
    00000035    0
    00000018    0
    00000017    0
    0000002b    0
    0000002c    0
    0000002d    0
    00000009    0
    00000045    0
    00000032    0
    00000031    0
    0000000d    0
    0000000b    0
    00000026    0
    0000001f    0
    00000021    0
    00000028    0
    00000025    0
    00000022    0
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
    00000033    0
    00000030    0
    0000002f    0
    0000002e    0
    0000002a    0
00000057 (D) C:\Program Files\Steam2\SteamApps\common\Skyrim\SkyrimLauncher.exe
    00000058    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-51-generic-pae
```

How do I fix this?  I have Xubuntu.

---

### Post by texaswriter on 2013-08-14
> **Wx83kXJ said:**
> I installed Steam, and updated the game.  Whenever I launch Skyrim from Steam, I get this message (attached).

This is the error information:
```
Unhandled exception: unimplemented function msvcp90.dll.??0?$basic_ifstream@_WU?$char_traits@_W@std@@@std@@QAE@PB_WHH@Z called in 32-bit code (0x7b839cf2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b839cf2 ESP:0033f7a0 EBP:0033f804 EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b826245 EBX:7b894ff4 ECX:7e5ad340 EDX:0033f7c0
 ESI:80000100 EDI:00429ef0
Stack dump:
0x0033f7a0:  0033f824 00000008 0041db3c 80000100
0x0033f7b0:  00000001 00000000 7b839cf2 00000002
0x0033f7c0:  7e5ad340 7e5b0992 00000004 7e5d3550
0x0033f7d0:  0041db3c 0033f8bc 0033f7ec 00403e52
0x0033f7e0:  00000001 00000000 0013c858 0033f81c
0x0033f7f0:  00403059 0033fb18 7b839caa 00000000
Backtrace:
=>0 0x7b839cf2 in kernel32 (+0x29cf2) (0x0033f804)
  1 0x7e5ad2a8 in msvcp90 (+0x3d2a7) (0x0033f834)
  2 0x7e578825 in msvcp90 (+0x8824) (0x0033fd38)
  3 0x0040a040 in skyrimlauncher (+0xa03f) (0x0033fd38)
  4 0x00412633 in skyrimlauncher (+0x12632) (0x0033fde0)
  5 0x00407acf in skyrimlauncher (+0x7ace) (0x0033fe70)
  6 0x7b859cdc call_process_entry+0xb() in kernel32 (0x0033fe88)
  7 0x7b85af4f in kernel32 (+0x4af4e) (0x0033fec8)
  8 0x7bc71db0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  9 0x7bc7486d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  10 0x7bc71d8e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  11 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x7b839cf2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (93 modules)
PE      400000-  5d2000    Export          skyrimlauncher
PE    10000000-100a3000    Deferred        gameoverlayrenderer
PE    3b400000-3b41e000    Deferred        steam_api
ELF    7b800000-7ba15000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d68a000-7d69d000    Deferred        gnome-keyring-pkcs11.so
ELF    7d69d000-7d6a6000    Deferred        librt.so.1
ELF    7d6a6000-7d6ab000    Deferred        libgpg-error.so.0
ELF    7d6ab000-7d6c3000    Deferred        libresolv.so.2
ELF    7d6c3000-7d70c000    Deferred        libdbus-1.so.3
ELF    7d70c000-7d71e000    Deferred        libp11-kit.so.0
ELF    7d71e000-7d7a3000    Deferred        libgcrypt.so.11
ELF    7d7a3000-7d7b5000    Deferred        libtasn1.so.3
ELF    7d7b5000-7d7be000    Deferred        libkrb5support.so.0
ELF    7d7be000-7d7e6000    Deferred        libk5crypto.so.3
ELF    7d7e6000-7d8b5000    Deferred        libkrb5.so.3
ELF    7d8b5000-7d8c7000    Deferred        libavahi-client.so.3
ELF    7d8c7000-7d8d5000    Deferred        libavahi-common.so.3
ELF    7d8d5000-7d999000    Deferred        libgnutls.so.26
ELF    7d999000-7d9d7000    Deferred        libgssapi_krb5.so.2
ELF    7d9d7000-7da2a000    Deferred        libcups.so.2
ELF    7df28000-7df5c000    Deferred        uxtheme<elf>
  \-PE    7df30000-7df5c000    \               uxtheme
ELF    7df5c000-7df62000    Deferred        libxfixes.so.3
ELF    7df62000-7df6d000    Deferred        libxcursor.so.1
ELF    7df71000-7df75000    Deferred        libkeyutils.so.1
ELF    7df75000-7df7a000    Deferred        libcom_err.so.2
ELF    7dfe3000-7e00d000    Deferred        libexpat.so.1
ELF    7e00d000-7e041000    Deferred        libfontconfig.so.1
ELF    7e041000-7e051000    Deferred        libxi.so.6
ELF    7e051000-7e055000    Deferred        libxcomposite.so.1
ELF    7e055000-7e05e000    Deferred        libxrandr.so.2
ELF    7e05e000-7e068000    Deferred        libxrender.so.1
ELF    7e068000-7e06e000    Deferred        libxxf86vm.so.1
ELF    7e06e000-7e075000    Deferred        libxdmcp.so.6
ELF    7e075000-7e096000    Deferred        libxcb.so.1
ELF    7e096000-7e0b0000    Deferred        libice.so.6
ELF    7e0b0000-7e1e4000    Deferred        libx11.so.6
ELF    7e1e4000-7e1f6000    Deferred        libxext.so.6
ELF    7e1f6000-7e1ff000    Deferred        libsm.so.6
ELF    7e20e000-7e2a1000    Deferred        winex11<elf>
  \-PE    7e220000-7e2a1000    \               winex11
ELF    7e2a1000-7e2b7000    Deferred        libz.so.1
ELF    7e2b7000-7e351000    Deferred        libfreetype.so.6
ELF    7e351000-7e373000    Deferred        imm32<elf>
  \-PE    7e360000-7e373000    \               imm32
ELF    7e373000-7e39b000    Deferred        msacm32<elf>
  \-PE    7e380000-7e39b000    \               msacm32
ELF    7e39b000-7e448000    Deferred        winmm<elf>
  \-PE    7e3a0000-7e448000    \               winmm
ELF    7e448000-7e48b000    Deferred        dsound<elf>
  \-PE    7e450000-7e48b000    \               dsound
ELF    7e48b000-7e4ba000    Deferred        msvcr90<elf>
  \-PE    7e490000-7e4ba000    \               msvcr90
ELF    7e4ba000-7e547000    Deferred        msvcrt<elf>
  \-PE    7e4d0000-7e547000    \               msvcrt
ELF    7e547000-7e62c000    Dwarf           msvcp90<elf>
  \-PE    7e570000-7e62c000    \               msvcp90
ELF    7e62c000-7e6a1000    Deferred        rpcrt4<elf>
  \-PE    7e640000-7e6a1000    \               rpcrt4
ELF    7e6a1000-7e7a9000    Deferred        ole32<elf>
  \-PE    7e6c0000-7e7a9000    \               ole32
ELF    7e7a9000-7e8a1000    Deferred        comctl32<elf>
  \-PE    7e7b0000-7e8a1000    \               comctl32
ELF    7e8a1000-7e8ba000    Deferred        version<elf>
  \-PE    7e8b0000-7e8ba000    \               version
ELF    7e8ba000-7e977000    Deferred        gdi32<elf>
  \-PE    7e8d0000-7e977000    \               gdi32
ELF    7e977000-7eab7000    Deferred        user32<elf>
  \-PE    7e990000-7eab7000    \               user32
ELF    7eab7000-7eb21000    Deferred        shlwapi<elf>
  \-PE    7eac0000-7eb21000    \               shlwapi
ELF    7eb21000-7ed32000    Deferred        shell32<elf>
  \-PE    7eb30000-7ed32000    \               shell32
ELF    7ed32000-7ed92000    Deferred        advapi32<elf>
  \-PE    7ed40000-7ed92000    \               advapi32
ELF    7ed92000-7ed9f000    Deferred        libnss_files.so.2
ELF    7ed9f000-7edab000    Deferred        libnss_nis.so.2
ELF    7edab000-7edc5000    Deferred        libnsl.so.1
ELF    7efc5000-7eff1000    Deferred        libm.so.6
ELF    7eff3000-7eff9000    Deferred        libuuid.so.1
ELF    b7490000-b7494000    Deferred        libxinerama.so.1
ELF    b7495000-b749a000    Deferred        libdl.so.2
ELF    b749a000-b7643000    Deferred        libc.so.6
ELF    b7644000-b765f000    Deferred        libpthread.so.0
ELF    b7660000-b7664000    Deferred        libxau.so.6
ELF    b7664000-b766d000    Deferred        libnss_compat.so.2
ELF    b766e000-b77b0000    Dwarf           libwine.so.1
ELF    b77b2000-b77d4000    Deferred        ld-linux.so.2
ELF    b77d4000-b77d5000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000027    0
    0000001e    0
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
00000023 explorer.exe
    00000024    0
00000029 Steam.exe
    00000056    0
    00000055    0
    00000054    0
    00000053    0
    00000052    0
    00000051    0
    00000050    0
    0000004f    0
    0000004e    0
    0000004d    0
    0000004a    0
    00000048    0
    00000035    0
    00000018    0
    00000017    0
    0000002b    0
    0000002c    0
    0000002d    0
    00000009    0
    00000045    0
    00000032    0
    00000031    0
    0000000d    0
    0000000b    0
    00000026    0
    0000001f    0
    00000021    0
    00000028    0
    00000025    0
    00000022    0
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
    00000033    0
    00000030    0
    0000002f    0
    0000002e    0
    0000002a    0
00000057 (D) C:\Program Files\Steam2\SteamApps\common\Skyrim\SkyrimLauncher.exe
    00000058    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-51-generic-pae
```

How do I fix this?  I have Xubuntu.

First off, can you provide more about your system like CPU, memory, graphics cards, driver type for graphics card. 
Secondly, what procedures did you follow to install Steam/Skyrim?

---

### Post by Wx83kXJ on 2013-08-15
Thank you for your reply!

I have a ThinkPad Edge 15 with a Core i5 processor that includes Integrated Graphics 3000.  I am not sure if there is a driver for integrated graphics, but I tried installing some video driver from Lenovo's website, but I got an error message saying something like my computer is not capable of installing software.

I installed Skyrim by loading the installation .exe file from the disc using WINE.  Steam will load, and the game will update.  It's just that whenever I try to launch the game, I get that error message.

**EDIT: Nevermind, I no longer need to play Skyrim on Xubuntu.  Thanks anyway**.  :)

---

