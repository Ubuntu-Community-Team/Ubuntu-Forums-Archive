---
title: "Playing Windows games through Steam (wine question)"
date: 2013-03-06
forum: Wine
---

### Post by areyouamogul on 2013-03-06
Hi everybody.

I'm trying to play games through Steam/Wine. Installing drivers+steam went smooth, but i've run into a problem while trying to make the actual game work. I'll appreciate your helping!

I installed Wine 1.4.1, and Steam right afterwards. Windows version ofc. Prior to that I'd downloaded Nvidia drivers, in such a manner that the 'Nvidia X Server...' now appears as an app.
Then I've downloaded a game (Magicka). And I've tried to play straight after, no previous configuration done through Wine Config whatsoever. There has to be something wrong, given that this message pops:

<<[I]Application has generated an exception that could not be handled.

Process ID=0x4B (75) Thread ID=0x18 (24).

Click OK to terminate the application.
Click Cancel to debug the application.[/I]>>

Debuging will lead to another message stating that I have no specific JIT debugger. Opting to allow the thing to find one by itself will do nothing. 
Regardless of what I do, a generic ''Program has encountered serious problem'' window will appear at the end of it, and the Magicka.exe will shut down. 

Thanks beforehands guys

---

### Post by Asatru9 on 2013-03-06
I suppose the first question(s) I have is are you trying to simply play on steam or are you trying to play your Windows games on steam?  If you are trying to play Windows games on steam try updating WINE and see how it goes.  Also which version of Ubuntu are you using?  Lastly have you checked the WINE website for compatibility for the game(s) you're trying to play?

The second link is for Magicka using WINE 1.5.16 and it's got a Gold rating.

[URL="http://appdb.winehq.org/"]http://appdb.winehq.org/

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12683](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12683)
[/URL]

---

### Post by areyouamogul on 2013-03-06
Ubuntu 12.10

I'm trying to play Steam games, I don't know what the difference may be between those two things you said. 

... Now this has to be awesome. Just updated Wine, and now most things in Steam wont even show up, menus and fonts missing. The game still won't run, now it throws some different error.

---

### Post by Asatru9 on 2013-03-06
I was talking about if you were wanting to play that one game specifically or more whatever games you had on steam in general.  Well, is Ubuntu fully updated?  If it is than try restarting the computer (this may or may not be needed but I'm throwing out some ideas that have worked for me).  Are you able to put the error message up on the forum that could help give a better more specific answer.  You updated to 1.5.25 WINE or something else?

---

### Post by areyouamogul on 2013-03-06
Updated to 1.5.25

Ubuntu is fully updated as far as I know. Will find out upon restarting though. 

The error message is basically the same thing I wrote on the first post, only the numbers between the parenthesis seem to have changed. 

Proceeding to restart.

---

### Post by areyouamogul on 2013-03-06
rebooting won't solve a thing.

What happens is that some of the windows while on Steam will pop 'empty', with no words in them. 

Also the main menu categories 'Magazine, Community, Games, etc'' doesn't even show up. It's like empty.

Here's the error:

Unhandled exception: 0xe0434f4d in 32-bit code (0x7b83bc25).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b83bc25 ESP:0033e1a4 EBP:0033e218 EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b82684d EBX:7b8b4ff4 ECX:80070002 EDX:0033e1c4
 ESI:00000001 EDI:e0434f4d
Stack dump:
0x0033e1a4:  0033e260 00000004 01e422e4 e0434f4d
0x0033e1b4:  00000001 00000000 7b83bc25 00000001
0x0033e1c4:  80070002 790c20c8 79fd4e9d 00000036
0x0033e1d4:  790c2000 00000036 00000006 790fabcc
0x0033e1e4:  79e7be3f e0434f4d 0033e260 790c2000
0x0033e1f4:  02000036 0033e20c 79e814da 0033e218
Backtrace:
=>0 0x7b83bc25 in kernel32 (+0x2bc25) (0x0033e218)
  1 0x79f97065 in mscorwks (+0x127064) (0x0033e288)
  2 0x7a05b942 in mscorwks (+0x1eb941) (0x0033e2c4)
  3 0x7a05b9eb in mscorwks (+0x1eb9ea) (0x0033e2f0)
  4 0x7a05b9f6 in mscorwks (+0x1eb9f5) (0x0033e3d0)
  5 0x79e96791 in mscorwks (+0x26790) (0x0033e450)
  6 0x79061526 in mscorjit (+0x1525) (0x0033e9b8)
0x7b83bc25: movl    0xfffffff0(%ebp),%ecx
Modules:
Module    Address            Debug info    Name (129 modules)
PE      400000-  6a6000    Export          magicka
PE     4070000- 4cf6000    Deferred        system.windows.forms.ni
PE     4d10000- 4d6b000    Deferred        steamwrapper
PE     5070000- 5077000    Deferred        x3daudio1_6
PE     50f0000- 510c000    Deferred        microsoft.xna.framework.game
PE     5110000- 5212000    Deferred        microsoft.xna.framework
PE     5330000- 5597000    Deferred        d3dx9_31
PE     5600000- 568e000    Deferred        polygonhead
PE    10000000-10098000    Deferred        gameoverlayrenderer
PE    30000000-302c4000    Deferred        steam
PE    38000000-38700000    Deferred        steamclient
PE    3b400000-3b41e000    Deferred        steam_api
PE    3f000000-3f0a8000    Deferred        tier0_s
PE    3f600000-3f646000    Deferred        vstdlib_s
PE    5e380000-5e409000    Deferred        diasymreader
PE    60000000-60021000    Deferred        cserhelper
PE    78130000-781cb000    Deferred        msvcr80
PE    783f0000-78433000    Deferred        msvcm90
PE    78520000-785c3000    Deferred        msvcr90
PE    79000000-79045000    Deferred        mscoree
PE    79060000-790b3000    Export          mscorjit
PE    790c0000-79ba6000    Deferred        mscorlib.ni
PE    79e70000-7a3d1000    Export          mscorwks
PE    7a440000-7abfe000    Deferred        system.ni
PE    7ade0000-7af74000    Deferred        system.drawing.ni
ELF    7b800000-7ba45000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba45000    \               kernel32
ELF    7bc00000-7bcd9000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcd9000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d332000-7d350000    Deferred        libgcc_s.so.1
ELF    7d551000-7d5b9000    Deferred        dbghelp<elf>
  \-PE    7d560000-7d5b9000    \               dbghelp
ELF    7d5b9000-7d5cd000    Deferred        libp11-kit.so.0
ELF    7d5cd000-7d651000    Deferred        libgcrypt.so.11
ELF    7d651000-7d715000    Deferred        libgnutls.so.26
ELF    7d719000-7d72c000    Deferred        gnome-keyring-pkcs11.so
ELF    7d72c000-7d759000    Deferred        netapi32<elf>
  \-PE    7d730000-7d759000    \               netapi32
ELF    7d759000-7d78b000    Deferred        secur32<elf>
  \-PE    7d760000-7d78b000    \               secur32
ELF    7d78b000-7d7b1000    Deferred        iphlpapi<elf>
  \-PE    7d790000-7d7b1000    \               iphlpapi
ELF    7d7b1000-7d7cf000    Deferred        pdh<elf>
  \-PE    7d7c0000-7d7cf000    \               pdh
ELF    7d7cf000-7d7e3000    Deferred        psapi<elf>
  \-PE    7d7d0000-7d7e3000    \               psapi
ELF    7d7e3000-7d819000    Deferred        ws2_32<elf>
  \-PE    7d7f0000-7d819000    \               ws2_32
ELF    7d819000-7d844000    Deferred        msacm32<elf>
  \-PE    7d820000-7d844000    \               msacm32
ELF    7d844000-7d8f9000    Deferred        winmm<elf>
  \-PE    7d850000-7d8f9000    \               winmm
ELF    7d8f9000-7da37000    Deferred        msvcp90<elf>
  \-PE    7d930000-7da37000    \               msvcp90
ELF    7da37000-7db45000    Deferred        opengl32<elf>
  \-PE    7da50000-7db45000    \               opengl32
ELF    7db45000-7dc7e000    Deferred        wined3d<elf>
  \-PE    7db50000-7dc7e000    \               wined3d
ELF    7dc7e000-7dcbb000    Deferred        d3d9<elf>
  \-PE    7dc80000-7dcbb000    \               d3d9
ELF    7dcbb000-7ddf5000    Deferred        oleaut32<elf>
  \-PE    7dcd0000-7ddf5000    \               oleaut32
ELF    7ddf5000-7debe000    Deferred        crypt32<elf>
  \-PE    7de00000-7debe000    \               crypt32
ELF    7debe000-7df00000    Deferred        rsaenh<elf>
  \-PE    7dec0000-7df00000    \               rsaenh
ELF    7e005000-7e00a000    Deferred        libgpg-error.so.0
ELF    7e00a000-7e024000    Deferred        imagehlp<elf>
  \-PE    7e010000-7e024000    \               imagehlp
ELF    7e024000-7e05a000    Deferred        uxtheme<elf>
  \-PE    7e030000-7e05a000    \               uxtheme
ELF    7e05a000-7e162000    Deferred        comctl32<elf>
  \-PE    7e060000-7e162000    \               comctl32
ELF    7e162000-7e390000    Deferred        shell32<elf>
  \-PE    7e170000-7e390000    \               shell32
ELF    7e390000-7e436000    Deferred        msvcrt<elf>
  \-PE    7e3a0000-7e436000    \               msvcrt
ELF    7e436000-7e4ae000    Deferred        shlwapi<elf>
  \-PE    7e440000-7e4ae000    \               shlwapi
ELF    7e4ae000-7e4b5000    Deferred        libxfixes.so.3
ELF    7e4b5000-7e4c0000    Deferred        libxcursor.so.1
ELF    7e4c0000-7e4d0000    Deferred        libxi.so.6
ELF    7e4d0000-7e4d4000    Deferred        libxcomposite.so.1
ELF    7e4d4000-7e4df000    Deferred        libxrandr.so.2
ELF    7e4df000-7e4e9000    Deferred        libxrender.so.1
ELF    7e4e9000-7e4ef000    Deferred        libxxf86vm.so.1
ELF    7e4ef000-7e4f3000    Deferred        libxinerama.so.1
ELF    7e4f3000-7e4fa000    Deferred        libxdmcp.so.6
ELF    7e4fa000-7e4fe000    Deferred        libxau.so.6
ELF    7e4fe000-7e520000    Deferred        libxcb.so.1
ELF    7e520000-7e526000    Deferred        libuuid.so.1
ELF    7e526000-7e540000    Deferred        libice.so.6
ELF    7e540000-7e676000    Deferred        libx11.so.6
ELF    7e676000-7e688000    Deferred        libxext.so.6
ELF    7e688000-7e691000    Deferred        libsm.so.6
ELF    7e694000-7e6a6000    Deferred        libtasn1.so.3
ELF    7e6a8000-7e73b000    Deferred        winex11<elf>
  \-PE    7e6b0000-7e73b000    \               winex11
ELF    7e787000-7e7af000    Deferred        libexpat.so.1
ELF    7e7af000-7e7e7000    Deferred        libfontconfig.so.1
ELF    7e7e7000-7e800000    Deferred        libz.so.1
ELF    7e800000-7e89a000    Deferred        libfreetype.so.6
ELF    7e89a000-7e91b000    Deferred        rpcrt4<elf>
  \-PE    7e8b0000-7e91b000    \               rpcrt4
ELF    7e91b000-7ea56000    Deferred        ole32<elf>
  \-PE    7e930000-7ea56000    \               ole32
ELF    7ea56000-7ea70000    Deferred        version<elf>
  \-PE    7ea60000-7ea70000    \               version
ELF    7ea70000-7eadf000    Deferred        advapi32<elf>
  \-PE    7ea80000-7eadf000    \               advapi32
ELF    7eadf000-7ebfa000    Deferred        gdi32<elf>
  \-PE    7eaf0000-7ebfa000    \               gdi32
ELF    7ebfa000-7ed54000    Deferred        user32<elf>
  \-PE    7ec10000-7ed54000    \               user32
ELF    7ed54000-7ed78000    Deferred        imm32<elf>
  \-PE    7ed60000-7ed78000    \               imm32
ELF    7ed78000-7ed85000    Deferred        libnss_files.so.2
ELF    7ed85000-7ed91000    Deferred        libnss_nis.so.2
ELF    7ed91000-7edab000    Deferred        libnsl.so.1
ELF    7edab000-7edb4000    Deferred        libnss_compat.so.2
ELF    7efb4000-7efe0000    Deferred        libm.so.6
ELF    7efe0000-7efe9000    Deferred        librt.so.1
ELF    b73d4000-b73d9000    Deferred        libdl.so.2
ELF    b73d9000-b7583000    Deferred        libc.so.6
ELF    b7584000-b759f000    Deferred        libpthread.so.0
ELF    b75b6000-b76fa000    Dwarf           libwine.so.1
ELF    b76fc000-b771e000    Deferred        ld-linux.so.2
ELF    b771e000-b771f000    Deferred        [vdso].so
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
00000021 explorer.exe
    00000022    0
00000023 steam.exe
    00000057    0
    00000056    0
    0000004f    0
    0000004e    0
    0000004c    0
    0000004b    0
    0000004a    0
    00000049    0
    00000048    0
    0000002f    0
    0000000b    0
    00000040    0
    0000002c    0
    0000002b    0
    0000000d    0
    00000009    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043   15
    00000042    0
    00000041    0
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
    0000002d    0
    0000002a    0
    00000029    0
    00000028    0
    00000024    0
00000026 (D) C:\Program Files\Steam\SteamApps\common\Magicka\Magicka.exe
    00000018    2
    0000004d    0
    00000025    0 <==
System information:
    Wine build: wine-1.5.25
    Platform: i386
    Host system: Linux
    Host version: 3.5.0-25-generic

---

### Post by Asatru9 on 2013-03-06
The only other question I would have is are you running 64 bit or 32 bit Ubuntu?  Unfortunately the problem you are having has surpassed my knowledge at this time to be able to fix it.

---

