---
title: "Wine has stopped playing my 3D games..."
date: 2012-12-19
forum: Wine
---

### Post by withnail420 on 2012-12-19
I have tried purging and reinstalling everything, multiple times. The games, the wine package itself, (and yes, I purged not just uninstalled), rm'ing .wine...it still throws the same exact problems every time. 

I DID recently update my nvidia driver to 304, but the games worked after this. It was a few days later they stopped working. One saying it couldn't access enough video memory (That was Vice City) Half Life 2 just straight up won't launch, Freespace 2 fails with a message that when I ask it to show me reasons spits out this:

```
Unhandled exception: page fault on read access to 0x00000030 in 32-bit code (0x7e5f509f).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e5f509f ESP:0031e810 EBP:0031e898 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:0014a368 EBX:7e6bcff4 ECX:00000000 EDX:00000000
 ESI:0031e8f0 EDI:0014a368
Stack dump:
0x0031e810:  0014a38c 0031e84c 0031e87c 7ececc8d
0x0031e820:  0005002c f76386c0 00000000 7bc35537
0x0031e830:  0014a368 00000000 0014a38c 00000000
0x0031e840:  00000000 0031e864 0031e870 7e6bcff4
0x0031e850:  0031edcc 0031e8f0 0031e888 7e6806c1
0x0031e860:  7e690c70 4d430003 7e5abac1 7e6806c1
Backtrace:
=>0 0x7e5f509f wined3d_get_device_caps+0x4cf() in wined3d (0x0031e898)
  1 0x7e6e3195 in ddraw (+0x13194) (0x0031ea88)
  2 0x7e6e3f1d in ddraw (+0x13f1c) (0x0031ef08)
  3 0x7e6e427e in ddraw (+0x1427d) (0x0031ef68)
0x7e5f509f wined3d_get_device_caps+0x4cf in wined3d: call	*0x30(%ecx)
Modules:
Module	Address			Debug info	Name (111 modules)
PE	  400000-  d1b000	Export          fs2
PE	10000000-10018000	Deferred        cd
ELF	764a8000-777ff000	Deferred        libllvm-3.0.so.1
ELF	7b800000-7ba33000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba33000	\               kernel32
ELF	7bc00000-7bcca000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcca000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c8d3000-7c907000	Deferred        libtxc_dxtn.so
ELF	7ca24000-7ca42000	Deferred        libgcc_s.so.1
ELF	7d6c5000-7d6d2000	Deferred        libdrm.so.2
ELF	7d6d2000-7d6ea000	Deferred        libxcb-glx.so.0
ELF	7d6ea000-7d700000	Deferred        libglapi.so.0
ELF	7d800000-7d807000	Deferred        libffi.so.6
ELF	7d807000-7d860000	Deferred        libgl.so.1
ELF	7d885000-7d89d000	Deferred        libresolv.so.2
ELF	7d89d000-7d8a5000	Deferred        libogg.so.0
ELF	7d8a5000-7d8d0000	Deferred        libvorbis.so.0
ELF	7d8d0000-7da48000	Deferred        libvorbisenc.so.2
ELF	7da48000-7da96000	Deferred        libflac.so.8
ELF	7da96000-7da9f000	Deferred        librt.so.1
ELF	7da9f000-7daa6000	Deferred        libasyncns.so.0
ELF	7daa6000-7db18000	Deferred        libsndfile.so.1
ELF	7db18000-7db22000	Deferred        libwrap.so.0
ELF	7db22000-7db6b000	Deferred        libdbus-1.so.3
ELF	7db6b000-7dbd0000	Deferred        libpulsecommon-1.1.so
ELF	7dbd0000-7dc1e000	Deferred        libpulse.so.0
ELF	7dc23000-7dc26000	Deferred        libx11-xcb.so.1
ELF	7dc26000-7dc2a000	Deferred        libxdamage.so.1
ELF	7dc2a000-7dc40000	Deferred        msadp32<elf>
  \-PE	7dc30000-7dc40000	\               msadp32
ELF	7dc43000-7dc69000	Deferred        winepulse<elf>
  \-PE	7dc50000-7dc69000	\               winepulse
ELF	7dc69000-7dd83000	Deferred        oleaut32<elf>
  \-PE	7dc80000-7dd83000	\               oleaut32
ELF	7dd83000-7dda3000	Deferred        mmdevapi<elf>
  \-PE	7dd90000-7dda3000	\               mmdevapi
ELF	7ddde000-7dde6000	Deferred        libjson.so.0
ELF	7de16000-7de5b000	Deferred        dsound<elf>
  \-PE	7de20000-7de5b000	\               dsound
ELF	7de5b000-7de8f000	Deferred        uxtheme<elf>
  \-PE	7de60000-7de8f000	\               uxtheme
ELF	7de8f000-7de95000	Deferred        libxfixes.so.3
ELF	7de95000-7dea0000	Deferred        libxcursor.so.1
ELF	7dea0000-7deb0000	Deferred        libxi.so.6
ELF	7deb0000-7deb4000	Deferred        libxcomposite.so.1
ELF	7deb4000-7debd000	Deferred        libxrandr.so.2
ELF	7debd000-7dec7000	Deferred        libxrender.so.1
ELF	7dec7000-7decd000	Deferred        libxxf86vm.so.1
ELF	7decd000-7deee000	Deferred        libxcb.so.1
ELF	7deee000-7df08000	Deferred        libice.so.6
ELF	7df08000-7e03c000	Deferred        libx11.so.6
ELF	7e03e000-7e061000	Deferred        imm32<elf>
  \-PE	7e040000-7e061000	\               imm32
ELF	7e061000-7e0eb000	Deferred        winex11<elf>
  \-PE	7e070000-7e0eb000	\               winex11
ELF	7e0eb000-7e101000	Deferred        libz.so.1
ELF	7e101000-7e19b000	Deferred        libfreetype.so.6
ELF	7e19c000-7e1a0000	Deferred        libxinerama.so.1
ELF	7e1a0000-7e1a7000	Deferred        libxdmcp.so.6
ELF	7e1a7000-7e1b9000	Deferred        libxext.so.6
ELF	7e1c0000-7e1e4000	Deferred        iphlpapi<elf>
  \-PE	7e1d0000-7e1e4000	\               iphlpapi
ELF	7e1e4000-7e217000	Deferred        ws2_32<elf>
  \-PE	7e1f0000-7e217000	\               ws2_32
ELF	7e217000-7e232000	Deferred        wsock32<elf>
  \-PE	7e220000-7e232000	\               wsock32
ELF	7e232000-7e2a0000	Deferred        shlwapi<elf>
  \-PE	7e240000-7e2a0000	\               shlwapi
ELF	7e2a0000-7e4b9000	Deferred        shell32<elf>
  \-PE	7e2b0000-7e4b9000	\               shell32
ELF	7e4b9000-7e590000	Deferred        opengl32<elf>
  \-PE	7e4d0000-7e590000	\               opengl32
ELF	7e590000-7e6c2000	Dwarf           wined3d<elf>
  \-PE	7e5a0000-7e6c2000	\               wined3d
ELF	7e6c2000-7e72c000	Dwarf           ddraw<elf>
  \-PE	7e6d0000-7e72c000	\               ddraw
ELF	7e72c000-7e828000	Deferred        comctl32<elf>
  \-PE	7e730000-7e828000	\               comctl32
ELF	7e828000-7e86e000	Deferred        dinput<elf>
  \-PE	7e830000-7e86e000	\               dinput
ELF	7e86e000-7e897000	Deferred        msacm32<elf>
  \-PE	7e870000-7e897000	\               msacm32
ELF	7e897000-7e90f000	Deferred        rpcrt4<elf>
  \-PE	7e8a0000-7e90f000	\               rpcrt4
ELF	7e90f000-7ea24000	Deferred        ole32<elf>
  \-PE	7e930000-7ea24000	\               ole32
ELF	7ea24000-7ead3000	Deferred        winmm<elf>
  \-PE	7ea30000-7ead3000	\               winmm
ELF	7ead3000-7eb38000	Deferred        advapi32<elf>
  \-PE	7eae0000-7eb38000	\               advapi32
ELF	7eb38000-7ec42000	Deferred        gdi32<elf>
  \-PE	7eb40000-7ec42000	\               gdi32
ELF	7ec42000-7ed88000	Deferred        user32<elf>
  \-PE	7ec50000-7ed88000	\               user32
ELF	7ed88000-7ed95000	Deferred        libnss_files.so.2
ELF	7ed95000-7edaf000	Deferred        libnsl.so.1
ELF	7efaf000-7efdb000	Deferred        libm.so.6
ELF	7efdd000-7efe6000	Deferred        libsm.so.6
ELF	7efe6000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f7481000-f748d000	Deferred        libnss_nis.so.2
ELF	f748e000-f7493000	Deferred        libdl.so.2
ELF	f7493000-f763d000	Deferred        libc.so.6
ELF	f763e000-f7659000	Deferred        libpthread.so.0
ELF	f765a000-f7660000	Deferred        libuuid.so.1
ELF	f7670000-f7674000	Deferred        libxau.so.6
ELF	f7674000-f767d000	Deferred        libnss_compat.so.2
ELF	f767e000-f77c0000	Dwarf           libwine.so.1
ELF	f77c2000-f77e4000	Deferred        ld-linux.so.2
ELF	f77e4000-f77e5000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001f    0
	0000001e    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000019    0
	00000014    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001d    0
	0000001b    0
00000021 explorer.exe
	00000022    0
00000023 (D) C:\Program Files (x86)\GOG.com\Freespace 2\FS2.exe
	00000028   15
	00000027    0
	00000026    0
	00000025   15
	00000024    0 <==
System information:
    Wine build: wine-1.5.19
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.2.0-35-generic

```

I'm running 12.04, AMD Phenom X2, 4G of RAM, and a 250 series Nvidia card. 

Apps that don't require 3D such as Tuareg (an old windows beat slicer) work fine, also the error reports point to video issues.

This occured after for some reason my Xorg broke...I had to do some rejiggering to get it to work, and I'm not entirely sure what happened. I basically reinstalled all the nvidia drivers again...after trying the bumblebee ones that didn't give high enough resolution. 

All Linux games that need 3D work fine. So...what the hell do I do?

---

### Post by withnail420 on 2012-12-19
Also, just installed the 310 driver to see if that changed anything...nothing.

---

### Post by withnail420 on 2012-12-19
Amnesia: The Dark Descent works fine - native linux game.

Regnum Online works fine - native linux client.

Everything that is native linux works fine. 

Anything that requires 3D graphics though wine doesn't work.

What a surprise, nobody on the Ubuntu forums even knows where to begin.

---

### Post by stanleyella on 2012-12-20
I can play games like castle wolfenstein and commanche 4 ok

---

