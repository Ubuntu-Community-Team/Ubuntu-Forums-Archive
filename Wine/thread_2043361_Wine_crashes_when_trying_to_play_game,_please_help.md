---
title: "Wine crashes when trying to play game, please help!"
date: 2012-08-16
forum: Wine
---

### Post by Futant on 2012-08-16
Hello, I've recently been experiencing problems running Morrowind in Wine, I have run it successfully in the past on this computer (Dell XPS L502X, Intel Core i5 2.0 GHz, Nvidia GeForce GT525) - the problems started shortly after (but not immediately) upgrading to Precise and Wine version 1.5.10. The fact that I've played it many times on this laptop, and that I have not had any other problems running things, means I don't think it is a graphics card issue, but I don't know really.

Whenever I try to run Morrowind lately (just the game, the installers worked fine) it usually crashes at or just before the menu screen. Wine becomes unresponsive and sometimes will not quit. Yesterday, after deleting the save files, the game actually loaded and played for a couple of minutes before crashing. I have tried running it in 'windows versions' 98, 2000, and Vista none of which make any difference. I have Play on Linux installed but haven't got anywhere with it and haven't used it lately, and I have not messed with anything in Winetricks.

Earlier today I tried running it from the terminal and got a black screen crash, which I used reisub to get out of (love that trick!). The next time I tried to run it from the terminal it did the usual crash at menu screen and I got this output: 
```

futant@futant-Dell-System-XPS-L502X:~$ wine "C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x32f024,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d03c,0x00000000), stub!
wine: Unhandled page fault on read access to 0x00000018 at address 0x6eb3c9 (thread 0009), starting debugger...

Unhandled exception: page fault on read access to 0x00000018 in 32-bit code (0x006eb3c9).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:006eb3c9 ESP:0032dc30 EBP:00020064 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:001c9ec0
 ESI:00000000 EDI:00000000
Stack dump:
0x0032dc30:  00000020 001cca88 00000000 00000000
0x0032dc40:  0032dc64 0032dc64 00734410 ffffffff
0x0032dc50:  0041aa1b 02e80400 00000005 00020064
0x0032dc60:  00000000 0032fa84 00728c48 ffffffff
0x0032dc70:  00416c17 00000400 00000300 00000020
0x0032dc80:  00020064 0032dd40 0032dcbc 7ed39ff4
Backtrace:
=>0 0x006eb3c9 in morrowind (+0x2eb3c9) (0x00020064)
0x006eb3c9: movl    0x18(%edi),%ecx
Modules:
Module    Address            Debug info    Name (92 modules)
PE      400000-  7e4000    Export          morrowind
PE    30000000-3006e000    Deferred        binkw32
PE    780c0000-78121000    Deferred        msvcp60
ELF    7b800000-7ba2d000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba2d000    \               kernel32
ELF    7bc00000-7bcc4000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc4000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cd07000-7cd4a000    Deferred        dinput<elf>
  \-PE    7cd10000-7cd4a000    \               dinput
ELF    7d82a000-7d835000    Deferred        libpciaccess.so.0
ELF    7d835000-7d853000    Deferred        libgcc_s.so.1
ELF    7d938000-7d957000    Deferred        libdrm_intel.so.1
ELF    7d957000-7da74000    Deferred        libglsl.so
ELF    7da74000-7dced000    Deferred        libdricore.so
ELF    7dced000-7ddcc000    Deferred        i965_dri.so
ELF    7ddcc000-7dde4000    Deferred        libxcb-glx.so.0
ELF    7dde4000-7dea3000    Deferred        opengl32<elf>
  \-PE    7de00000-7dea3000    \               opengl32
ELF    7dede000-7dee7000    Deferred        librt.so.1
ELF    7dee7000-7def4000    Deferred        libdrm.so.2
ELF    7def4000-7def7000    Deferred        libx11-xcb.so.1
ELF    7def7000-7defb000    Deferred        libxdamage.so.1
ELF    7defb000-7df11000    Deferred        libglapi.so.0
ELF    7df11000-7df6a000    Deferred        libgl.so.1
ELF    7df83000-7dfb7000    Deferred        uxtheme<elf>
  \-PE    7df90000-7dfb7000    \               uxtheme
ELF    7dfcd000-7dfd8000    Deferred        libxcursor.so.1
ELF    7e1c0000-7e1ea000    Deferred        libexpat.so.1
ELF    7e1ea000-7e21e000    Deferred        libfontconfig.so.1
ELF    7e21e000-7e22e000    Deferred        libxi.so.6
ELF    7e22e000-7e232000    Deferred        libxcomposite.so.1
ELF    7e232000-7e23b000    Deferred        libxrandr.so.2
ELF    7e23b000-7e245000    Deferred        libxrender.so.1
ELF    7e245000-7e24b000    Deferred        libxxf86vm.so.1
ELF    7e24b000-7e24f000    Deferred        libxinerama.so.1
ELF    7e24f000-7e271000    Deferred        imm32<elf>
  \-PE    7e260000-7e271000    \               imm32
ELF    7e271000-7e278000    Deferred        libxdmcp.so.6
ELF    7e278000-7e299000    Deferred        libxcb.so.1
ELF    7e299000-7e2b3000    Deferred        libice.so.6
ELF    7e2b3000-7e3e7000    Deferred        libx11.so.6
ELF    7e3e7000-7e3f9000    Deferred        libxext.so.6
ELF    7e3f9000-7e482000    Deferred        winex11<elf>
  \-PE    7e400000-7e482000    \               winex11
ELF    7e482000-7e498000    Deferred        libz.so.1
ELF    7e498000-7e532000    Deferred        libfreetype.so.6
ELF    7e532000-7e551000    Deferred        libtinfo.so.5
ELF    7e551000-7e573000    Deferred        libncurses.so.5
ELF    7e577000-7e57d000    Deferred        libxfixes.so.3
ELF    7e58c000-7e685000    Deferred        comctl32<elf>
  \-PE    7e590000-7e685000    \               comctl32
ELF    7e685000-7e713000    Deferred        msvcrt<elf>
  \-PE    7e6a0000-7e713000    \               msvcrt
ELF    7e713000-7e83b000    Deferred        wined3d<elf>
  \-PE    7e720000-7e83b000    \               wined3d
ELF    7e83b000-7e86c000    Deferred        d3d8<elf>
  \-PE    7e840000-7e86c000    \               d3d8
ELF    7e86c000-7e8b3000    Deferred        dsound<elf>
  \-PE    7e870000-7e8b3000    \               dsound
ELF    7e8b3000-7e8cf000    Deferred        dinput8<elf>
  \-PE    7e8c0000-7e8cf000    \               dinput8
ELF    7e8cf000-7e8f7000    Deferred        msacm32<elf>
  \-PE    7e8d0000-7e8f7000    \               msacm32
ELF    7e8f7000-7e9a5000    Deferred        winmm<elf>
  \-PE    7e900000-7e9a5000    \               winmm
ELF    7e9a5000-7ea1b000    Deferred        rpcrt4<elf>
  \-PE    7e9b0000-7ea1b000    \               rpcrt4
ELF    7ea1b000-7eb22000    Deferred        ole32<elf>
  \-PE    7ea30000-7eb22000    \               ole32
ELF    7eb22000-7eb3b000    Deferred        version<elf>
  \-PE    7eb30000-7eb3b000    \               version
ELF    7eb3b000-7eb9d000    Deferred        advapi32<elf>
  \-PE    7eb50000-7eb9d000    \               advapi32
ELF    7eb9d000-7ec61000    Deferred        gdi32<elf>
  \-PE    7ebb0000-7ec61000    \               gdi32
ELF    7ec61000-7eda1000    Deferred        user32<elf>
  \-PE    7ec70000-7eda1000    \               user32
ELF    7efa1000-7efbb000    Deferred        libnsl.so.1
ELF    7efbb000-7efe7000    Deferred        libm.so.6
ELF    7efe7000-7eff4000    Deferred        libnss_files.so.2
ELF    7eff4000-7f000000    Deferred        libnss_nis.so.2
ELF    b73b1000-b73b5000    Deferred        libxau.so.6
ELF    b73b5000-b73be000    Deferred        libnss_compat.so.2
ELF    b73bf000-b73c4000    Deferred        libdl.so.2
ELF    b73c4000-b7569000    Deferred        libc.so.6
ELF    b756a000-b7585000    Deferred        libpthread.so.0
ELF    b7586000-b758c000    Deferred        libuuid.so.1
ELF    b758c000-b7595000    Deferred        libsm.so.6
ELF    b759e000-b76e0000    Dwarf           libwine.so.1
ELF    b76e2000-b7704000    Deferred        ld-linux.so.2
ELF    b7704000-b7705000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe
    00000026    0
    00000009    0 
0000000e services.exe
    00000020    0
    0000001f    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    0000001a    0
    00000014    0
    00000013    0
0000001c plugplay.exe
    00000021    0
    0000001e    0
    0000001d    0
00000022 explorer.exe
    00000023    0

```None of this means anything to me! Please could someone shed a bit of light on this? Let me know if you need more information...

---

### Post by ergo-proxy on 2012-08-17
Did you make an upgrade or clean installation? If upgrade I would advise reinstalling wine.

---

### Post by Futant on 2012-08-17
Hey, thanks for replying. It was a clean install. This problem has been going on for about a month (I asked on here when it first happened, got no replies, and without you lot I'm lost!). Over that time I have un and reinstalled Wine, and the game, several times, to no avail...

---

### Post by ergo-proxy on 2012-08-17
Do you have 64bit or 32bit Ubuntu?

---

### Post by Futant on 2012-08-17
64 bit

---

### Post by ergo-proxy on 2012-08-17
In Ubuntu x64 default wineprefixes are 64bit and that might be the reason. In a terminal try this:
 
export WINEARCH=win32
export WINEPREFIX=/location/where/you/wanttostore/winefiles
wine "C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe"

---

### Post by Futant on 2012-08-17
Hey thanks I'll try that soon, got to go out now though...

---

### Post by Futant on 2012-08-27
Sorry for the late reply, just tried to take your advice, I'm doing something wrong... not used the terminal much at all and I need help :S  Here's what I got in the terminal when I finally typed it out.. ```
futant@futant-Dell-System-XPS-L502X:~$ export WINEARCH=win32 futant@futant-Dell-System-XPS-L502X:~$ export WINEPREFIX=/home/futant/Games/Morrowind  futant@futant-Dell-System-XPS-L502X:~$ wine &quot;C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe&quot;  wine: cannot find 'C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe'  futant@futant-Dell-System-XPS-L502X:~$
``` What mistakes am I making please?

---

### Post by javajames79 on 2012-08-29
> **Futant said:**
> Sorry for the late reply, just tried to take your advice, I'm doing something wrong... not used the terminal much at all and I need help :S  Here's what I got in the terminal when I finally typed it out.. ```
futant@futant-Dell-System-XPS-L502X:~$ export WINEARCH=win32 futant@futant-Dell-System-XPS-L502X:~$ export WINEPREFIX=/home/futant/Games/Morrowind  futant@futant-Dell-System-XPS-L502X:~$ wine &quot;C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe&quot;  wine: cannot find 'C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe'  futant@futant-Dell-System-XPS-L502X:~$
``` What mistakes am I making please?

You'l need to reinstall the Morrowwind app in the new wine prefix. From what wine said it sounds like you haven't actually got anything in your new wine prefix. Also, have you tried/are you using the PlayOnLinux script specifically for this game? (Which you can find by clicking install and then search Morrowin.) Usually the play on linux scripts are really successful, and if you have any problems to do with 32 bit libraries you can change the value of LD_LIBRARY_PATH to "/usr/lib32:/usr/lib/i386-linux-gnu"

---

### Post by Futant on 2012-08-29
> **javajames79 said:**
> You'l need to reinstall the Morrowwind app in the new wine prefix. From what wine said it sounds like you haven't actually got anything in your new wine prefix. Also, have you tried/are you using the PlayOnLinux script specifically for this game? (Which you can find by clicking install and then search Morrowin.) Usually the play on linux scripts are really successful, and if you have any problems to do with 32 bit libraries you can change the value of LD_LIBRARY_PATH to &quot;/usr/lib32:/usr/lib/i386-linux-gnu&quot;

Hello, thanks for your reply, and please excuse the COMPLETE noobness. Is my wine prefix the hidden .wine folder? If so Morrowind is installed in there, in drice_c/Program Files/Bethesda Softworks/Morrowind. I think I'm missing something. Also, I do have PlayOnLinux installed, can't remember doing much with it but in the POL folder there is a folder called 'wineprefix', and in there there are three folders 'default', 'Morrowind' and 'TES3 Morrowind'. In there there are various folders, similar to in the .wine folder, but inside Program Files there is no Bethesda Softworks etc. Is this perhaps where I need to install the game? I'm not sure if I've used a script for Morrowind, don't know what I'm doing AT ALL with POL... Stumbling in the dark!

---

### Post by javajames79 on 2012-08-29
"export WINEPREFIX=/home/futant/Games/Morrowind"

You posted this in your previous post. This would indicate that your wine prefix is in ~/Games/Morrowind. I assumed you hadn't installed the game there, and i might be right in that assumption.

Play on linux creates new prefix's specifically for certain games/apps. Usually to apply a specific patch to that "virtual os".

Open up play on linux, and you should see "Morrowind" and "TES3 Morrowind" in the main menu. If you don't you wont have it install through POL. And as you say, those prefix' don't have bethesda software folders in them. So maybe not. Try installing the morrowing app through the PlayOnLinux install menu - click install, then search "Morrowind", i got three results, i don't have the game so you may have to work that bit out :S. Select the game and click install

When you have it in the playonlinux menu, try selecting it, clicking configure, then enabling debugging. Then once it's crashed (ALT+F2 and xkill if the game appears to crash the OS, usually in wine it will never fully grab your keyboard.) you should get a log of what happened. If it's the same as before. Probably better try something else.

If you have it in playonlinux, it should be set to 32 bit mode, if it's trying to access 64bit libraries you could force it to use 32 bit libraries by running in terminal:

```
export LD_LIBRARY_PATH=/usr/lib32:/usr/lib/i386-linux-gnu
/usr/share/playonlinux/playonlinux --run "Morrowind"
``` where "Morrowind" is the name it displays in the play on linux menu.



Failing the auto installer script. It seems the unoficial bethesda wiki has a page for linux users; [http://www.uesp.net/wiki/Morrowind:Linux](http://www.uesp.net/wiki/Morrowind:Linux)

You could have a look at what they do there (although i imagine giving the nature of POL that it does the same thing though) and trying and replicate it, maybe getting some info along the way.

---

