---
title: "[SOLVED] Star Wars Jedi Knight 3 won't start"
date: 2008-06-04
forum: Wine
---

### Post by S3loth on 2008-06-04
I am using Wine 1.0 rc3 and JK install perfectly. However, when I try to begin the game I click on single or multiplayer, the menu disappears and nothing happens. Don't know if it will help, but here's what happens in terminal:
> patrick@revolution:~$ wine  /media/JEDIACAD_1/JediAcademy.exe
patrick@revolution:~$ err:mmio:MMIO_ParseExtA No . in szFileName: "C:\\Program Files\\LucasArts\\Star Wars Jedi Knight Jedi Academy\\Install\\HOVER"
fixme:wave:wodPlayer_Reset shouldn't have headers left
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D8 is not available without opengl
wine: Unhandled page fault on read access to 0x00000000 at address 0x7df983c5 (thread 001a), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7df983c5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7df983c5 ESP:0033ef14 EBP:0033ef38 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7dfa6640 ECX:7dfa6d28 EDX:ffffffff
 ESI:00157808 EDI:7dfa6d24
Stack dump:
0x0033ef14:  7dfa6d70 7dfa3324 7dfa37f8 00157808
0x0033ef24:  10016460 7df900c0 00000000 00157808
0x0033ef34:  00766da8 00000000 10005334 00157808
0x0033ef44:  10000000 0033f5d0 00686438 00000000
0x0033ef54:  00766da8 7df80000 7bc46ec1 00157600
0x0033ef64:  00151c78 00000000 00000000 b7dabff4
Backtrace:
=>1 0x7df983c5 in d3d8 (+0x183c5) (0x0033ef38)
0x7df983c5: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (86 modules)
PE	  400000-  429000	Deferred        jediacademy
PE	10000000-1001f000	Deferred        lecsetup
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d14f000-7dc64000	Deferred        libglcore.so.1
ELF	7dc64000-7dd66000	Deferred        wined3d<elf>
  \-PE	7dc80000-7dd66000	\               wined3d
ELF	7ded8000-7df7c000	Deferred        libgl.so.1
ELF	7df7c000-7dfa7000	Export          d3d8<elf>
  \-PE	7df80000-7dfa7000	\               d3d8
ELF	7dfa7000-7dfb2000	Deferred        libgcc_s.so.1
ELF	7e29d000-7e2b0000	Deferred        libresolv.so.2
ELF	7e2cb000-7e2e9000	Deferred        iphlpapi<elf>
  \-PE	7e2d0000-7e2e9000	\               iphlpapi
ELF	7e2e9000-7e34a000	Deferred        rpcrt4<elf>
  \-PE	7e300000-7e34a000	\               rpcrt4
ELF	7e34a000-7e3ee000	Deferred        ole32<elf>
  \-PE	7e360000-7e3ee000	\               ole32
ELF	7e416000-7e449000	Deferred        uxtheme<elf>
  \-PE	7e420000-7e449000	\               uxtheme
ELF	7e449000-7e46f000	Deferred        msacm32<elf>
  \-PE	7e450000-7e46f000	\               msacm32
ELF	7e46f000-7e532000	Deferred        libasound.so.2
ELF	7e539000-7e54d000	Deferred        midimap<elf>
  \-PE	7e540000-7e54d000	\               midimap
ELF	7e54d000-7e583000	Deferred        winealsa<elf>
  \-PE	7e560000-7e583000	\               winealsa
ELF	7e583000-7e58c000	Deferred        libxcursor.so.1
ELF	7e58c000-7e591000	Deferred        libxfixes.so.3
ELF	7e591000-7e594000	Deferred        libxcomposite.so.1
ELF	7e594000-7e59a000	Deferred        libxrandr.so.2
ELF	7e59a000-7e5a2000	Deferred        libxrender.so.1
ELF	7e5a2000-7e5a5000	Deferred        libxinerama.so.1
ELF	7e5a5000-7e5c5000	Deferred        imm32<elf>
  \-PE	7e5b0000-7e5c5000	\               imm32
ELF	7e5c5000-7e5ca000	Deferred        libxdmcp.so.6
ELF	7e5ca000-7e5e2000	Deferred        libxcb.so.1
ELF	7e5e2000-7e5e5000	Deferred        libxau.so.6
ELF	7e5e5000-7e6cc000	Deferred        libx11.so.6
ELF	7e6cc000-7e6da000	Deferred        libxext.so.6
ELF	7e6da000-7e6f2000	Deferred        libice.so.6
ELF	7e6f2000-7e6fa000	Deferred        libsm.so.6
ELF	7e6fa000-7e6fc000	Deferred        libnvidia-tls.so.1
ELF	7e6fc000-7e713000	Deferred        msacm32<elf>
  \-PE	7e700000-7e713000	\               msacm32
ELF	7e715000-7e7ac000	Deferred        winex11<elf>
  \-PE	7e720000-7e7ac000	\               winex11
ELF	7e852000-7e873000	Deferred        libexpat.so.1
ELF	7e873000-7e89d000	Deferred        libfontconfig.so.1
ELF	7e89d000-7e8b2000	Deferred        libz.so.1
ELF	7e8b2000-7e922000	Deferred        libfreetype.so.6
ELF	7e922000-7e927000	Deferred        libxxf86vm.so.1
ELF	7e93d000-7e996000	Deferred        shlwapi<elf>
  \-PE	7e950000-7e996000	\               shlwapi
ELF	7e996000-7eaa6000	Deferred        shell32<elf>
  \-PE	7e9b0000-7eaa6000	\               shell32
ELF	7eaa6000-7eaba000	Deferred        lz32<elf>
  \-PE	7eab0000-7eaba000	\               lz32
ELF	7eaba000-7eae2000	Deferred        msvfw32<elf>
  \-PE	7eac0000-7eae2000	\               msvfw32
ELF	7eae2000-7eba1000	Deferred        comctl32<elf>
  \-PE	7eaf0000-7eba1000	\               comctl32
ELF	7eba1000-7ec33000	Deferred        winmm<elf>
  \-PE	7ebb0000-7ec33000	\               winmm
ELF	7ec33000-7ec85000	Deferred        advapi32<elf>
  \-PE	7ec40000-7ec85000	\               advapi32
ELF	7ec85000-7ed20000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed20000	\               gdi32
ELF	7ed20000-7ee67000	Deferred        user32<elf>
  \-PE	7ed40000-7ee67000	\               user32
ELF	7ee67000-7ee72000	Deferred        libnss_files.so.2
ELF	7ee72000-7ee7c000	Deferred        libnss_nis.so.2
ELF	7ee7c000-7ee85000	Deferred        libnss_compat.so.2
ELF	7ee85000-7ee87000	Deferred        libxcb-xlib.so.0
ELF	7ee87000-7eea0000	Deferred        version<elf>
  \-PE	7ee90000-7eea0000	\               version
ELF	7efc0000-7efe5000	Deferred        libm.so.6
ELF	7efe8000-7f000000	Deferred        libnsl.so.1
ELF	b7c5d000-b7c61000	Deferred        libdl.so.2
ELF	b7c61000-b7db0000	Deferred        libc.so.6
ELF	b7db1000-b7dc9000	Deferred        libpthread.so.0
ELF	b7de4000-b7f1a000	Deferred        libwine.so.1
ELF	b7f1c000-b7f38000	Deferred        ld-linux.so.2
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
00000019 (D) C:\Program Files\LucasArts\Star Wars Jedi Knight Jedi Academy\JediAcademy.exe
	0000001a    0 <==
Backtrace:
=>1 0x7df983c5 in d3d8 (+0x183c5) (0x0033ef38)


---

### Post by cogadh on 2008-06-04
```
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D8 is not available without opengl
```
Those errors would seem to indicate that you do not have the restricted drivers installed for your video hardware and you do not have 3D acceleration. Run this:
```
glxinfo | grep direct
```
If it comes back saying "Direct Rendering: No" then you do not have the necessary drivers installed or they are installed but not active.

---

### Post by S3loth on 2008-06-04
Alright, it did come back saying no. How would I fix this?

---

### Post by cogadh on 2008-06-04
What do you have for video hardware?

---

### Post by S3loth on 2008-06-04
I have nvidia. I tried to enable it with "sudo nvidia-glx-config enable" but it says command not found.

---

### Post by cogadh on 2008-06-04
Did you already install the driver through the Restricted Drivers Manager?

---

### Post by S3loth on 2008-06-05
Yes, that was a HUGE pain too.

---

### Post by cogadh on 2008-06-05
Are you using Ubuntu 8.04? If so, I may not be able to help you. I too had huge problems getting the Nvidia driver to work, so many problems that I ended up downgrading to 7.10 (it actually wasn't just the driver that made me do it, there were other issues with 8.04). I'm sure others have figured out how to get the Nvidia driver working in 8.04, I'll leave the help on this one to them, since I never did figure it out.

---

### Post by S3loth on 2008-06-05
All right, thanks for your help. Hopefully in later versions of Ubuntu they fix the nvidia problems.

---

