---
title: "A problem with half life 2 (again)."
date: 2008-06-01
forum: Wine
---

### Post by emshains on 2008-06-01
I played more or less ithout problems till I got to Ravenholm. I am no playing around with my new gravity gun and now I get to the place where this dude is burning zombies. And around here I usually hang up, sometimes I get to the place where there is the electric fence or something. 

But these look like some random hang ups, it either hangs up or it exits, and takes me to the desktop without changing the resolution of the desktop. 

Here is the text wine puts out: ```
fixme:win:EnumDisplayDevicesW ((null),0,0x32e078,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x139fa8) : stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:shdocvw:ViewObject_SetAdvise (0x89b2108)->(1 00000002 0x8fb8f98)
fixme:shdocvw:PersistStreamInit_InitNew (0x89b2108)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x89b2108)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x89b2108)->(ffffffff)
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x139fa8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0xcd79840) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0xcdb9ec0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0xcdfa540) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0xce50050) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x139fa8) : stub
wine: Unhandled page fault on read access to 0x3f7ffff4 at address 0x7bc40984 (thread 001f), starting debugger...
Unhandled exception: page fault on read access to 0x3f7ffff4 in 32-bit code (0x7bc40984).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc40984 ESP:0032e5c8 EBP:0032e5cc EFLAGS:00210212(   - 00      - RIA1)
 EAX:3f800000 EBX:7bc88444 ECX:3f7ffff4 EDX:006489f8
 ESI:0064003c EDI:006489f8
Stack dump:
0x0032e5c8:  00648a00 0032e60c 7bc427c9 00640048
0x0032e5d8:  001250c0 00000000 00000000 00000000
0x0032e5e8:  00000000 00000000 00000000 00000000
0x0032e5f8:  00640000 00000002 003421a0 00648a00
0x0032e608:  00000000 0032e654 0035de6e 00640000
0x0032e618:  00000000 00648a00 00000000 003421ac
Backtrace:
=>1 0x7bc40984 in ntdll (+0x30984) (0x0032e5cc)
  2 0x7bc427c9 RtlFreeHeap+0x69() in ntdll (0x0032e60c)
  3 0x0035de6e in tier0 (+0xde6e) (0x0032e654)
  4 0x0035369a in tier0 (+0x369a) (0x003421a0)
  5 0x00648ab0 (0x0033f0fc)
  6 0x00331230 in vstdlib (+0x1230) (0x003311b0)
  7 0x56550000 (0x0800ec81)
  8 0x9b938d8a (0x87828382)
0x7bc40984: movl	0x0(%ecx),%eax
Modules:
Module	Address			Debug info	Name (117 modules)
PE	  330000-  346000	Export          vstdlib
PE	  350000-  387000	Export          tier0
PE	  3b0000-  3c4000	Deferred        steam
PE	  3d0000-  3e3000	Deferred        steamy
PE	  3f0000-  3fe000	Deferred        unicode
PE	  400000-  416000	Deferred        hl2
PE	 1040000- 105f000	Deferred        stdshader_dbg
PE	 1060000- 108d000	Deferred        stdshader_dx6
PE	 5f70000- 61e0000	Deferred        studiorender
PE	 61e0000- 638c000	Deferred        gameui
PE	 68c0000- 68cd000	Deferred        vaudio_miles
PE	 8da0000- 8e3c000	Deferred        trackerui
PE	 8e40000- 8f67000	Deferred        serverbrowser
PE	 8f70000- 8fad000	Deferred        trackernet
PE	10000000-10010000	Deferred        launcher
PE	21100000-21164000	Deferred        mss32
PE	22000000-2262d000	Deferred        server
PE	24000000-24388000	Deferred        client
PE	26000000-26109000	Deferred        vphysics
PE	26400000-26439000	Deferred        mssvoice.asi
PE	26f00000-26f2e000	Deferred        mssmp3.asi
PE	2a000000-2a07d000	Deferred        shaderapidx9
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7bfc4000-7c000000	Deferred        shdocvw<elf>
  \-PE	7bfd0000-7c000000	\               shdocvw
ELF	7c5ad000-7c5c1000	Deferred        winejoystick<elf>
  \-PE	7c5b0000-7c5c1000	\               winejoystick
ELF	7c880000-7c8ca000	Deferred        dsound<elf>
  \-PE	7c890000-7c8ca000	\               dsound
ELF	7d040000-7d057000	Deferred        mcicda<elf>
  \-PE	7d050000-7d057000	\               mcicda
ELF	7d4fc000-7e011000	Deferred        libglcore.so.1
ELF	7e011000-7e0b5000	Deferred        libgl.so.1
ELF	7e0b5000-7e1b7000	Deferred        wined3d<elf>
  \-PE	7e0d0000-7e1b7000	\               wined3d
ELF	7e237000-7e267000	Deferred        d3d9<elf>
  \-PE	7e240000-7e267000	\               d3d9
ELF	7e315000-7e348000	Deferred        uxtheme<elf>
  \-PE	7e320000-7e348000	\               uxtheme
ELF	7e348000-7e407000	Deferred        comctl32<elf>
  \-PE	7e350000-7e407000	\               comctl32
ELF	7e407000-7e517000	Deferred        shell32<elf>
  \-PE	7e420000-7e517000	\               shell32
ELF	7e517000-7e570000	Deferred        shlwapi<elf>
  \-PE	7e520000-7e570000	\               shlwapi
ELF	7e570000-7e584000	Deferred        midimap<elf>
  \-PE	7e580000-7e584000	\               midimap
ELF	7e584000-7e5aa000	Deferred        msacm32<elf>
  \-PE	7e590000-7e5aa000	\               msacm32
ELF	7e5aa000-7e5c1000	Deferred        msacm32<elf>
  \-PE	7e5b0000-7e5c1000	\               msacm32
ELF	7e5c1000-7e684000	Deferred        libasound.so.2
ELF	7e684000-7e6ba000	Deferred        winealsa<elf>
  \-PE	7e690000-7e6ba000	\               winealsa
ELF	7e6ba000-7e74c000	Deferred        winmm<elf>
  \-PE	7e6d0000-7e74c000	\               winmm
ELF	7e74c000-7e783000	Deferred        dinput<elf>
  \-PE	7e750000-7e783000	\               dinput
ELF	7e783000-7e79b000	Deferred        dinput8<elf>
  \-PE	7e790000-7e79b000	\               dinput8
ELF	7e79b000-7e83d000	Deferred        oleaut32<elf>
  \-PE	7e7b0000-7e83d000	\               oleaut32
ELF	7e83d000-7e89e000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e89e000	\               rpcrt4
ELF	7e89e000-7e942000	Deferred        ole32<elf>
  \-PE	7e8b0000-7e942000	\               ole32
ELF	7e942000-7e955000	Deferred        libresolv.so.2
ELF	7e967000-7e985000	Deferred        iphlpapi<elf>
  \-PE	7e970000-7e985000	\               iphlpapi
ELF	7e985000-7e9b1000	Deferred        ws2_32<elf>
  \-PE	7e990000-7e9b1000	\               ws2_32
ELF	7e9b1000-7e9cb000	Deferred        wsock32<elf>
  \-PE	7e9c0000-7e9cb000	\               wsock32
ELF	7e9cb000-7e9d4000	Deferred        libxcursor.so.1
ELF	7e9d4000-7e9d9000	Deferred        libxfixes.so.3
ELF	7e9d9000-7e9dc000	Deferred        libxcomposite.so.1
ELF	7e9dc000-7e9e2000	Deferred        libxrandr.so.2
ELF	7e9e2000-7e9ea000	Deferred        libxrender.so.1
ELF	7e9ea000-7e9ed000	Deferred        libxinerama.so.1
ELF	7e9ed000-7ea0d000	Deferred        imm32<elf>
  \-PE	7e9f0000-7ea0d000	\               imm32
ELF	7ea0d000-7ea12000	Deferred        libxdmcp.so.6
ELF	7ea12000-7ea2a000	Deferred        libxcb.so.1
ELF	7ea2a000-7ea2d000	Deferred        libxau.so.6
ELF	7ea2d000-7eb14000	Deferred        libx11.so.6
ELF	7eb14000-7eb22000	Deferred        libxext.so.6
ELF	7eb22000-7eb27000	Deferred        libxxf86vm.so.1
ELF	7eb27000-7eb3f000	Deferred        libice.so.6
ELF	7eb3f000-7eb47000	Deferred        libsm.so.6
ELF	7eb55000-7eb57000	Deferred        libnvidia-tls.so.1
ELF	7eb59000-7ebf0000	Deferred        winex11<elf>
  \-PE	7eb70000-7ebf0000	\               winex11
ELF	7ec1b000-7ec3c000	Deferred        libexpat.so.1
ELF	7ec3c000-7ec66000	Deferred        libfontconfig.so.1
ELF	7ec78000-7ec8d000	Deferred        libz.so.1
ELF	7ec8d000-7ecfd000	Deferred        libfreetype.so.6
ELF	7ed0f000-7ed61000	Deferred        advapi32<elf>
  \-PE	7ed20000-7ed61000	\               advapi32
ELF	7ed61000-7edfc000	Deferred        gdi32<elf>
  \-PE	7ed70000-7edfc000	\               gdi32
ELF	7edfc000-7ef43000	Deferred        user32<elf>
  \-PE	7ee20000-7ef43000	\               user32
ELF	7ef9c000-7efa7000	Deferred        libnss_files.so.2
ELF	7efa7000-7efb1000	Deferred        libnss_nis.so.2
ELF	7efb1000-7efc9000	Deferred        libnsl.so.1
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	7efee000-7eff0000	Deferred        libxcb-xlib.so.0
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c57000-b7c5b000	Deferred        libdl.so.2
ELF	b7c5b000-b7daa000	Deferred        libc.so.6
ELF	b7daa000-b7dc2000	Deferred        libpthread.so.0
ELF	b7dd4000-b7f0a000	Deferred        libwine.so.1
ELF	b7f0c000-b7f28000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	0000001d    0
	0000001c    0
	0000001b    0
	0000001a   15
	00000019    0
	00000018    0
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
0000001e (D) Z:\home\emils\hl\hl2.exe
	00000025    0
	00000024    0
	00000023    0
	00000022   15
	00000021    0
	00000020    0
	0000001f    0 <==
Backtrace:
=>1 0x7bc40984 in ntdll (+0x30984) (0x0032e5cc)
  2 0x7bc427c9 RtlFreeHeap+0x69() in ntdll (0x0032e60c)
  3 0x0035de6e in tier0 (+0xde6e) (0x0032e654)
  4 0x0035369a in tier0 (+0x369a) (0x003421a0)
  5 0x00648ab0 (0x0033f0fc)
  6 0x00331230 in vstdlib (+0x1230) (0x003311b0)
  7 0x56550000 (0x0800ec81)
  8 0x9b938d8a (0x87828382)

```


Please help, I am looking forward to finish the game in a couple of days, or I was looking.

---

### Post by Horomancer on 2008-06-01
1) I had simular troubles with HL2 back when i was using WinXP. It resulted from the vid card crapping out do to low ram and a memory leak.

2) I'm having the same trouble now as i experiment with Wine, but i don't even get to the title screen. I think it may be a simluar problem as 1) but compounded with running HL2 through Wine.

will post if I make any progress with my own setup.

---

### Post by emshains on 2008-06-02
> **Horomancer said:**
> 1) I had simular troubles with HL2 back when i was using WinXP. It resulted from the vid card crapping out do to low ram and a memory leak.

2) I'm having the same trouble now as i experiment with Wine, but i don't even get to the title screen. I think it may be a simluar problem as 1) but compounded with running HL2 through Wine.

will post if I make any progress with my own setup.

Well, I just woke up this morning and felt like trying HL2 out, and what do you know, It ran with several pauses for 1h gameplay. But then this kind of problem happened:[http://ubuntuforums.org/showthread.php?t=813806]("http://ubuntuforums.org/showthread.php?t=813806"). But it was fixed, and like 3 autosaves later it struck again and it repeated like this 2-3 times. After that, I had no problems.

It is really tricky to get some applications on wine to work, but it is quite hard to even diagnose this mysterious problem, because everything works just the way it works from dudes in appdb in wine. But then again, those programs were not designed for use in linux, so we should be happy they do work, sometimes, kind of.

---

### Post by aoanla on 2008-06-03
> **emshains said:**
> 
It is really tricky to get some applications on wine to work, but it is quite hard to even diagnose this mysterious problem, because everything works just the way it works from dudes in appdb in wine. But then again, those programs were not designed for use in linux, so we should be happy they do work, sometimes, kind of.

Well, this doesn't look like a Wine problem anyway - it looks like one of the random HL2 problems that people sometimes have in Windows, too. Don't be down on Wine just because one program has bugs!

---

