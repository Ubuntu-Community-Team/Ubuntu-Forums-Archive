---
title: "Brood war wont connect to Bnet"
date: 2007-08-28
forum: Wine
---

### Post by Opeth115 on 2007-08-28
Ive recently installed Starcraft and Brood war on my feisty fawn box.  Everything works fine except for battle.net.  Every time i try to log in the program just crashes and closes it&#347;elf.  I tried applying the latest patch from the download section of the Blizzard website but it still does the same thing...  Here is the error i get form running it through the terminal:

```
matt@ubuntu:~$ wine ´/home/matt/.wine/drive_c/Program Files/Starcraft/Starcraft.exe´
fixme:win:EnumDisplayDevicesW ((null),0,0x33f4e4,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x130b38) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12e658)->(0x10024,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
wine: Unhandled page fault on write access to 0x013fc000 at address 0x7d0480 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x013fc000 in 32-bit code (0x007d0480).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:007d0480 ESP:0033f080 EBP:0033f140 EFLAGS:00010206(   - 00      - RIP1)
 EAX:cccd676b EBX:007d0078 ECX:00000000 EDX:00000010
 ESI:02838914 EDI:013fc000
Stack dump:
0x0033f080:  00000000 013e2000 013e2000 00000000
0x0033f090:  0281e910 00000000 7ce0dff4 0033f0ec
0x0033f0a0:  7cdf2155 7ce0edac 00130368 0000006c
0x0033f0b0:  00000001 7c19e924 7e58e94c 7c0c2098
0x0033f0c0:  00000000 0033f0cc 00130368 00000000
0x0033f0d0:  7e4cf6e5 7c036dd0 00000280 013b0000
Backtrace:
=>1 0x007d0480 (0x0033f140)
  2 0x1500194d in storm (+0x194d) (0x00000280)
  3 0x00000000 (0x00000000)
0x007d0480: movl        %eax,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (104 modules)
PE        400000-  6bb000       Deferred        starcraft
PE       2000000- 2011000       Deferred        local
PE      10000000-1001a000       Deferred        smackw32
PE      15000000-1503a000       Export          storm
PE      19000000-19046000       Deferred        battle.snp
ELF     41000000-41114000       Deferred        libwine.so.1
ELF     47cd7000-47cf2000       Deferred        ld-linux.so.2
ELF     47cf4000-486d5000       Deferred        libglcore.so.1
ELF     47ed6000-47f07000       Deferred        libcups.so.2
ELF     486d7000-486d9000       Deferred        libnvidia-tls.so.1
ELF     486db000-4881c000       Deferred        libc.so.6
ELF     4881e000-48822000       Deferred        libdl.so.2
ELF     48824000-4884b000       Deferred        libm.so.6
ELF     4884d000-48864000       Deferred        libpthread.so.0
ELF     48866000-4887a000       Deferred        libz.so.1
ELF     4887c000-48881000       Deferred        libxdmcp.so.6
ELF     48883000-4889b000       Deferred        libxcb.so.1
ELF     4889d000-48989000       Deferred        libx11.so.6
ELF     4898b000-4898e000       Deferred        libxau.so.6
ELF     48990000-48992000       Deferred        libxcb-xlib.so.0
ELF     48994000-489a2000       Deferred        libxext.so.6
ELF     48a3b000-48a43000       Deferred        libxrender.so.1
ELF     48a45000-48ab0000       Deferred        libfreetype.so.6
ELF     48ab2000-48add000       Deferred        libfontconfig.so.1
ELF     48adf000-48aff000       Deferred        libexpat.so.1
ELF     48b26000-48b2b000       Deferred        libxfixes.so.3
ELF     48b2d000-48b33000       Deferred        libxrandr.so.2
ELF     48b35000-48b3e000       Deferred        libxcursor.so.1
ELF     48b90000-48b99000       Deferred        libsm.so.6
ELF     48b9b000-48bb3000       Deferred        libice.so.6
ELF     490b6000-490cd000       Deferred        libnsl.so.1
ELF     490cf000-490e2000       Deferred        libresolv.so.2
ELF     490e4000-490f0000       Deferred        libgcc_s.so.1
ELF     49207000-4921c000       Deferred        libtasn1.so.3
ELF     4921e000-4928e000       Deferred        libgnutls.so.13
ELF     492de000-492e2000       Deferred        libgpg-error.so.0
ELF     492e4000-49335000       Deferred        libgcrypt.so.11
ELF     496d0000-496fe000       Deferred        libcrypt.so.1
ELF     4970c000-49711000       Deferred        libxxf86vm.so.1
ELF     4a267000-4a306000       Deferred        libgl.so.1
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c5ca000-7c5f7000       Deferred        ws2_32<elf>
  \-PE  7c5d0000-7c5f7000       \               ws2_32
ELF     7c5f7000-7c611000       Deferred        wsock32<elf>
  \-PE  7c600000-7c611000       \               wsock32
ELF     7ca55000-7ca7b000       Deferred        msacm32<elf>
  \-PE  7ca60000-7ca7b000       \               msacm32
ELF     7ca7b000-7cb09000       Deferred        winmm<elf>
  \-PE  7ca90000-7cb09000       \               winmm
ELF     7cc40000-7cc7a000       Deferred        wineoss<elf>
  \-PE  7cc50000-7cc7a000       \               wineoss
ELF     7cc84000-7cc9c000       Deferred        msacm32<elf>
  \-PE  7cc90000-7cc9c000       \               msacm32
ELF     7cc9c000-7cce5000       Deferred        dsound<elf>
  \-PE  7cca0000-7cce5000       \               dsound
ELF     7cce5000-7cdba000       Deferred        wined3d<elf>
  \-PE  7cd00000-7cdba000       \               wined3d
ELF     7cdba000-7ce0f000       Deferred        ddraw<elf>
  \-PE  7cdc0000-7ce0f000       \               ddraw
ELF     7d055000-7d06a000       Deferred        midimap<elf>
  \-PE  7d060000-7d06a000       \               midimap
ELF     7d0a1000-7d0bf000       Deferred        iphlpapi<elf>
  \-PE  7d0b0000-7d0bf000       \               iphlpapi
ELF     7d0bf000-7d118000       Deferred        rpcrt4<elf>
  \-PE  7d0d0000-7d118000       \               rpcrt4
ELF     7d118000-7d1b7000       Deferred        ole32<elf>
  \-PE  7d130000-7d1b7000       \               ole32
ELF     7d1b7000-7d1e9000       Deferred        uxtheme<elf>
  \-PE  7d1c0000-7d1e9000       \               uxtheme
ELF     7d4a0000-7d4bd000       Deferred        imm32<elf>
  \-PE  7d4b0000-7d4bd000       \               imm32
ELF     7e5db000-7e665000       Deferred        winex11<elf>
  \-PE  7e5f0000-7e665000       \               winex11
ELF     7e7bd000-7e7d7000       Deferred        version<elf>
  \-PE  7e7c0000-7e7d7000       \               version
ELF     7e7d7000-7e80c000       Deferred        winspool<elf>
  \-PE  7e7e0000-7e80c000       \               winspool
ELF     7e80c000-7e8ca000       Deferred        comctl32<elf>
  \-PE  7e820000-7e8ca000       \               comctl32
ELF     7e8ca000-7e923000       Deferred        shlwapi<elf>
  \-PE  7e8e0000-7e923000       \               shlwapi
ELF     7e923000-7ea26000       Deferred        shell32<elf>
  \-PE  7e930000-7ea26000       \               shell32
ELF     7ea26000-7eac7000       Deferred        comdlg32<elf>
  \-PE  7ea30000-7eac7000       \               comdlg32
ELF     7eac7000-7eb0f000       Deferred        advapi32<elf>
  \-PE  7ead0000-7eb0f000       \               advapi32
ELF     7ec08000-7ec1c000       Deferred        lz32<elf>
  \-PE  7ec10000-7ec1c000       \               lz32
ELF     7ec1c000-7ecdc000       Deferred        gdi32<elf>
  \-PE  7ec30000-7ecdc000       \               gdi32
ELF     7ecdc000-7ee1a000       Deferred        user32<elf>
  \-PE  7ed00000-7ee1a000       \               user32
ELF     7ee1a000-7ee81000       Deferred        msvcrt<elf>
  \-PE  7ee30000-7ee81000       \               msvcrt
ELF     7ee81000-7ee9b000       Deferred        crtdll<elf>
  \-PE  7ee90000-7ee9b000       \               crtdll
ELF     7efeb000-7eff6000       Deferred        libnss_files.so.2
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d42000-b7d4b000       Deferred        libnss_compat.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000b 
        0000000d    0
        0000000c    0
00000008 (D) C:\Program_Files\Starcraft\Starcraft.exe
        00000013    2
        00000012    0
        00000011   15
        00000010   15
        0000000a    1
        00000009    0 <==

```

---

### Post by Opeth115 on 2007-08-28
anyone have any idea?

EDIT:  Fixed nevermind

---

### Post by jcfisher on 2007-09-07
How did you fix it?  I'm having the same problem.

---

### Post by Dadsiepootwo on 2007-09-13
OMG, someone actually fixed that problem? PLEASE post the solution this prob is way beyond me to fix!

---

### Post by heimo11656 on 2007-09-14
Must Have Solution!

---

### Post by yowshi on 2007-09-15
yes please share the solution. i wanna play on bnet

the solution is you have to download the fonts for wine. that will elt you get into bnet. but the bnet display is rather...well you'll see when you log on

---

### Post by jcfisher on 2007-09-16
I had seen something like that... Which fonts do you have to download to make it work, and is there a special way to download them?

---

### Post by yowshi on 2007-09-16
i think it's the msttcorefonts in synaptic. will take a while to download the whole lot.

---

### Post by jcfisher on 2007-09-17
That did the trick -- thank you.

---

### Post by yowshi on 2007-09-17
no problem :) dont forget to look me up on bnet east under the nick yowshi

---

### Post by heimo11656 on 2007-09-22
I can get in with the screwed up menus and everything... then I go into a game and it starts out fine.

But as the game progresses it begins to lag badly (in terms of both connection and my own computer). Eventually it becomes unplayably laggy.

This doesnt happen on single player no matter how many units on the screen

---

### Post by OrbitWhite on 2008-03-18
I Did the fonts thing.. and everything...

Basically my game runs fine single player. But when i try to connect to bnet this thing comes up:

[IMG]http://i203.photobucket.com/albums/aa312/OrbitWhitex/Screenshot-7.png[/IMG]
and then freezes like that

---

### Post by OrbitWhite on 2008-03-18
Ok... i installed the latest patch... this time it gave me a choice of Realms. I  chose US EAST and clicked "OK"

now its stuck on this screen: [IMG]http://i203.photobucket.com/albums/aa312/OrbitWhitex/Screenshot-8.png[/IMG]

---

### Post by OrbitWhite on 2008-03-22
Can someone please help me... :(

---

### Post by Y2K Blackout on 2009-06-06
I have downloaded the fonts and I have patched to the latest version of BroodWar.

I still cannot connect to Bnet. Something about Blizzard not being able to detect which version that I am using.

Here's what I see:

[http://picasaweb.google.com/lh/photo/HEhnRkxhs6tu7Jq5CWCeeg?authkey=Gv1sRgCOuSvNXww4W0dQ&feat=directlink](http://picasaweb.google.com/lh/photo/HEhnRkxhs6tu7Jq5CWCeeg?authkey=Gv1sRgCOuSvNXww4W0dQ&feat=directlink)

(also attached to this msg)

---

