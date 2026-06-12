---
title: "Dark Ages Problems..."
date: 2008-05-20
forum: Wine
---

### Post by dxrom on 2008-05-20
Hello... I have installed Dark Ages successfully... Or so I believe...
But when I attempt to run it I get the following errors...
```
fixme:spoolsv:serv_main (0 (nil))
[COLOR="Red"]err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
wine: Unhandled page fault on read access to 0x00000000 at address 0x7d70a91c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7d70a91c).[/COLOR]
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d70a91c ESP:0033eec0 EBP:7d179008 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c0661c4 ECX:7dd31500 EDX:7c0661d4
 ESI:7dd31438 EDI:7c065f68
Stack dump:
0x0033eec0:  7c0661c4 00000000 00000000 00000000
0x0033eed0:  00000001 7d179008 00000004 30000000
0x0033eee0:  7d179008 00000000 00000000 7dda0e2f
0x0033eef0:  7d179008 beef0201 00000002 30000000
0x0033ef00:  beef0014 00000000 00000000 3fffffff
0x0033ef10:  00000000 b7e38b20 00000000 b7d7798d
Backtrace:
=>1 0x7d70a91c _nv000082gl+0x3dc() in libglcore.so.1 (0x7d179008)
  2 0x00000000 (0x00000000)
0x7d70a91c _nv000082gl+0x3dc in libglcore.so.1: movl	0x0(%eax),%eax
Modules:
Module	Address			Debug info	Name (106 modules)
PE	  340000-  38e000	Deferred        scskapplink
PE	  400000-  928000	Deferred        darkages
PE	10000000-10057000	Deferred        binkw32
PE	21100000-2115d000	Deferred        mss32
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d21e000-7dd34000	Export          libglcore.so.1
ELF	7dd34000-7ddd8000	Deferred        libgl.so.1
ELF	7ddec000-7dee2000	Deferred        wined3d<elf>
  \-PE	7de00000-7dee2000	\               wined3d
ELF	7df2b000-7df5e000	Deferred        uxtheme<elf>
  \-PE	7df30000-7df5e000	\               uxtheme
ELF	7df5e000-7df73000	Deferred        midimap<elf>
  \-PE	7df60000-7df73000	\               midimap
ELF	7df73000-7df9a000	Deferred        msacm32<elf>
  \-PE	7df80000-7df9a000	\               msacm32
ELF	7df9a000-7dfb2000	Deferred        msacm32<elf>
  \-PE	7dfa0000-7dfb2000	\               msacm32
ELF	7dfb2000-7e064000	Deferred        libasound.so.2
ELF	7e078000-7e0ae000	Deferred        winealsa<elf>
  \-PE	7e080000-7e0ae000	\               winealsa
ELF	7e0ae000-7e0b8000	Deferred        libxcursor.so.1
ELF	7e0b8000-7e0be000	Deferred        libxfixes.so.3
ELF	7e0be000-7e0c2000	Deferred        libxcomposite.so.1
ELF	7e0c2000-7e0c9000	Deferred        libxrandr.so.2
ELF	7e0c9000-7e0d2000	Deferred        libxrender.so.1
ELF	7e0d2000-7e0d6000	Deferred        libxinerama.so.1
ELF	7e0d6000-7e0dc000	Deferred        libxdmcp.so.6
ELF	7e0dc000-7e0f5000	Deferred        libxcb.so.1
ELF	7e0f5000-7e0f8000	Deferred        libxcb-xlib.so.0
ELF	7e0f8000-7e0fc000	Deferred        libxau.so.6
ELF	7e0fc000-7e1e5000	Deferred        libx11.so.6
ELF	7e1e5000-7e1f4000	Deferred        libxext.so.6
ELF	7e1f4000-7e1fa000	Deferred        libxxf86vm.so.1
ELF	7e1fa000-7e212000	Deferred        libice.so.6
ELF	7e212000-7e21b000	Deferred        libsm.so.6
ELF	7e21b000-7e2ad000	Deferred        winex11<elf>
  \-PE	7e230000-7e2ad000	\               winex11
ELF	7e2f8000-7e415000	Deferred        libxml2.so.2
ELF	7e415000-7e440000	Deferred        libfontconfig.so.1
ELF	7e440000-7e452000	Deferred        libz.so.1
ELF	7e452000-7e4ce000	Deferred        libfreetype.so.6
ELF	7e4ce000-7e502000	Deferred        winspool<elf>
  \-PE	7e4e0000-7e502000	\               winspool
ELF	7e502000-7e517000	Deferred        lz32<elf>
  \-PE	7e510000-7e517000	\               lz32
ELF	7e517000-7e531000	Deferred        version<elf>
  \-PE	7e520000-7e531000	\               version
ELF	7e531000-7e597000	Deferred        setupapi<elf>
  \-PE	7e540000-7e597000	\               setupapi
ELF	7e597000-7e63a000	Deferred        oleaut32<elf>
  \-PE	7e5b0000-7e63a000	\               oleaut32
ELF	7e63a000-7e6fa000	Deferred        comctl32<elf>
  \-PE	7e640000-7e6fa000	\               comctl32
ELF	7e6fa000-7e801000	Deferred        shell32<elf>
  \-PE	7e710000-7e801000	\               shell32
ELF	7e801000-7e85a000	Deferred        shlwapi<elf>
  \-PE	7e810000-7e85a000	\               shlwapi
ELF	7e85a000-7e87c000	Deferred        mpr<elf>
  \-PE	7e860000-7e87c000	\               mpr
ELF	7e87c000-7e8c8000	Deferred        wininet<elf>
  \-PE	7e890000-7e8c8000	\               wininet
ELF	7e8c8000-7e8de000	Deferred        psapi<elf>
  \-PE	7e8d0000-7e8de000	\               psapi
ELF	7e8de000-7e929000	Deferred        dbghelp<elf>
  \-PE	7e8f0000-7e929000	\               dbghelp
ELF	7e929000-7e941000	Deferred        imagehlp<elf>
  \-PE	7e930000-7e941000	\               imagehlp
ELF	7e941000-7e95f000	Deferred        imm32<elf>
  \-PE	7e950000-7e95f000	\               imm32
ELF	7e95f000-7e9ed000	Deferred        winmm<elf>
  \-PE	7e970000-7e9ed000	\               winmm
ELF	7e9ed000-7ea4c000	Deferred        rpcrt4<elf>
  \-PE	7ea00000-7ea4c000	\               rpcrt4
ELF	7ea4c000-7eae5000	Deferred        gdi32<elf>
  \-PE	7ea60000-7eae5000	\               gdi32
ELF	7eae5000-7ec24000	Deferred        user32<elf>
  \-PE	7eb00000-7ec24000	\               user32
ELF	7ec24000-7ecc7000	Deferred        ole32<elf>
  \-PE	7ec30000-7ecc7000	\               ole32
ELF	7ecc7000-7ed1d000	Deferred        ddraw<elf>
  \-PE	7ecd0000-7ed1d000	\               ddraw
ELF	7ed1d000-7ed6a000	Deferred        advapi32<elf>
  \-PE	7ed30000-7ed6a000	\               advapi32
ELF	7ed6a000-7ed7c000	Deferred        libresolv.so.2
ELF	7ed7c000-7ed9b000	Deferred        iphlpapi<elf>
  \-PE	7ed80000-7ed9b000	\               iphlpapi
ELF	7ed9b000-7edc8000	Deferred        ws2_32<elf>
  \-PE	7eda0000-7edc8000	\               ws2_32
ELF	7edc8000-7ede3000	Deferred        wsock32<elf>
  \-PE	7edd0000-7ede3000	\               wsock32
ELF	7ede3000-7ef0d000	Deferred        kernel32<elf>
  \-PE	7ee00000-7ef0d000	\               kernel32
ELF	7ef0d000-7ef17000	Deferred        libnss_files.so.2
ELF	7ef17000-7ef21000	Deferred        libnss_nis.so.2
ELF	7ef21000-7ef37000	Deferred        libnsl.so.1
ELF	7ef37000-7ef5c000	Deferred        libm.so.6
ELF	7ef5c000-7f000000	Deferred        ntdll<elf>
  \-PE	7ef70000-7f000000	\               ntdll
ELF	b7d02000-b7d0a000	Deferred        libnss_compat.so.2
ELF	b7d0b000-b7d0f000	Deferred        libdl.so.2
ELF	b7d0f000-b7e3d000	Deferred        libc.so.6
ELF	b7e3d000-b7e54000	Deferred        libpthread.so.0
ELF	b7e5b000-b7e5d000	Deferred        libnvidia-tls.so.1
ELF	b7e5d000-b7e66000	Deferred        librt.so.1
ELF	b7e68000-b7f7d000	Deferred        libwine.so.1
ELF	b7f7e000-b7f9a000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\KRU\Dark Ages\Darkages.exe
	00000009    0 <==
0000000a 
	0000000b    0
00000010 
	00000011    0
Backtrace:
=>1 0x7d70a91c _nv000082gl+0x3dc() in libglcore.so.1 (0x7d179008)
  2 0x00000000 (0x00000000)
[COLOR="Red"]err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7d70cbb1[/COLOR]

```

Anyone have a solution? Im fairly new to the usage of Wine...
Im runnin Gentoo aswell btw... So I apologize if this is the wrong BBS... Im just trying to get help from everywhere... heh... ^^

---

