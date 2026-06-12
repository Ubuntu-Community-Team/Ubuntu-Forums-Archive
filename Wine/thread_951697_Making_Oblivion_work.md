---
title: "Making Oblivion work"
date: 2008-10-18
forum: Wine
---

### Post by Eax.exe on 2008-10-18
Hi :)

I have an Acer Aspire 9300 with a GeForce Go 7600 and I'm trying to make Oblivion work.
I followed this guide: [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

And when I run the game I get this error:
```

err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
wine: Unhandled page fault on read access to 0x00000000 at address 0x7de6f0c5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7de6f0c5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7de6f0c5 ESP:0032f3e4 EBP:0032f408 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7de82678 ECX:7de82e80 EDX:ffffffff
 ESI:0013fde8 EDI:7de82e7c
Stack dump:
0x0032f3e4:  7de82ed0 7de7dba4 7de7f379 0013fde8
0x0032f3f4:  00000000 00000014 15000578 15000578
0x0032f404:  0032f9b6 0013fde8 00775cd3 0013fde8
0x0032f414:  0032f9b6 15000578 00000000 00400000
0x0032f424:  00775e24 0013fde8 00b28e00 0013fde8
0x0032f434:  00763e45 0013fde8 00b28e00 00010024
Backtrace:
=>1 0x7de6f0c5 in d3d9 (+0xf0c5) (0x0032f408)
  2 0x00775cd3 in oblivion (+0x375cd3) (0x0013fde8)
  3 0x00000001 (0x7de81fa0)
  4 0x7de6e8d0 in d3d9 (+0xe8d0) (0x7de6f1a0)
  5 0xe5890000 (0x0010b955)
0x7de6f0c5: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (96 modules)
PE	  400000-  baf000	Export          oblivion
PE	  bb0000-  dff000	Deferred        d3dx9_27
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d186000-7dc9b000	Deferred        libglcore.so.1
ELF	7dc9b000-7dd3f000	Deferred        libgl.so.1
ELF	7dd50000-7de53000	Deferred        wined3d<elf>
  \-PE	7dd60000-7de53000	\               wined3d
ELF	7de53000-7de83000	Export          d3d9<elf>
  \-PE	7de60000-7de83000	\               d3d9
ELF	7e224000-7e238000	Deferred        midimap<elf>
  \-PE	7e230000-7e238000	\               midimap
ELF	7e238000-7e25e000	Deferred        msacm32<elf>
  \-PE	7e240000-7e25e000	\               msacm32
ELF	7e25e000-7e275000	Deferred        msacm32<elf>
  \-PE	7e260000-7e275000	\               msacm32
ELF	7e275000-7e338000	Deferred        libasound.so.2
ELF	7e349000-7e37f000	Deferred        winealsa<elf>
  \-PE	7e350000-7e37f000	\               winealsa
ELF	7e37f000-7e3b2000	Deferred        uxtheme<elf>
  \-PE	7e390000-7e3b2000	\               uxtheme
ELF	7e3b2000-7e3bb000	Deferred        libxcursor.so.1
ELF	7e3bb000-7e3c0000	Deferred        libxfixes.so.3
ELF	7e3c0000-7e3c3000	Deferred        libxcomposite.so.1
ELF	7e3c3000-7e3c9000	Deferred        libxrandr.so.2
ELF	7e3c9000-7e3d1000	Deferred        libxrender.so.1
ELF	7e3d1000-7e3d4000	Deferred        libxinerama.so.1
ELF	7e3d4000-7e3f4000	Deferred        imm32<elf>
  \-PE	7e3e0000-7e3f4000	\               imm32
ELF	7e3f4000-7e3f9000	Deferred        libxdmcp.so.6
ELF	7e3f9000-7e411000	Deferred        libxcb.so.1
ELF	7e411000-7e414000	Deferred        libxau.so.6
ELF	7e414000-7e4fb000	Deferred        libx11.so.6
ELF	7e4fb000-7e509000	Deferred        libxext.so.6
ELF	7e509000-7e521000	Deferred        libice.so.6
ELF	7e521000-7e529000	Deferred        libsm.so.6
ELF	7e533000-7e535000	Deferred        libnvidia-tls.so.1
ELF	7e53a000-7e5d1000	Deferred        winex11<elf>
  \-PE	7e550000-7e5d1000	\               winex11
ELF	7e602000-7e623000	Deferred        libexpat.so.1
ELF	7e623000-7e64d000	Deferred        libfontconfig.so.1
ELF	7e64d000-7e662000	Deferred        libz.so.1
ELF	7e662000-7e6cf000	Deferred        libfreetype.so.6
ELF	7e6cf000-7e6fb000	Deferred        ws2_32<elf>
  \-PE	7e6e0000-7e6fb000	\               ws2_32
ELF	7e6fb000-7e715000	Deferred        wsock32<elf>
  \-PE	7e700000-7e715000	\               wsock32
ELF	7e715000-7e77f000	Deferred        msvcrt<elf>
  \-PE	7e730000-7e77f000	\               msvcrt
ELF	7e77f000-7e793000	Deferred        lz32<elf>
  \-PE	7e780000-7e793000	\               lz32
ELF	7e793000-7e7ac000	Deferred        version<elf>
  \-PE	7e7a0000-7e7ac000	\               version
ELF	7e7ac000-7e805000	Deferred        shlwapi<elf>
  \-PE	7e7c0000-7e805000	\               shlwapi
ELF	7e805000-7e918000	Deferred        shell32<elf>
  \-PE	7e820000-7e918000	\               shell32
ELF	7e918000-7e962000	Deferred        dsound<elf>
  \-PE	7e920000-7e962000	\               dsound
ELF	7e962000-7e9f4000	Deferred        winmm<elf>
  \-PE	7e970000-7e9f4000	\               winmm
ELF	7e9f4000-7ea07000	Deferred        libresolv.so.2
ELF	7ea07000-7ea09000	Deferred        libxcb-xlib.so.0
ELF	7ea09000-7ea0e000	Deferred        libxxf86vm.so.1
ELF	7ea18000-7ea36000	Deferred        iphlpapi<elf>
  \-PE	7ea20000-7ea36000	\               iphlpapi
ELF	7ea36000-7ea97000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea97000	\               rpcrt4
ELF	7ea97000-7eb3b000	Deferred        ole32<elf>
  \-PE	7eab0000-7eb3b000	\               ole32
ELF	7eb3b000-7eb72000	Deferred        dinput<elf>
  \-PE	7eb40000-7eb72000	\               dinput
ELF	7eb72000-7eb8a000	Deferred        dinput8<elf>
  \-PE	7eb80000-7eb8a000	\               dinput8
ELF	7eb8a000-7ebdc000	Deferred        advapi32<elf>
  \-PE	7eba0000-7ebdc000	\               advapi32
ELF	7ebdc000-7ec77000	Deferred        gdi32<elf>
  \-PE	7ebf0000-7ec77000	\               gdi32
ELF	7ec77000-7edbe000	Deferred        user32<elf>
  \-PE	7ec90000-7edbe000	\               user32
ELF	7edbe000-7ee7d000	Deferred        comctl32<elf>
  \-PE	7edd0000-7ee7d000	\               comctl32
ELF	7ef9d000-7efa8000	Deferred        libnss_files.so.2
ELF	7efa8000-7efb2000	Deferred        libnss_nis.so.2
ELF	7efb2000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c32000-b7c36000	Deferred        libdl.so.2
ELF	b7c36000-b7d85000	Deferred        libc.so.6
ELF	b7d86000-b7d9e000	Deferred        libpthread.so.0
ELF	b7daf000-b7ee5000	Deferred        libwine.so.1
ELF	b7ee7000-b7f03000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
	0000001a   15
	00000019   15
	00000018    0
	00000009    0 <==
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:
=>1 0x7de6f0c5 in d3d9 (+0xf0c5) (0x0032f408)
  2 0x00775cd3 in oblivion (+0x375cd3) (0x0013fde8)
  3 0x00000001 (0x7de81fa0)
  4 0x7de6e8d0 in d3d9 (+0xe8d0) (0x7de6f1a0)
  5 0xe5890000 (0x0010b955)
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

I tried googling but found no solution :S

Anyone have any ideas?

Thanks in advance :D

---

### Post by Eax.exe on 2008-10-19
Does anyone know a solution to my problem?

---

### Post by Ferrat on 2008-10-20
```

err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

```

looks like it can't initialize OpenGL, are you sure your drivers are installed and activated for your graphics?

---

### Post by Eax.exe on 2008-11-01
Yeah I'm pretty certain that they are activated and they work :)
I get no error from glxgears and it's activated in Device Manager.

Any ideas?

---

### Post by Eax.exe on 2008-11-02
This is the error I get when I run "wine Oblivion.exe -opengl":

```
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
wine: Unhandled page fault on read access to 0x00000000 at address 0x7de6f0c5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7de6f0c5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7de6f0c5 ESP:0032f3e4 EBP:0032f408 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7de82678 ECX:7de82e80 EDX:ffffffff
 ESI:0013fe00 EDI:7de82e7c
Stack dump:
0x0032f3e4:  7de82ed0 7de7dba4 7de7f379 0013fe00
0x0032f3f4:  00000000 00000014 15000578 15000578
0x0032f404:  0032f9b6 0013fe00 00775cd3 0013fe00
0x0032f414:  0032f9b6 15000578 00000000 00400000
0x0032f424:  00775e24 0013fe00 00b28e00 0013fe00
0x0032f434:  00763e45 0013fe00 00b28e00 00010024
Backtrace:
=>1 0x7de6f0c5 in d3d9 (+0xf0c5) (0x0032f408)
  2 0x00775cd3 in oblivion (+0x375cd3) (0x0013fe00)
  3 0x00000001 (0x7de81fa0)
  4 0x7de6e8d0 in d3d9 (+0xe8d0) (0x7de6f1a0)
  5 0xe5890000 (0x0010b955)
0x7de6f0c5: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (96 modules)
PE	  400000-  baf000	Export          oblivion
PE	  bb0000-  dff000	Deferred        d3dx9_27
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d186000-7dc9b000	Deferred        libglcore.so.1
ELF	7dc9b000-7dd3f000	Deferred        libgl.so.1
ELF	7dd50000-7de53000	Deferred        wined3d<elf>
  \-PE	7dd60000-7de53000	\               wined3d
ELF	7de53000-7de83000	Export          d3d9<elf>
  \-PE	7de60000-7de83000	\               d3d9
ELF	7e224000-7e238000	Deferred        midimap<elf>
  \-PE	7e230000-7e238000	\               midimap
ELF	7e238000-7e25e000	Deferred        msacm32<elf>
  \-PE	7e240000-7e25e000	\               msacm32
ELF	7e25e000-7e275000	Deferred        msacm32<elf>
  \-PE	7e260000-7e275000	\               msacm32
ELF	7e275000-7e338000	Deferred        libasound.so.2
ELF	7e349000-7e37f000	Deferred        winealsa<elf>
  \-PE	7e350000-7e37f000	\               winealsa
ELF	7e37f000-7e3b2000	Deferred        uxtheme<elf>
  \-PE	7e390000-7e3b2000	\               uxtheme
ELF	7e3b2000-7e3bb000	Deferred        libxcursor.so.1
ELF	7e3bb000-7e3c0000	Deferred        libxfixes.so.3
ELF	7e3c0000-7e3c3000	Deferred        libxcomposite.so.1
ELF	7e3c3000-7e3c9000	Deferred        libxrandr.so.2
ELF	7e3c9000-7e3d1000	Deferred        libxrender.so.1
ELF	7e3d1000-7e3d4000	Deferred        libxinerama.so.1
ELF	7e3d4000-7e3f4000	Deferred        imm32<elf>
  \-PE	7e3e0000-7e3f4000	\               imm32
ELF	7e3f4000-7e3f9000	Deferred        libxdmcp.so.6
ELF	7e3f9000-7e411000	Deferred        libxcb.so.1
ELF	7e411000-7e414000	Deferred        libxau.so.6
ELF	7e414000-7e4fb000	Deferred        libx11.so.6
ELF	7e4fb000-7e509000	Deferred        libxext.so.6
ELF	7e509000-7e521000	Deferred        libice.so.6
ELF	7e521000-7e529000	Deferred        libsm.so.6
ELF	7e533000-7e535000	Deferred        libnvidia-tls.so.1
ELF	7e53a000-7e5d1000	Deferred        winex11<elf>
  \-PE	7e550000-7e5d1000	\               winex11
ELF	7e602000-7e623000	Deferred        libexpat.so.1
ELF	7e623000-7e64d000	Deferred        libfontconfig.so.1
ELF	7e64d000-7e662000	Deferred        libz.so.1
ELF	7e662000-7e6cf000	Deferred        libfreetype.so.6
ELF	7e6cf000-7e6fb000	Deferred        ws2_32<elf>
  \-PE	7e6e0000-7e6fb000	\               ws2_32
ELF	7e6fb000-7e715000	Deferred        wsock32<elf>
  \-PE	7e700000-7e715000	\               wsock32
ELF	7e715000-7e77f000	Deferred        msvcrt<elf>
  \-PE	7e730000-7e77f000	\               msvcrt
ELF	7e77f000-7e793000	Deferred        lz32<elf>
  \-PE	7e780000-7e793000	\               lz32
ELF	7e793000-7e7ac000	Deferred        version<elf>
  \-PE	7e7a0000-7e7ac000	\               version
ELF	7e7ac000-7e805000	Deferred        shlwapi<elf>
  \-PE	7e7c0000-7e805000	\               shlwapi
ELF	7e805000-7e918000	Deferred        shell32<elf>
  \-PE	7e820000-7e918000	\               shell32
ELF	7e918000-7e962000	Deferred        dsound<elf>
  \-PE	7e920000-7e962000	\               dsound
ELF	7e962000-7e9f4000	Deferred        winmm<elf>
  \-PE	7e970000-7e9f4000	\               winmm
ELF	7e9f4000-7ea07000	Deferred        libresolv.so.2
ELF	7ea07000-7ea09000	Deferred        libxcb-xlib.so.0
ELF	7ea09000-7ea0e000	Deferred        libxxf86vm.so.1
ELF	7ea18000-7ea36000	Deferred        iphlpapi<elf>
  \-PE	7ea20000-7ea36000	\               iphlpapi
ELF	7ea36000-7ea97000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea97000	\               rpcrt4
ELF	7ea97000-7eb3b000	Deferred        ole32<elf>
  \-PE	7eab0000-7eb3b000	\               ole32
ELF	7eb3b000-7eb72000	Deferred        dinput<elf>
  \-PE	7eb40000-7eb72000	\               dinput
ELF	7eb72000-7eb8a000	Deferred        dinput8<elf>
  \-PE	7eb80000-7eb8a000	\               dinput8
ELF	7eb8a000-7ebdc000	Deferred        advapi32<elf>
  \-PE	7eba0000-7ebdc000	\               advapi32
ELF	7ebdc000-7ec77000	Deferred        gdi32<elf>
  \-PE	7ebf0000-7ec77000	\               gdi32
ELF	7ec77000-7edbe000	Deferred        user32<elf>
  \-PE	7ec90000-7edbe000	\               user32
ELF	7edbe000-7ee7d000	Deferred        comctl32<elf>
  \-PE	7edd0000-7ee7d000	\               comctl32
ELF	7ef9d000-7efa8000	Deferred        libnss_files.so.2
ELF	7efa8000-7efb2000	Deferred        libnss_nis.so.2
ELF	7efb2000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7cc2000-b7cc6000	Deferred        libdl.so.2
ELF	b7cc6000-b7e15000	Deferred        libc.so.6
ELF	b7e16000-b7e2e000	Deferred        libpthread.so.0
ELF	b7e3f000-b7f75000	Deferred        libwine.so.1
ELF	b7f77000-b7f93000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
	0000001a   15
	00000019   15
	00000018    0
	00000009    0 <==
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:
=>1 0x7de6f0c5 in d3d9 (+0xf0c5) (0x0032f408)
  2 0x00775cd3 in oblivion (+0x375cd3) (0x0013fe00)
  3 0x00000001 (0x7de81fa0)
  4 0x7de6e8d0 in d3d9 (+0xe8d0) (0x7de6f1a0)
  5 0xe5890000 (0x0010b955)
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

---

### Post by Eax.exe on 2008-11-07
Anyone?

---

