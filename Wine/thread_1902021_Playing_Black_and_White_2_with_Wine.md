---
title: "Playing Black and White 2 with Wine"
date: 2011-12-29
forum: Wine
---

### Post by christophski on 2011-12-29
Hi, I am trying to play Black and WHite 2 with wine. The wineappdb says that it runs perfectly with no faults. I have installed it fine and it loads up but when I try to start a new game it just crashes on the loading screen. I can't seem to find anybody else who has had this problem though so I am not sure what is wrong, can anybody help me? :S

---

### Post by oldos2er on 2011-12-30
Moved to Wine.

---

### Post by christophski on 2011-12-30
Thankyou, I didn't see that.

I have more details, it seems to be something to do with opengl. When I run the program it shows the splash screen then a blank window comes up and a dialog box that says "could not create the 3d device". In the terminal it says a lot of things along the lines of "Direct3d9 is not available without OpenGL" and "Couldn't initialise OpenGL" which is odd because I have opengl and glxgears works fine.

The other day I had the game working up until after the main menu (at which point it would crash when I made a new game) then I reinstalled wine and also did an "apt-get autoremove" and it has been doing this opengl thing since. I have a feeling that the autoremove got rid of something I need but I don't know what. I have een done a complete reinstall of ubuntu but no luck :/

---

### Post by Dlambert on 2011-12-31
Install freeglut (just try it) :

[http://ubuntuforums.org/showthread.php?t=345177]("http://ubuntuforums.org/showthread.php?t=345177")

Are your graphics drivers installed? Latest versions?

Maybe add the -opengl to the command.

---

### Post by christophski on 2012-01-01
I am having this problem on both of my computers, one with open source radeon drivers and one with open source intel and nvidia drivers (nvidia optimus card using Ironhide). Both are latest versions as far as I can tell.
Which command do I add -opengl to? the wine command?

---

### Post by christophski on 2012-01-02
can anybody help me? this is the output when I run it on my desktop:
```
christie@christie-desktop:~/.wine/drive_c/Program Files/Lionhead Studios/Black & White 2$ wine white.exe 
fixme:heap:HeapSetInformation 0x2a31000 0 0x25afd34 4
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x25af764,0x25af768): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x25af764,0x25af768): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x25af0f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x25af2b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x25aed34,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x25af238,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:query_init Unhandled query type 0x5.
fixme:d3d:query_init Unhandled query type 0x6.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
wine: Unhandled page fault on read access to 0x7bfe6200 at address 0x7cf86de8 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x7bfe6200 in 32-bit code (0x7cf86de8).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7cf86de8 ESP:0259ecf8 EBP:7bfe6200 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:7d05fff4 ECX:00000e00 EDX:00000e00
 ESI:00000320 EDI:0259edd8
Stack dump:
0x0259ecf8:  7c798408 7c7ce420 0259edd8 7d73aef0
0x0259ed08:  00000320 00000001 00000000 00000c80
0x0259ed18:  00000000 00000320 00000258 7d05fff4
0x0259ed28:  00000256 00000001 0259edd8 7cfc0cd4
0x0259ed38:  7c798408 7c7ce420 00000000 00000001
0x0259ed48:  00000320 00000001 0259edd8 00000258
Backtrace:
=>0 0x7cf86de8 pipe_get_tile_z+0x178() in libgallium.so (0x7bfe6200)
  1 0x7cfc0cd4 in libgallium.so (+0xebcd3) (0x0259edd8)
  2 0x7cfc115d in libgallium.so (+0xec15c) (0x7c89fac0)
  3 0x7d283f2c in libdricore.so (+0xcaf2b) (0x7c74cd28)
  4 0x7e72cc59 in wined3d (+0xbcc58) (0x025aefb0)
  5 0x7e6ccca6 in wined3d (+0x5cca5) (0x025af260)
  6 0x7e6ae588 wined3d_device_draw_primitive+0x77() in wined3d (0x025af2a0)
  7 0x7e7a7cad in d3d9 (+0x17cac) (0x025af2e0)
0x7cf86de8 pipe_get_tile_z+0x178 in libgallium.so: movl	0x0(%ebp,%eax,4),%ecx
Modules:
Module	Address			Debug info	Name (130 modules)
PE	  400000- 2340000	Export          white
PE	 25b0000- 2803000	Deferred        d3dx9_25
PE	10000000-100b0000	Deferred        scriptlibraryr
PE	18000000-18068000	Deferred        binkw32
PE	66700000-668a9000	Deferred        ~df394b.tmp
ELF	7a714000-7b800000	Deferred        libllvm-2.9.so.1
ELF	7b800000-7b9aa000	Deferred        kernel32<elf>
  \-PE	7b810000-7b9aa000	\               kernel32
ELF	7bc00000-7bcc4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc4000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ced5000-7d0a5000	Dwarf           libgallium.so
ELF	7d0a5000-7d1b9000	Deferred        libglsl.so
ELF	7d1b9000-7d400000	Dwarf           libdricore.so
ELF	7d637000-7d676000	Deferred        dinput<elf>
  \-PE	7d640000-7d676000	\               dinput
ELF	7d67e000-7d6b0000	Deferred        usp10<elf>
  \-PE	7d680000-7d6b0000	\               usp10
ELF	7d6b0000-7d6b7000	Deferred        libffi.so.6
ELF	7d6b7000-7d793000	Deferred        r600_dri.so
ELF	7d793000-7d79f000	Deferred        libdrm.so.2
ELF	7d79f000-7d7b5000	Deferred        libglapi.so.0
ELF	7d7b5000-7d809000	Deferred        libgl.so.1
ELF	7d82e000-7d84c000	Deferred        libgcc_s.so.1
ELF	7d84c000-7d867000	Deferred        spoolss<elf>
  \-PE	7d850000-7d867000	\               spoolss
ELF	7d867000-7d870000	Deferred        librt.so.1
ELF	7d870000-7d875000	Deferred        libgpg-error.so.0
ELF	7d875000-7d88c000	Deferred        libresolv.so.2
ELF	7d88c000-7d890000	Deferred        libkeyutils.so.1
ELF	7d890000-7d8d9000	Deferred        libdbus-1.so.3
ELF	7d8d9000-7d95e000	Deferred        libgcrypt.so.11
ELF	7d95e000-7d970000	Deferred        libtasn1.so.3
ELF	7d970000-7d979000	Deferred        libkrb5support.so.0
ELF	7d979000-7d9a2000	Deferred        libk5crypto.so.3
ELF	7d9a2000-7da6b000	Deferred        libkrb5.so.3
ELF	7da6b000-7da7e000	Deferred        libavahi-client.so.3
ELF	7da7e000-7da8c000	Deferred        libavahi-common.so.3
ELF	7da8c000-7db3c000	Deferred        libgnutls.so.26
ELF	7db3c000-7db7a000	Deferred        libgssapi_krb5.so.2
ELF	7db7a000-7dbcc000	Deferred        libcups.so.2
ELF	7dbcc000-7dbd0000	Deferred        libxdamage.so.1
ELF	7dbd0000-7dbf1000	Deferred        localspl<elf>
  \-PE	7dbe0000-7dbf1000	\               localspl
ELF	7dc1e000-7dc52000	Deferred        uxtheme<elf>
  \-PE	7dc20000-7dc52000	\               uxtheme
ELF	7dc68000-7dc6e000	Deferred        libxfixes.so.3
ELF	7dc6e000-7dc79000	Deferred        libxcursor.so.1
ELF	7dc79000-7dc89000	Deferred        libxi.so.6
ELF	7dc89000-7dc8d000	Deferred        libxcomposite.so.1
ELF	7dc8d000-7dc96000	Deferred        libxrandr.so.2
ELF	7dc96000-7dca1000	Deferred        libxrender.so.1
ELF	7dca1000-7dca7000	Deferred        libxxf86vm.so.1
ELF	7dca7000-7dcae000	Deferred        libxdmcp.so.6
ELF	7dcae000-7dccd000	Deferred        libxcb.so.1
ELF	7dccd000-7dcd3000	Deferred        libuuid.so.1
ELF	7dcd3000-7dced000	Deferred        libice.so.6
ELF	7dced000-7de23000	Deferred        libx11.so.6
ELF	7de23000-7de36000	Deferred        libxext.so.6
ELF	7de36000-7de3f000	Deferred        libsm.so.6
ELF	7de45000-7de49000	Deferred        libcom_err.so.2
ELF	7de64000-7df0a000	Deferred        winex11<elf>
  \-PE	7de70000-7df0a000	\               winex11
ELF	7df5d000-7df87000	Deferred        libexpat.so.1
ELF	7df87000-7dfbc000	Deferred        libfontconfig.so.1
ELF	7dfbc000-7dfd1000	Deferred        libz.so.1
ELF	7dfd1000-7e068000	Deferred        libfreetype.so.6
ELF	7e068000-7e087000	Deferred        libtinfo.so.5
ELF	7e087000-7e0a9000	Deferred        libncurses.so.5
ELF	7e0a9000-7e0ad000	Deferred        libxinerama.so.1
ELF	7e0ce000-7e0f0000	Deferred        imm32<elf>
  \-PE	7e0d0000-7e0f0000	\               imm32
ELF	7e0f0000-7e156000	Deferred        ddraw<elf>
  \-PE	7e100000-7e156000	\               ddraw
ELF	7e156000-7e178000	Deferred        iphlpapi<elf>
  \-PE	7e160000-7e178000	\               iphlpapi
ELF	7e178000-7e1a2000	Deferred        netapi32<elf>
  \-PE	7e180000-7e1a2000	\               netapi32
ELF	7e1a2000-7e1bd000	Deferred        dinput8<elf>
  \-PE	7e1b0000-7e1bd000	\               dinput8
ELF	7e1bd000-7e1f6000	Deferred        winspool<elf>
  \-PE	7e1c0000-7e1f6000	\               winspool
ELF	7e1f6000-7e2ec000	Deferred        comctl32<elf>
  \-PE	7e200000-7e2ec000	\               comctl32
ELF	7e2ec000-7e4fd000	Deferred        shell32<elf>
  \-PE	7e300000-7e4fd000	\               shell32
ELF	7e4fd000-7e5f2000	Deferred        comdlg32<elf>
  \-PE	7e500000-7e5f2000	\               comdlg32
ELF	7e5f2000-7e65b000	Deferred        shlwapi<elf>
  \-PE	7e600000-7e65b000	\               shlwapi
ELF	7e65b000-7e78e000	Dwarf           wined3d<elf>
  \-PE	7e670000-7e78e000	\               wined3d
ELF	7e78e000-7e7c6000	Dwarf           d3d9<elf>
  \-PE	7e790000-7e7c6000	\               d3d9
ELF	7e7c6000-7e852000	Deferred        msvcrt<elf>
  \-PE	7e7e0000-7e852000	\               msvcrt
ELF	7e852000-7e884000	Deferred        ws2_32<elf>
  \-PE	7e860000-7e884000	\               ws2_32
ELF	7e884000-7e898000	Deferred        psapi<elf>
  \-PE	7e890000-7e898000	\               psapi
ELF	7e898000-7e8f5000	Deferred        dbghelp<elf>
  \-PE	7e8a0000-7e8f5000	\               dbghelp
ELF	7e8f5000-7e91e000	Deferred        msacm32<elf>
  \-PE	7e900000-7e91e000	\               msacm32
ELF	7e91e000-7e994000	Deferred        rpcrt4<elf>
  \-PE	7e930000-7e994000	\               rpcrt4
ELF	7e994000-7ea9b000	Deferred        ole32<elf>
  \-PE	7e9b0000-7ea9b000	\               ole32
ELF	7ea9b000-7eb3d000	Deferred        winmm<elf>
  \-PE	7eaa0000-7eb3d000	\               winmm
ELF	7eb3d000-7ec7a000	Deferred        user32<elf>
  \-PE	7eb50000-7ec7a000	\               user32
ELF	7ec7a000-7ed1f000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed1f000	\               gdi32
ELF	7ed1f000-7ed7f000	Deferred        advapi32<elf>
  \-PE	7ed30000-7ed7f000	\               advapi32
ELF	7ef7f000-7ef8c000	Deferred        libnss_files.so.2
ELF	7ef8c000-7ef98000	Deferred        libnss_nis.so.2
ELF	7ef98000-7efb1000	Deferred        libnsl.so.1
ELF	7efb1000-7efdb000	Deferred        libm.so.6
ELF	7efdb000-7efdf000	Deferred        libxau.so.6
ELF	7efe7000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f73e9000-f73ee000	Deferred        libdl.so.2
ELF	f73ee000-f7568000	Deferred        libc.so.6
ELF	f7569000-f7584000	Deferred        libpthread.so.0
ELF	f7586000-f7590000	Deferred        libnss_compat.so.2
ELF	f75a9000-f76eb000	Dwarf           libwine.so.1
ELF	f76ed000-f770d000	Deferred        ld-linux.so.2
ELF	f770d000-f770e000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Lionhead Studios\Black & White 2\white.exe
	00000029    0
	00000009    0 <==
0000000e services.exe
	00000020    0
	0000001b    0
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000013    0
	00000012    0
00000018 plugplay.exe
	0000001c    0
	0000001a    0
	00000019    0
0000001d winedevice.exe
	00000021    0
	0000001f    0
	0000001e    0
00000022 explorer.exe
	00000023    0
00000024 ~e5.0001
	00000026    0
	00000025    0
Backtrace:
=>0 0x7cf86de8 pipe_get_tile_z+0x178() in libgallium.so (0x7bfe6200)
  1 0x7cfc0cd4 in libgallium.so (+0xebcd3) (0x0259edd8)
  2 0x7cfc115d in libgallium.so (+0xec15c) (0x7c89fac0)
  3 0x7d283f2c in libdricore.so (+0xcaf2b) (0x7c74cd28)
  4 0x7e72cc59 in wined3d (+0xbcc58) (0x025aefb0)
  5 0x7e6ccca6 in wined3d (+0x5cca5) (0x025af260)
  6 0x7e6ae588 wined3d_device_draw_primitive+0x77() in wined3d (0x025af2a0)
  7 0x7e7a7cad in d3d9 (+0x17cac) (0x025af2e0)

```

---

