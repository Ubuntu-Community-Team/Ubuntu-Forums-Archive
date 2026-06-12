---
title: "Oblivion Doesn't Play"
date: 2008-06-14
forum: Wine
---

### Post by Spartacus84 on 2008-06-14
I am using the 64 bit version of Ubuntu 8.04. I successfully installed Oblivion in Wine and got it to the menu screen, but when I clicked play, it opened a new window with a black screen and immediately quit out with no error messages. Anybody know how to fix this?

---

### Post by cogadh on 2008-06-14
You should post this in the [Wine subforums](http://ubuntuforums.org/forumdisplay.php?f=313). 

It might help if you would run the game from the terminal and post Wine's terminal output. It likely contains an informative error message that will pinpoint the exact cause of the problem.

---

### Post by Perfect Storm on 2008-06-14
moved

---

### Post by Spartacus84 on 2008-06-14
> **cogadh said:**
> You should post this in the [Wine subforums](http://ubuntuforums.org/forumdisplay.php?f=313). 

It might help if you would run the game from the terminal and post Wine's terminal output. It likely contains an informative error message that will pinpoint the exact cause of the problem.

OK, when I run it tin the terminal, I get this:

```
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
jack@jack-ubuntu:~$ err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_27.dll". If you are using builtin L"d3dx9_27.dll", try using the native one instead.
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
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
wine: Call from 0x6c5851 to unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory, aborting
wine: Unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory called at address 0x6c5851 (thread 001b), starting debugger...
Unhandled exception: unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory called in 32-bit code (0x7bc4569c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4569c ESP:0033ec58 EBP:0033ecbc EFLAGS:00000206(   - 00      - -IP1)
 EAX:00aa0fba EBX:7bc88444 ECX:0033ed00 EDX:00ad4984
 ESI:0033ec64 EDI:0178e780
Stack dump:
0x0033ec58:  016d0d0c 016cc00c 016d0d0c 80000100
0x0033ec68:  00000001 00000000 006c5851 00000002
0x0033ec78:  00aa1184 00aa0fba 004018ef 0178e980
0x0033ec88:  0178e778 0178e980 00401a09 7bc3377f
0x0033ec98:  0178e980 0178e980 0000ab38 00401027
0x0033eca8:  00ad4980 00401da8 0168cef0 0168cef0
Backtrace:
=>1 0x7bc4569c in ntdll (+0x3569c) (0x0033ecbc)
0x7bc4569c: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (97 modules)
PE	  400000-  b59000	Deferred        oblivion
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d401000-7df16000	Deferred        libglcore.so.1
ELF	7df16000-7dfba000	Deferred        libgl.so.1
ELF	7dfce000-7e0d1000	Deferred        wined3d<elf>
  \-PE	7dfe0000-7e0d1000	\               wined3d
ELF	7e0d1000-7e101000	Deferred        d3d9<elf>
  \-PE	7e0e0000-7e101000	\               d3d9
ELF	7e260000-7e286000	Deferred        msacm32<elf>
  \-PE	7e270000-7e286000	\               msacm32
ELF	7e286000-7e29d000	Deferred        msacm32<elf>
  \-PE	7e290000-7e29d000	\               msacm32
ELF	7e29d000-7e360000	Deferred        libasound.so.2
ELF	7e360000-7e374000	Deferred        midimap<elf>
  \-PE	7e370000-7e374000	\               midimap
ELF	7e374000-7e3aa000	Deferred        winealsa<elf>
  \-PE	7e380000-7e3aa000	\               winealsa
ELF	7e3aa000-7e3dd000	Deferred        uxtheme<elf>
  \-PE	7e3b0000-7e3dd000	\               uxtheme
ELF	7e3dd000-7e3e6000	Deferred        libxcursor.so.1
ELF	7e3e6000-7e3eb000	Deferred        libxfixes.so.3
ELF	7e3eb000-7e3ee000	Deferred        libxcomposite.so.1
ELF	7e3ee000-7e3f4000	Deferred        libxrandr.so.2
ELF	7e3f4000-7e3fc000	Deferred        libxrender.so.1
ELF	7e3fc000-7e3ff000	Deferred        libxinerama.so.1
ELF	7e3ff000-7e41f000	Deferred        imm32<elf>
  \-PE	7e410000-7e41f000	\               imm32
ELF	7e41f000-7e424000	Deferred        libxdmcp.so.6
ELF	7e424000-7e43c000	Deferred        libxcb.so.1
ELF	7e43c000-7e43f000	Deferred        libxau.so.6
ELF	7e43f000-7e526000	Deferred        libx11.so.6
ELF	7e526000-7e534000	Deferred        libxext.so.6
ELF	7e534000-7e539000	Deferred        libxxf86vm.so.1
ELF	7e549000-7e54b000	Deferred        libnvidia-tls.so.1
ELF	7e54d000-7e5e4000	Deferred        winex11<elf>
  \-PE	7e560000-7e5e4000	\               winex11
ELF	7e62e000-7e64f000	Deferred        libexpat.so.1
ELF	7e64f000-7e679000	Deferred        libfontconfig.so.1
ELF	7e679000-7e68e000	Deferred        libz.so.1
ELF	7e68e000-7e6fe000	Deferred        libfreetype.so.6
ELF	7e6fe000-7e700000	Deferred        libxcb-xlib.so.0
ELF	7e712000-7e73e000	Deferred        ws2_32<elf>
  \-PE	7e720000-7e73e000	\               ws2_32
ELF	7e73e000-7e758000	Deferred        wsock32<elf>
  \-PE	7e740000-7e758000	\               wsock32
ELF	7e758000-7e777000	Deferred        d3dx8<elf>
  \-PE	7e760000-7e777000	\               d3dx8
ELF	7e777000-7e794000	Deferred        d3dx9_36<elf>
  \-PE	7e780000-7e794000	\               d3dx9_36
ELF	7e794000-7e7ad000	Deferred        d3dx9_27<elf>
  \-PE	7e7a0000-7e7ad000	\               d3dx9_27
ELF	7e7ad000-7e7c6000	Deferred        version<elf>
  \-PE	7e7b0000-7e7c6000	\               version
ELF	7e7c6000-7e81f000	Deferred        shlwapi<elf>
  \-PE	7e7d0000-7e81f000	\               shlwapi
ELF	7e81f000-7e931000	Deferred        shell32<elf>
  \-PE	7e830000-7e931000	\               shell32
ELF	7e931000-7e97b000	Deferred        dsound<elf>
  \-PE	7e940000-7e97b000	\               dsound
ELF	7e97b000-7ea0d000	Deferred        winmm<elf>
  \-PE	7e990000-7ea0d000	\               winmm
ELF	7ea0d000-7ea2b000	Deferred        iphlpapi<elf>
  \-PE	7ea10000-7ea2b000	\               iphlpapi
ELF	7ea2b000-7ea8c000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea8c000	\               rpcrt4
ELF	7ea8c000-7eb30000	Deferred        ole32<elf>
  \-PE	7eaa0000-7eb30000	\               ole32
ELF	7eb30000-7eb67000	Deferred        dinput<elf>
  \-PE	7eb40000-7eb67000	\               dinput
ELF	7eb67000-7eb7f000	Deferred        dinput8<elf>
  \-PE	7eb70000-7eb7f000	\               dinput8
ELF	7eb7f000-7ebd1000	Deferred        advapi32<elf>
  \-PE	7eb90000-7ebd1000	\               advapi32
ELF	7ebd1000-7ec6c000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec6c000	\               gdi32
ELF	7ec6c000-7edb3000	Deferred        user32<elf>
  \-PE	7ec90000-7edb3000	\               user32
ELF	7edb3000-7ee72000	Deferred        comctl32<elf>
  \-PE	7edc0000-7ee72000	\               comctl32
ELF	7ee72000-7ee8a000	Deferred        libnsl.so.1
ELF	7ee8a000-7ee93000	Deferred        libnss_compat.so.2
ELF	7ee94000-7eea7000	Deferred        libresolv.so.2
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7efec000-7f000000	Deferred        lz32<elf>
  \-PE	7eff0000-7f000000	\               lz32
ELF	f7c80000-f7c8b000	Deferred        libnss_files.so.2
ELF	f7c8c000-f7c90000	Deferred        libdl.so.2
ELF	f7c90000-f7ddf000	Deferred        libc.so.6
ELF	f7de0000-f7df8000	Deferred        libpthread.so.0
ELF	f7df8000-f7e02000	Deferred        libnss_nis.so.2
ELF	f7e0c000-f7f42000	Deferred        libwine.so.1
ELF	f7f44000-f7f63000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
00000017 
	00000018    0
0000001a (D) C:\windows\profiles\jack\Desktop\My Games\Oblivion.exe
	0000001e   -1
	0000001d   -1
	0000001c    0
	0000001b    0 <==
Backtrace:
=>1 0x7bc4569c in ntdll (+0x3569c) (0x0033ecbc)
wine: Call from 0x6c5851 to unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory, aborting


```

Ideas?

---

### Post by cogadh on 2008-06-14
Oblivion is looking for some of the DirectX support files that are not present in Wine. Copy the d3dx9_24.dll through d3dx9_36.dll files from a Windows machine into Wine's sytem32 directory and apply library overrides for each one. If you don't have access to a Windows machine, you can try actually installing DirectX into Wine following this guide [here](http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html). If you choose to go the guide route, make sure you follow the instructions precisely as you will need to specify certain overrides correctly or Wine won't work at all (for games).

---

