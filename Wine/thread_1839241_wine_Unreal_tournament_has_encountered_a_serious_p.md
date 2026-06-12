---
title: "wine: Unreal tournament has encountered a serious problem and needs to clsoe"
date: 2011-09-05
forum: Wine
---

### Post by wardy277 on 2011-09-05
I am running wine on ubuntu 11.04 x64. I can run other wine application fine.

I have installed unreal tournament through wine and that went through fine. My problem is when actually trying to run the game i get a wine error:
Program error:
The program UnrealTournament.exe has encountered a serious problem and needs to close.

I have tried running it through playonlinux as that gives a wine debug output:

```
wine: Unhandled privileged instruction at address 0x40aae4 (thread 001b), starting debugger...
Unhandled exception: privileged instruction in 32-bit code (0x0040aae4).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0040aae4 ESP:0033fd20 EBP:0033fe04 EFLAGS:00010217(  R- --  I   -A-P-C)
 EAX:00330012 EBX:00000000 ECX:00000067 EDX:00400000
 ESI:7b860090 EDI:00400000
Stack dump:
0x0033fd20:  00410fed 00000000 00400000 00000067
0x0033fd30:  0041ab90 00127539 7b882ff4 7bc454d4
0x0033fd40:  0044c2e0 00000002 0044bdd0 7bc9dff4
0x0033fd50:  7bc34f1f 00000800 00000094 00000005
0x0033fd60:  00000000 00000893 00000002 76726553
0x0033fd70:  20656369 6b636150 00003420 00000800
Backtrace:
=>0 0x0040aae4 in unrealtournament (+0xaae4) (0x0033fe04)
  1 0x0041ace2 in unrealtournament (+0x1ace1) (0x0033fe90)
  2 0x7b85483c call_process_entry+0xb() in kernel32 (0x0033fea8)
  3 0x7b8554df ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  4 0x7bc71ee0 call_thread_func+0xb() in ntdll (0x0033fef8)
  5 0x7bc74a40 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  6 0x7bc4a47a call_dll_entry_point+0x659() in ntdll (0x0033ffe8)
0x0040aae4: outl	%eax,$0x99
Modules:
Module	Address			Debug info	Name (49 modules)
PE	  400000-  44b000	Export          unrealtournament
ELF	7b800000-7b97c000	Export          kernel32<elf>
  \-PE	7b810000-7b97c000	\               kernel32
ELF	7bc00000-7bcba000	Export          ntdll<elf>
  \-PE	7bc10000-7bcba000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e783000-7e789000	Deferred        libxfixes.so.3
ELF	7e789000-7e793000	Deferred        libxcursor.so.1
ELF	7e793000-7e797000	Deferred        libxcomposite.so.1
ELF	7e797000-7e79f000	Deferred        libxrandr.so.2
ELF	7e79f000-7e7a9000	Deferred        libxrender.so.1
ELF	7e7a9000-7e7af000	Deferred        libxxf86vm.so.1
ELF	7e7af000-7e7b3000	Deferred        libxinerama.so.1
ELF	7e7b3000-7e7d4000	Deferred        imm32<elf>
  \-PE	7e7c0000-7e7d4000	\               imm32
ELF	7e7d4000-7e7da000	Deferred        libxdmcp.so.6
ELF	7e7da000-7e7de000	Deferred        libxau.so.6
ELF	7e7de000-7e7f7000	Deferred        libxcb.so.1
ELF	7e7f7000-7e7fc000	Deferred        libuuid.so.1
ELF	7e7fc000-7e917000	Deferred        libx11.so.6
ELF	7e917000-7e926000	Deferred        libxext.so.6
ELF	7e926000-7e93e000	Deferred        libice.so.6
ELF	7e93e000-7e946000	Deferred        libsm.so.6
ELF	7e96a000-7ea0b000	Deferred        winex11<elf>
  \-PE	7e980000-7ea0b000	\               winex11
ELF	7ea45000-7ea6f000	Deferred        libexpat.so.1
ELF	7ea6f000-7ea9e000	Deferred        libfontconfig.so.1
ELF	7ea9e000-7eab3000	Deferred        libz.so.1
ELF	7eab3000-7eb39000	Deferred        libfreetype.so.6
ELF	7eb5d000-7eb71000	Deferred        lz32<elf>
  \-PE	7eb60000-7eb71000	\               lz32
ELF	7eb71000-7ebcb000	Deferred        advapi32<elf>
  \-PE	7eb80000-7ebcb000	\               advapi32
ELF	7ebcb000-7ec56000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec56000	\               gdi32
ELF	7ec56000-7ed88000	Deferred        user32<elf>
  \-PE	7ec70000-7ed88000	\               user32
ELF	7ed88000-7ed94000	Deferred        libnss_files.so.2
ELF	7ed94000-7ed9f000	Deferred        libnss_nis.so.2
ELF	7ed9f000-7edb6000	Deferred        libnsl.so.1
ELF	7efb6000-7efdc000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f74d7000-f74db000	Deferred        libdl.so.2
ELF	f74db000-f7638000	Deferred        libc.so.6
ELF	f7638000-f7651000	Deferred        libpthread.so.0
ELF	f7658000-f7660000	Deferred        libnss_compat.so.2
ELF	f7675000-f77b5000	Export          libwine.so.1
ELF	f77b7000-f77d5000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 explorer.exe
	00000019    0
0000001a (D) C:\UnrealTournament\System\UnrealTournament.exe
	0000001b    0 <==
Backtrace:
=>0 0x0040aae4 in unrealtournament (+0xaae4) (0x0033fe04)
  1 0x0041ace2 in unrealtournament (+0x1ace1) (0x0033fe90)
  2 0x7b85483c call_process_entry+0xb() in kernel32 (0x0033fea8)
  3 0x7b8554df ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  4 0x7bc71ee0 call_thread_func+0xb() in ntdll (0x0033fef8)
  5 0x7bc74a40 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  6 0x7bc4a47a call_dll_entry_point+0x659() in ntdll (0x0033ffe8)

```

---

### Post by Toz on 2011-09-05
Have you had a look at the winehq entry for unreal tournament? There are a few suggestions to crashing related issues that you can try. See: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=124&iTestingId=64980]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=124&iTestingId=51263")

---

### Post by wardy277 on 2011-09-05
strange, it seems that it needs to be patched. but when i ran the unrealtournament.exe from within its system directory it worked.

the only issue is that the whole screen is black with a small box at the top left which has the game in.how do i get it to run in proper fullscreen or even force it to windowed mode?

also, when running a game i could not move the mouse up or down, it was stuck looking at the floor. i could move and even move the mouse left and right (spinning on the spot)

Chris

---

### Post by Toz on 2011-09-05
> **wardy277 said:**
> the only issue is that the whole screen is black with a small box at the top left which has the game in.how do i get it to run in proper fullscreen or even force it to windowed mode?
Do you have an intel or ati card? From the wine appdb page, have you tried:
> For users of some intel or ati/amd graphics drivers, the game may display a black screen upon startup. Set the registry key "HKEY_CURRENT_USER>Software>Wine>AppDefaults>UnrealTournament.exe>Direct3D>OffscreenRenderingMode" to "backbuffer" to fix this. 

> also, when running a game i could not move the mouse up or down, it was stuck looking at the floor. i could move and even move the mouse left and right (spinning on the spot
I've been able to resolve mouse issues in the past with other software by installing the dinput8 libraries:
```
winetricks dinput8
```

---

### Post by Toz on 2011-09-05
I just dug up my old copy of Unreal Tournament - Game of the Year Edition. Installed it and it works without any problems. I'm running Xubuntu Natty 11.04, wine version 1.3.27 with an ATI HD2600 video card with proprietary drivers.

---

### Post by Brebs on 2011-09-06
> **wardy277 said:**
> stuck looking at the floor
You can try compiling wine with this ./configure option:  *--without-xinput2*

---

### Post by wardy277 on 2011-09-06
> **Toz said:**
> 
I've been able to resolve mouse issues in the past with other software by installing the dinput8 libraries:
```
winetricks dinput8
```

I have run that and it didnt seem to fix it. i had a look through the settings and i saw a centre button which will centre the camera, but when i move the mouse in any direction it goes back to looking at the floor. this is odd as the mouse works find in the menu, could this be a problem with unreal tournament itself? maybe a setting?

i turned off "mouse look" and i can use the mosue to move and the page up and page down to look up and down, so i know that it picks up forward and backward mouse motion fine.

I do have 2 monitors by the way, could that be an issue?

Oh, and  i have an nvidia graphics card

---

### Post by Toz on 2011-09-06
What version of wine are you running?
```
wine --version
```

---

### Post by wardy277 on 2011-09-06
I am running wine-1.2.2

i had a similar problem when i tried running it on my XP virtual machine (plays impresivly well). i fixed the mouse issue by disabling mouse integration, then the mouse was confined to the virtual box window. would like it to work in wine through as i have 3 sets of window decorations, one for ubuntu, one for windows in the virtualbox and then another within the game itself :p

---

### Post by Toz on 2011-09-06
You could try updating your version of wine to see if it helps. Instructions are located here: [http://www.winehq.org/download/ubuntu]("http://www.winehq.org/download/ubuntu")
Links of interest:
- [http://forum.winehq.org/viewtopic.php?t=12806&sid=e0b6c25515221e9ae5daa911263c7032]("http://forum.winehq.org/viewtopic.php?t=12806&sid=e0b6c25515221e9ae5daa911263c7032")


Another option maybe to run **winecfg** and have a look at the "Graphics" tab. On my version, there is an option to "Automatically capture the mouse in full-screen windows" and a virtual desktop emulation option you could try to tweak.
Links of interest:
- [http://ubuntuforums.org/showthread.php?t=1772575]("http://ubuntuforums.org/showthread.php?t=1772575")

---

### Post by disabledaccount on 2011-09-06
I would suggest to run this game in single core mode (by setting CPU affinity for process) - otherwise it can crash, generate "negative delta time" errors (and quit) or get "choppy" graphics due to timing problems. I'm using "schedtool" for this (available in repositories)

---

