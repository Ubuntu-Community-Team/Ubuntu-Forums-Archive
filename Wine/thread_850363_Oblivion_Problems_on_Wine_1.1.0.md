---
title: "Oblivion Problems on Wine 1.1.0"
date: 2008-07-05
forum: Wine
---

### Post by Zavior on 2008-07-05
I am really not sure what happened. I had Oblivion working fine for a while and then I didn't play it for some time and now it won't work. The only thing that has changed I think is that Ubuntu automatically updated Wine to its current version. Here is the output when Oblivion is started in the console.

```
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(1152,864)
wine: Unhandled page fault on read access to 0x00000004 at address 0x58dc7c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x0058dc7c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0058dc7c ESP:0032e64c EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:3e84c6d3 EDX:ffffffff
 ESI:00000000 EDI:00a691d8
Stack dump:
0x0032e64c:  00000000 00000000 3eb6208b 1f001aa0
0x0032e65c:  1b000f28 00000000 00000000 0032f500
0x0032e66c:  0032e864 7fffffa6 0032e80c 150009ec
0x0032e67c:  00a691d8 00002800 00000000 00000000
0x0032e68c:  00000000 3eb62343 00802431 0032e80c
0x0032e69c:  00000000 3eb62077 00000001 00000000
Backtrace:
0x0058dc7c: movl	0x4(%ebp),%ecx
Modules:
Module	Address			Debug info	Name (97 modules)
PE	  400000-  baf000	Export          oblivion
PE	  bb0000-  dff000	Deferred        d3dx9_27
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b930000	Deferred        kernel32<elf>
  \-PE	7b820000-7b930000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7cfcf000-7cfda000	Deferred        libgcc_s.so.1
ELF	7d0fa000-7dc0f000	Deferred        libglcore.so.1
ELF	7dc0f000-7dcb3000	Deferred        libgl.so.1
ELF	7dcc3000-7ddc6000	Deferred        wined3d<elf>
  \-PE	7dce0000-7ddc6000	\               wined3d
ELF	7ddc6000-7ddf6000	Deferred        d3d9<elf>
  \-PE	7ddd0000-7ddf6000	\               d3d9
ELF	7e232000-7e246000	Deferred        midimap<elf>
  \-PE	7e240000-7e246000	\               midimap
ELF	7e246000-7e26c000	Deferred        msacm32<elf>
  \-PE	7e250000-7e26c000	\               msacm32
ELF	7e26c000-7e283000	Deferred        msacm32<elf>
  \-PE	7e270000-7e283000	\               msacm32
ELF	7e283000-7e346000	Deferred        libasound.so.2
ELF	7e356000-7e38c000	Deferred        winealsa<elf>
  \-PE	7e360000-7e38c000	\               winealsa
ELF	7e38c000-7e3bf000	Deferred        uxtheme<elf>
  \-PE	7e390000-7e3bf000	\               uxtheme
ELF	7e3bf000-7e3c8000	Deferred        libxcursor.so.1
ELF	7e3c8000-7e3cd000	Deferred        libxfixes.so.3
ELF	7e3cd000-7e3d0000	Deferred        libxcomposite.so.1
ELF	7e3d0000-7e3d6000	Deferred        libxrandr.so.2
ELF	7e3d6000-7e3de000	Deferred        libxrender.so.1
ELF	7e3de000-7e3e1000	Deferred        libxinerama.so.1
ELF	7e3e1000-7e401000	Deferred        imm32<elf>
  \-PE	7e3f0000-7e401000	\               imm32
ELF	7e401000-7e406000	Deferred        libxdmcp.so.6
ELF	7e406000-7e41e000	Deferred        libxcb.so.1
ELF	7e41e000-7e421000	Deferred        libxau.so.6
ELF	7e421000-7e508000	Deferred        libx11.so.6
ELF	7e508000-7e516000	Deferred        libxext.so.6
ELF	7e516000-7e51b000	Deferred        libxxf86vm.so.1
ELF	7e51b000-7e533000	Deferred        libice.so.6
ELF	7e533000-7e53b000	Deferred        libsm.so.6
ELF	7e544000-7e546000	Deferred        libnvidia-tls.so.1
ELF	7e54b000-7e5e2000	Deferred        winex11<elf>
  \-PE	7e560000-7e5e2000	\               winex11
ELF	7e5f5000-7e616000	Deferred        libexpat.so.1
ELF	7e616000-7e640000	Deferred        libfontconfig.so.1
ELF	7e650000-7e665000	Deferred        libz.so.1
ELF	7e665000-7e6d5000	Deferred        libfreetype.so.6
ELF	7e6d5000-7e701000	Deferred        ws2_32<elf>
  \-PE	7e6e0000-7e701000	\               ws2_32
ELF	7e701000-7e71b000	Deferred        wsock32<elf>
  \-PE	7e710000-7e71b000	\               wsock32
ELF	7e71b000-7e785000	Deferred        msvcrt<elf>
  \-PE	7e730000-7e785000	\               msvcrt
ELF	7e785000-7e799000	Deferred        lz32<elf>
  \-PE	7e790000-7e799000	\               lz32
ELF	7e799000-7e7b2000	Deferred        version<elf>
  \-PE	7e7a0000-7e7b2000	\               version
ELF	7e7b2000-7e80b000	Deferred        shlwapi<elf>
  \-PE	7e7c0000-7e80b000	\               shlwapi
ELF	7e80b000-7e920000	Deferred        shell32<elf>
  \-PE	7e820000-7e920000	\               shell32
ELF	7e920000-7e96a000	Deferred        dsound<elf>
  \-PE	7e930000-7e96a000	\               dsound
ELF	7e96a000-7e9fc000	Deferred        winmm<elf>
  \-PE	7e980000-7e9fc000	\               winmm
ELF	7e9fc000-7ea0f000	Deferred        libresolv.so.2
ELF	7ea0f000-7ea11000	Deferred        libxcb-xlib.so.0
ELF	7ea1f000-7ea3d000	Deferred        iphlpapi<elf>
  \-PE	7ea30000-7ea3d000	\               iphlpapi
ELF	7ea3d000-7ea9f000	Deferred        rpcrt4<elf>
  \-PE	7ea50000-7ea9f000	\               rpcrt4
ELF	7ea9f000-7eb43000	Deferred        ole32<elf>
  \-PE	7eab0000-7eb43000	\               ole32
ELF	7eb43000-7eb7a000	Deferred        dinput<elf>
  \-PE	7eb50000-7eb7a000	\               dinput
ELF	7eb7a000-7eb92000	Deferred        dinput8<elf>
  \-PE	7eb80000-7eb92000	\               dinput8
ELF	7eb92000-7ebe4000	Deferred        advapi32<elf>
  \-PE	7eba0000-7ebe4000	\               advapi32
ELF	7ebe4000-7ec82000	Deferred        gdi32<elf>
  \-PE	7ebf0000-7ec82000	\               gdi32
ELF	7ec82000-7edc9000	Deferred        user32<elf>
  \-PE	7eca0000-7edc9000	\               user32
ELF	7edc9000-7ee88000	Deferred        comctl32<elf>
  \-PE	7edd0000-7ee88000	\               comctl32
ELF	7efa8000-7efb3000	Deferred        libnss_files.so.2
ELF	7efb3000-7efcb000	Deferred        libnsl.so.1
ELF	7efcb000-7eff0000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c95000-b7c9e000	Deferred        libnss_compat.so.2
ELF	b7c9f000-b7ca3000	Deferred        libdl.so.2
ELF	b7ca3000-b7df2000	Deferred        libc.so.6
ELF	b7df3000-b7e0b000	Deferred        libpthread.so.0
ELF	b7e1b000-b7f51000	Deferred        libwine.so.1
ELF	b7f53000-b7f6f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
	00000028   15
	00000027   15
	00000026    0
	00000009    0 <==
0000000c 
	00000025    0
	00000022    0
	00000021    0
	0000000d    0
0000000e 
	0000001c    0
	0000001b    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 
	0000001d    0
	0000001a    0
	00000019    0
0000001e 
	0000001f    0
Backtrace:
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

The top error message is repeated many times. This occurs while a small window is showed with "Oblivion" in the title. The window then goes away, that message stops, it shows the rest, then ends.
Wine version is 1.1.0, Ubuntu Hardy, Nvidia GeForce 8600. Wine has been configured according to the instructions on UESP. Any help would be greatly appreciated!

---

### Post by aestrivex on 2008-07-08
i have oblivion with OOO running well on wine 1.1.0

the source of the problem appears to be some error in graphical configuration.

my registry configuration for direct3D is as follows (the UESPWiki page has instructions for how to edit this)

```

DirectDrawRenderer - opengl
OffscreenRenderingMode - pbuffer
PixelShaderMode - enabled
UseGLSL - enabled
VertexShaderMode - hardware
VideoMemorySize - 512 (obviously, set this to the configuration of your video card.)

```

You might try implementing that.


if all else fails, you can always go back to the version of wine in which you had things working.

---

### Post by Zavior on 2008-07-22
Thanks for the info. Sorry it took me so long to reply. Got really busy and haven't used Ubuntu for a little while. I tried playing with my registry settings and the best I got is that now Oblivion launcher will let me select resolutions. It wouldn't before. I do have a question: what is actually happening when you set the renderer to opengl. After all the place where I am putting this is in the Wine/D3D key. Any idea? Also Oblivion launcher claims to only be able to use "Direct3D HAL" no matter what I have set. I may have a misunderstanding of OpenGL and D3D but I was under the impression they are both software layers to render 3d objects. As such someone would only use one at a time.

---

### Post by OliW on 2008-09-28
You ever get this fixed? I'm having the same issue now.

---

### Post by Zavior on 2008-10-10
> You ever get this fixed? I'm having the same issue now. 

Yes I did. I can't recall exactly how I fixed it though. Let me know if you're still having problems and I'll look at it again and try to remember. I just haven't played it much since there is no HDR support :(.

---

### Post by OliW on 2008-10-10
Yeah still getting it. I've gone to the drastic extreme of doing a full reinstall to Intrepid (which might actually be the source of my issue - unsure) and it hasn't helped a single bit.

I have to admit, even though it's been over a year since I've had to deal with a real install of Windows on this computer, I'm slightly tempted to set aside 20gigs of HD an install TinyXP just for Oblivion. I really, *really* miss it. Sad times.

---

### Post by jdeslip on 2008-12-07
I also only have direct3d hal and I have terrible performance.  Is there suppossed to be another option?  Did you guys ever figure out how to fix it?

---

