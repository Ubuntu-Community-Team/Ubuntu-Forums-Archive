---
title: "Bionic Commando Rearmed?"
date: 2008-08-15
forum: Wine
---

### Post by thepoeticdragon on 2008-08-15
Hey all,

This remake of the classic NES game came out just yesterday, and I'm sure there are some linux users that are fans. I have tried to install my copy (bought off of Direct2Drive) using WINE, but when I try to run the .exe, nothing comes up.

I am wondering if anybody has managed to get this game running, or if there are some tips that people can give me so that I can continue testing and trying. Some info about the installation: the game installs/needs DirectX (which I installed into my WINE setup using [this]("http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html") guide). The game also installs/needs the PhysX engine. I'm pretty certain I am running the most recent version of WINE. 

Some other notes: being a digital download, there is a prompt before the initial run of the game where a code must be inserted (as per the purchase of one from Direct2Drive). After installation, which seemed successful, this prompt never appeared during run attempts.

This is, I will say, a great remake. A wonderful game, anyone that is fan of any Bionic Commando game should try this one. You won't be disappointed.

Hope we can get this thing running in WINE soon enough, I hate going to my Vista boot just so I can play this. I can't really imagine it being too disagreeable with WINE - despite the DirectX and PhysX, it is a simple albeit very beautiful looking platformer.

---

### Post by Conzar on 2008-08-15
I've been really excited about this game; however, I don't have a windows install on my gaming box.  So I'm reluctant to buy this game b/c I may not be able to play it.

So here is my initial suggestion assuming your using wine from winehq

* type winecfg in a terminal
* click add application (this is for bionic commando)
// there are many different settings ... but you might want to initially try this
* click on Graphics
* Click on "Emulate a virtual desktop
* set to 640x480 (the default rez of BC:R)

Also make sure the "Windows Version:" is set to "Windows XP"

Let me know if this helps at all.

Thanks

---

### Post by thepoeticdragon on 2008-08-15
I totally forgot about desktop emulation, but still no dice. I also played around with the shader settings, but to no avail again.

Is there anything in the command line for WINE that we can try? I know that for some games there are dxlevel commands and such.

---

### Post by Conzar on 2008-08-15
I couldn't resist...

Anyways, here is the debug that I get from running it (after I installed it).

```

fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1c3a3b0,0x00000004,0x1c3a3ac) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1c3929c): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1c390e8,0x00000000), stub!
wine: Unhandled page fault on write access to 0x7ff72000 at address 0xe51a54 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x7ff72000 in 32-bit code (0x00e51a54).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00e51a54 ESP:01c3a770 EBP:01c3a780 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:ffffffff ECX:3fff3801 EDX:00000003
 ESI:7ff40000 EDI:7ff71ffe
Stack dump:
0x01c3a770:  01c3a7b4 00000000 7ff40006 48590000
0x01c3a780:  01c3abcc 00e41f9f 7ff40006 ffffffff
0x01c3a790:  013eec84 00000000 01c2ce4a 01365f60
0x01c3a7a0:  016bd000 00000001 00000000 00032000
0x01c3a7b0:  00000030 5c3f3f5c 756c6f56 307b656d
0x01c3a7c0:  30303030 2d303030 30303030 3030302d
Backtrace:
=>1 0x00e51a54 in bcr (+0xa51a54) (0x01c3a780)
  2 0x00e41f9f in bcr (+0xa41f9f) (0x01c3abcc)
  3 0x00eea9d0 in bcr (+0xaea9d0) (0x01c4f914)
  4 0x00d2dcec in bcr (+0x92dcec) (0x01c4fdbc)
  5 0x00000008 (0x00f5acaf)
0x00e51a54: repe stosl  %es:(%edi)
Modules:
Module  Address                 Debug info      Name (102 modules)
PE        230000-  293000       Deferred        nxcooking
PE        2a0000-  2b2000       Deferred        physxloader
PE        2c0000-  2d6000       Deferred        xinput1_3
PE        400000- 1743000       Export          bcr
PE       1c50000- 1ff8000       Deferred        d3dx9_35
PE      10000000-1001d000       Deferred        openal32
PE      18000000-18038000       Deferred        binkw32
ELF     8bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d2c8000-7dddd000       Deferred        libglcore.so.1
ELF     7dddd000-7de81000       Deferred        libgl.so.1
ELF     7dec5000-7def8000       Deferred        uxtheme<elf>
  \-PE  7ded0000-7def8000       \               uxtheme
ELF     7df20000-7df34000       Deferred        midimap<elf>
  \-PE  7df30000-7df34000       \               midimap
ELF     7df34000-7df5a000       Deferred        msacm32<elf>
  \-PE  7df40000-7df5a000       \               msacm32
ELF     7df5a000-7e002000       Deferred        libasound.so.2
ELF     7e002000-7e019000       Deferred        msacm32<elf>
  \-PE  7e010000-7e019000       \               msacm32
ELF     7e019000-7e04e000       Deferred        winealsa<elf>
  \-PE  7e020000-7e04e000       \               winealsa
ELF     7e04e000-7e053000       Deferred        libxfixes.so.3
ELF     7e053000-7e05c000       Deferred        libxcursor.so.1
ELF     7e05c000-7e062000       Deferred        libxrandr.so.2
ELF     7e062000-7e06a000       Deferred        libxrender.so.1
ELF     7e06a000-7e08a000       Deferred        imm32<elf>
  \-PE  7e070000-7e08a000       \               imm32
ELF     7e08a000-7e08f000       Deferred        libxdmcp.so.6
ELF     7e08f000-7e177000       Deferred        libx11.so.6
ELF     7e177000-7e184000       Deferred        libxext.so.6
ELF     7e184000-7e189000       Deferred        libxxf86vm.so.1
ELF     7e189000-7e1a0000       Deferred        libice.so.6
ELF     7e1a0000-7e1a8000       Deferred        libsm.so.6
ELF     7e1b2000-7e1b4000       Deferred        libnvidia-tls.so.1
ELF     7e1b4000-7e1bd000       Deferred        librt.so.1
ELF     7e1bf000-7e253000       Deferred        winex11<elf>
  \-PE  7e1d0000-7e253000       \               winex11
ELF     7e2ab000-7e3bb000       Deferred        libxml2.so.2
ELF     7e3bb000-7e3e3000       Deferred        libfontconfig.so.1
ELF     7e3e3000-7e3f5000       Deferred        libz.so.1
ELF     7e3f5000-7e46f000       Deferred        libfreetype.so.6
ELF     7e470000-7e473000       Deferred        libxinerama.so.1
ELF     7e486000-7e523000       Deferred        oleaut32<elf>
  \-PE  7e4a0000-7e523000       \               oleaut32
ELF     7e523000-7e5df000       Deferred        comctl32<elf>
  \-PE  7e530000-7e5df000       \               comctl32
ELF     7e5df000-7e635000       Deferred        shlwapi<elf>
  \-PE  7e5f0000-7e635000       \               shlwapi
ELF     7e635000-7e745000       Deferred        shell32<elf>
  \-PE  7e650000-7e745000       \               shell32
ELF     7e745000-7e759000       Deferred        lz32<elf>
  \-PE  7e750000-7e759000       \               lz32
ELF     7e759000-7e772000       Deferred        version<elf>
  \-PE  7e760000-7e772000       \               version
ELF     7e772000-7e7d7000       Deferred        setupapi<elf>
  \-PE  7e780000-7e7d7000       \               setupapi
ELF     7e7d7000-7e876000       Deferred        ole32<elf>
  \-PE  7e7e0000-7e876000       \               ole32
ELF     7e876000-7e8ac000       Deferred        dinput<elf>
  \-PE  7e880000-7e8ac000       \               dinput
ELF     7e8ac000-7e8c4000       Deferred        dinput8<elf>
  \-PE  7e8b0000-7e8c4000       \               dinput8
ELF     7e8c4000-7e92b000       Deferred        msvcrt<elf>
  \-PE  7e8d0000-7e92b000       \               msvcrt
ELF     7e92b000-7ea2f000       Deferred        wined3d<elf>
  \-PE  7e940000-7ea2f000       \               wined3d
ELF     7ea2f000-7ea5e000       Deferred        d3d9<elf>
  \-PE  7ea40000-7ea5e000       \               d3d9
ELF     7ea5e000-7eabe000       Deferred        rpcrt4<elf>
  \-PE  7ea70000-7eabe000       \               rpcrt4
ELF     7eabe000-7ead0000       Deferred        libresolv.so.2
ELF     7ead0000-7eaee000       Deferred        iphlpapi<elf>
  \-PE  7eae0000-7eaee000       \               iphlpapi
ELF     7eaee000-7eb19000       Deferred        ws2_32<elf>
  \-PE  7eb00000-7eb19000       \               ws2_32
ELF     7eb19000-7eb33000       Deferred        wsock32<elf>
  \-PE  7eb20000-7eb33000       \               wsock32
ELF     7eb33000-7eb83000       Deferred        advapi32<elf>
  \-PE  7eb40000-7eb83000       \               advapi32
ELF     7eb83000-7ec1b000       Deferred        gdi32<elf>
  \-PE  7eb90000-7ec1b000       \               gdi32
ELF     7ec1b000-7ed5a000       Deferred        user32<elf>
  \-PE  7ec30000-7ed5a000       \               user32
ELF     7ed5a000-7edea000       Deferred        winmm<elf>
  \-PE  7ed60000-7edea000       \               winmm
ELF     7edea000-7ef12000       Deferred        kernel32<elf>
  \-PE  7ee00000-7ef12000       \               kernel32
ELF     7ef12000-7ef1c000       Deferred        libnss_files.so.2
ELF     7ef1c000-7ef26000       Deferred        libnss_nis.so.2
ELF     7ef26000-7ef3c000       Deferred        libnsl.so.1
ELF     7ef3c000-7ef61000       Deferred        libm.so.6
ELF     7ef61000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef70000-7f000000       \               ntdll
ELF     b7cf1000-b7cf4000       Deferred        libxau.so.6
ELF     b7cf7000-b7cff000       Deferred        libnss_compat.so.2
ELF     b7d01000-b7d05000       Deferred        libdl.so.2
ELF     b7d05000-b7e2d000       Deferred        libc.so.6
ELF     b7e2d000-b7e44000       Deferred        libpthread.so.0
ELF     b7e46000-b7e5b000       Deferred        psapi<elf>
  \-PE  b7e50000-b7e5b000       \               psapi
ELF     b7e5b000-b7f91000       Deferred        libwine.so.1
ELF     b7f92000-b7fae000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Capcom\BionicCommandoRearmed\bcr.exe
        00000009    0 <==
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
00000021
        00000022    0
Backtrace:
=>1 0x00e51a54 in bcr (+0xa51a54) (0x01c3a780)
  2 0x00e41f9f in bcr (+0xa41f9f) (0x01c3abcc)
  3 0x00eea9d0 in bcr (+0xaea9d0) (0x01c4f914)
  4 0x00d2dcec in bcr (+0x92dcec) (0x01c4fdbc)
  5 0x00000008 (0x00f5acaf)

```

---

### Post by thepoeticdragon on 2008-08-16
Wow I wish I knew how to decipher that. Any WINE experts in the house?

---

### Post by GrnFrag on 2008-08-16
> **thepoeticdragon said:**
> Wow I wish I knew how to decipher that. Any WINE experts in the house?

I'm no WINE expert, but if i got that dump outta windows, i'd look to make sure all my dll's were in order.     
```
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1c3a3b0,0x00000004,0x1c3a3ac) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3

```
this appears to be where things start to go bad, looks like your program incorrectly tried to access a dll and then everything took a dump :(  You might have better luck over on the WINE boards, that log should get you a long way.

---

### Post by aoanla on 2008-08-16
Some thoughts:

> **thepoeticdragon said:**
> 
I am wondering if anybody has managed to get this game running, or if there are some tips that people can give me so that I can continue testing and trying. Some info about the installation: the game installs/needs DirectX (which I installed into my WINE setup using [this]("http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html") guide). 

Wine actually contains a very functional DirectX implementation internally, and it is very rare for you to need to install the "official" DirectX dlls to get something to work. Indeed, especially with modern versions of Wine, this can break things, and is generally not advised.
So, you *did* try the game in Wine *before* following that guide, didn't you?

> The game also installs/needs the PhysX engine. I'm pretty certain I am running the most recent version of WINE. 

The latest version of Wine is 1.1.2. Is this what you have installed?



> This is, I will say, a great remake. A wonderful game, anyone that is fan of any Bionic Commando game should try this one. You won't be disappointed.

Hope we can get this thing running in WINE soon enough, I hate going to my Vista boot just so I can play this. I can't really imagine it being too disagreeable with WINE - despite the DirectX and PhysX, it is a simple albeit very beautiful looking platformer.

How do other games work in Wine for you, out of interest? What's your graphics card, and drivers?

Also, ignoring the irrelevant fixme: lines at the top of the dump, it does look like Wine is having problems initialising a proper Direct3D environment for the game - it seems that something is requesting more vertex samplers than Wine can provide. This *might* explain the black display. The actual crash is a segmentation fault in something, though, so may or may not be related...

I'd definitely start an AppDB entry for the game, and put in a bug report.
Especially if you've tried it *before* installing "official" DirectX dlls...

---

### Post by thepoeticdragon on 2008-08-16
My WINE version is 1.1.2, and I did try the game before following the guide. I was just kind of doing a trial and error. I'm really not an expert with WINE or even linux for that matter, so I was just looking to try anything that came to mind. 

I once tried to install my copy of Oblivion, and the guide I used claimed that the game would not launch without DirectX installed as directed. Turned out to be true - it didn't launch without DirectX installed in that way, so I just tried it with this.

My laptop is a System76 Gazelle, with a NVIDIA 8400GM, and a Core2Duo at 2GHZ. My driver is version 169.12.

I have a few games installed, but they are rather old (Half-Life, Mafia, Freedom Force) and run just fine after successful installation (as per the 'Platinum' ratings in the APPDB).

---

### Post by Flecko on 2008-08-16
I really wish that this game worked in Wine. I've been waiting patiently for it ever since I saw the first trailer that shows the NES version and then slowly fades into the new version.

See here: [http://www.youtube.com/watch?v=cqECtTE4Opk](http://www.youtube.com/watch?v=cqECtTE4Opk)

I only own a Wii as well so the fact that its available on the Xbox360 and PS3 does me no good.

Oh well...I might buy it anyways and just hope it eventually works.

---

### Post by Conzar on 2008-08-17
Yea, I posted over at winehq here:
[http://forum.winehq.org/viewtopic.php?t=2050](http://forum.winehq.org/viewtopic.php?t=2050)

Its been kinda quite ... not sure what to do in order to get it to work

---

### Post by mattchew on 2008-08-31
I will test this out in a few minutes...grabbed my own copy and burning it to an ISO.

First thing noted: msls31.dll was requested by the installer. Downloaded a copy of the web and put it in system32 and then restarted installation executable. 
Also: Requires PhysX (or tries to install it at least during the installation of bionic commando rearmed). No error messages of any sort while installing it, and the installation finishes.

Continuing documentation.

Updates: When I tried to run it, I get a separate window when it crashes, which contains the following info:

```
Crash in application version: 1.0.0.7482

Direct3D - Unknown capability violation exception.


SYSTEM:
	CPU : Intel(R) Core(TM)2 CPU 6700 @ 2.66GHz (1 core)
	DirectX : 9.0c
	Distribution : D2D
	Language : 0x0009
	Memory : 2915    MB
	Physics : normal
	Renderer : DX9 normal
	Sound :  ()
```


Wine output is at follows from execution to crash:

```
wine bcr.exe
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1c3a3b0,0x00000004,0x1c3a3ac) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1c3929c): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1c390e8,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x11698d0, 0x1c1988c) stub
fixme:psapi:EnumPageFilesA (0x11698d0, 0x1be41a8) stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1c4f918): Stub!
fixme:console:AttachConsole stub ffffffff
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:create_server class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x17
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,0,2): stub!
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dplayx.dll")
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,3,2): stub!
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dmscript.dll")
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,6,2): stub!
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"dmusic.dll")
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,9,2): stub!
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x144998,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x1c4e738,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x149e00)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x149e18)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Indeo\00ae audio software"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{B4CA2970-DD2B-11D0-9DFA-00AA00AF3494}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x149e30)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14a240)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Indeo\00ae video 5.07 Compression Filter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1F73E9B1-8C3A-11D0-A3BE-00A0C9244436}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14a5e8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Indeo\00ae video 5.07 Decompression Filter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{30355649-0000-0010-8000-00AA00389B71}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14a9f8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14adf0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14b1d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14b668)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14b980)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14bd30)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Indeo\00ae audio software"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{B4CA2970-DD2B-11D0-9DFA-00AA00AF3494}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14c0e0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14c438)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14c830)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14cc68)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,12,2): stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x149e00, 1, 0x14cf28)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x14da28)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14da28, 1, 0x14da40)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Indeo\00ae video 5.07 Compression Filter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1F73E9B1-8C3A-11D0-A3BE-00A0C9244436}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x14e3c8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14e3c8, 1, 0x14d9f8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Indeo\00ae audio software"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{B4CA2970-DD2B-11D0-9DFA-00AA00AF3494}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x14d9d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14d9d0, 1, 0x14dc88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x14eb50)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14eb50, 1, 0x14d998)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Midi Through Port-0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x14d9b0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14d9b0, 1, 0x14ea10)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"gl860"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1B544C22-FD0B-11CE-8C63-00AA0044B51E}"
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x14d9b0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14d9b0, 1, 0x14f270)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x14d9b0, 1, 0x14e9d8)
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,15,2): stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,21,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,24,2): stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1440x900x32 @60! (XRandR)
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,27,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,30,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,33,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,36,2): stub!
fixme:d3d:debug_d3dformat Unrecognized 1111774798 (as fourcc: NVDB) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 1111774798 (as fourcc: NVDB) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1111774798) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,39,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,42,2): stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,45,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,48,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,51,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,54,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,57,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,60,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,63,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,66,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,69,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,72,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,75,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,78,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,81,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,84,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,87,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,90,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,93,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,96,2): stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,99,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,102,2): stub!
fixme:dsound:DllCanUnloadNow (void): stub
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,105,2): stub!
fixme:dsound:DllCanUnloadNow (void): stub
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,108,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,111,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,114,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,117,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,120,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,123,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,126,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,129,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,132,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,138,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,141,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,144,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,147,2): stub!
fixme:dsound:DllCanUnloadNow (void): stub
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,150,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,153,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,156,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,159,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,162,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,165,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,168,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,171,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,174,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,177,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,180,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,183,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,186,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,189,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,192,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,198,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,201,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,204,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,207,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,213,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,216,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,219,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,222,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,228,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,231,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,234,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,237,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,240,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,243,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,246,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,249,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,252,2): stub!
fixme:win:SetLayeredWindowAttributes (0x120148,0x00000000,255,2): stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(1440,900)
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:faultrep:ReportFault 0x1c4e3d0 0x0 stub
designerfx@Matt-laptop:~/.wine/drive_c/Program Files/Capcom/Bionic Commando Rearmed$ fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x1c3a3b0,0x00000004,0x1c3a3ac) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1c3929c): Stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1c390e8,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x11698d0, 0x1c1988c) stub
fixme:psapi:EnumPageFilesA (0x11698d0, 0x1be41a8) stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1c4f918): Stub!
fixme:console:AttachConsole stub ffffffff

```

---

