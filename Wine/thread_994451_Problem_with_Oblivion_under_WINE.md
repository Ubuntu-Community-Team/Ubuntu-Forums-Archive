---
title: "Problem with Oblivion under WINE"
date: 2008-11-26
forum: Wine
---

### Post by Dunkler Vagabund on 2008-11-26
heres the list of what happened in terminal


mike@mike-desktop:~$ '/home/mike/.wine/drive_c/Program Files/Bethesda Softworks/Oblivion/OblivionLauncher.exe' 
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3dc,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,70,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,105,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,245,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,255,2): stub!
fixme:wave:wodPlayer_Reset shouldn't have headers left
mike@mike-desktop:~$ err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_27.dll". If you are using builtin L"d3dx9_27.dll", try using the native one instead.
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:win:EnumDisplayDevicesW ((null),0,0x33ef4c,0x00000000), stub!
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
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface MultisampleQuality set to -1, bstituting 0
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface MultisampleQuality set to -1, bstituting 0
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface MultisampleQuality set to -1, bstituting 0
wine: Call from 0x6c5851 to unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory, aborting
wine: Unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory called at address 0x6c5851 (thread 001c), starting debugger...
Unhandled exception: unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory called in 32-bit code (0x7bc451ec).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc451ec ESP:0033ec58 EBP:0033ecbc EFLAGS:00200206(   - 00      - -IP1)
 EAX:00aa0fba EBX:7bc88444 ECX:0033ed00 EDX:00ad4984
 ESI:0033ec64 EDI:0178c068
Stack dump:
0x0033ec58:  016d3338 016ce638 016d3338 80000100
0x0033ec68:  00000001 00000000 006c5851 00000002
0x0033ec78:  00aa1184 00aa0fba 004018ef 0178c268
0x0033ec88:  0178c060 0178c268 00401a09 7bc336cf
0x0033ec98:  0178c268 0178c268 0000ab38 00401027
0x0033eca8:  00ad4980 00401da8 0168f51c 0168f51c
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0033ecbc)
0x7bc451ec: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (99 modules)
PE	  400000-  b59000	Deferred        oblivion
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d3fd000-7df12000	Deferred        libglcore.so.1
ELF	7df12000-7dfb6000	Deferred        libgl.so.1
ELF	7dfb6000-7e0b9000	Deferred        wined3d<elf>
  \-PE	7dfd0000-7e0b9000	\               wined3d
ELF	7e0b9000-7e0e9000	Deferred        d3d9<elf>
  \-PE	7e0c0000-7e0e9000	\               d3d9
ELF	7e246000-7e25a000	Deferred        midimap<elf>
  \-PE	7e250000-7e25a000	\               midimap
ELF	7e25a000-7e280000	Deferred        msacm32<elf>
  \-PE	7e260000-7e280000	\               msacm32
ELF	7e280000-7e297000	Deferred        msacm32<elf>
  \-PE	7e290000-7e297000	\               msacm32
ELF	7e297000-7e35a000	Deferred        libasound.so.2
ELF	7e36a000-7e3a0000	Deferred        winealsa<elf>
  \-PE	7e370000-7e3a0000	\               winealsa
ELF	7e3a0000-7e3d3000	Deferred        uxtheme<elf>
  \-PE	7e3b0000-7e3d3000	\               uxtheme
ELF	7e3d3000-7e3dc000	Deferred        libxcursor.so.1
ELF	7e3dc000-7e3e1000	Deferred        libxfixes.so.3
ELF	7e3e1000-7e3e4000	Deferred        libxcomposite.so.1
ELF	7e3e4000-7e3ea000	Deferred        libxrandr.so.2
ELF	7e3ea000-7e3f2000	Deferred        libxrender.so.1
ELF	7e3f2000-7e3f5000	Deferred        libxinerama.so.1
ELF	7e3f5000-7e415000	Deferred        imm32<elf>
  \-PE	7e400000-7e415000	\               imm32
ELF	7e415000-7e41a000	Deferred        libxdmcp.so.6
ELF	7e41a000-7e432000	Deferred        libxcb.so.1
ELF	7e432000-7e434000	Deferred        libxcb-xlib.so.0
ELF	7e434000-7e51b000	Deferred        libx11.so.6
ELF	7e51b000-7e529000	Deferred        libxext.so.6
ELF	7e529000-7e52e000	Deferred        libxxf86vm.so.1
ELF	7e52e000-7e546000	Deferred        libice.so.6
ELF	7e546000-7e54e000	Deferred        libsm.so.6
ELF	7e55a000-7e55c000	Deferred        libnvidia-tls.so.1
ELF	7e55e000-7e5f5000	Deferred        winex11<elf>
  \-PE	7e570000-7e5f5000	\               winex11
ELF	7e60a000-7e62b000	Deferred        libexpat.so.1
ELF	7e62b000-7e655000	Deferred        libfontconfig.so.1
ELF	7e665000-7e67a000	Deferred        libz.so.1
ELF	7e67a000-7e6e7000	Deferred        libfreetype.so.6
ELF	7e6e7000-7e713000	Deferred        ws2_32<elf>
  \-PE	7e6f0000-7e713000	\               ws2_32
ELF	7e713000-7e72d000	Deferred        wsock32<elf>
  \-PE	7e720000-7e72d000	\               wsock32
ELF	7e72d000-7e74c000	Deferred        d3dx8<elf>
  \-PE	7e730000-7e74c000	\               d3dx8
ELF	7e74c000-7e769000	Deferred        d3dx9_36<elf>
  \-PE	7e750000-7e769000	\               d3dx9_36
ELF	7e769000-7e782000	Deferred        d3dx9_27<elf>
  \-PE	7e770000-7e782000	\               d3dx9_27
ELF	7e782000-7e796000	Deferred        lz32<elf>
  \-PE	7e790000-7e796000	\               lz32
ELF	7e796000-7e7af000	Deferred        version<elf>
  \-PE	7e7a0000-7e7af000	\               version
ELF	7e7af000-7e808000	Deferred        shlwapi<elf>
  \-PE	7e7c0000-7e808000	\               shlwapi
ELF	7e808000-7e91b000	Deferred        shell32<elf>
  \-PE	7e820000-7e91b000	\               shell32
ELF	7e91b000-7e965000	Deferred        dsound<elf>
  \-PE	7e920000-7e965000	\               dsound
ELF	7e965000-7e9f7000	Deferred        winmm<elf>
  \-PE	7e970000-7e9f7000	\               winmm
ELF	7e9f7000-7ea0a000	Deferred        libresolv.so.2
ELF	7ea0a000-7ea28000	Deferred        iphlpapi<elf>
  \-PE	7ea10000-7ea28000	\               iphlpapi
ELF	7ea28000-7ea89000	Deferred        rpcrt4<elf>
  \-PE	7ea30000-7ea89000	\               rpcrt4
ELF	7ea89000-7eb2d000	Deferred        ole32<elf>
  \-PE	7eaa0000-7eb2d000	\               ole32
ELF	7eb2d000-7eb64000	Deferred        dinput<elf>
  \-PE	7eb40000-7eb64000	\               dinput
ELF	7eb64000-7eb7c000	Deferred        dinput8<elf>
  \-PE	7eb70000-7eb7c000	\               dinput8
ELF	7eb7c000-7ebce000	Deferred        advapi32<elf>
  \-PE	7eb90000-7ebce000	\               advapi32
ELF	7ebce000-7ec69000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec69000	\               gdi32
ELF	7ec69000-7edb0000	Deferred        user32<elf>
  \-PE	7ec80000-7edb0000	\               user32
ELF	7edb0000-7ee6f000	Deferred        comctl32<elf>
  \-PE	7edc0000-7ee6f000	\               comctl32
ELF	7ee6f000-7ee7a000	Deferred        libnss_files.so.2
ELF	7ee7a000-7ee92000	Deferred        libnsl.so.1
ELF	7ee92000-7ee9b000	Deferred        libnss_compat.so.2
ELF	7efcb000-7eff0000	Deferred        libm.so.6
ELF	7eff0000-7eff3000	Deferred        libxau.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d17000-b7d1b000	Deferred        libdl.so.2
ELF	b7d1b000-b7e6a000	Deferred        libc.so.6
ELF	b7e6b000-b7e83000	Deferred        libpthread.so.0
ELF	b7e93000-b7fc9000	Deferred        libwine.so.1
ELF	b7fcb000-b7fe7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000015    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000014    0
	00000011    0
	00000010    0
00000018 
	00000019    0
0000001b (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
	0000001f   -1
	0000001e   -1
	0000001d    0
	0000001c    0 <==
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0033ecbc)
wine: Call from 0x6c5851 to unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory, aborting



thanks for your help~!

---

### Post by Progressive on 2008-11-27
First let's get the easy questions out of the way

Do you have the actual Microsoft version of d3dx9_27.dll installed in Wine's Windows System32 folder? It won't run otherwise. It is on your Oblivion DVD, or you can download it online.

Have you followed the instructions on [UESP's linux guide]("http://www.uesp.net/wiki/Oblivion:Linux")? You may have to tweak the ini settings a bit. I also recommend downloading *Oldblivion*, and other tweaks.

Are you running an ATI card? If so, see [my thread]("http://ubuntuforums.org/showthread.php?t=984826")

Cheers

---

### Post by Dunkler Vagabund on 2008-11-27
incredible! I got it working! My problem was with the sound driver config in WINE... thanks

---

