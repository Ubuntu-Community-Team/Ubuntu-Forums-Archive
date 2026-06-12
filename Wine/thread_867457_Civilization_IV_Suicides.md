---
title: "Civilization IV Suicides"
date: 2008-07-22
forum: Wine
---

### Post by Jeeeep on 2008-07-22
*warning* Absolute noob!

After recently switching I started to try to install a few of my older Windows applications that don't have Linux ports with Wine, and it's been working quite well thus far. However, when trying to use Civilization 4 (Which got a gold rating on the app DB) the installation file just dies. Here's the output from the terminal...

```
Unhandled page fault on read access to 0x3d002200 at address 0xb7d21283 (thread 001a), starting debugger...
Unhandled exception: page fault on read access to 0x3d002200 in 32-bit code (0xb7d21283).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d21283 ESP:0033dd1c EBP:0033de28 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:3d002200 EBX:7bc89464 ECX:00000000 EDX:00130510
 ESI:00000000 EDI:3d002200
Stack dump:
0x0033dd1c:  7bc48ce6 3d002200 00000000 000000b4
0x0033dd2c:  0033de10 00130478 00000088 7bc91d20
0x0033dd3c:  0033dd5c 7bc89464 7bc80608 00130518
0x0033dd4c:  7bc3386f 00130478 7bc89464 0033ddb8
0x0033dd5c:  0033de10 001303b0 0012ada8 00130510
0x0033dd6c:  00000000 0000002d 00000000 00000000
Backtrace:
=>1 0xb7d21283 strlen+0x33() in libc.so.6 (0x0033de28)
  2 0x7bc49aa0 in ntdll (+0x39aa0) (0x0033df28)
  3 0x7bc48012 in ntdll (+0x38012) (0x0033e078)
  4 0x7bc48358 LdrLoadDll+0x48() in ntdll (0x0033e0a8)
  5 0x7b867a85 in kernel32 (+0x47a85) (0x0033e308)
  6 0x7b867c88 LoadLibraryExW+0x48() in kernel32 (0x0033e338)
  7 0x7b867dd1 LoadLibraryExA+0x41() in kernel32 (0x0033e358)
  8 0x7b867e0d LoadLibraryA+0x2d() in kernel32 (0x0033e378)
  9 0x0040de3c in _is23b8 (+0xde3c) (0x0033e3c4)
  10 0x0040dbdf in _is23b8 (+0xdbdf) (0x0033e5f4)
  11 0x0040c38a in _is23b8 (+0xc38a) (0x0033fe7c)
  12 0x00422b09 in _is23b8 (+0x22b09) (0x0033ff08)
  13 0x7b8776a7 in kernel32 (+0x576a7) (0x0033ffe8)
0xb7d21283 strlen+0x33 in libc.so.6: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (70 modules)
PE	  400000-  470000	Export          _is23b8
ELF	7b800000-7b931000	Export          kernel32<elf>
  \-PE	7b820000-7b931000	\               kernel32
ELF	7bc00000-7bca5000	Export          ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e3a0000-7e3db000	Deferred        rsaenh<elf>
  \-PE	7e3b0000-7e3db000	\               rsaenh
ELF	7e3db000-7e443000	Deferred        crypt32<elf>
  \-PE	7e3f0000-7e443000	\               crypt32
ELF	7e498000-7e4cb000	Deferred        uxtheme<elf>
  \-PE	7e4a0000-7e4cb000	\               uxtheme
ELF	7e4cb000-7e4d4000	Deferred        libxcursor.so.1
ELF	7e4d4000-7e4d9000	Deferred        libxfixes.so.3
ELF	7e4d9000-7e4dc000	Deferred        libxcomposite.so.1
ELF	7e4dc000-7e4e2000	Deferred        libxrandr.so.2
ELF	7e4e2000-7e4ea000	Deferred        libxrender.so.1
ELF	7e4ea000-7e4ef000	Deferred        libxxf86vm.so.1
ELF	7e4ef000-7e4f2000	Deferred        libxinerama.so.1
ELF	7e4f2000-7e512000	Deferred        imm32<elf>
  \-PE	7e500000-7e512000	\               imm32
ELF	7e512000-7e52a000	Deferred        libxcb.so.1
ELF	7e52a000-7e611000	Deferred        libx11.so.6
ELF	7e611000-7e61f000	Deferred        libxext.so.6
ELF	7e61f000-7e637000	Deferred        libice.so.6
ELF	7e637000-7e63f000	Deferred        libsm.so.6
ELF	7e64b000-7e6e2000	Deferred        winex11<elf>
  \-PE	7e660000-7e6e2000	\               winex11
ELF	7e721000-7e742000	Deferred        libexpat.so.1
ELF	7e742000-7e76c000	Deferred        libfontconfig.so.1
ELF	7e76d000-7e772000	Deferred        libxdmcp.so.6
ELF	7e778000-7e78d000	Deferred        libz.so.1
ELF	7e78d000-7e7fd000	Deferred        libfreetype.so.6
ELF	7e809000-7e8ae000	Deferred        oleaut32<elf>
  \-PE	7e820000-7e8ae000	\               oleaut32
ELF	7e8ae000-7e8c1000	Deferred        libresolv.so.2
ELF	7e8c1000-7e8df000	Deferred        iphlpapi<elf>
  \-PE	7e8d0000-7e8df000	\               iphlpapi
ELF	7e8df000-7e941000	Deferred        rpcrt4<elf>
  \-PE	7e8f0000-7e941000	\               rpcrt4
ELF	7e941000-7e9e5000	Deferred        ole32<elf>
  \-PE	7e950000-7e9e5000	\               ole32
ELF	7e9e5000-7ea3e000	Deferred        shlwapi<elf>
  \-PE	7e9f0000-7ea3e000	\               shlwapi
ELF	7ea3e000-7eb53000	Deferred        shell32<elf>
  \-PE	7ea50000-7eb53000	\               shell32
ELF	7eb53000-7eb67000	Deferred        lz32<elf>
  \-PE	7eb60000-7eb67000	\               lz32
ELF	7eb67000-7eb80000	Deferred        version<elf>
  \-PE	7eb70000-7eb80000	\               version
ELF	7eb80000-7ebd2000	Deferred        advapi32<elf>
  \-PE	7eb90000-7ebd2000	\               advapi32
ELF	7ebd2000-7ec70000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec70000	\               gdi32
ELF	7ec70000-7edb7000	Deferred        user32<elf>
  \-PE	7ec90000-7edb7000	\               user32
ELF	7edb7000-7ee77000	Deferred        comctl32<elf>
  \-PE	7edc0000-7ee77000	\               comctl32
ELF	7ee77000-7ee82000	Deferred        libnss_files.so.2
ELF	7ee82000-7ee9a000	Deferred        libnsl.so.1
ELF	7ee9a000-7eea3000	Deferred        libnss_compat.so.2
ELF	7eea3000-7eea6000	Deferred        libxau.so.6
ELF	7efcf000-7eff4000	Deferred        libm.so.6
ELF	7eff4000-7eff6000	Deferred        libxcb-xlib.so.0
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cab000-b7caf000	Deferred        libdl.so.2
ELF	b7caf000-b7dfe000	Export          libc.so.6
ELF	b7dff000-b7e17000	Deferred        libpthread.so.0
ELF	b7e23000-b7f59000	Deferred        libwine.so.1
ELF	b7f5b000-b7f77000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
00000019 (D) C:\windows\temp\_is23b8.exe
	0000001a    0 <==
Backtrace:
=>1 0xb7d21283 strlen+0x33() in libc.so.6 (0x0033de28)
  2 0x7bc49aa0 in ntdll (+0x39aa0) (0x0033df28)
  3 0x7bc48012 in ntdll (+0x38012) (0x0033e078)
  4 0x7bc48358 LdrLoadDll+0x48() in ntdll (0x0033e0a8)
  5 0x7b867a85 in kernel32 (+0x47a85) (0x0033e308)
  6 0x7b867c88 LoadLibraryExW+0x48() in kernel32 (0x0033e338)
  7 0x7b867dd1 LoadLibraryExA+0x41() in kernel32 (0x0033e358)
  8 0x7b867e0d LoadLibraryA+0x2d() in kernel32 (0x0033e378)
  9 0x0040de3c in _is23b8 (+0xde3c) (0x0033e3c4)
  10 0x0040dbdf in _is23b8 (+0xdbdf) (0x0033e5f4)
  11 0x0040c38a in _is23b8 (+0xc38a) (0x0033fe7c)
  12 0x00422b09 in _is23b8 (+0x22b09) (0x0033ff08)
  13 0x7b8776a7 in kernel32 (+0x576a7) (0x0033ffe8)
```

It's Civilzation IV Gold Edition on Xubuntu 8.04.1, if that helps at all.

Absolutely no clue what to do or what most of this stuff means (not much of a nerd for that kinda stuff). Help?

---

