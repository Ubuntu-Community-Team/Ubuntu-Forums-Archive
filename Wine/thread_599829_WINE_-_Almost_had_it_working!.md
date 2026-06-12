---
title: "WINE - Almost had it working!"
date: 2007-11-01
forum: Wine
---

### Post by victor9098 on 2007-11-01
Hello Again,

Right, my original issue had to do with not being able to get the setup.exe files to run. Which I managed to fix, but now another bump in the road...

When I run the game I get:

> Warning
There will be no voice or sound effects because the system does not support ADPCM files. Do you wish to continue? (CODE = 0:0)


I Click 'YES'

Then the window 'frame' appears then closes :(

Now what is going on? :confused:

Thank you for any help!

---

### Post by cogadh on 2007-11-01
What game are you trying to install/run?

---

### Post by victor9098 on 2007-11-01
Does this help?

f> ixme:mixer:MIX_GetLineInfo Unhandled component type (MIXERLINE_COMPONENTTYPE_SRC_AUXILIARY)
fixme:mixer:MIX_GetLineInfo Unhandled component type (MIXERLINE_COMPONENTTYPE_SRC_DIGITAL)
fixme:mixer:MIX_GetLineInfo Unhandled component type (MIXERLINE_COMPONENTTYPE_SRC_AUXILIARY)
fixme:mixer:MIX_GetLineInfo Unhandled component type (MIXERLINE_COMPONENTTYPE_SRC_DIGITAL)
fixme:imm:ImmGetDefaultIMEWnd (0x10028 - (nil) 0x121e90 ): semi-stub
wine: Unhandled page fault on read access to 0x00000010 at address 0x403d28 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000010 in 32-bit code (0x00403d28).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00403d28 ESP:0033fe00 EBP:004ca8f8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00707808 EBX:00000000 ECX:00000000 EDX:0033fe04
 ESI:00000000 EDI:00000c64
Stack dump:
0x0033fe00:  00707808 00000000 004068f7 00000001
0x0033fe10:  004468dc 00000021 004ca8c8 00000c64
0x0033fe20:  0044e354 00000c00 004ca8c8 00000001
0x0033fe30:  00000000 0000a8c8 0047a5a7 00000000
0x0033fe40:  004ca8c8 004ca8c8 0033ff08 ffffffff
0x0033fe50:  00000001 0047a321 004ca8c8 0047b548
Backtrace:
=>1 0x00403d28 in purucus (+0x3d28) (0x004ca8f8)
  2 0x0000000f (0x00010028)
  3 0x00000000 (0x00000000)
0x00403d28: movl        0x10(%esi),%eax
Modules:
Module  Address                 Debug info      Name (89 modules)
PE        400000-  4de000       Export          purucus
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7df56000-7df61000       Deferred        libgcc_s.so.1
ELF     7e072000-7e0c3000       Deferred        libgcrypt.so.11
ELF     7e0c3000-7e0c7000       Deferred        libgpg-error.so.0
ELF     7e0c7000-7e0d7000       Deferred        libtasn1.so.3
ELF     7e0d7000-7e105000       Deferred        libcrypt.so.1
ELF     7e105000-7e175000       Deferred        libgnutls.so.13
ELF     7e175000-7e19a000       Deferred        libk5crypto.so.3
ELF     7e19a000-7e222000       Deferred        libkrb5.so.3
ELF     7e222000-7e24b000       Deferred        libgssapi_krb5.so.2
ELF     7e24b000-7e280000       Deferred        libcups.so.2
ELF     7e2dc000-7e30e000       Deferred        uxtheme<elf>
  \-PE  7e2e0000-7e30e000       \               uxtheme
ELF     7e30e000-7e323000       Deferred        midimap<elf>
  \-PE  7e310000-7e323000       \               midimap
ELF     7e323000-7e33b000       Deferred        msacm32<elf>
  \-PE  7e330000-7e33b000       \               msacm32
ELF     7e33b000-7e377000       Deferred        wineoss<elf>
  \-PE  7e340000-7e377000       \               wineoss
ELF     7e377000-7e380000       Deferred        libxcursor.so.1
ELF     7e380000-7e383000       Deferred        libxcomposite.so.1
ELF     7e383000-7e389000       Deferred        libxrandr.so.2
ELF     7e389000-7e391000       Deferred        libxrender.so.1
ELF     7e391000-7e39b000       Deferred        libdrm.so.2
ELF     7e39b000-7e3a0000       Deferred        libxfixes.so.3
ELF     7e3a0000-7e3a3000       Deferred        libxdamage.so.1
ELF     7e3a3000-7e404000       Deferred        libgl.so.1
ELF     7e404000-7e409000       Deferred        libxdmcp.so.6
ELF     7e409000-7e40c000       Deferred        libxau.so.6
ELF     7e40c000-7e4fd000       Deferred        libx11.so.6
ELF     7e4fd000-7e50b000       Deferred        libxext.so.6
ELF     7e50b000-7e510000       Deferred        libxxf86vm.so.1
ELF     7e510000-7e528000       Deferred        libice.so.6
ELF     7e528000-7e530000       Deferred        libsm.so.6
ELF     7e530000-7e532000       Deferred        libkeyutils.so.1
ELF     7e532000-7e53a000       Deferred        libkrb5support.so.0
ELF     7e53a000-7e53d000       Deferred        libcom_err.so.2
ELF     7e53f000-7e5cc000       Deferred        winex11<elf>
  \-PE  7e550000-7e5cc000       \               winex11
ELF     7e653000-7e673000       Deferred        libexpat.so.1
ELF     7e673000-7e69e000       Deferred        libfontconfig.so.1
ELF     7e69e000-7e6b3000       Deferred        libz.so.1
ELF     7e6b3000-7e723000       Deferred        libfreetype.so.6
ELF     7e723000-7e758000       Deferred        winspool<elf>
  \-PE  7e730000-7e758000       \               winspool
ELF     7e758000-7e817000       Deferred        comctl32<elf>
  \-PE  7e760000-7e817000       \               comctl32
ELF     7e817000-7e86f000       Deferred        shlwapi<elf>
  \-PE  7e830000-7e86f000       \               shlwapi
ELF     7e86f000-7e972000       Deferred        shell32<elf>
  \-PE  7e880000-7e972000       \               shell32
ELF     7e972000-7ea13000       Deferred        comdlg32<elf>
  \-PE  7e980000-7ea13000       \               comdlg32
ELF     7ea13000-7ea3a000       Deferred        msacm32<elf>
  \-PE  7ea20000-7ea3a000       \               msacm32
ELF     7ea3a000-7ea83000       Deferred        dsound<elf>
  \-PE  7ea40000-7ea83000       \               dsound
ELF     7ea83000-7eaa0000       Deferred        imm32<elf>
  \-PE  7ea90000-7eaa0000       \               imm32
ELF     7eaa0000-7eab3000       Deferred        libresolv.so.2
ELF     7eac2000-7eae0000       Deferred        iphlpapi<elf>
  \-PE  7ead0000-7eae0000       \               iphlpapi
ELF     7eae0000-7eb39000       Deferred        rpcrt4<elf>
  \-PE  7eaf0000-7eb39000       \               rpcrt4
ELF     7eb39000-7ebda000       Deferred        ole32<elf>
  \-PE  7eb50000-7ebda000       \               ole32
ELF     7ebda000-7ec23000       Deferred        advapi32<elf>
  \-PE  7ebf0000-7ec23000       \               advapi32
ELF     7ec23000-7ecbe000       Deferred        gdi32<elf>
  \-PE  7ec40000-7ecbe000       \               gdi32
ELF     7ecbe000-7edfc000       Deferred        user32<elf>
  \-PE  7ece0000-7edfc000       \               user32
ELF     7edfc000-7ee8a000       Deferred        winmm<elf>
  \-PE  7ee10000-7ee8a000       \               winmm
ELF     7efa9000-7efb4000       Deferred        libnss_files.so.2
ELF     7efb4000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d05000-b7d0e000       Deferred        libnss_compat.so.2
ELF     b7d0f000-b7d13000       Deferred        libdl.so.2
ELF     b7d13000-b7e5d000       Deferred        libc.so.6
ELF     b7e5e000-b7e76000       Deferred        libpthread.so.0
ELF     b7e85000-b7f99000       Deferred        libwine.so.1
ELF     b7f9b000-b7fb7000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) D:\Bazooka\PURUCUS.exe
        0000000f   15
        0000000e   15
        00000009    0 <==
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
keith@keith-vaio:/media/cdrom0$

---

### Post by hikaricore on 2007-11-01
> **victor9098 said:**
> Does this help?



**NO**

What game are you trying to install/run?
Check here to see if it's even possible to run under WINE:  [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by cogadh on 2007-11-01
Not really, I asked what game you were trying to run, not what errors were produced. I am kind of curious why you are running the game from within the CD-ROM directory and not the game's install directory though.

Wine has an application database where you can look up applications and see if they can run and what you might need to do to get it to run. I was going to check it out and see if there was anything mentioned that might be helpful, but that is kind of hard to do if you don't tell what the game's name is. If you want, you can check it out yourself:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

EDIT - Apparently I need to spend less time talking to my wife and more time typing, hikari beat me to it.

---

### Post by hikaricore on 2007-11-01
Sorry, I just couldn't let that terrible disregard to the question being presented go unchecked.  ^_^

---

### Post by victor9098 on 2007-11-01
SORRY! :(

I really do not have a clue with this side of things...no GUI and I am completely lost.

No, game is not listed anywhere so I guess the next option is to look into setting up a Windows Partition or something?

Thank you for your help.

---

### Post by JusticeZero on 2007-11-01
Not that anyone can help if they don't know what 'The Game' is. If people knew WHICH game, since there are an awful lot, maybe someone could help you.

---

