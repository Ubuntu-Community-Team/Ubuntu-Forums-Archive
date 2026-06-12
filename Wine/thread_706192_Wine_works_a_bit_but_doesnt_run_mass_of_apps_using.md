---
title: "Wine works a bit but doesnt run mass of apps using 3d and gets almost the same buglog"
date: 2008-02-24
forum: Wine
---

### Post by kacperpl1 on 2008-02-24
I have some problems using wine from time when i started installing it from gutsy cd. The first time installed ubuntu from feisty cd and upgraded to gutsy wine worked perfectly but i had some issues with memory support and badly compiled new kernel and after that i screwed sth when clearing system and i had to completely reinstall it so i did it from gutsy cd because it was alot easier to make my wifi work. Now i have always the same problem on both computers when running some apps that i would like to use. For example here's the debug log from running warcraft3 acid's pvpgn launcher but it worked fine before system reinstall.

> /media/sda1/Games/WarcraftIII$ wine ./w3l.exe -opengl
wine: Unhandled page fault on read access to 0x737fff4e at address 0x407163 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x737fff4e in 32-bit code (0x00407163).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00407163 ESP:0034ff04 EBP:003060d8 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000038 EBX:737fff00 ECX:b4c919ae EDX:00002049
 ESI:00409a68 EDI:00401086
Stack dump:
0x0034ff04:  00000000 00401086 7b86e6d5 7ffdf000
0x0034ff14:  00000000 00000000 00000000 ffffffff
0x0034ff24:  7b82c134 7b840edc 7b8ac540 00110000
0x0034ff34:  7ffd8000 0034ffe8 7dfe21fe 19cc9b09
0x0034ff44:  00000001 10012a03 00000000 00000000
0x0034ff54:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x00407163 in w3l (+0x7163) (0x003060d8)
  2 0x00000000 (0x00000000)
0x00407163: cmpl        $0x73696854,0x4e(%ebx)
Modules:
Module  Address                 Debug info      Name (46 modules)
PE        400000-  40f000       Export          w3l
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ca63000-7ca6c000       Deferred        libxcursor.so.1
ELF     7ca6c000-7ca89000       Deferred        imm32<elf>
  \-PE  7ca70000-7ca89000       \               imm32
ELF     7ca89000-7ca8e000       Deferred        libxfixes.so.3
ELF     7ca8e000-7ca91000       Deferred        libxcomposite.so.1
ELF     7ca91000-7ca97000       Deferred        libxrandr.so.2
ELF     7ca97000-7ca9f000       Deferred        libxrender.so.1
ELF     7d88e000-7d897000       Deferred        librt.so.1
ELF     7d897000-7e8bb000       Deferred        fglrx_dri.so
ELF     7e8bb000-7e8c6000       Deferred        libgcc_s.so.1
ELF     7e8c6000-7e940000       Deferred        libgl.so.1
ELF     7e940000-7e945000       Deferred        libxdmcp.so.6
ELF     7e945000-7e948000       Deferred        libxau.so.6
ELF     7e948000-7ea39000       Deferred        libx11.so.6
ELF     7ea39000-7ea47000       Deferred        libxext.so.6
ELF     7ea47000-7ea4c000       Deferred        libxxf86vm.so.1
ELF     7ea4c000-7ea64000       Deferred        libice.so.6
ELF     7ea64000-7ea6c000       Deferred        libsm.so.6
ELF     7ea7a000-7eb09000       Deferred        winex11<elf>
  \-PE  7ea90000-7eb09000       \               winex11
ELF     7eb8b000-7ebab000       Deferred        libexpat.so.1
ELF     7ebab000-7ebd6000       Deferred        libfontconfig.so.1
ELF     7ebd6000-7ebeb000       Deferred        libz.so.1
ELF     7ebeb000-7ec5b000       Deferred        libfreetype.so.6
ELF     7ec69000-7ecb3000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecb3000       \               advapi32
ELF     7ecb3000-7ed4a000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed4a000       \               gdi32
ELF     7ed4a000-7ee81000       Deferred        user32<elf>
  \-PE  7ed60000-7ee81000       \               user32
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c96000-b7c9a000       Deferred        libdl.so.2
ELF     b7c9a000-b7de4000       Deferred        libc.so.6
ELF     b7de5000-b7dfd000       Deferred        libpthread.so.0
ELF     b7e0b000-b7f1f000       Deferred        libwine.so.1
ELF     b7f21000-b7f3d000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\sda1\Games\WarcraftIII\w3l.exe
        00000009    0 <==
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
Backtrace:
=>1 0x00407163 in w3l (+0x7163) (0x003060d8)
  2 0x00000000 (0x00000000)

This happens on both of my computers: hp nx6325 with turion64x2 and radeon xpress  1150 and my desktop workstation with dual opterons 270 and geforce 6600GT on gutsy and hardy on every version of wine. I think there's something I'm doing wrong every time i try to reinstall wine. Next thing is that, when i install versions 55 and 56 from packages using it hangs system and there is no wine menu in applications menus. I'd like to run SolidWorks and other pro apps on Ubuntu but because of this i cant make it work.

I tried reinstalling, removing .wine folder, reinstalling vga drivers etc. Plz try to help me with sth i didnt tried before.

---

### Post by happyhamster on 2008-02-24
You could always try to use one of the older wine packages. Each new wine release will close several bugs, but also regress to some previous bugs and introduce brand new ones. (Wine is still a beta afterall.)

The newest wine releases  (> 52) crash far more frequently on color depth/resolution-/window-size-changes. And they seem far more picky concerning the configuration of your video-driver. Which driver(s) are you using?

Also: did you compile wine yourself, or did you use .deb packages? The app you're trying to run is on a different hard drive I believe, how did you install that game? (Is it an usb-drive you use between different computers perhaps?)

---

### Post by kacperpl1 on 2008-02-24
I have already tried a lot of older version from 49 up to 56 now and every time its the same. I'm using fglrx driver on my notebook and nvidia driver on desktop and i think they are working as they should work. Ask about something that isn't that obvious as checking older versions.

---

### Post by Nameless_one on 2008-02-24
I had some problems running 3D games with wine. I too have an ATi and had installed the version from the repositories, however, that is very old. Recently I installed the latest fglrx from source, and now 3D works fine on wine. Maybe you should try it. 

Here's the HowTo: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by kacperpl1 on 2008-02-24
I have installed the newest drivers from packages so i dont think it is a problem because it happens on both pcs - with ati and nvidia cards.

---

### Post by Nameless_one on 2008-02-25
I don't think there are packages for the newest drivers of ATi.

---

### Post by kacperpl1 on 2008-02-25
I mean the .run file from ati web page.

---

