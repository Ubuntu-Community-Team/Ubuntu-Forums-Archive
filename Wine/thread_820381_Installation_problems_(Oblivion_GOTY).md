---
title: "Installation problems (Oblivion GOTY)"
date: 2008-06-06
forum: Wine
---

### Post by thezood on 2008-06-06
First off, I know there is a huge Oblivion thread in the forum. I have read it and it does not help me. I'd rather create a new thread than writing in that one, because I think this has more to do with installation than Oblivion. I have also googled. :)

My problem is that I can't install the game. When I run setup.exe, I get a huge error message (see below) and then it crashes. The Wine desktop shows up but no program window. The desktop doesn't disappear until I close it. I've been trying different things but nothing seems to work, among other installing directx (which worked fine) and I've followed the instructions at [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux) (including the Securom notes about the GOTY edition).
There was also an instruction in a blog that I can't find now, which included overriding some libraries, but that made no difference.

Currently using wine-1.0rc1 but I've tried earlier versions too. My specs: Ubuntu 8.04 AMD64, 4Gb RAM, Geforce 8800 (not that it really matters for this purpose).

Anyone have any ideas?

**UPDATE:** I now know this problem is related to the Securom protection used by Oblivion GOTY. If anyone knows how to deal with this, feel free to reply.

```

foo@bar:/media/cdrom0$ wine setup.exe 
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xeda520,0x00000004,0xeda51c) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xed940c): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0xed9258,0x00000000), stub!
wine: Unhandled page fault on write access to 0x003d2000 at address 0x4d86e6 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x003d2000 in 32-bit code (0x004d86e6).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:004d86e6 ESP:00eda8dc EBP:00eda8f0 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:ffffffff ECX:3fff3801 EDX:00000003
 ESI:003a0000 EDI:003d1ffe
Stack dump:
0x00eda8dc:  00eda924 00000000 003a0006 48590000
0x00eda8ec:  004d867b 00edad3c 004d54b7 003a0006
0x00eda8fc:  ffffffff 009b7900 00000000 00eccfba
0x00eda90c:  00c3ae94 00c94000 00000001 00000000
0x00eda91c:  00032000 00000030 5c3f3f5c 756c6f56
0x00eda92c:  307b656d 30303030 2d303030 30303030
Backtrace:
=>1 0x004d86e6 in setup (+0xd86e6) (0x00eda8f0)
  2 0x004d54b7 in setup (+0xd54b7) (0x00edad3c)
  3 0x00481e75 in setup (+0x81e75) (0x00eef93c)
  4 0x00434383 in setup (+0x34383) (0x00eefdbc)
  5 0x00a026d4 in setup (+0x6026d4) (0x00768e48)
  6 0xcccccccc (0xccccccc3)
0x004d86e6: repe stosl	%es:(%edi)
Modules:
Module	Address			Debug info	Name (75 modules)
PE	  400000-  cf0000	Export          setup
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d72e000-7e243000	Deferred        libglcore.so.1
ELF	7e243000-7e2e7000	Deferred        libgl.so.1
ELF	7e2fc000-7e3fe000	Deferred        wined3d<elf>
  \-PE	7e310000-7e3fe000	\               wined3d
ELF	7e3fe000-7e42e000	Deferred        d3d9<elf>
  \-PE	7e410000-7e42e000	\               d3d9
ELF	7e47a000-7e4ad000	Deferred        uxtheme<elf>
  \-PE	7e480000-7e4ad000	\               uxtheme
ELF	7e4ad000-7e4b6000	Deferred        libxcursor.so.1
ELF	7e4b6000-7e4bb000	Deferred        libxfixes.so.3
ELF	7e4bb000-7e4be000	Deferred        libxcomposite.so.1
ELF	7e4be000-7e4c4000	Deferred        libxrandr.so.2
ELF	7e4c4000-7e4cc000	Deferred        libxrender.so.1
ELF	7e4cc000-7e4cf000	Deferred        libxinerama.so.1
ELF	7e4cf000-7e4ef000	Deferred        imm32<elf>
  \-PE	7e4e0000-7e4ef000	\               imm32
ELF	7e4ef000-7e4f4000	Deferred        libxdmcp.so.6
ELF	7e4f4000-7e50c000	Deferred        libxcb.so.1
ELF	7e50c000-7e50f000	Deferred        libxau.so.6
ELF	7e50f000-7e5f6000	Deferred        libx11.so.6
ELF	7e5f6000-7e604000	Deferred        libxext.so.6
ELF	7e604000-7e609000	Deferred        libxxf86vm.so.1
ELF	7e61a000-7e61c000	Deferred        libnvidia-tls.so.1
ELF	7e61e000-7e6b5000	Deferred        winex11<elf>
  \-PE	7e630000-7e6b5000	\               winex11
ELF	7e6f7000-7e718000	Deferred        libexpat.so.1
ELF	7e718000-7e742000	Deferred        libfontconfig.so.1
ELF	7e742000-7e757000	Deferred        libz.so.1
ELF	7e757000-7e7c7000	Deferred        libfreetype.so.6
ELF	7e7c7000-7e7f3000	Deferred        ws2_32<elf>
  \-PE	7e7d0000-7e7f3000	\               ws2_32
ELF	7e7f3000-7e80d000	Deferred        wsock32<elf>
  \-PE	7e800000-7e80d000	\               wsock32
ELF	7e80d000-7e8af000	Deferred        oleaut32<elf>
  \-PE	7e820000-7e8af000	\               oleaut32
ELF	7e8af000-7e8c2000	Deferred        libresolv.so.2
ELF	7e8d7000-7e8f5000	Deferred        iphlpapi<elf>
  \-PE	7e8e0000-7e8f5000	\               iphlpapi
ELF	7e8f5000-7e956000	Deferred        rpcrt4<elf>
  \-PE	7e900000-7e956000	\               rpcrt4
ELF	7e956000-7e9fa000	Deferred        ole32<elf>
  \-PE	7e960000-7e9fa000	\               ole32
ELF	7e9fa000-7eab9000	Deferred        comctl32<elf>
  \-PE	7ea00000-7eab9000	\               comctl32
ELF	7eab9000-7eb12000	Deferred        shlwapi<elf>
  \-PE	7ead0000-7eb12000	\               shlwapi
ELF	7eb12000-7ec22000	Deferred        shell32<elf>
  \-PE	7eb20000-7ec22000	\               shell32
ELF	7ec22000-7ec74000	Deferred        advapi32<elf>
  \-PE	7ec30000-7ec74000	\               advapi32
ELF	7ec74000-7ed0f000	Deferred        gdi32<elf>
  \-PE	7ec80000-7ed0f000	\               gdi32
ELF	7ed0f000-7ee56000	Deferred        user32<elf>
  \-PE	7ed30000-7ee56000	\               user32
ELF	7ee56000-7ee6a000	Deferred        lz32<elf>
  \-PE	7ee60000-7ee6a000	\               lz32
ELF	7ee6a000-7ee83000	Deferred        version<elf>
  \-PE	7ee70000-7ee83000	\               version
ELF	7efa3000-7efae000	Deferred        libnss_files.so.2
ELF	7efae000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efeb000	Deferred        libm.so.6
ELF	7efeb000-7efed000	Deferred        libxcb-xlib.so.0
ELF	7efed000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7cd9000-f7cdd000	Deferred        libdl.so.2
ELF	f7cdd000-f7e2c000	Deferred        libc.so.6
ELF	f7e2d000-f7e45000	Deferred        libpthread.so.0
ELF	f7e5a000-f7f90000	Deferred        libwine.so.1
ELF	f7f92000-f7fb1000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\setup.exe
	00000009    0 <==
0000000c 
	00000017    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000021 
	00000022    0
Backtrace:
=>1 0x004d86e6 in setup (+0xd86e6) (0x00eda8f0)
  2 0x004d54b7 in setup (+0xd54b7) (0x00edad3c)
  3 0x00481e75 in setup (+0x81e75) (0x00eef93c)
  4 0x00434383 in setup (+0x34383) (0x00eefdbc)
  5 0x00a026d4 in setup (+0x6026d4) (0x00768e48)
  6 0xcccccccc (0xccccccc3)

```

---

### Post by xpxzampop on 2008-06-13
I have a similar problem:

```
foo@bar:/media/cdrom$ wine setup.exe
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xeda520,0x00000004,0xeda51c) Unknown information class
foo@bar:/media/cdrom$
```

I am also trying to install the GOTY edition, and that code is what I get after following all the instructions on [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

If anyone has had success with GOTY, please tell us. I'm beginning to wish I just had regular oblivion...

[Edit] Good news! After doing this ```
ln -s /dev/scd0 ~/.wine/dosdevices/d\:\:
```, when I go into the cd, right click and click open with, then open it with wine, OblivionLauncher.exe works. Setup.exe doesn't, and neither of them work in the terminal.
[/Edit]

---

### Post by thezood on 2008-06-23
Oblivion GOTY won't work until newer versions of Securom protection is supported. I know this is being worked on but I haven't been able to find out when they think they might be done.

[Wine bug](http://bugs.winehq.org/show_bug.cgi?id=7065)

---

### Post by leewang on 2008-12-24
lucky i dont even get an error i right click run with wine and get nothing

---

### Post by slowtrain on 2009-09-29
I ran into the same problem trying to install Oblivion GOTY using current stable version of Wine: 1.0.1.  I then followed the installation instructions here: [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux) .  Those instructions explain how to get the most recent Beta version of Wine on your system, 1.1.30.  With that version, I was able to install the game.  

Only problem is it is unplayable--even on very low quality video settings, I get slow & jumpy video, no sound, and I can't see anything as my character gets started in a new game (well, I see a torch, but otherwise a black screen).  That may have something to do w/ my hardware, which isn't particularly high end (AMD64 X2 4200 and video card Nvidia GE 6200SE TurboCache).  On the other hand, the Beta Wine may be an issue as well.

If I can find a copy of Windows, I might try running it under VirtualBox to see what's different.

What's upsetting is that I paid for the game with the understanding, from the Wine pages, that it was a "Platinum" piece of software that should run smoothly under Wine.  I guess there's some fine print on that.

---

### Post by Progressive on 2009-09-30
Virtualbox now supports DirectX via WineD3D... and since windows has full support for DRM schemes, you should be able to play, albeit with some performance degradation... and the humiliation of using Windows.

Non-GOTY editions work fine. Though I have *absolutely no idea* where you might find one for free. And I certainly don't think one would have any right to use such a nefarious free copy after the one you legally purchased doesn't work because of cripple-ware.

---

