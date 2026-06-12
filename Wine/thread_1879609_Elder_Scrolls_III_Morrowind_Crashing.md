---
title: "Elder Scrolls III: Morrowind Crashing"
date: 2011-11-11
forum: Wine
---

### Post by SirDakkalot on 2011-11-11
I'm using Ubuntu 11.10 and what I'm pretty sure is the newest version of WINE. I've been attempting to play Morrowind GOTY Edition through Steam, but it immediately crashes with the error "Morrowind Launcher.exe has encountered a serious problem". I've tried several things on the wineHQ site (what I could wrap my head around, anyways), and non of it worked. Here's the output from the console:

```
wine c:/Program\ Files/Steam/steamapps/common/Morrowind/Morrowind\ Launcher.exe
wine: Call from 0x7ed27f72 to unimplemented function msvcp60.dll.??0Init@ios_base@std@@QAE@XZ, aborting
wine: Unimplemented function msvcp60.dll.??0Init@ios_base@std@@QAE@XZ called at address 0x7ed27f72 (thread 0077), starting debugger...
Unhandled exception: unimplemented function msvcp60.dll.??0Init@ios_base@std@@QAE@XZ called in 32-bit code (0x7ed27f72).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7ed27f72 ESP:0032fcc8 EBP:0032fd2c EFLAGS:00000287(   - --  I S - -P-C)
 EAX:7ed140fd EBX:7ed90ff4 ECX:7e06ecd2 EDX:0032fce8
 ESI:80000100 EDI:0052f570
Stack dump:
0x0032fcc8:  0032fd4c 00000008 0052f570 80000100
0x0032fcd8:  00000001 00000000 7ed27f72 00000002
0x0032fce8:  7e06ecd2 7e0754b9 000000fc 7e043560
0x0032fcf8:  0032fd48 7ef64d3f 7e043660 00000000
0x0032fd08:  00000000 00000000 00000000 7e03aff4
0x0032fd18:  0032fd48 0032fd70 7ed27f2a 7e03aff4
Backtrace:
=>0 0x7ed27f72 in kernel32 (+0x27f72) (0x0032fd2c)
  1 0x7e06ec78 in msvcp60 (+0x1ec77) (0x0032fd5c)
  2 0x7e05d885 in msvcp60 (+0xd884) (0x0032fdc0)
  3 0x00402065 in morrowind launcher (+0x2064) (0x0032fdc0)
  4 0x004dca86 in morrowind launcher (+0xdca85) (0x0032fe70)
  5 0x7ed47a4c call_process_entry+0xb() in kernel32 (0x0032fe88)
  6 0x7ed48aef in kernel32 (+0x48aee) (0x0032fec8)
  7 0x7efa2de0 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  8 0x7efa5bbd call_thread_func+0x7c() in ntdll (0x0032ffa8)
  9 0x7efa2dbe RtlRaiseException+0x21() in ntdll (0x0032ffc8)
  10 0x7ef79f0e call_dll_entry_point+0x33d() in ntdll (0x0032ffe8)
  11 0xf76966ad wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
0x7ed27f72: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (75 modules)
PE      400000-  7c2000    Export          morrowind launcher
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7da0b000-7dabb000    Deferred        winex11<elf>
  \-PE    7da20000-7dabb000    \               winex11
ELF    7dbb2000-7dbe8000    Deferred        uxtheme<elf>
  \-PE    7dbc0000-7dbe8000    \               uxtheme
ELF    7dbe8000-7dbee000    Deferred        libxfixes.so.3
ELF    7dbee000-7dbf9000    Deferred        libxcursor.so.1
ELF    7dc65000-7dc8f000    Deferred        libexpat.so.1
ELF    7dc8f000-7dcc4000    Deferred        libfontconfig.so.1
ELF    7dcc4000-7dcd4000    Deferred        libxi.so.6
ELF    7dcd4000-7dcd8000    Deferred        libxcomposite.so.1
ELF    7dcd8000-7dce1000    Deferred        libxrandr.so.2
ELF    7dce1000-7dcec000    Deferred        libxrender.so.1
ELF    7dcec000-7dcf2000    Deferred        libxxf86vm.so.1
ELF    7dcf2000-7dcf6000    Deferred        libxinerama.so.1
ELF    7dcf6000-7dd1a000    Deferred        imm32<elf>
  \-PE    7dd00000-7dd1a000    \               imm32
ELF    7dd1a000-7dd21000    Deferred        libxdmcp.so.6
ELF    7dd21000-7dd40000    Deferred        libxcb.so.1
ELF    7dd40000-7dd46000    Deferred        libuuid.so.1
ELF    7dd46000-7dd60000    Deferred        libice.so.6
ELF    7dd60000-7de96000    Deferred        libx11.so.6
ELF    7de96000-7dea9000    Deferred        libxext.so.6
ELF    7dea9000-7deb2000    Deferred        libsm.so.6
ELF    7deb2000-7df49000    Deferred        libfreetype.so.6
ELF    7df49000-7df68000    Deferred        libtinfo.so.5
ELF    7df68000-7df8a000    Deferred        libncurses.so.5
ELF    7dfaa000-7e044000    Deferred        msvcrt<elf>
  \-PE    7dfc0000-7e044000    \               msvcrt
ELF    7e044000-7e0c9000    Dwarf           msvcp60<elf>
  \-PE    7e050000-7e0c9000    \               msvcp60
ELF    7e0c9000-7e0f5000    Deferred        msacm32<elf>
  \-PE    7e0d0000-7e0f5000    \               msacm32
ELF    7e0f5000-7e172000    Deferred        rpcrt4<elf>
  \-PE    7e100000-7e172000    \               rpcrt4
ELF    7e172000-7e299000    Deferred        ole32<elf>
  \-PE    7e190000-7e299000    \               ole32
ELF    7e299000-7e342000    Deferred        winmm<elf>
  \-PE    7e2a0000-7e342000    \               winmm
ELF    7e342000-7e486000    Deferred        wined3d<elf>
  \-PE    7e350000-7e486000    \               wined3d
ELF    7e486000-7e4bc000    Deferred        d3d8<elf>
  \-PE    7e490000-7e4bc000    \               d3d8
ELF    7e4bc000-7e5c2000    Deferred        comctl32<elf>
  \-PE    7e4c0000-7e5c2000    \               comctl32
ELF    7e5c2000-7e633000    Deferred        shlwapi<elf>
  \-PE    7e5d0000-7e633000    \               shlwapi
ELF    7e633000-7e862000    Deferred        shell32<elf>
  \-PE    7e640000-7e862000    \               shell32
ELF    7e862000-7e87c000    Deferred        version<elf>
  \-PE    7e870000-7e87c000    \               version
ELF    7e87c000-7e8e4000    Deferred        advapi32<elf>
  \-PE    7e890000-7e8e4000    \               advapi32
ELF    7e8e4000-7e99e000    Deferred        gdi32<elf>
  \-PE    7e8f0000-7e99e000    \               gdi32
ELF    7e99e000-7eaee000    Deferred        user32<elf>
  \-PE    7e9b0000-7eaee000    \               user32
ELF    7ecee000-7eeb2000    Dwarf           kernel32<elf>
  \-PE    7ed00000-7eeb2000    \               kernel32
ELF    7eeb2000-7eebf000    Deferred        libnss_files.so.2
ELF    7eebf000-7eecb000    Deferred        libnss_nis.so.2
ELF    7eecb000-7eee4000    Deferred        libnsl.so.1
ELF    7eee4000-7ef0e000    Deferred        libm.so.6
ELF    7ef0e000-7ef12000    Deferred        libxau.so.6
ELF    7ef12000-7ef27000    Deferred        libz.so.1
ELF    7ef2e000-7f000000    Dwarf           ntdll<elf>
  \-PE    7ef40000-7f000000    \               ntdll
ELF    f74d2000-f74d7000    Deferred        libdl.so.2
ELF    f74d7000-f7651000    Deferred        libc.so.6
ELF    f7652000-f766d000    Deferred        libpthread.so.0
ELF    f7683000-f768d000    Deferred        libnss_compat.so.2
ELF    f768d000-f77d0000    Dwarf           libwine.so.1
ELF    f77d2000-f77f2000    Deferred        ld-linux.so.2
ELF    f77f2000-f77f3000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001e    0
    0000001d    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    0000001f    0
    0000001c    0
    0000001b    0
00000020 explorer.exe
    00000021    0
00000079 Steam.exe
    00000092    1
    00000046    0
    00000045    0
    00000044    0
    00000043    1
    00000042    1
    00000041    0
    00000040    0
    0000003f    0
    0000003d    0
    0000003e    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
    00000036    0
    00000035    0
    00000033    0
    00000032    0
    00000030    0
    0000002b    0
    00000023    0
    0000002a    0
    00000028    0
    00000027    0
    00000026    0
    00000024    0
    00000031    0
    0000002f    0
    0000002e    0
    0000002d    0
    00000029    0
    00000083    0
    0000007c    0
    00000069    0
    00000068    0
    00000065    0
    00000051    0
    00000017    0
    00000067    0
    00000052    0
    0000007a    0
    0000007b    0
    00000078    0
00000072 (D) C:\Program Files\Steam\steamapps\common\Morrowind\Morrowind Launcher.exe
    00000077    0 <==
Backtrace:
=>0 0x7ed27f72 in kernel32 (+0x27f72) (0x0032fd2c)
  1 0x7e06ec78 in msvcp60 (+0x1ec77) (0x0032fd5c)
  2 0x7e05d885 in msvcp60 (+0xd884) (0x0032fdc0)
  3 0x00402065 in morrowind launcher (+0x2064) (0x0032fdc0)
  4 0x004dca86 in morrowind launcher (+0xdca85) (0x0032fe70)
  5 0x7ed47a4c call_process_entry+0xb() in kernel32 (0x0032fe88)
  6 0x7ed48aef in kernel32 (+0x48aee) (0x0032fec8)
  7 0x7efa2de0 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  8 0x7efa5bbd call_thread_func+0x7c() in ntdll (0x0032ffa8)
  9 0x7efa2dbe RtlRaiseException+0x21() in ntdll (0x0032ffc8)
  10 0x7ef79f0e call_dll_entry_point+0x33d() in ntdll (0x0032ffe8)
  11 0xf76966ad wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
wine: Call from 0x7ed27f72 to unimplemented function msvcp60.dll.??0Init@ios_base@std@@QAE@XZ, aborting
wine: Call from 0x7ed27f72 to unimplemented function msvcp60.dll.??0Init@ios_base@std@@QAE@XZ, aborting
```

---

### Post by SirDakkalot on 2011-11-12
Bump

---

### Post by SirDakkalot on 2011-11-12
All right, so I decided I'd try using PlayOnLinux to install Morrowind. Thing is, I don't know how to do it with PlayOnLinux because I have Morrowind on Steam, which there doesn't seem to be an option for. Does anyone have any tips for this?

---

### Post by Dlambert on 2011-11-12
Um, I'm not sure about steam...but have you tried OpenMW? 

> What is OpenMW?

OpenMW is an attempt to reimplement the popular role playing game Morrowind. It aims to be a fully playable, open source implementation of the game. You must own Morrowind to use OpenMW.
To give you a better idea of what this project is about, here are some of the aims for the future of OpenMW:
be a full featured reimplementation of Morrowind
run natively on Windows, Linux and MacOS X
support all existing content, including Tribunal, Bloodmoon and all user created mods
allow much greater modability: change game rules, create new spell effects, etc through scripting.
fix system design bugs, like the "dirty" GMST entries in mods, and the savegame "doubling" problem
improve the interface and journal system
(possibly) improve game mechanics, physics, combat and AI
(possibly) support multiplayer at some point
(possibly) improve graphics to use more modern hardware
It's a pretty ambitious list, and there's a lot left to do before these goals can become reality. You should check below for information about the current development status.
OpenMW is released under the GNU General Public License version 3, all source code has been written completely from scratch. It also builds on various other open source tools, most notably OGRE for graphics.
Do I need Morrowind?

YES. You must legally own and install Morrowind before you can use OpenMW.
OpenMW is a reimplementation of the technical aspects of the game only. It does not come with ANY art, game data or other copyrighted material that you need to play the game. You have to provide these yourself, by installing Morrowind and then configuring OpenMW to use the existing installation.
Seriously, if you don't have Morrowind, go buy it. It's worth every penny even if it's no longer a "new" game. And besides, you can get it for peanuts these days.
What is the current development status?

Status
OpenMW is currently undergoing a port from D to C++, which means we have temporarily taken a step backwards in development, but this will phase will be over as soon as the rest of the old D code is translated. In any case, OpenMW is currently at a pre-alpha stage. Most of the work is going into lower-level engine features like graphics and sound, with very little work so far on the gameplay elements of the engine.

Supported platforms
The new code base is pure C++ and should work on most platforms supported by OGRE and our other dependencies. That includes Windows XP/Vista and newer, Linux, MacOS X, FreeBSD and more. However, the current development version has only been fully tested on Ubuntu Linux.
If you want to help test or port OpenMW on other platforms (like MacOS X), we'd love to hear from you on the newsgroup.
Features
This feature list applies to the OLD code base (written in D), but they should all be easy to port over to C++.
loads any interior cell (geometry, items, lights, and evironmental sounds) from the command line
renders maps, with somewhat natural lighting
basic character walk-and-fall physics, collision with walls and objects
GUI and HUD system
backend script system (using Monster script)
partially displays creature meshes, using leveled creature lists
basic sound and music support
backend can load Morrowind, Tribunal, Bloodmoon ESMs and any combination of mods
ignores dirty GMST entries in mods
loads data directly from .esm and .bsa files, as well as from the file system
loads meshes directly from .nif files
Still on the TODO list
any kind of animation or creature movement
interactivity and game mechanics
exterior cells with landscape
moving between cells
rendering NPCs (including the player)
everything else
What technologies do you use?

OpenMW is built with various open source tools and libraries:
Programming language: C++
Graphics: OGRE
Physics: Bullet
Sound: OpenAL and Audiere
GUI: MyGUI
Input: OIS
Scripting: not determined
The ESM/ESP and BSA loading code was written from scratch, but with much help from available community-generated documentation.
Likewise, the NIF (proprietary 3D mesh) loading code was written with the help of available online information. Special thanks to the NIFLA / NifTools gang!
I want to help!

If you have suggestions, ideas, comments, or if you want to contribute code, you are very welcome to join the official OpenMW forum / mailing list over at Google groups. To get new posts per email, just put your address in the box below:


[URL="http://openmw.org/"]
http://openmw.org/[/URL]

Hope this helps! :)

---

### Post by SirDakkalot on 2011-11-12
I decided to scratch the whole PlayOnLinux thing. Come one, isn't anyone going to help me? I've confirmed I'm running WINE 1.3.28, incidentally.

EDIT: Didn't notice that reply. I'll try it out.

EDIT 2: I'm pretty new to Linux. Which one do I download?

---

### Post by Dlambert on 2011-11-12
It's not perfect. But first, what version of Linux are you using?

---

### Post by Dlambert on 2011-11-12
msvcp60.dll Maybe install that dll into wine/ POL

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> It's not perfect. But first, what version of Linux are you using?

Sorry, I'm using Ubuntu 11.10 64-bit

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> msvcp60.dll Maybe install that dll into wine/ POL
If you're talking about putting that into the Morrowind installation folder, I all ready tried that. Didn't work.

---

### Post by Dlambert on 2011-11-12
Okay, did you use the play on linux script for installation?

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> Okay, did you use the play on linux script for installation?
No, I decided not to use POL. I just installed it with steam.

---

### Post by Dlambert on 2011-11-12
> **SirDakkalot said:**
> If you're talking about putting that into the Morrowind installation folder, I all ready tried that. Didn't work.

In terminal, type winecfg

Go to libraries (i think) find that dll and set it to native or built in. You could also use play on linux to install it by clicking configure then install

---

### Post by Dlambert on 2011-11-12
> **SirDakkalot said:**
> No, I decided not to use POL. I just installed it with steam.

That's gonna be more tricky...

---

### Post by Dlambert on 2011-11-12
> WINETRICKS:
d3dx9 + vcrun6sp6 

WINE SETTINGS:
In winecfg: sound is set to emulation,  Morrowind.exe and Morrowind Launcher.exe set to use Windows 98 

Taken from : [http://www.steamgamesonlinux.com/the-elder-scrolls-iii-morrowind/]("http://www.steamgamesonlinux.com/the-elder-scrolls-iii-morrowind/")

Latest version of wine right?

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> Taken from : [http://www.steamgamesonlinux.com/the-elder-scrolls-iii-morrowind/](http://www.steamgamesonlinux.com/the-elder-scrolls-iii-morrowind/)

Latest version of wine right?

Correct, I'm using the latest version. I'm doing the winetricks for those now. Will set to windows 98 compatibility mode. I don't see a spot for emulation in the audio tab anymore, which is strange. Adding the dll to libraries did nothing as far as I can tell.

EDIT: Nevermind, I found the emulation thing. It decided to go on a vacation, apparently.

---

### Post by Dlambert on 2011-11-12
> **SirDakkalot said:**
> Correct, I'm using the latest version. I'm doing the winetricks for those now. Will set to windows 98 compatibility mode. I don't see a spot for emulation in the audio tab anymore, which is strange. Adding the dll to libraries did nothing as far as I can tell.

EDIT: Nevermind, I found the emulation thing. It decided to go on a vacation, apparently.

And PlayOnLinux is a great tool for having several WINE setups without modifying the main one

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> And PlayOnLinux is a great tool for having several WINE setups without modifying the main one
I garnered that. I'm going to look into prefixes later.

EDIT: I've finished with the winetricks downloads, set Morrowind to 98, and set sound to emulation now. Tried launching Morrowind again, no dice. The .dll should look like "msvcp60 (native,builtin)" (no quotation marks) right? I noticed that everything else in libraries has an asterisk next to it.

---

### Post by Dlambert on 2011-11-12
Hows it going now?

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> Hows it going now?

Being the paranoid I am, I'm going to go ahead and make sure you noticed my edit in the comment above yours.

---

### Post by Dlambert on 2011-11-12
Try installing it in POL, no steam (if you have the cds)

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> Try installing it in POL, no steam (if you have the cds)

I don't, unfortunately. Theoretically I could always download an ISO and mount the image.

---

### Post by Dlambert on 2011-11-12
try just sh winetricks vcrun6

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> try just sh winetricks vcrun6

```
sh winetricks vcrun6
Executing w_do_call vcrun6
vcrun6 already installed, skipping

```

---

### Post by Dlambert on 2011-11-12
Solution: download the dll from here and place it in .wine/drive_c/windows/system to get rid of that error and be able to successfully apply the patch. [http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60]("http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60")

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> Solution: download the dll from here and place it in .wine/drive_c/windows/system to get rid of that error and be able to successfully apply the patch. [http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)

Do you mean msvcp60.dll?

EDIT:Nevermind, I'm an idiot.

---

### Post by Dlambert on 2011-11-12
Try it, it may be systems32 but try system first

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> Try it, it may be systems32 but try system first
Oh man, it worked! Funny, considering the only difference between it and the one I had (as far as I can tell) was capitalization.

EDIT: Oh, and thanks a bundle for your help, mate.

---

### Post by Dlambert on 2011-11-12
Not a problem at all. So the game is running? If so mark this thread as SOLVED!

---

### Post by Dlambert on 2011-11-12
I'll take the long response time as a YES! Well game on my friend, game on. Befriend me if you want.

---

### Post by SirDakkalot on 2011-11-12
> **Dlambert said:**
> I'll take the long response time as a YES! Well game on my friend, game on. Befriend me if you want.

Haha, sorry. Someone asked me to help them with something on Minecraft right when I got it working. Anyways, thanks for all the help.

---

