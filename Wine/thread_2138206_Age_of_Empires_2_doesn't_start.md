---
title: "Age of Empires 2 doesn't start"
date: 2013-04-23
forum: Wine
---

### Post by gicanzo on 2013-04-23
Hi guys,
as in the title, i can't get AoE2 starting on my Ubuntu 12.10. This is what i've done so far:

- installed wine v1.5--
- tried to install aoe2 trhough wine but didn't work
- installed playonlinux (which i think installed Wine back to v1.4), added some files that i read were needed (mscf40 and mscf42, or something like that), installed directplay through terminal, installed directx drivers through playonlinux
- then i was able to install aoe2 (and the conquerors expansion as well)

so setup completed successfully, but now i can't get the game started. If i try to start it through playonlinux, i get the error message (my translation):

"the program empires2.exe encountered an error and has to be closed. We are sorry for the inconvenience and blablabla"

If i try to start it through the terminal with wine, with the command "wine empires2.exe" (is it the right command??), i get this:

```
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
wine: cannot find L"C:\\windows\\system32\\empires2.exe"

```

So it should be a graphics card error, right? What should I do? Thanks in advance for any replies :D

---

### Post by zombifier25 on 2013-04-23
Did you install Age of Empire II using PlayOnLinux's provided config? Or did you just manually add a bunch of libraries?
If the latter, then PlayOnLinux has a AOE2 config that automatically does all the hard work of configuring the required settings for you. You may want to try that and see if it works.

---

### Post by gicanzo on 2013-04-23
I just took it from the list in playonlinux's install menu. Anway, it really seems that the problem derives from my graphic card. How can i see card's model and install proper, updated drivers?

---

### Post by myromance123 on 2013-04-23
To find out what graphics card you have, you can open a new Terminal and Enter the following:
```
lspci | grep VGA
```

From there, we'll try to figure out how to install your graphics drivers.

---

### Post by gicanzo on 2013-04-24
> **myromance123 said:**
> To find out what graphics card you have, you can open a new Terminal and Enter the following:
```
lspci | grep VGA
```

From there, we'll try to figure out how to install your graphics drivers.

GeForce G 105M:

```
01:00.0 VGA compatible controller: NVIDIA Corporation G98M [GeForce G 105M] (rev a1)
```

---

### Post by gicanzo on 2013-04-24
Guys, if I enable debugging on PlayonLinux and try to start the game through it, this is what i get:
```
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x0040aaad).Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0040aaad ESP:0032fd00 EBP:0032fde4 EFLAGS:00010293(  R- --  I S -A- -C)
 EAX:00000001 EBX:bde78d9d ECX:00000067 EDX:00400000
 ESI:7b867c00 EDI:00400000
Stack dump:
0x0032fd00:  00410fed 00000000 00400000 00000067
0x0032fd10:  0041ab90 0012d8d2 7b895848 7bc483b1
0x0032fd20:  0055b000 00000002 0044bdd0 7bca4e6c
0x0032fd30:  7bc3590f 00000800 00000094 00000005
0x0032fd40:  00000000 00000893 00000002 76726553
0x0032fd50:  20656369 6b636150 00003420 00000800
Backtrace:
=>0 0x0040aaad in empires2 (+0xaaad) (0x0032fde4)
  1 0x0041ace2 in empires2 (+0x1ace1) (0x0032fe70)
  2 0x7b85ac0c call_process_entry+0xb() in kernel32 (0x0032fe88)
  3 0x7b85e13b in kernel32 (+0x4e13a) (0x0032fec8)
  4 0x7bc714f0 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  5 0x7bc7172d call_thread_func+0x7c() in ntdll (0x0032ffa8)
  6 0x7bc714ce RtlRaiseException+0x21() in ntdll (0x0032ffc8)
  7 0x7bc4c30e in ntdll (+0x3c30d) (0x0032ffe8)
0x0040aaad: pop	%ss
Modules:
Module	Address			Debug info	Name (51 modules)
PE	  400000-  44b000	Export          empires2
PE	10000000-1000c000	Deferred        drvmgt
ELF	7b800000-7b8f5000	Dwarf           kernel32<elf>
  \-PE	7b810000-7b8f5000	\               kernel32
ELF	7bc00000-7bcc1000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcc1000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e635000-7e6ab000	Deferred        rpcrt4<elf>
  \-PE	7e640000-7e6ab000	\               rpcrt4
ELF	7e6fd000-7e704000	Deferred        libxfixes.so.3
ELF	7e704000-7e70f000	Deferred        libxcursor.so.1
ELF	7e797000-7e7bf000	Deferred        libexpat.so.1
ELF	7e7bf000-7e7f7000	Deferred        libfontconfig.so.1
ELF	7e7f7000-7e807000	Deferred        libxi.so.6
ELF	7e807000-7e80b000	Deferred        libxcomposite.so.1
ELF	7e80b000-7e82c000	Deferred        imm32<elf>
  \-PE	7e810000-7e82c000	\               imm32
ELF	7e82c000-7e830000	Deferred        libxau.so.6
ELF	7e830000-7e855000	Deferred        libxcb.so.1
ELF	7e855000-7e98b000	Deferred        libx11.so.6
ELF	7e98b000-7e99d000	Deferred        libxext.so.6
ELF	7e99d000-7e9b7000	Deferred        libice.so.6
ELF	7e9b9000-7e9c4000	Deferred        libxrandr.so.2
ELF	7e9c4000-7e9ce000	Deferred        libxrender.so.1
ELF	7e9ce000-7ea60000	Deferred        winex11<elf>
  \-PE	7e9e0000-7ea60000	\               winex11
ELF	7ea60000-7ea74000	Deferred        libz.so.1
ELF	7ea74000-7eb0e000	Deferred        libfreetype.so.6
ELF	7eb25000-7eb3d000	Deferred        version<elf>
  \-PE	7eb30000-7eb3d000	\               version
ELF	7eb3d000-7eb9d000	Deferred        advapi32<elf>
  \-PE	7eb50000-7eb9d000	\               advapi32
ELF	7eb9d000-7ec58000	Deferred        gdi32<elf>
  \-PE	7ebb0000-7ec58000	\               gdi32
ELF	7ec58000-7ed96000	Deferred        user32<elf>
  \-PE	7ec70000-7ed96000	\               user32
ELF	7ef96000-7efa3000	Deferred        libnss_files.so.2
ELF	7efa3000-7efbd000	Deferred        libnsl.so.1
ELF	7efbd000-7efe9000	Deferred        libm.so.6
ELF	7efea000-7eff0000	Deferred        libxxf86vm.so.1
ELF	7eff0000-7eff4000	Deferred        libxinerama.so.1
ELF	7eff4000-7f000000	Deferred        libnss_nis.so.2
ELF	b7441000-b744a000	Deferred        libnss_compat.so.2
ELF	b744b000-b7450000	Deferred        libdl.so.2
ELF	b7450000-b75fa000	Deferred        libc.so.6
ELF	b75fa000-b7615000	Deferred        libpthread.so.0
ELF	b7616000-b761c000	Deferred        libuuid.so.1
ELF	b761c000-b7625000	Deferred        libsm.so.6
ELF	b762d000-b776e000	Dwarf           libwine.so.1
ELF	b7770000-b7792000	Deferred        ld-linux.so.2
ELF	b7792000-b7793000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Microsoft Games\Age of Empires II\empires2.exe
	00000009    0 <==
0000000e services.exe
	0000002a    0
	00000029    0
	0000001f    0
	00000019    0
	00000018    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001d    0
	0000001a    0
	00000014    0
	00000013    0
0000001b plugplay.exe
	00000021    0
	0000001e    0
	0000001c    0
00000022 explorer.exe
	00000023    0
00000026 winedevice.exe
	0000002b    0
	00000028    0
	00000027    0
wine: Unhandled page fault on read access to 0xffffffff at address 0x40aaad (thread 0009), starting debugger...
err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x11207c), expect failure

```

i have no clue what that means :)

---

### Post by gicanzo on 2013-04-24
wait, if start it on terminal with "wine empires2.exe", last error line also says that empires wasn't found:
```

~$ wine empires2.exe
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
wine: cannot find L"C:\\windows\\system32\\empires2.exe"

```

---

### Post by myromance123 on 2013-04-24
Don't worry about Wine not finding empires2. This is because PlayOnLinux stores it's Wineprefixes in a different place from the standalone Wine version.

May I know if you've installed the Nvidia proprietary driver yet?

One way you can install the Nvidia driver is by the Additional Drivers application. Open Ubuntu's Dash, and search for "Software Sources". Now go to the very right tab that says "Additional Drivers". Do you have any of the Nvidia drivers selected? (whether Experimental or not, either is fine).

For example, on my system I have selected "Using Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-experimental-310(proprietary)".

P.S: Could you also list out your entire computers hardware specs? I'm trying to figure out if your card is an Nvidia Optimus card, or a normal GeForce card.

---

### Post by gicanzo on 2013-04-25
I installed NVIDIA drivers taking them directly from NVIDIA's website. It was the 310.19 i think. I installed it as explained on their website and, apparently, everything went fine.
However, i still get the same errors when starting the game.

---

### Post by gicanzo on 2013-04-28
anyone can help???

---

### Post by seruling on 2013-09-16
I can install and play age of empire the conqueror in standalone Wine 1.6. Without playonlinux. I can install the 1.0c patch as well. If you can play other window games on wine, I do think it would play AOE as well.

---

