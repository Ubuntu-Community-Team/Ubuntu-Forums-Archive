---
title: "installing Oblivion on Wine"
date: 2008-11-21
forum: Wine
---

### Post by AvengingAngel718 on 2008-11-21
i'm trying to get oblivion running on wine and i've run into a little snag. i'm following the tutorial here: [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

i got to the part where you actually have to install the game and when i try to open setup.exe my wine desktop comes up and then....nothing

i thought i might get a little more insight on this if i tried running it in a terminal, and this is what it spit back at me:

caleb@caleb-fhqwgads:/media/cdrom0$ wine setup.exe
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xeda520,0x00000004,0xeda51c) Unknown information class
caleb@caleb-fhqwgads:/media/cdrom0$ wine OblivionLauncher.exe
caleb@caleb-fhqwgads:/media/cdrom0$ fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xeda520,0x00000004,0xeda51c) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xed940c): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0xed9258,0x00000000), stub!
wine: Unhandled page fault on write access to 0x003e2000 at address 0x4d86e6 (thread 0018), starting debugger...
Unhandled exception: page fault on write access to 0x003e2000 in 32-bit code (0x004d86e6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004d86e6 ESP:00eda8dc EBP:00eda8f0 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:ffffffff ECX:3fff3801 EDX:00000003
 ESI:003b0000 EDI:003e1ffe
Stack dump:
0x00eda8dc:  00eda924 00edad2c 003b0006 48590000
0x00eda8ec:  004d867b 00edad3c 004d54b7 003b0006
0x00eda8fc:  ffffffff 009b7900 00000000 00eccfba
0x00eda90c:  00c3ae94 00c94000 00000001 00000000
0x00eda91c:  00032000 00000030 5c3f3f5c 756c6f56
0x00eda92c:  307b656d 30303030 2d303030 30303030
Backtrace:
=>1 0x004d86e6 in setup (+0xd86e6) (0x00eda8f0)
  2 0x004d54b7 in setup (+0xd54b7) (0x00edad3c)
  3 0x00481e75 in setup (+0x81e75) (0x00eef93c)
  4 0x00434383 in setup (+0x34383) (0x00eefdbc)
  5 0x00000008 (0x00768e48)
0x004d86e6: repe stosl	%es:(%edi)
Modules:
Module	Address			Debug info	Name (77 modules)
PE	  400000-  cf0000	Export          setup
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7cc39000-7d9ab000	Deferred        libglcore.so.1
ELF	7e1e7000-7e28a000	Deferred        libgl.so.1
ELF	7e29b000-7e3b0000	Deferred        wined3d<elf>
  \-PE	7e2b0000-7e3b0000	\               wined3d
ELF	7e3b0000-7e3e1000	Deferred        d3d9<elf>
  \-PE	7e3c0000-7e3e1000	\               d3d9
ELF	7e42d000-7e460000	Deferred        uxtheme<elf>
  \-PE	7e430000-7e460000	\               uxtheme
ELF	7e460000-7e469000	Deferred        libxcursor.so.1
ELF	7e469000-7e46e000	Deferred        libxfixes.so.3
ELF	7e46e000-7e472000	Deferred        libxcomposite.so.1
ELF	7e472000-7e479000	Deferred        libxrandr.so.2
ELF	7e479000-7e483000	Deferred        libxrender.so.1
ELF	7e483000-7e486000	Deferred        libxinerama.so.1
ELF	7e486000-7e4a7000	Deferred        imm32<elf>
  \-PE	7e490000-7e4a7000	\               imm32
ELF	7e4a7000-7e4ac000	Deferred        libxdmcp.so.6
ELF	7e4ac000-7e4c5000	Deferred        libxcb.so.1
ELF	7e4c5000-7e4c8000	Deferred        libxcb-xlib.so.0
ELF	7e4c8000-7e4cb000	Deferred        libxau.so.6
ELF	7e4cb000-7e5ba000	Deferred        libx11.so.6
ELF	7e5ba000-7e5c9000	Deferred        libxext.so.6
ELF	7e5c9000-7e5cf000	Deferred        libxxf86vm.so.1
ELF	7e5cf000-7e5e7000	Deferred        libice.so.6
ELF	7e5e7000-7e5f0000	Deferred        libsm.so.6
ELF	7e5ff000-7e601000	Deferred        libnvidia-tls.so.1
ELF	7e601000-7e69c000	Deferred        winex11<elf>
  \-PE	7e610000-7e69c000	\               winex11
ELF	7e6ca000-7e6f1000	Deferred        libexpat.so.1
ELF	7e6f1000-7e71e000	Deferred        libfontconfig.so.1
ELF	7e71e000-7e734000	Deferred        libz.so.1
ELF	7e734000-7e7aa000	Deferred        libfreetype.so.6
ELF	7e7aa000-7e7d7000	Deferred        ws2_32<elf>
  \-PE	7e7b0000-7e7d7000	\               ws2_32
ELF	7e7d7000-7e7f2000	Deferred        wsock32<elf>
  \-PE	7e7e0000-7e7f2000	\               wsock32
ELF	7e7f2000-7e898000	Deferred        oleaut32<elf>
  \-PE	7e800000-7e898000	\               oleaut32
ELF	7e898000-7e8ac000	Deferred        libresolv.so.2
ELF	7e8ac000-7e8cb000	Deferred        iphlpapi<elf>
  \-PE	7e8b0000-7e8cb000	\               iphlpapi
ELF	7e8cb000-7e92e000	Deferred        rpcrt4<elf>
  \-PE	7e8e0000-7e92e000	\               rpcrt4
ELF	7e92e000-7e9d4000	Deferred        ole32<elf>
  \-PE	7e940000-7e9d4000	\               ole32
ELF	7e9d4000-7ea99000	Deferred        comctl32<elf>
  \-PE	7e9e0000-7ea99000	\               comctl32
ELF	7ea99000-7eaf4000	Deferred        shlwapi<elf>
  \-PE	7eab0000-7eaf4000	\               shlwapi
ELF	7eaf4000-7ec08000	Deferred        shell32<elf>
  \-PE	7eb00000-7ec08000	\               shell32
ELF	7ec08000-7ec5b000	Deferred        advapi32<elf>
  \-PE	7ec10000-7ec5b000	\               advapi32
ELF	7ec5b000-7ecfa000	Deferred        gdi32<elf>
  \-PE	7ec70000-7ecfa000	\               gdi32
ELF	7ecfa000-7ee46000	Deferred        user32<elf>
  \-PE	7ed10000-7ee46000	\               user32
ELF	7ee46000-7ee5b000	Deferred        lz32<elf>
  \-PE	7ee50000-7ee5b000	\               lz32
ELF	7ee5b000-7ee76000	Deferred        version<elf>
  \-PE	7ee60000-7ee76000	\               version
ELF	7ee76000-7ee8f000	Deferred        libnsl.so.1
ELF	7ee8f000-7ee98000	Deferred        libnss_compat.so.2
ELF	7efc9000-7efef000	Deferred        libm.so.6
ELF	7eff4000-7f000000	Deferred        libnss_files.so.2
ELF	b7dc4000-b7dcf000	Deferred        libnss_nis.so.2
ELF	b7dd0000-b7dd4000	Deferred        libdl.so.2
ELF	b7dd4000-b7f32000	Deferred        libc.so.6
ELF	b7f33000-b7f4c000	Deferred        libpthread.so.0
ELF	b7f5d000-b8094000	Deferred        libwine.so.1
ELF	b8096000-b80b3000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000001a    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000017 (D) D:\setup.exe
	00000018    0 <==
00000024 
	00000025    0
Backtrace:
=>1 0x004d86e6 in setup (+0xd86e6) (0x00eda8f0)
  2 0x004d54b7 in setup (+0xd54b7) (0x00edad3c)
  3 0x00481e75 in setup (+0x81e75) (0x00eef93c)
  4 0x00434383 in setup (+0x34383) (0x00eefdbc)
  5 0x00000008 (0x00768e48)


if anyone understands this mess and can help me, i'd greatly appreciate it.

---

