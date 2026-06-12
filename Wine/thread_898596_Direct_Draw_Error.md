---
title: "Direct Draw Error"
date: 2008-08-23
forum: Wine
---

### Post by Niedra on 2008-08-23
Hello, I'm trying to run 2 old Blizzard games - Diablo II and StarCraft (both for Battle.net). But I can't manage to run them, not atliest fullscreen. I've tried changing Windows Version in winecfg, emulating a virtual desktop. Nothing seems to help. There were some times when I managed to run Diablo in emulated virtual desktop, but it's painful to play it that way. I have wine-1.1.3.

Diablo II terminal log:
```
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x8 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1680x1050x32 @0! (XRandR)
```
after that I get an popup saying
```
Error 22: A critical error has occurred while initializing DirectDraw
```

And terminal log for SC:
```
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f410,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x8 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1680x1050x8 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1680x1050x32 @0! (XRandR)
```
also I get **[this]("http://ubuntuforums.org/attachment.php?attachmentid=82567&d=1219511916")** popup.

I appreciated any help.

---

### Post by YokoZar on 2008-08-24
The problem launching 256 color apps is a bug in Wine, this might help: [http://wiki.winehq.org/256ColorsWorkarounds](http://wiki.winehq.org/256ColorsWorkarounds)

---

### Post by cherva on 2008-08-24
Wine version 1.1.3 has a MAJOR REGRESSION in DDRAW try version 1.1.2 with the Cure for slowness here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=149]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=149")

---

### Post by Niedra on 2008-08-24
> **cherva said:**
> Wine version 1.1.3 has a MAJOR REGRESSION in DDRAW try version 1.1.2 with the Cure for slowness here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149)

I noticed that I upgraded to 1.1.3 only yesterday. I installed 1.1.2 today, and tried what you suggested, but now I can only run it using emulated desktop. Is it even possible to run it fullscreen ? It's painful to play in a little window...

---

### Post by cherva on 2008-08-24
Well there should be no problem ... go to the Video tab in winecfg and remove the checkbox "Emulate a virtual desktop"

---

### Post by Niedra on 2008-08-24
Then I get the old errors again :( I'm not quite sure if the problem is in wine.

---

### Post by Twitch6000 on 2008-08-24
You could try installing the games through PlayOnLinux which is like Wine Doors And Cedega,but free and has its own goals.

I used it and I got my starcraft to run somewhat better in windowed mode.In fullscreen mode I have to use the cure for slowness and hope it connects lol.

Really for these games its all about luck right now,until the dib engine is made.

---

### Post by cherva on 2008-08-24
Niedra what video card do you have and did you installed the drivers for it ?

---

### Post by Niedra on 2008-08-24
I'll try PlayOnLinux, thanks.
I have a GeForce 6600GT and I have installed drivers for it.

---

### Post by Niedra on 2008-08-29
Finally got time to try PlayOnLinux, so I installed StarCraft, patched and tried to play. This is what terminal gives
```
wine: Unhandled page fault on read access to 0x0000000c at address 0x7dfbd63d (thread 001f), starting debugger...
Unhandled exception: page fault on read access to 0x0000000c in 32-bit code (0x7dfbd63d).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7dfbd63d ESP:0032f758 EBP:0032f890 EFLAGS:00010202(   - 00      - -RI1)
 EAX:0013d058 EBX:7e080e08 ECX:7e07a1e0 EDX:0032f8e0
 ESI:00000000 EDI:0013d058
Stack dump:
0x0032f758:  ffffffff 00000000 00000000 f7dbff8e
0x0032f768:  0032f788 0032f834 f7c9eb9c 0032f788
0x0032f778:  f7d8b940 00000000 00137c4c 00000000
0x0032f788:  f7edd48c 7e0da2c0 0032f7d0 f7dc0042
0x0032f798:  7e0da2c0 00137c5b ffffffff 00137c4c
0x0032f7a8:  ffffffff 00000000 00000000 7b867191
Backtrace:
=>1 0x7dfbd63d in wined3d (+0x2d63d) (0x0032f890)
  2 0x7e0996d5 in ddraw (+0x166d5) (0x0032f8f0)
  3 0x7e0a03cd in ddraw (+0x1d3cd) (0x0032f910)
  4 0x0041da00 in starcraft (+0x1da00) (0x0032fd9c)
  5 0x004dac97 in starcraft (+0xdac97) (0x0032fdbc)
  6 0x004e0437 in starcraft (+0xe0437) (0x0032fdd4)
  7 0x004e06e0 in starcraft (+0xe06e0) (0x0032fde0)
  8 0x00404da5 in starcraft (+0x4da5) (0x0032ff08)
  9 0x7b8780b7 in kernel32 (+0x580b7) (0x0032ffe8)
0x7dfbd63d: movl    0xc(%esi),%eax
Modules:
Module    Address            Debug info    Name (88 modules)
PE      400000-  6ec000    Export          starcraft
PE     2000000- 2011000    Deferred        local
PE    15000000-15069000    Deferred        storm
ELF    7b800000-7b93c000    Export          kernel32<elf>
  \-PE    7b820000-7b93c000    \               kernel32
ELF    7bc00000-7bca6000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bca6000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7d33b000-7de50000    Deferred        libglcore.so.1
ELF    7de50000-7def4000    Deferred        libgl.so.1
ELF    7def4000-7df75000    Deferred        opengl32<elf>
  \-PE    7df10000-7df75000    \               opengl32
ELF    7df75000-7e083000    Export          wined3d<elf>
  \-PE    7df90000-7e083000    \               wined3d
PE    7e083000-7e0db000    Export          ddraw
ELF    7e1ec000-7e1f0000    Deferred        libgpg-error.so.0
ELF    7e1f0000-7e23d000    Deferred        libgcrypt.so.11
ELF    7e23d000-7e24d000    Deferred        libtasn1.so.3
ELF    7e24d000-7e250000    Deferred        libkeyutils.so.1
ELF    7e250000-7e258000    Deferred        libkrb5support.so.0
ELF    7e258000-7e28a000    Deferred        libcrypt.so.1
ELF    7e28a000-7e2ff000    Deferred        libgnutls.so.13
ELF    7e2ff000-7e322000    Deferred        libk5crypto.so.3
ELF    7e322000-7e3af000    Deferred        libkrb5.so.3
ELF    7e3af000-7e3d8000    Deferred        libgssapi_krb5.so.2
ELF    7e3d8000-7e40b000    Deferred        libcups.so.2
ELF    7e42f000-7e442000    Deferred        libresolv.so.2
ELF    7e454000-7e473000    Deferred        iphlpapi<elf>
  \-PE    7e460000-7e473000    \               iphlpapi
ELF    7e473000-7e4d7000    Deferred        rpcrt4<elf>
  \-PE    7e480000-7e4d7000    \               rpcrt4
ELF    7e4d7000-7e57b000    Deferred        ole32<elf>
  \-PE    7e4f0000-7e57b000    \               ole32
ELF    7e5a3000-7e5d6000    Deferred        uxtheme<elf>
  \-PE    7e5b0000-7e5d6000    \               uxtheme
ELF    7e5d6000-7e5df000    Deferred        libxcursor.so.1
ELF    7e5df000-7e5e4000    Deferred        libxfixes.so.3
ELF    7e5e4000-7e5e7000    Deferred        libxcomposite.so.1
ELF    7e5e7000-7e5ed000    Deferred        libxrandr.so.2
ELF    7e5ed000-7e5f5000    Deferred        libxrender.so.1
ELF    7e5f5000-7e5fa000    Deferred        libxxf86vm.so.1
ELF    7e5fa000-7e5fd000    Deferred        libxinerama.so.1
ELF    7e5fd000-7e602000    Deferred        libxdmcp.so.6
ELF    7e602000-7e61a000    Deferred        libxcb.so.1
ELF    7e61a000-7e61d000    Deferred        libxau.so.6
ELF    7e61d000-7e704000    Deferred        libx11.so.6
ELF    7e704000-7e712000    Deferred        libxext.so.6
ELF    7e71d000-7e71f000    Deferred        libnvidia-tls.so.1
ELF    7e71f000-7e722000    Deferred        libcom_err.so.2
ELF    7e724000-7e7bc000    Deferred        winex11<elf>
  \-PE    7e730000-7e7bc000    \               winex11
ELF    7e7fb000-7e81c000    Deferred        libexpat.so.1
ELF    7e81c000-7e846000    Deferred        libfontconfig.so.1
ELF    7e858000-7e86d000    Deferred        libz.so.1
ELF    7e86d000-7e8dd000    Deferred        libfreetype.so.6
ELF    7e8dd000-7e8df000    Deferred        libxcb-xlib.so.0
ELF    7e8ef000-7e924000    Deferred        winspool<elf>
  \-PE    7e900000-7e924000    \               winspool
ELF    7e924000-7e9cf000    Deferred        comdlg32<elf>
  \-PE    7e930000-7e9cf000    \               comdlg32
ELF    7e9cf000-7ea8f000    Deferred        comctl32<elf>
  \-PE    7e9e0000-7ea8f000    \               comctl32
ELF    7ea8f000-7eae8000    Deferred        shlwapi<elf>
  \-PE    7eaa0000-7eae8000    \               shlwapi
ELF    7eae8000-7ec01000    Deferred        shell32<elf>
  \-PE    7eb00000-7ec01000    \               shell32
ELF    7ec01000-7ec15000    Deferred        lz32<elf>
  \-PE    7ec10000-7ec15000    \               lz32
ELF    7ec15000-7ec2e000    Deferred        version<elf>
  \-PE    7ec20000-7ec2e000    \               version
ELF    7ec2e000-7ec4e000    Deferred        imm32<elf>
  \-PE    7ec30000-7ec4e000    \               imm32
ELF    7ec4e000-7eca0000    Deferred        advapi32<elf>
  \-PE    7ec60000-7eca0000    \               advapi32
ELF    7eca0000-7ed3e000    Deferred        gdi32<elf>
  \-PE    7ecb0000-7ed3e000    \               gdi32
ELF    7ed3e000-7ee86000    Deferred        user32<elf>
  \-PE    7ed60000-7ee86000    \               user32
ELF    7efa6000-7efb1000    Deferred        libnss_files.so.2
ELF    7efb1000-7efc9000    Deferred        libnsl.so.1
ELF    7efc9000-7efee000    Deferred        libm.so.6
ELF    7eff6000-7f000000    Deferred        libnss_nis.so.2
ELF    f7c33000-f7c3c000    Deferred        libnss_compat.so.2
ELF    f7c3d000-f7c41000    Deferred        libdl.so.2
ELF    f7c41000-f7d90000    Deferred        libc.so.6
ELF    f7d91000-f7da9000    Deferred        libpthread.so.0
ELF    f7dbb000-f7ef1000    Deferred        libwine.so.1
ELF    f7ef3000-f7f12000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000015    0
    00000014    0
    00000011    0
    00000010    0
0000001e (D) C:\Program Files\Starcraft\StarCraft.exe
    00000022    1
    0000001f    0 <==
00000023 
    00000024    0
Backtrace:
=>1 0x7dfbd63d in wined3d (+0x2d63d) (0x0032f890)
  2 0x7e0996d5 in ddraw (+0x166d5) (0x0032f8f0)
  3 0x7e0a03cd in ddraw (+0x1d3cd) (0x0032f910)
  4 0x0041da00 in starcraft (+0x1da00) (0x0032fd9c)
  5 0x004dac97 in starcraft (+0xdac97) (0x0032fdbc)
  6 0x004e0437 in starcraft (+0xe0437) (0x0032fdd4)
  7 0x004e06e0 in starcraft (+0xe06e0) (0x0032fde0)
  8 0x00404da5 in starcraft (+0x4da5) (0x0032ff08)
  9 0x7b8780b7 in kernel32 (+0x580b7) (0x0032ffe8)

```

---

### Post by cherva on 2008-08-29
I tried PlayOnLinux too but couldn't started star craft at all ... I use just wine and it works.... well ok it lags on my pc I don't know why.... so I don't know how to help you. Go to #winehq in irc.freenode.net :)

---

