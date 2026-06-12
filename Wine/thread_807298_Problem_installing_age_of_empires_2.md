---
title: "Problem installing age of empires 2"
date: 2008-05-25
forum: Wine
---

### Post by Zigon on 2008-05-25
I installed Wine through synaptic package manager, all went smoothly :)

When trying to run the aoesetup.exe I get this big long list of errors.
I HATE vista so I'm giving Ubuntu a go on my new laptop, aoe is a must!

```
zigon@zigon-laptop:/media/cdrom0$ wine /media/cdrom0/aoesetup.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
zigon@zigon-laptop:/media/cdrom0$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0019), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:7f22f28c EBP:7f22f2b8 EFLAGS:00210202(   - 00      - -RI1)
 EAX:7f22f900 EBX:7e05bec8 ECX:00000000 EDX:00010026
 ESI:7f0211a8 EDI:00010026
Stack dump:
0x7f22f28c:  7e0572c0 7f0211a8 00000000 00010026
0x7f22f29c:  7f22f2b0 0041927e 00010026 00000000
0x7f22f2ac:  7e05727a 7ee1d70c 00000000 7f22f2c8
0x7f22f2bc:  00419159 7f0211a8 7f0211a8 7f22f334
0x7f22f2cc:  0043d2a0 00010026 00000100 00000110
0x7f22f2dc:  00000002 7ffd80cc 7f22f324 7b88e4e6
Backtrace:
=>1 0x00000000 (0x7f22f2b8)
  2 0x00419159 in ebu2bb (+0x19159) (0x7f22f2c8)
  3 0x0043d2a0 in ebu2bb (+0x3d2a0) (0x7f22f334)
  4 0x7edf869a WINPROC_wrapper+0x1a() in user32 (0x7f22f364)
  5 0x7edfa4d8 in user32 (+0xaa4d8) (0x7f22f3a4)
  6 0x7edfd615 in user32 (+0xad615) (0x7f22f874)
  7 0x7edfdf40 in user32 (+0xadf40) (0x7f22f8b4)
  8 0x7ed87b87 DefDlgProcW+0x87() in user32 (0x7f22f8e4)
  9 0x7edf869a WINPROC_wrapper+0x1a() in user32 (0x7f22f914)
  10 0x7edf8d7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f954)
  11 0x7edfe151 in user32 (+0xae151) (0x7f22f994)
  12 0x7edc187a in user32 (+0x7187a) (0x7f22fa04)
  13 0x7edc4afd in user32 (+0x74afd) (0x7f22fa64)
  14 0x7edc4f6a SendMessageW+0x4a() in user32 (0x7f22faa4)
  15 0x7ed8d43c in user32 (+0x3d43c) (0x7f22fc74)
  16 0x7ed8e666 CreateDialogIndirectParamAorW+0x36() in user32 (0x7f22fc94)
  17 0x7ed8e791 CreateDialogIndirectParamA+0x41() in user32 (0x7f22fcc4)
  18 0x0043cd5c in ebu2bb (+0x3cd5c) (0x7f22fd04)
  19 0x0042d54c in ebu2bb (+0x2d54c) (0x7f22fd18)
  20 0x0043cd01 in ebu2bb (+0x3cd01) (0x7f22fd24)
  21 0x0043cfc3 in ebu2bb (+0x3cfc3) (0x7f22fd34)
  22 0x0040456b in ebu2bb (+0x456b) (0x7f22ff08)
  23 0x7b875be7 in kernel32 (+0x55be7) (0x7f22ffe8)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (94 modules)
PE	  400000-  497000	Export          ebu2bb
PE	10000000-1021c000	Deferred        ebu6d8
ELF	7b800000-7b92c000	Export          kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e03f000-7e05e000	Deferred        imm32<elf>
  \-PE	7e050000-7e05e000	\               imm32
ELF	7e05e000-7e072000	Deferred        winejoystick<elf>
  \-PE	7e060000-7e072000	\               winejoystick
ELF	7e072000-7e086000	Deferred        midimap<elf>
  \-PE	7e080000-7e086000	\               midimap
ELF	7e086000-7e0ac000	Deferred        msacm32<elf>
  \-PE	7e090000-7e0ac000	\               msacm32
ELF	7e0ac000-7e0c3000	Deferred        msacm32<elf>
  \-PE	7e0b0000-7e0c3000	\               msacm32
ELF	7e0c3000-7e186000	Deferred        libasound.so.2
ELF	7e186000-7e1bc000	Deferred        winealsa<elf>
  \-PE	7e190000-7e1bc000	\               winealsa
ELF	7e1bc000-7e1c0000	Deferred        libgpg-error.so.0
ELF	7e1c0000-7e20d000	Deferred        libgcrypt.so.11
ELF	7e20d000-7e21d000	Deferred        libtasn1.so.3
ELF	7e21d000-7e220000	Deferred        libkeyutils.so.1
ELF	7e220000-7e228000	Deferred        libkrb5support.so.0
ELF	7e228000-7e25a000	Deferred        libcrypt.so.1
ELF	7e25a000-7e2d0000	Deferred        libgnutls.so.13
ELF	7e2d0000-7e2d3000	Deferred        libcom_err.so.2
ELF	7e2d3000-7e2f6000	Deferred        libk5crypto.so.3
ELF	7e2f6000-7e383000	Deferred        libkrb5.so.3
ELF	7e383000-7e3ac000	Deferred        libgssapi_krb5.so.2
ELF	7e3ac000-7e3df000	Deferred        libcups.so.2
ELF	7e431000-7e463000	Deferred        uxtheme<elf>
  \-PE	7e440000-7e463000	\               uxtheme
ELF	7e463000-7e46c000	Deferred        libxcursor.so.1
ELF	7e46c000-7e471000	Deferred        libxfixes.so.3
ELF	7e471000-7e474000	Deferred        libxcomposite.so.1
ELF	7e474000-7e47a000	Deferred        libxrandr.so.2
ELF	7e47a000-7e482000	Deferred        libxrender.so.1
ELF	7e482000-7e485000	Deferred        libxinerama.so.1
ELF	7e485000-7e48a000	Deferred        libxdmcp.so.6
ELF	7e48a000-7e4a2000	Deferred        libxcb.so.1
ELF	7e4a2000-7e589000	Deferred        libx11.so.6
ELF	7e589000-7e597000	Deferred        libxext.so.6
ELF	7e597000-7e59c000	Deferred        libxxf86vm.so.1
ELF	7e59c000-7e5b4000	Deferred        libice.so.6
ELF	7e5b4000-7e5bc000	Deferred        libsm.so.6
ELF	7e5c8000-7e659000	Deferred        winex11<elf>
  \-PE	7e5e0000-7e659000	\               winex11
ELF	7e678000-7e699000	Deferred        libexpat.so.1
ELF	7e699000-7e6c3000	Deferred        libfontconfig.so.1
ELF	7e6c4000-7e6c7000	Deferred        libxau.so.6
ELF	7e6cf000-7e6e4000	Deferred        libz.so.1
ELF	7e6e4000-7e754000	Deferred        libfreetype.so.6
ELF	7e754000-7e7e2000	Deferred        winmm<elf>
  \-PE	7e760000-7e7e2000	\               winmm
ELF	7e7e2000-7e7f6000	Deferred        lz32<elf>
  \-PE	7e7f0000-7e7f6000	\               lz32
ELF	7e7f6000-7e80f000	Deferred        version<elf>
  \-PE	7e800000-7e80f000	\               version
ELF	7e80f000-7e822000	Deferred        libresolv.so.2
ELF	7e822000-7e840000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e840000	\               iphlpapi
ELF	7e840000-7e8a0000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e8a0000	\               rpcrt4
ELF	7e8a0000-7e944000	Deferred        ole32<elf>
  \-PE	7e8b0000-7e944000	\               ole32
ELF	7e944000-7e97a000	Deferred        winspool<elf>
  \-PE	7e950000-7e97a000	\               winspool
ELF	7e97a000-7e9d3000	Deferred        shlwapi<elf>
  \-PE	7e990000-7e9d3000	\               shlwapi
ELF	7e9d3000-7eadd000	Deferred        shell32<elf>
  \-PE	7e9e0000-7eadd000	\               shell32
ELF	7eadd000-7eb86000	Deferred        comdlg32<elf>
  \-PE	7eae0000-7eb86000	\               comdlg32
ELF	7eb86000-7ec45000	Deferred        comctl32<elf>
  \-PE	7eb90000-7ec45000	\               comctl32
ELF	7ec45000-7ec96000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec96000	\               advapi32
ELF	7ec96000-7ed31000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed31000	\               gdi32
ELF	7ed31000-7ee77000	Export          user32<elf>
  \-PE	7ed50000-7ee77000	\               user32
ELF	7ee77000-7ee82000	Deferred        libnss_files.so.2
ELF	7ee82000-7ee9a000	Deferred        libnsl.so.1
ELF	7ee9a000-7eea3000	Deferred        libnss_compat.so.2
ELF	7efcf000-7eff4000	Deferred        libm.so.6
ELF	7eff4000-7eff6000	Deferred        libxcb-xlib.so.0
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d3c000-b7d40000	Deferred        libdl.so.2
ELF	b7d40000-b7e8f000	Deferred        libc.so.6
ELF	b7e90000-b7ea8000	Deferred        libpthread.so.0
ELF	b7eb4000-b7fc9000	Deferred        libwine.so.1
ELF	b7fcb000-b7fe7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000017    0
	00000016    0
	00000013    0
	00000010    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000014    0
	00000012    0
00000018 (D) C:\windows\temp\EBU2bb.EXE
	00000019    0 <==
0000001a 
	0000001c    0
	0000001b    0
Backtrace:
=>1 0x00000000 (0x7f22f2b8)
  2 0x00419159 in ebu2bb (+0x19159) (0x7f22f2c8)
  3 0x0043d2a0 in ebu2bb (+0x3d2a0) (0x7f22f334)
  4 0x7edf869a WINPROC_wrapper+0x1a() in user32 (0x7f22f364)
  5 0x7edfa4d8 in user32 (+0xaa4d8) (0x7f22f3a4)
  6 0x7edfd615 in user32 (+0xad615) (0x7f22f874)
  7 0x7edfdf40 in user32 (+0xadf40) (0x7f22f8b4)
  8 0x7ed87b87 DefDlgProcW+0x87() in user32 (0x7f22f8e4)
  9 0x7edf869a WINPROC_wrapper+0x1a() in user32 (0x7f22f914)
  10 0x7edf8d7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f954)
  11 0x7edfe151 in user32 (+0xae151) (0x7f22f994)
  12 0x7edc187a in user32 (+0x7187a) (0x7f22fa04)
  13 0x7edc4afd in user32 (+0x74afd) (0x7f22fa64)
  14 0x7edc4f6a SendMessageW+0x4a() in user32 (0x7f22faa4)
  15 0x7ed8d43c in user32 (+0x3d43c) (0x7f22fc74)
  16 0x7ed8e666 CreateDialogIndirectParamAorW+0x36() in user32 (0x7f22fc94)
  17 0x7ed8e791 CreateDialogIndirectParamA+0x41() in user32 (0x7f22fcc4)
  18 0x0043cd5c in ebu2bb (+0x3cd5c) (0x7f22fd04)
  19 0x0042d54c in ebu2bb (+0x2d54c) (0x7f22fd18)
  20 0x0043cd01 in ebu2bb (+0x3cd01) (0x7f22fd24)
  21 0x0043cfc3 in ebu2bb (+0x3cfc3) (0x7f22fd34)
  22 0x0040456b in ebu2bb (+0x456b) (0x7f22ff08)
  23 0x7b875be7 in kernel32 (+0x55be7) (0x7f22ffe8)

```

---

