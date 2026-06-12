---
title: "oblivion crashes on startup"
date: 2008-10-18
forum: Wine
---

### Post by c4tly5t on 2008-10-18
my oblivion crashes on startup 
im running AMD64 hardy with the newest version of wine on a HP pavilion dv5-1003nr AMD 64bit dual core turion and ati radeon HD 3200 graphics card


i ran ~/.wine/drive_c/Program Files/Bethesda Softworks/Oblivion$ wine oblivion.exe
in terminal and got

err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_27.dll". If you are using builtin L"d3dx9_27.dll", try using the native one instead.
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef4c,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3554
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
wine: Call from 0x6c58d1 to unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory, aborting
wine: Unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory called at address 0x6c58d1 (thread 0009), starting debugger...
Unhandled exception: unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory called in 32-bit code (0x7bc4569c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4569c ESP:0032ec58 EBP:0032ecbc EFLAGS:00000206(   - 00      - -IP1)
 EAX:00ab1df6 EBX:7bc88444 ECX:0032ed00 EDX:00aea084
 ESI:0032ec64 EDI:017ae768
Stack dump:
0x0032ec58:  016f0da4 016ec0a4 016f0da4 80000100
0x0032ec68:  00000001 00000000 006c58d1 00000002
0x0032ec78:  00ab1f54 00ab1df6 004019ef 017ae968
0x0032ec88:  017ae760 017ae968 00401b09 7bc3377f
0x0032ec98:  017ae968 016acf01 0000ab38 00401087
0x0032eca8:  00aea080 00401e89 016acf88 016acf88
Backtrace:
=>1 0x7bc4569c in ntdll (+0x3569c) (0x0032ecbc)
0x7bc4569c: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (99 modules)
PE	  400000-  b73000	Deferred        oblivion
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7cbf8000-7cc01000	Deferred        librt.so.1
ELF	7cc01000-7dce1000	Deferred        fglrx_dri.so
ELF	7dce1000-7dcec000	Deferred        libgcc_s.so.1
ELF	7dcec000-7dd66000	Deferred        libgl.so.1
ELF	7dd78000-7de7b000	Deferred        wined3d<elf>
  \-PE	7dd90000-7de7b000	\               wined3d
ELF	7de7b000-7deab000	Deferred        d3d9<elf>
  \-PE	7de80000-7deab000	\               d3d9
ELF	7e24c000-7e260000	Deferred        midimap<elf>
  \-PE	7e250000-7e260000	\               midimap
ELF	7e260000-7e286000	Deferred        msacm32<elf>
  \-PE	7e270000-7e286000	\               msacm32
ELF	7e286000-7e29d000	Deferred        msacm32<elf>
  \-PE	7e290000-7e29d000	\               msacm32
ELF	7e29d000-7e360000	Deferred        libasound.so.2
ELF	7e372000-7e3a8000	Deferred        winealsa<elf>
  \-PE	7e380000-7e3a8000	\               winealsa
ELF	7e3a8000-7e3db000	Deferred        uxtheme<elf>
  \-PE	7e3b0000-7e3db000	\               uxtheme
ELF	7e3db000-7e3e4000	Deferred        libxcursor.so.1
ELF	7e3e4000-7e3e9000	Deferred        libxfixes.so.3
ELF	7e3e9000-7e3ec000	Deferred        libxcomposite.so.1
ELF	7e3ec000-7e3f2000	Deferred        libxrandr.so.2
ELF	7e3f2000-7e3fa000	Deferred        libxrender.so.1
ELF	7e3fa000-7e3fd000	Deferred        libxinerama.so.1
ELF	7e3fd000-7e41d000	Deferred        imm32<elf>
  \-PE	7e400000-7e41d000	\               imm32
ELF	7e41d000-7e422000	Deferred        libxdmcp.so.6
ELF	7e422000-7e43a000	Deferred        libxcb.so.1
ELF	7e43a000-7e43c000	Deferred        libxcb-xlib.so.0
ELF	7e43c000-7e43f000	Deferred        libxau.so.6
ELF	7e43f000-7e526000	Deferred        libx11.so.6
ELF	7e526000-7e534000	Deferred        libxext.so.6
ELF	7e534000-7e539000	Deferred        libxxf86vm.so.1
PE	7e544000-7e548000	Deferred        libasound_module_rate_speexrate.
ELF	7e54b000-7e5e2000	Deferred        winex11<elf>
  \-PE	7e560000-7e5e2000	\               winex11
ELF	7e60a000-7e62b000	Deferred        libexpat.so.1
ELF	7e62b000-7e655000	Deferred        libfontconfig.so.1
ELF	7e667000-7e67c000	Deferred        libz.so.1
ELF	7e67c000-7e6ec000	Deferred        libfreetype.so.6
ELF	7e6ec000-7e718000	Deferred        ws2_32<elf>
  \-PE	7e6f0000-7e718000	\               ws2_32
ELF	7e718000-7e732000	Deferred        wsock32<elf>
  \-PE	7e720000-7e732000	\               wsock32
ELF	7e732000-7e751000	Deferred        d3dx8<elf>
  \-PE	7e740000-7e751000	\               d3dx8
ELF	7e751000-7e76e000	Deferred        d3dx9_36<elf>
  \-PE	7e760000-7e76e000	\               d3dx9_36
ELF	7e76e000-7e787000	Deferred        d3dx9_27<elf>
  \-PE	7e770000-7e787000	\               d3dx9_27
ELF	7e787000-7e79b000	Deferred        lz32<elf>
  \-PE	7e790000-7e79b000	\               lz32
ELF	7e79b000-7e7b4000	Deferred        version<elf>
  \-PE	7e7a0000-7e7b4000	\               version
ELF	7e7b4000-7e80d000	Deferred        shlwapi<elf>
  \-PE	7e7c0000-7e80d000	\               shlwapi
ELF	7e80d000-7e920000	Deferred        shell32<elf>
  \-PE	7e820000-7e920000	\               shell32
ELF	7e920000-7e96a000	Deferred        dsound<elf>
  \-PE	7e930000-7e96a000	\               dsound
ELF	7e96a000-7e9fc000	Deferred        winmm<elf>
  \-PE	7e980000-7e9fc000	\               winmm
ELF	7e9fc000-7ea0f000	Deferred        libresolv.so.2
ELF	7ea21000-7ea3f000	Deferred        iphlpapi<elf>
  \-PE	7ea30000-7ea3f000	\               iphlpapi
ELF	7ea3f000-7eaa0000	Deferred        rpcrt4<elf>
  \-PE	7ea50000-7eaa0000	\               rpcrt4
ELF	7eaa0000-7eb44000	Deferred        ole32<elf>
  \-PE	7eab0000-7eb44000	\               ole32
ELF	7eb44000-7eb7b000	Deferred        dinput<elf>
  \-PE	7eb50000-7eb7b000	\               dinput
ELF	7eb7b000-7eb93000	Deferred        dinput8<elf>
  \-PE	7eb80000-7eb93000	\               dinput8
ELF	7eb93000-7ebe5000	Deferred        advapi32<elf>
  \-PE	7eba0000-7ebe5000	\               advapi32
ELF	7ebe5000-7ec80000	Deferred        gdi32<elf>
  \-PE	7ec00000-7ec80000	\               gdi32
ELF	7ec80000-7edc7000	Deferred        user32<elf>
  \-PE	7eca0000-7edc7000	\               user32
ELF	7edc7000-7ee86000	Deferred        comctl32<elf>
  \-PE	7edd0000-7ee86000	\               comctl32
ELF	7efa6000-7efb1000	Deferred        libnss_files.so.2
ELF	7efb1000-7efc9000	Deferred        libnsl.so.1
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	f7cf1000-f7cfa000	Deferred        libnss_compat.so.2
ELF	f7cfb000-f7cff000	Deferred        libdl.so.2
ELF	f7cff000-f7e4e000	Deferred        libc.so.6
ELF	f7e4f000-f7e67000	Deferred        libpthread.so.0
ELF	f7e79000-f7faf000	Deferred        libwine.so.1
ELF	f7fb1000-f7fd0000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\oblivion.exe
	0000001c   -1
	0000001b   -1
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
=>1 0x7bc4569c in ntdll (+0x3569c) (0x0032ecbc)
wine: Call from 0x6c58d1 to unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory, aborting
fixme:winmm:MMDRV_Exit Closing while ll-driver open

---

