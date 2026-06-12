---
title: "Sacred Underworld"
date: 2007-03-08
forum: Wine
---

### Post by oVIXx on 2007-03-08
Has anyone gotten Sacred Underworld to work? I've been trying since Wine 0.9.28 but no luck. It installs fine and launches good, because of the latest game patch (2.28) doesn't require a game cd to play sacred anymore, so no need for game loader hax. But as soon and the graphic for loading the game comes up, it crashes. I tried launching it from the terminal instead of the menu shortcut, and I got a big list of errors. Can anyone help me interpret this message or give me some useful advice on how they got it to work. The message is....

:~/.wine/drive_c/Games/Sacred$ wine sacred.exe
fixme:system:SystemParametersInfoW Unimplemented action: 8192 (SPI_GETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:imm:ImmReleaseContext (0x10024, 0x183cc8): stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x18f808) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x18eec0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x18f2a0)->(0x10024,00000c08)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x18f2a0) Unhandled flag DDSCL_MULTITHREADED, Uh Oh...
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x18f2a0)->(1,(nil)): Stub
wine: Unhandled page fault on read access to 0x0000026c at address 0x7e5b1e26 (thread 000d), starting debugger...
Unhandled exception: page fault on read access to 0x0000026c in 32-bit code (0x7e5b1e26).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e5b1e26 ESP:7a6458ac EBP:7a645928 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:7c669158 ECX:0018fa78 EDX:001dc440
 ESI:001ddc40 EDI:00000000
Stack dump:
0x7a6458ac:  7c5d4bc0 00000405 7c6640a8 7a645918
0x7a6458bc:  7a64590c 7c664108 03440380 00000028
0x7a6458cc:  7c669158 001dc440 7c6640a8 7a645928
0x7a6458dc:  7c619105 001dc440 7c6640a8 7a6459a4
0x7a6458ec:  00440000 7bc28b00 001dc9c8 00000000
0x7a6458fc:  7bc28b00 034504a0 00000000 00000148
Backtrace:
=>1 0x7e5b1e26 glTexImage2D+0x266() in libgl.so.1 (0x7a645928)
  2 0x7c61f75c in wined3d (+0x5f75c) (0x7a6459b8)
  3 0x7c619e5a IWineD3DSurfaceImpl_ReleaseDC+0x32() in wined3d (0x7a6459e8)
  4 0x7ee88064 in ddraw (+0x28064) (0x7a645a18)
  5 0x00646b3d in sacred (+0x246b3d) (0x03432cfc)
0x7e5b1e26 glTexImage2D+0x266 in libgl.so.1: jmp        *0x26c(%eax)
Modules:
Module  Address                 Debug info      Name (86 modules)
PE      340000-394000   Deferred        tincat2
PE      400000-1d6c000  Export          sacred
PE      1d70000-1e2f000 Deferred        libxml2
PE      1e30000-1f05000 Deferred        iconv
PE      10000000-10084000       Deferred        granny
PE      21100000-21164000       Deferred        mss32
PE      60000000-60058000       Deferred        ijl15
ELF     7b800000-7b923000       Deferred        kernel32<elf>
  \-PE  7b820000-7b923000       \               kernel32
ELF     7bc00000-7bc93000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc93000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c536000-7c5b0000       Deferred        libglu.so.1
ELF     7c5b0000-7c66a000       Export          wined3d<elf>
  \-PE  7c5c0000-7c66a000       \               wined3d
ELF     7c66a000-7c67f000       Deferred        midimap<elf>
  \-PE  7c670000-7c67f000       \               midimap
ELF     7c6a5000-7c6e1000       Deferred        wineoss<elf>
  \-PE  7c6b0000-7c6e1000       \               wineoss
ELF     7d801000-7d819000       Deferred        msacm32<elf>
  \-PE  7d810000-7d819000       \               msacm32
ELF     7d81b000-7d820000       Deferred        libxfixes.so.3
ELF     7d820000-7d829000       Deferred        libxcursor.so.1
ELF     7d829000-7d847000       Deferred        ximcp.so.2
ELF     7d847000-7d849000       Deferred        xlcutf8load.so.2
ELF     7d849000-7d84c000       Deferred        libxrandr.so.2
ELF     7d84c000-7d854000       Deferred        libxrender.so.1
ELF     7d854000-7d857000       Deferred        libxinerama.so.1
ELF     7dd70000-7dd72000       Deferred        libnvidia-tls.so.1
ELF     7dd72000-7e535000       Deferred        libglcore.so.1
ELF     7e535000-7e5ba000       Export          libgl.so.1
ELF     7e5ba000-7e646000       Deferred        winex11<elf>
  \-PE  7e5d0000-7e646000       \               winex11
ELF     7e646000-7e664000       Deferred        libexpat.so.1
ELF     7e664000-7e693000       Deferred        libfontconfig.so.1
ELF     7e693000-7e6a7000       Deferred        libz.so.1
ELF     7e6a7000-7e711000       Deferred        libfreetype.so.6
ELF     7e711000-7e72a000       Deferred        version<elf>
  \-PE  7e720000-7e72a000       \               version
ELF     7e72a000-7e746000       Deferred        imm32<elf>
  \-PE  7e730000-7e746000       \               imm32
ELF     7e746000-7e7dd000       Deferred        oleaut32<elf>
  \-PE  7e760000-7e7dd000       \               oleaut32
ELF     7e7dd000-7e808000       Deferred        ws2_32<elf>
  \-PE  7e7f0000-7e808000       \               ws2_32
ELF     7e808000-7e822000       Deferred        wsock32<elf>
  \-PE  7e810000-7e822000       \               wsock32
ELF     7e822000-7e884000       Deferred        msvcrt<elf>
  \-PE  7e830000-7e884000       \               msvcrt
ELF     7e884000-7e911000       Deferred        winmm<elf>
  \-PE  7e890000-7e911000       \               winmm
ELF     7e911000-7e924000       Deferred        libresolv.so.2
ELF     7e924000-7e943000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e943000       \               iphlpapi
ELF     7e943000-7e997000       Deferred        rpcrt4<elf>
  \-PE  7e950000-7e997000       \               rpcrt4
ELF     7e997000-7e9a2000       Deferred        libgcc_s.so.1
ELF     7e9a3000-7e9b7000       Deferred        lz32<elf>
  \-PE  7e9b0000-7e9b7000       \               lz32
ELF     7ea96000-7eb4b000       Deferred        gdi32<elf>
  \-PE  7eab0000-7eb4b000       \               gdi32
ELF     7eb4b000-7ec81000       Deferred        user32<elf>
  \-PE  7eb70000-7ec81000       \               user32
ELF     7ec81000-7ecc5000       Deferred        advapi32<elf>
  \-PE  7ec90000-7ecc5000       \               advapi32
ELF     7ecc5000-7ed5b000       Deferred        ole32<elf>
  \-PE  7ecd0000-7ed5b000       \               ole32
ELF     7ed5b000-7ed60000       Deferred        libxdmcp.so.6
ELF     7ed60000-7ee29000       Deferred        libx11.so.6
ELF     7ee29000-7ee36000       Deferred        libxext.so.6
ELF     7ee36000-7ee4e000       Deferred        libice.so.6
ELF     7ee4e000-7ee57000       Deferred        libsm.so.6
ELF     7ee57000-7eea5000       Export          ddraw<elf>
  \-PE  7ee60000-7eea5000       \               ddraw
ELF     7efaf000-7efc5000       Deferred        libnsl.so.1
ELF     7efc5000-7efeb000       Deferred        libm.so.6
ELF     7efeb000-7eff6000       Deferred        libnss_files.so.2
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d10000-b7d15000       Deferred        libxxf86vm.so.1
ELF     b7d15000-b7d1e000       Deferred        libnss_compat.so.2
ELF     b7d1f000-b7d23000       Deferred        libdl.so.2
ELF     b7d23000-b7e57000       Deferred        libc.so.6
ELF     b7e57000-b7e6a000       Deferred        libpthread.so.0
ELF     b7e6b000-b7e6e000       Deferred        libxau.so.6
ELF     b7e7f000-b7f90000       Deferred        libwine.so.1
ELF     b7f92000-b7fad000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Games\Sacred\sacred.exe
        0000000d    0 <==
        00000009    0

 Thats a lot of messages, I don't know which is bad or keeping sacred from launching correctly.
Any suggestion?  Thanx in advance.

---

### Post by timjayko on 2007-03-09
wait for sacred 2 and dual boot windows and linux

---

### Post by Gannin on 2007-03-09
I would say your best bet at this point is just to post a bug with Wine about the game.

---

### Post by oVIXx on 2007-04-06
> timjayko: wait for sacred 2 and dual boot windows and linux

  That's it? Thats your reply? People post here to find answers to questions, better not to bother posting than write something like that. What you posted is not even a well thought out post.
  
  Fist off, I already CAN dual boot os's, no need for that having 3 rigs. 
  
  Secondly, Sacred won the buggiest game EVER award. Four years after the initial release and using an expansion pack as a patch (which is just bad business) and it's still riddled full of glitches and bugs. So that leaves Sacred 2 out of the question, too many better made games out there.

  You see it's an experiment for experience, I want to try and get the game to run on Ubuntu using Wine, I already have it running on Win 2K.

> Gannin: I would say your best bet at this point is just to post a bug with Wine about the game.

  I tried that one before posting here, but to no avail. Not even one reply on the app db post for Sacred Underworld.:(  But after a few weeks of reading and searching I've found a potential problem lying with my video card. That particular rig has a cheapo MSI MX440 SE video card, which I'm finding out is notorious for not working even as good as a Geo 3 series card. It has something to do with how it loads the graphics system, or lack thereof. I'll try loading up Sacred again when I get around to swapping out the video card. If anything changes I'll re-post.

---

### Post by hikaricore on 2007-04-06
Sorry the game doesn't work in wine.

[http://appdb.winehq.org/appview.php?iAppId=1898](http://appdb.winehq.org/appview.php?iAppId=1898)

Every review for every version is labeled as garbage.

You will need to dual boot unless you find another solution, wine isn't it.

---

### Post by Gannin on 2007-04-06
When I mentioned posting a bug about it, I didn't mean in their application database.  They have a bugzilla bug tracker system, and that's where the bug should go.

---

### Post by oni5115 on 2008-10-27
I know it's an old post, but I figure I'd post anyways just in case its useful to someone.

I did some digging today and discovered some posts on the german ubuntu forums describing the game would run fine when wine was in windowed mode, but not when wine was fullscreen. (Something to do with widescreen resolutions blowing up the game I assume.)

Using windowed mode, the game auto sets itself to 1024x768 or 800x600 as appropriate.  In wine FullScreen mode it just explodes - unless I set my desktop resolution to 1024x768.

I manually modified my xorg.conf to handle 1680x1050 and 1024x768 (laptop, so I use twinView and flat panel).  Then wrote a shell script to launch the game.

```

#!/bin/bash

xrandr -s 1024x768
sleep 2

#wine command goes here

xrandr -s 1680x1050

```

Running the script will set the resolution to the games default, run the game, then switch back to whatever you use by default (1680x1050 in my case) after you're done.

Seems to work perfectly for me now.  You could try out various resolutions as well.  If my assumption about it being wide screen exploding the game is correct, perhaps you can do higher resolutions as long as they are the correct ratio.

Works fine for me using Ubuntu 8.04, Wine 1.1.7, and Sacred Gold 2.28.  I know Sacred 2 is coming out soon, but I figured I'd explore sacred 1 before 2 comes out.

---

