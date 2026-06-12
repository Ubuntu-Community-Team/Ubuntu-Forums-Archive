---
title: "Tib Sun via Wine problem"
date: 2007-08-20
forum: Wine
---

### Post by Bohlio on 2007-08-20
Im baffled... Ive been trying to get Ubuntu to run Tiberian Sun, but I've had many problems...
First it said that I was missing ntoskrnl.exe, so I got that from my windows partition and copied it into the fake windows, also, there was a Unhanded page fault error.

then it said I needed BOOTVID.dll, HAL.dll, and KDCOM.dll, along with the unhandled page fault error, I copied the dll's over and now those messages are gone, but I am still left with the unhandled page fault error...

does anyone know what this means??
```
chad@chad-desktop:~$ wine /home/chad/.wine/drive_c/Westwood/SUN/GAME.EXE
wine: Unhandled page fault on read access to 0x00000051 at address 0x37dce2 (thread 000e), starting debugger...
Unhandled exception: page fault on read access to 0x00000051 in 32-bit code (0x0037dce2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0037dce2 ESP:0035fca8 EBP:0035fcb8 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7bc7b550 ECX:00390000 EDX:00000001
 ESI:0000000d EDI:00110890
Stack dump:
0x0035fca8:  00110890 00000001 7bc7b550 00390000
0x0035fcb8:  0035fcd8 7bc39075 00390000 00000001
0x0035fcc8:  00000001 00000001 7bc7b550 7bc7b550
0x0035fcd8:  0035fd68 7bc3ac3d 00390ce6 00390000
0x0035fce8:  00000001 00000001 b7cba1a9 b7dde163
0x0035fcf8:  00000006 0035fd2c 0035fd94 0035fd84
Backtrace:
=>1 0x0037dce2 in hal (+0x1dce2) (0x0035fcb8)
  2 0x7bc39075 call_dll_entry_point+0x15() in ntdll (0x0035fcd8)
  3 0x7bc3ac3d in ntdll (+0x2ac3d) (0x0035fd68)
  4 0x7bc3b41d in ntdll (+0x2b41d) (0x0035fda8)
  5 0x7bc3b362 in ntdll (+0x2b362) (0x0035fde8)
  6 0x7bc3b362 in ntdll (+0x2b362) (0x0035fe28)
  7 0x7bc3b362 in ntdll (+0x2b362) (0x0035fe68)
  8 0x7bc3b362 in ntdll (+0x2b362) (0x0035fea8)
  9 0x7bc3d42e LdrInitializeThunk+0x2be() in ntdll (0x0035ff08)
  10 0x7b8721ea in kernel32 (+0x521ea) (0x0035ffe8)
  11 0xb7dfd897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0037dce2: cmpb        $0x0,0x51(%eax)
Modules:
Module  Address                 Debug info      Name (20 modules)
PE      240000-242ea0   Deferred        secdrv.sys
PE      360000-380d00   Export          hal
PE      390000-391b80   Deferred        kdcom
PE      400000-626000   Deferred        ntoskrnl
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Export          ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ee82000-7ee8d000       Deferred        libnss_files.so.2
ELF     7ee8d000-7eea4000       Deferred        libnsl.so.1
ELF     7eea4000-7eead000       Deferred        libnss_compat.so.2
ELF     7efcc000-7eff3000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
PE      80010000-80013000       Deferred        bootvid
ELF     b7c8c000-b7c90000       Deferred        libdl.so.2
ELF     b7c90000-b7dd1000       Deferred        libc.so.6
ELF     b7dd2000-b7de9000       Deferred        libpthread.so.0
ELF     b7df6000-b7f07000       Export          libwine.so.1
ELF     b7f09000-b7f24000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000d (D) C:\windows\system32\drivers\SECDRV.SYS
        0000000e    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000009    0
wine: Unhandled page fault on read access to 0x00000051 at address 0x37dce2 (thread 0012), starting debugger...
Unhandled exception: page fault on read access to 0x00000051 in 32-bit code (0x0037dce2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0037dce2 ESP:0035fca8 EBP:0035fcb8 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7bc7b550 ECX:00390000 EDX:00000001
 ESI:00000011 EDI:00110890
Stack dump:
0x0035fca8:  00110890 00000001 7bc7b550 00390000
0x0035fcb8:  0035fcd8 7bc39075 00390000 00000001
0x0035fcc8:  00000001 00000001 7bc7b550 7bc7b550
0x0035fcd8:  0035fd68 7bc3ac3d 00390ce6 00390000
0x0035fce8:  00000001 00000001 b7d0f1a9 b7e33163
0x0035fcf8:  00000006 0035fd2c 0035fd94 0035fd84
Backtrace:
=>1 0x0037dce2 in hal (+0x1dce2) (0x0035fcb8)
  2 0x7bc39075 call_dll_entry_point+0x15() in ntdll (0x0035fcd8)
  3 0x7bc3ac3d in ntdll (+0x2ac3d) (0x0035fd68)
  4 0x7bc3b41d in ntdll (+0x2b41d) (0x0035fda8)
  5 0x7bc3b362 in ntdll (+0x2b362) (0x0035fde8)
  6 0x7bc3b362 in ntdll (+0x2b362) (0x0035fe28)
  7 0x7bc3b362 in ntdll (+0x2b362) (0x0035fe68)
  8 0x7bc3b362 in ntdll (+0x2b362) (0x0035fea8)
  9 0x7bc3d42e LdrInitializeThunk+0x2be() in ntdll (0x0035ff08)
  10 0x7b8721ea in kernel32 (+0x521ea) (0x0035ffe8)
  11 0xb7e52897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0037dce2: cmpb        $0x0,0x51(%eax)
Modules:
Module  Address                 Debug info      Name (20 modules)
PE      240000-242ea0   Deferred        secdrv.sys
PE      360000-380d00   Export          hal
PE      390000-391b80   Deferred        kdcom
PE      400000-626000   Deferred        ntoskrnl
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Export          ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ee78000-7ee83000       Deferred        libnss_files.so.2
ELF     7ee83000-7ee8d000       Deferred        libnss_nis.so.2
ELF     7ee8d000-7eea4000       Deferred        libnsl.so.1
ELF     7eea4000-7eead000       Deferred        libnss_compat.so.2
ELF     7efcc000-7eff3000       Deferred        libm.so.6
PE      80010000-80013000       Deferred        bootvid
ELF     b7ce1000-b7ce5000       Deferred        libdl.so.2
ELF     b7ce5000-b7e26000       Deferred        libc.so.6
ELF     b7e27000-b7e3e000       Deferred        libpthread.so.0
ELF     b7e4b000-b7f5c000       Export          libwine.so.1
ELF     b7f5e000-b7f79000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000011 (D) C:\windows\system32\drivers\SECDRV.SYS
        00000012    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000009    0
wine: Unhandled page fault on write access to 0xe39874a9 at address 0x406b37 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0xe39874a9 in 32-bit code (0x00406b37).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00406b37 ESP:0033fda0 EBP:0033fe7c EFLAGS:00010206(   - 00      - RIP1)
 EAX:00400000 EBX:e3987453 ECX:00000000 EDX:0003f000
 ESI:00400000 EDI:00000001
Stack dump:
0x0033fda0:  0040b1c7 00000000 00400000 7ffdf000
0x0033fdb0:  001158b6 7b8ad908 00000094 00000005
0x0033fdc0:  00000000 00000893 00000002 76726553
0x0033fdd0:  20656369 6b636150 7b003420 00450f18
0x0033fde0:  7bc7b550 0033fe44 7bc381fe 00450020
0x0033fdf0:  7b862931 00000800 0033fe28 0033ff08
Backtrace:
=>1 0x00406b37 in game (+0x6b37) (0x0033fe7c)
  2 0x004114e2 in game (+0x114e2) (0x0033ff08)
  3 0x7b87221e in kernel32 (+0x5221e) (0x0033ffe8)
  4 0xb7df4897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00406b37: sbbb        %bl,0x56(%ebx)
Modules:
Module  Address                 Debug info      Name (51 modules)
PE      400000-441000   Export          game
PE      10000000-1000c000       Deferred        drvmgt
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c97d000-7c986000       Deferred        libxcursor.so.1
ELF     7c986000-7c9a3000       Deferred        imm32<elf>
  \-PE  7c990000-7c9a3000       \               imm32
ELF     7c9a3000-7c9a9000       Deferred        libxrandr.so.2
ELF     7d3d3000-7d3db000       Deferred        libxrender.so.1
ELF     7d4d9000-7d4de000       Deferred        libxfixes.so.3
ELF     7dd6f000-7dd78000       Deferred        librt.so.1
ELF     7dd79000-7dd7c000       Deferred        libxinerama.so.1
ELF     7de3f000-7e770000       Deferred        fglrx_dri.so
ELF     7e770000-7e810000       Deferred        libgl.so.1
ELF     7e810000-7e815000       Deferred        libxdmcp.so.6
ELF     7e815000-7e818000       Deferred        libxau.so.6
ELF     7e818000-7e909000       Deferred        libx11.so.6
ELF     7e909000-7e917000       Deferred        libxext.so.6
ELF     7e917000-7e91c000       Deferred        libxxf86vm.so.1
ELF     7e91c000-7e934000       Deferred        libice.so.6
ELF     7e934000-7e93d000       Deferred        libsm.so.6
ELF     7e93d000-7e9cb000       Deferred        winex11<elf>
  \-PE  7e950000-7e9cb000       \               winex11
ELF     7ea55000-7ea75000       Deferred        libexpat.so.1
ELF     7ea75000-7eaa0000       Deferred        libfontconfig.so.1
ELF     7eaa0000-7eab4000       Deferred        libz.so.1
ELF     7eab4000-7eb1f000       Deferred        libfreetype.so.6
ELF     7eb1f000-7eb33000       Deferred        lz32<elf>
  \-PE  7eb30000-7eb33000       \               lz32
ELF     7eb33000-7eb4c000       Deferred        version<elf>
  \-PE  7eb40000-7eb4c000       \               version
ELF     7eb4c000-7eb92000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb92000       \               advapi32
ELF     7eb92000-7eb9e000       Deferred        libgcc_s.so.1
ELF     7ec95000-7ed52000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed52000       \               gdi32
ELF     7ed52000-7ee8e000       Deferred        user32<elf>
  \-PE  7ed70000-7ee8e000       \               user32
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff3000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c83000-b7c87000       Deferred        libdl.so.2
ELF     b7c87000-b7dc8000       Deferred        libc.so.6
ELF     b7dc9000-b7de0000       Deferred        libpthread.so.0
ELF     b7ded000-b7efe000       Export          libwine.so.1
ELF     b7f00000-b7f1b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Westwood\SUN\GAME.EXE
        00000009    0 <==

```

---

### Post by QOLIM on 2007-08-21
I got it working with a no-cd crack

---

### Post by Bohlio on 2007-08-22
did you have that same error? or did you just have a less than legal torrented iso that needed a crack? I'm not accusing you, I am just wondering. I have the original CD and it doesnt work...

---

### Post by splintercellguy on 2007-08-23
The AppDb might have some insight: [http://appdb.winehq.org/appview.php?iVersionId=296](http://appdb.winehq.org/appview.php?iVersionId=296)

---

### Post by RudolfMDLT on 2007-08-23
No game will work with the CD in wine - you must crack it - because wine doesn't support the copy protection software on the game.

I recently installed CnC: Tiberian Wars, i also baught the game - but I still need to crack it in order to play it.

---

### Post by cogadh on 2007-08-23
> **RudolfMDLT said:**
> No game will work with the CD in wine - you must crack it - because wine doesn't support the copy protection software on the game.

I recently installed CnC: Tiberian Wars, i also baught the game - but I still need to crack it in order to play it.
Not entirely true. Most games require a crack, but some copy protection schemes are implemented in a functional way and a crack won't be required. For example, I run Star Trek: Armada II through Wine and it detects and reads the CD fine, launches the game and doesn't complain one bit about copy protection. It does complain if I forget to put in the CD, however.

Fully functional copy protection support is in the works for Wine, but it is difficult to accomplish, since copy protection is closed source and it costs money to buy a license for it. Also, any alternative way to support the copy protection could be seen as a technical violation of some copyright protection laws (like the DMCA). 

Some copy protection schemes are implemented in a very bad way that will never work on Wine, like StarForce. It actually installs hidden device drivers on your Windows system that are known to break certain CD/DVD drives over time. Those hidden drivers even stay present even if you uninstall the game that used them. Since Wine can't use Windows device drivers, StarForce as it is currently implemented will never work in Wine.

---

### Post by RudolfMDLT on 2007-08-23
I stand corrected! :) Sorry - I only spoke out of my own experience ( one or two games and the opinions of some friends! )

I wish I had read you post - Stuff I've learned about Wine - earlier! I had to reformat my machine this weekend because I installed CnC as root! :'(

Thanks - was an awsome read!

Cheers,

Rudolf

---

### Post by Bohlio on 2007-08-23
Ok, so that is because of the copy protection? How do I identify errors that are caused by the copy protection in the future? Will they all have the Page fault on read access... error?

---

### Post by cogadh on 2007-08-23
Honestly, copy protection errors present themselves in many ways. Sometimes you could get a page fault, other times nothing at all will happen when the game launches, still other times you will get drive access error messages in the terminal and even other times you might actually get a real Windows style error message saying "insert disk".

My basic rule is, try it without a crack, if it fails, try the crack, if it still fails, then it might not work at all. Of course, I only do this for games that I can't already find a how-to or Wine AppDB entry for.

---

