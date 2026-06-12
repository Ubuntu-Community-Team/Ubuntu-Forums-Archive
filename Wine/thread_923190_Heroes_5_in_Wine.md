---
title: "Heroes 5 in Wine ?"
date: 2008-09-18
forum: Wine
---

### Post by MaximB on 2008-09-18
Hello !

I have looked at the wine databese and it says that Heroes5 is supported and working well.

I have installed Heroes5 with no errors.
But when I start heroes5 the screen goes blank and partly comes back forcing me to restart the x-server and the game never starts.

How can I configure Wine to play heroes 5 ?

---

### Post by asdfoo on 2008-09-18
> **MaximB said:**
> Hello !

I have looked at the wine databese and it says that Heroes5 is supported and working well.

I have installed Heroes5 with no errors.
But when I start heroes5 the screen goes blank and partly comes back forcing me to restart the x-server and the game never starts.

How can I configure Wine to play heroes 5 ?

first run winecfg

Set the virtual desktop to 1024x768 then start your program, maybe it will progress further but now you should not have to restart X.

Can you post the terminal output?

---

### Post by MaximB on 2008-09-18
I will as soon as I get back home ;)
Thanks.

---

### Post by MaximB on 2008-09-18
Ok, I have tried what you said and it won't run.
Here is the output :

```
maximb@maximb-home:~$ wine /home/maximb/maxddark/games/heroes5/bin/H5_Game.exe 
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,9,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,27,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,36,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,45,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,54,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,63,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,72,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,81,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,90,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,99,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,108,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,117,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,126,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,144,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,153,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,162,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,171,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,180,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,189,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,198,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,207,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,216,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,234,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,243,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,252,2): stub!
ERROR: Failed to open file with type descriptions (types.xml)
wine: Unhandled page fault on read access to 0x0000004c at address 0x941542 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000004c in 32-bit code (0x00941542).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00941542 ESP:01c8fda8 EBP:01c8fdcc EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:00cd636c ECX:01c8fef8 EDX:10025330
 ESI:00000000 EDI:00000000
Stack dump:
0x01c8fda8:  00000000 1019f870 ffffffff 00cd636c
0x01c8fdb8:  01c8fdcc 0099625e 00000002 10339c10
0x01c8fdc8:  00000001 1062ed90 1062eda6 1062eda7
0x01c8fdd8:  00a2be15 00b1d868 10339c10 004092cd
0x01c8fde8:  7b866bb0 00000000 00000000 00000001
0x01c8fdf8:  00cc4e80 01c8fe18 00b43dc3 0011172b
Backtrace:
=>1 0x00941542 in h5_game (+0x541542) (0x01c8fdcc)
  2 0x1062eda6 (0x1062ed90)
  3 0x5f4a424f (0x5f564441)
0x00941542: movl	0x4c(%esi),%ecx
Modules:
Module	Address			Debug info	Name (129 modules)
PE	  340000-  37b000	Deferred        libcurl
PE	  380000-  396000	Deferred        zlibwapi
PE	  3a0000-  3cc000	Deferred        ubistats
PE	  400000- 1a90000	Export          h5_game
PE	 1c90000- 1d26000	Deferred        fmod
PE	10000000-10013000	Deferred        zlib1
PE	50000000-50086000	Deferred        granny2
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7dc14000-7dc18000	Deferred        libgpg-error.so.0
ELF	7dc18000-7dc65000	Deferred        libgcrypt.so.11
ELF	7dc65000-7dc75000	Deferred        libtasn1.so.3
ELF	7dc75000-7dc7d000	Deferred        libkrb5support.so.0
ELF	7dc7d000-7dcaf000	Deferred        libcrypt.so.1
ELF	7dcaf000-7dd25000	Deferred        libgnutls.so.13
ELF	7dd25000-7dd48000	Deferred        libk5crypto.so.3
ELF	7dd48000-7ddd5000	Deferred        libkrb5.so.3
ELF	7ddd5000-7ddfe000	Deferred        libgssapi_krb5.so.2
ELF	7ddfe000-7de31000	Deferred        libcups.so.2
ELF	7de45000-7de5c000	Deferred        msacm32<elf>
  \-PE	7de50000-7de5c000	\               msacm32
ELF	7de5c000-7df1f000	Deferred        libasound.so.2
ELF	7df1f000-7df33000	Deferred        midimap<elf>
  \-PE	7df20000-7df33000	\               midimap
ELF	7df33000-7df69000	Deferred        winealsa<elf>
  \-PE	7df40000-7df69000	\               winealsa
ELF	7dfb5000-7dfe8000	Deferred        uxtheme<elf>
  \-PE	7dfc0000-7dfe8000	\               uxtheme
ELF	7dfe8000-7dff1000	Deferred        libxcursor.so.1
ELF	7dff1000-7dff6000	Deferred        libxfixes.so.3
ELF	7dff6000-7dff9000	Deferred        libxcomposite.so.1
ELF	7dff9000-7dfff000	Deferred        libxrandr.so.2
ELF	7dfff000-7e007000	Deferred        libxrender.so.1
ELF	7e007000-7e00a000	Deferred        libxinerama.so.1
ELF	7e00a000-7e02a000	Deferred        imm32<elf>
  \-PE	7e010000-7e02a000	\               imm32
ELF	7e02a000-7e02f000	Deferred        libxdmcp.so.6
ELF	7e02f000-7e047000	Deferred        libxcb.so.1
ELF	7e047000-7e04a000	Deferred        libxau.so.6
ELF	7e04a000-7e131000	Deferred        libx11.so.6
ELF	7e131000-7e13f000	Deferred        libxext.so.6
ELF	7e13f000-7e144000	Deferred        libxxf86vm.so.1
ELF	7e144000-7e15c000	Deferred        libice.so.6
ELF	7e15c000-7e164000	Deferred        libsm.so.6
ELF	7e166000-7e169000	Deferred        libkeyutils.so.1
ELF	7e173000-7e176000	Deferred        libcom_err.so.2
ELF	7e178000-7e20f000	Deferred        winex11<elf>
  \-PE	7e190000-7e20f000	\               winex11
ELF	7e251000-7e272000	Deferred        libexpat.so.1
ELF	7e272000-7e29c000	Deferred        libfontconfig.so.1
ELF	7e29c000-7e2b1000	Deferred        libz.so.1
ELF	7e2b1000-7e31e000	Deferred        libfreetype.so.6
ELF	7e31e000-7e320000	Deferred        libxcb-xlib.so.0
ELF	7e332000-7e3dd000	Deferred        comdlg32<elf>
  \-PE	7e340000-7e3dd000	\               comdlg32
ELF	7e3dd000-7e413000	Deferred        winspool<elf>
  \-PE	7e3e0000-7e413000	\               winspool
ELF	7e413000-7e434000	Deferred        mpr<elf>
  \-PE	7e420000-7e434000	\               mpr
ELF	7e434000-7e482000	Deferred        wininet<elf>
  \-PE	7e440000-7e482000	\               wininet
ELF	7e482000-7e4a8000	Deferred        msacm32<elf>
  \-PE	7e490000-7e4a8000	\               msacm32
ELF	7e4a8000-7e4df000	Deferred        dinput<elf>
  \-PE	7e4b0000-7e4df000	\               dinput
ELF	7e4df000-7e4f7000	Deferred        dinput8<elf>
  \-PE	7e4e0000-7e4f7000	\               dinput8
ELF	7e4f7000-7e511000	Deferred        wsock32<elf>
  \-PE	7e500000-7e511000	\               wsock32
ELF	7e511000-7e52a000	Deferred        crtdll<elf>
  \-PE	7e520000-7e52a000	\               crtdll
ELF	7e52a000-7e5bc000	Deferred        winmm<elf>
  \-PE	7e540000-7e5bc000	\               winmm
ELF	7e5bc000-7e5e8000	Deferred        ws2_32<elf>
  \-PE	7e5c0000-7e5e8000	\               ws2_32
ELF	7e5e8000-7e652000	Deferred        msvcrt<elf>
  \-PE	7e600000-7e652000	\               msvcrt
ELF	7e652000-7e671000	Deferred        d3dx8<elf>
  \-PE	7e660000-7e671000	\               d3dx8
ELF	7e671000-7e68e000	Deferred        d3dx9_36<elf>
  \-PE	7e680000-7e68e000	\               d3dx9_36
ELF	7e68e000-7e6a7000	Deferred        d3dx9_25<elf>
  \-PE	7e690000-7e6a7000	\               d3dx9_25
ELF	7e6a7000-7e7aa000	Deferred        wined3d<elf>
  \-PE	7e6c0000-7e7aa000	\               wined3d
ELF	7e7aa000-7e7da000	Deferred        d3d9<elf>
  \-PE	7e7b0000-7e7da000	\               d3d9
ELF	7e7da000-7e7ef000	Deferred        psapi<elf>
  \-PE	7e7e0000-7e7ef000	\               psapi
ELF	7e7ef000-7e839000	Deferred        dbghelp<elf>
  \-PE	7e800000-7e839000	\               dbghelp
ELF	7e839000-7e8db000	Deferred        oleaut32<elf>
  \-PE	7e850000-7e8db000	\               oleaut32
ELF	7e8db000-7e8ee000	Deferred        libresolv.so.2
ELF	7e8ee000-7e902000	Deferred        oleacc<elf>
  \-PE	7e8f0000-7e902000	\               oleacc
ELF	7e902000-7e920000	Deferred        iphlpapi<elf>
  \-PE	7e910000-7e920000	\               iphlpapi
ELF	7e920000-7e981000	Deferred        rpcrt4<elf>
  \-PE	7e930000-7e981000	\               rpcrt4
ELF	7e981000-7ea25000	Deferred        ole32<elf>
  \-PE	7e990000-7ea25000	\               ole32
ELF	7ea25000-7eae4000	Deferred        comctl32<elf>
  \-PE	7ea30000-7eae4000	\               comctl32
ELF	7eae4000-7eb3d000	Deferred        shlwapi<elf>
  \-PE	7eaf0000-7eb3d000	\               shlwapi
ELF	7eb3d000-7ec50000	Deferred        shell32<elf>
  \-PE	7eb50000-7ec50000	\               shell32
ELF	7ec50000-7eca2000	Deferred        advapi32<elf>
  \-PE	7ec60000-7eca2000	\               advapi32
ELF	7eca2000-7ed3d000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed3d000	\               gdi32
ELF	7ed3d000-7ee84000	Deferred        user32<elf>
  \-PE	7ed60000-7ee84000	\               user32
ELF	7efa4000-7efaf000	Deferred        libnss_files.so.2
ELF	7efaf000-7efc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7efed000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c77000-b7c7b000	Deferred        libdl.so.2
ELF	b7c7b000-b7dca000	Deferred        libc.so.6
ELF	b7dcb000-b7de3000	Deferred        libpthread.so.0
ELF	b7df7000-b7f2d000	Deferred        libwine.so.1
ELF	b7f2f000-b7f4b000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\maximb\maxddark\games\heroes5\bin\H5_Game.exe
	0000001a    0
	00000019    0
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
00000017 
	00000018    0
Backtrace:
=>1 0x00941542 in h5_game (+0x541542) (0x01c8fdcc)
  2 0x1062eda6 (0x1062ed90)
  3 0x5f4a424f (0x5f564441)

```

What's the problem ?

---

### Post by asdfoo on 2008-09-18
Well, first of all, it looks like you might be starting the program the wrong way...

maximb@maximb-home:~$ wine /home/maximb/maxddark/games/heroes5/bin/H5_Game.exe 

On Windows, most programs expect you to cd to the install directory before launching the program, or the shortcut you use sets the working directory to the install directory.

Otherwise, did you run the installer for this program under Wine?  It looks like you have the files in a non-standard place...

You should run the installer then do something like:
cd ~/.wine/drive_c/Program\ Files\Heroes5
wine bin\H5_Game.exe

Or, just use the shortcut the game sets up on your Start Menu (if it installs icons)

---

### Post by MaximB on 2008-09-19
I have installed the game, when it asked me where I would like to install it to I chose this directory.
I don't see that the choice of installation should somehow effect the outcome.
I still run the same file.

---

### Post by asdfoo on 2008-09-19
ok - that's fine for the second part of my response, can you answer my first?

are you starting it correctly, per above?

---

### Post by MaximB on 2008-09-19
I think that this command :

```
wine /home/maximb/maxddark/games/heroes5/bin/H5_Game.exe 

```
Is the SAME as running :

```
cd /home/maximb/maxddark/games/heroes5/bin/
wine H5_Game.exe
```

Don't you agree ?

---

### Post by asdfoo on 2008-09-19
then you'd be incorrect...  I've explained above.

It also states this in the FAQ: [http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0](http://wiki.winehq.org/FAQ#head-8d8c06cf7fb33269c085a07531b61e5c730566e0)

---

### Post by MaximB on 2008-09-19
OK, I've cd'd to the installation directory first and still the same output :

```
maximb@maximb-home:~$ cd /home/maximb/maxddark/games/heroes5/bin/
maximb@maximb-home:~/maxddark/games/heroes5/bin$ ls
dbghelp.dll  granny2.dll  libcurl.dll  msvcr71.dll   zlib1.dll
fmod.dll     H5_Game.exe  msvcp71.dll  UbiStats.dll  zlibwapi.dll
maximb@maximb-home:~/maxddark/games/heroes5/bin$ wine H5_Game.exe 
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,9,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,27,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,36,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,45,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,54,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,63,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,72,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,81,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,90,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,99,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,108,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,117,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,126,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,135,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,144,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,153,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,162,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,171,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,180,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,189,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,198,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,207,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,216,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,234,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,243,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,252,2): stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x1c8f98c,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3554
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x140700) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:D3D9CB_CreateSurface (0x140700) IDirect3DDevice9_CreateSurface failed
fixme:d3d:IWineD3DDeviceImpl_CreateTexture Failed to create surface  0x3580bf8
fixme:d3d9:IDirect3DDevice9Impl_CreateTexture (0x140700) call to IWineD3DDevice_CreateTexture failed
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x14ee50) Unhandled query type 4
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x13ffb0) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x14ee50) Event query: Unimplemented, but pretending to be supported
wine: Unhandled page fault on read access to 0x1a9ea7d4 at address 0x7e6d70c0 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x1a9ea7d4 in 32-bit code (0x7e6d70c0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e6d70c0 ESP:01c8ee00 EBP:01c8ee10 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:02cbe478 EBX:7e79fc84 ECX:00000000 EDX:02cbe490
 ESI:05f4acb8 EDI:04000000
Stack dump:
0x01c8ee00:  04000000 be95971a 0316fdc8 0316fdc8
0x01c8ee10:  01c8ee40 7e7411b4 0014ee50 7e797996
0x01c8ee20:  0014ee50 00000009 7d69cf62 00000009
0x01c8ee30:  001422c8 7e7977c4 7e79fc84 0014ee50
0x01c8ee40:  01c8ef40 7e74a0e5 0316fdc8 00000001
0x01c8ee50:  00000001 01c8ef2c 01c8ef28 01c8ef24
Backtrace:
=>1 0x7e6d70c0 IWineD3DDeviceImpl_MarkStateDirty+0x50() in wined3d (0x01c8ee10)
  2 0x7e7411b4 in wined3d (+0x911b4) (0x01c8ee40)
  3 0x7e74a0e5 in wined3d (+0x9a0e5) (0x01c8ef40)
  4 0x7e749268 in wined3d (+0x99268) (0x01c8ef70)
  5 0x7e74f892 in wined3d (+0x9f892) (0x01c8efa0)
  6 0x7e7299a8 in wined3d (+0x799a8) (0x01c8eff0)
  7 0x7e6d354c ActivateContext+0x4fc() in wined3d (0x01c8f070)
  8 0x7e70825b drawPrimitive+0x17b() in wined3d (0x01c8f380)
  9 0x7e6dfd6b in wined3d (+0x2fd6b) (0x01c8f3f0)
  10 0x7e7bac5e in d3d9 (+0xac5e) (0x01c8f420)
0x7e6d70c0 IWineD3DDeviceImpl_MarkStateDirty+0x50 in wined3d: testl	%edi,0x1064(%edx,%esi,4)
Modules:
Module	Address			Debug info	Name (133 modules)
PE	  340000-  37b000	Deferred        libcurl
PE	  380000-  396000	Deferred        zlibwapi
PE	  3a0000-  3cc000	Deferred        ubistats
PE	  400000- 1a90000	Deferred        h5_game
PE	 1c90000- 1d26000	Deferred        fmod
PE	10000000-10013000	Deferred        zlib1
PE	50000000-50086000	Deferred        granny2
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7c5a8000-7c5b1000	Deferred        librt.so.1
ELF	7c5b1000-7d628000	Deferred        fglrx_dri.so
ELF	7d628000-7d633000	Deferred        libgcc_s.so.1
ELF	7d633000-7d6ae000	Deferred        libgl.so.1
ELF	7dbfc000-7dc00000	Deferred        libgpg-error.so.0
ELF	7dc00000-7dc4d000	Deferred        libgcrypt.so.11
ELF	7dc4d000-7dc5d000	Deferred        libtasn1.so.3
ELF	7dc5d000-7dc60000	Deferred        libkeyutils.so.1
ELF	7dc60000-7dc68000	Deferred        libkrb5support.so.0
ELF	7dc68000-7dc9a000	Deferred        libcrypt.so.1
ELF	7dc9a000-7dd10000	Deferred        libgnutls.so.13
ELF	7dd10000-7dd33000	Deferred        libk5crypto.so.3
ELF	7dd33000-7ddc0000	Deferred        libkrb5.so.3
ELF	7ddc0000-7dde9000	Deferred        libgssapi_krb5.so.2
ELF	7dde9000-7de1c000	Deferred        libcups.so.2
ELF	7de34000-7de48000	Deferred        midimap<elf>
  \-PE	7de40000-7de48000	\               midimap
ELF	7de48000-7df0b000	Deferred        libasound.so.2
ELF	7df0c000-7df23000	Deferred        msacm32<elf>
  \-PE	7df10000-7df23000	\               msacm32
ELF	7df23000-7df59000	Deferred        winealsa<elf>
  \-PE	7df30000-7df59000	\               winealsa
ELF	7df87000-7df8a000	Deferred        libcom_err.so.2
ELF	7df9d000-7dfd0000	Deferred        uxtheme<elf>
  \-PE	7dfa0000-7dfd0000	\               uxtheme
ELF	7dfd0000-7dfd9000	Deferred        libxcursor.so.1
ELF	7dfd9000-7dfde000	Deferred        libxfixes.so.3
ELF	7dfde000-7dfe1000	Deferred        libxcomposite.so.1
ELF	7dfe1000-7dfe7000	Deferred        libxrandr.so.2
ELF	7dfe7000-7dfef000	Deferred        libxrender.so.1
ELF	7dfef000-7dff2000	Deferred        libxinerama.so.1
ELF	7dff2000-7e012000	Deferred        imm32<elf>
  \-PE	7e000000-7e012000	\               imm32
ELF	7e012000-7e017000	Deferred        libxdmcp.so.6
ELF	7e017000-7e02f000	Deferred        libxcb.so.1
ELF	7e02f000-7e031000	Deferred        libxcb-xlib.so.0
ELF	7e031000-7e034000	Deferred        libxau.so.6
ELF	7e034000-7e11b000	Deferred        libx11.so.6
ELF	7e11b000-7e129000	Deferred        libxext.so.6
ELF	7e129000-7e12e000	Deferred        libxxf86vm.so.1
ELF	7e12e000-7e146000	Deferred        libice.so.6
ELF	7e146000-7e14e000	Deferred        libsm.so.6
ELF	7e166000-7e1fd000	Deferred        winex11<elf>
  \-PE	7e170000-7e1fd000	\               winex11
ELF	7e233000-7e254000	Deferred        libexpat.so.1
ELF	7e254000-7e27e000	Deferred        libfontconfig.so.1
ELF	7e27e000-7e293000	Deferred        libz.so.1
ELF	7e293000-7e300000	Deferred        libfreetype.so.6
ELF	7e318000-7e3c3000	Deferred        comdlg32<elf>
  \-PE	7e320000-7e3c3000	\               comdlg32
ELF	7e3c3000-7e3f9000	Deferred        winspool<elf>
  \-PE	7e3d0000-7e3f9000	\               winspool
ELF	7e3f9000-7e40d000	Deferred        oleacc<elf>
  \-PE	7e400000-7e40d000	\               oleacc
ELF	7e40d000-7e42e000	Deferred        mpr<elf>
  \-PE	7e410000-7e42e000	\               mpr
ELF	7e42e000-7e47c000	Deferred        wininet<elf>
  \-PE	7e440000-7e47c000	\               wininet
ELF	7e47c000-7e4a2000	Deferred        msacm32<elf>
  \-PE	7e480000-7e4a2000	\               msacm32
ELF	7e4a2000-7e4d9000	Deferred        dinput<elf>
  \-PE	7e4b0000-7e4d9000	\               dinput
ELF	7e4d9000-7e4f1000	Deferred        dinput8<elf>
  \-PE	7e4e0000-7e4f1000	\               dinput8
ELF	7e4f1000-7e50b000	Deferred        wsock32<elf>
  \-PE	7e500000-7e50b000	\               wsock32
ELF	7e50b000-7e524000	Deferred        crtdll<elf>
  \-PE	7e510000-7e524000	\               crtdll
ELF	7e524000-7e5b6000	Deferred        winmm<elf>
  \-PE	7e530000-7e5b6000	\               winmm
ELF	7e5b6000-7e5e2000	Deferred        ws2_32<elf>
  \-PE	7e5c0000-7e5e2000	\               ws2_32
ELF	7e5e2000-7e64c000	Deferred        msvcrt<elf>
  \-PE	7e5f0000-7e64c000	\               msvcrt
ELF	7e64c000-7e66b000	Deferred        d3dx8<elf>
  \-PE	7e650000-7e66b000	\               d3dx8
ELF	7e66b000-7e688000	Deferred        d3dx9_36<elf>
  \-PE	7e670000-7e688000	\               d3dx9_36
ELF	7e688000-7e6a1000	Deferred        d3dx9_25<elf>
  \-PE	7e690000-7e6a1000	\               d3dx9_25
ELF	7e6a1000-7e7a4000	Export          wined3d<elf>
  \-PE	7e6b0000-7e7a4000	\               wined3d
ELF	7e7a4000-7e7d4000	Export          d3d9<elf>
  \-PE	7e7b0000-7e7d4000	\               d3d9
ELF	7e7d4000-7e81e000	Deferred        dbghelp<elf>
  \-PE	7e7e0000-7e81e000	\               dbghelp
ELF	7e81e000-7e8c0000	Deferred        oleaut32<elf>
  \-PE	7e830000-7e8c0000	\               oleaut32
ELF	7e8c0000-7e8d3000	Deferred        libresolv.so.2
ELF	7e8d6000-7e8eb000	Deferred        psapi<elf>
  \-PE	7e8e0000-7e8eb000	\               psapi
ELF	7e8eb000-7e909000	Deferred        iphlpapi<elf>
  \-PE	7e8f0000-7e909000	\               iphlpapi
ELF	7e909000-7e96a000	Deferred        rpcrt4<elf>
  \-PE	7e920000-7e96a000	\               rpcrt4
ELF	7e96a000-7ea0e000	Deferred        ole32<elf>
  \-PE	7e980000-7ea0e000	\               ole32
ELF	7ea0e000-7eacd000	Deferred        comctl32<elf>
  \-PE	7ea20000-7eacd000	\               comctl32
ELF	7eacd000-7eb26000	Deferred        shlwapi<elf>
  \-PE	7eae0000-7eb26000	\               shlwapi
ELF	7eb26000-7ec39000	Deferred        shell32<elf>
  \-PE	7eb40000-7ec39000	\               shell32
ELF	7ec39000-7ec8b000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec8b000	\               advapi32
ELF	7ec8b000-7ed26000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed26000	\               gdi32
ELF	7ed26000-7ee6d000	Deferred        user32<elf>
  \-PE	7ed40000-7ee6d000	\               user32
ELF	7ef8d000-7ef98000	Deferred        libnss_files.so.2
ELF	7ef98000-7efa2000	Deferred        libnss_nis.so.2
ELF	7efa2000-7efba000	Deferred        libnsl.so.1
ELF	7efba000-7efc3000	Deferred        libnss_compat.so.2
ELF	7efc3000-7efe8000	Deferred        libm.so.6
ELF	b7d21000-b7d25000	Deferred        libdl.so.2
ELF	b7d25000-b7e74000	Deferred        libc.so.6
ELF	b7e75000-b7e8d000	Deferred        libpthread.so.0
ELF	b7ea5000-b7fdb000	Deferred        libwine.so.1
ELF	b7fdd000-b7ff9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\maximb\maxddark\games\heroes5\bin\H5_Game.exe
	0000001b    0
	0000001a    0
	00000019    0
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
00000017 
	00000018    0
Backtrace:
=>1 0x7e6d70c0 IWineD3DDeviceImpl_MarkStateDirty+0x50() in wined3d (0x01c8ee10)
  2 0x7e7411b4 in wined3d (+0x911b4) (0x01c8ee40)
  3 0x7e74a0e5 in wined3d (+0x9a0e5) (0x01c8ef40)
  4 0x7e749268 in wined3d (+0x99268) (0x01c8ef70)
  5 0x7e74f892 in wined3d (+0x9f892) (0x01c8efa0)
  6 0x7e7299a8 in wined3d (+0x799a8) (0x01c8eff0)
  7 0x7e6d354c ActivateContext+0x4fc() in wined3d (0x01c8f070)
  8 0x7e70825b drawPrimitive+0x17b() in wined3d (0x01c8f380)
  9 0x7e6dfd6b in wined3d (+0x2fd6b) (0x01c8f3f0)
  10 0x7e7bac5e in d3d9 (+0xac5e) (0x01c8f420)
maximb@maximb-home:~/maxddark/games/heroes5/bin$ 

```

---

### Post by asdfoo on 2008-09-19
ok - thanks for confirming that.

It looks like you're using an ATI video card?  If that's the case, I suggest you upgrade to the latest drivers that were released two days ago.


Do you know if there's a demo available, I can try it on my machine since I have an nvidia video card, we can rule out if that's the problem.

if not, then a bug report should be filed at [http://bugs.winehq.org](http://bugs.winehq.org)

---

### Post by MaximB on 2008-09-21
> **asdfoo said:**
> ok - thanks for confirming that.

It looks like you're using an ATI video card?  If that's the case, I suggest you upgrade to the latest drivers that were released two days ago.


Do you know if there's a demo available, I can try it on my machine since I have an nvidia video card, we can rule out if that's the problem.

if not, then a bug report should be filed at [http://bugs.winehq.org](http://bugs.winehq.org)

Does anyone managed to run heroes5 with wine ? tell me how please.

---

### Post by cireland0307 on 2008-09-21
> **MaximB said:**
> Does anyone managed to run heroes5 with wine ? tell me how please.

Hey MaximB,

Here's how I got it to work.

Make sure you are using a later version of Wine...such as 1.1...
This goes for the game and all the expansion packs, the same procedure.

1. Install the game using wine as usual.
2. Look for the No-CD (highest version that has a patch).
3. Patch the game up to that version, which for main game is 1.5. You have
   to download the patches.
4. Use the No-CD, not sure if its necessary, but read that it is, and 
   heck, its just easier.
5. Make sure you are playing in a virtual desktop or there is a chance    
   the game will minimize and won't come back. I discovered a lot of 
   games run better that way anyway.

That's it! Now you can rock on!!! :guitar:

---

### Post by MaximB on 2008-09-22
No luck here either.
I get :

> maximb@maximb-home:~$ wine /home/maximb/maxddark/games/heroes5/bin/H5_Game.exe 
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
ERROR: Failed to open file with type descriptions (types.xml)
wine: Unhandled page fault on read access to 0x0000004c at address 0x576e12 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000004c in 32-bit code (0x00576e12).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00576e12 ESP:0032fc20 EBP:0032fc44 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:00e048dc ECX:0032fef8 EDX:1033e320
 ESI:00000000 EDI:00000000
Stack dump:
0x0032fc20:  00000000 10195460 ffffffff 00e048dc
0x0032fc30:  0032fc44 005d460e 00000002 10038650
0x0032fc40:  00000001 1052f318 1052f32e 1052f32f
0x0032fc50:  0067caf5 007be668 10038650 007ce2fd
0x0032fc60:  00000000 00000000 00400000 00000001
0x0032fc70:  00dd52d4 0032fc90 00be8531 00111663
Backtrace:
=>1 0x00576e12 in h5_game (+0x176e12) (0x0032fc44)
  2 0x1052f32e (0x1052f318)
  3 0x5f4a424f (0x5f564441)
0x00576e12: movl	0x4c(%esi),%ecx
Modules:
Module	Address			Debug info	Name (129 modules)
PE	  330000-  36b000	Deferred        libcurl
PE	  370000-  386000	Deferred        zlibwapi
PE	  390000-  3bc000	Deferred        ubistats
PE	  400000- 1183000	Export          h5_game
PE	 12a0000- 1336000	Deferred        fmod
PE	10000000-10013000	Deferred        zlib1
PE	50000000-50086000	Deferred        granny2
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7db41000-7db45000	Deferred        libgpg-error.so.0
ELF	7db45000-7db92000	Deferred        libgcrypt.so.11
ELF	7db92000-7dba2000	Deferred        libtasn1.so.3
ELF	7dba2000-7dba5000	Deferred        libkeyutils.so.1
ELF	7dba5000-7dbad000	Deferred        libkrb5support.so.0
ELF	7dbad000-7dbdf000	Deferred        libcrypt.so.1
ELF	7dbdf000-7dc55000	Deferred        libgnutls.so.13
ELF	7dc55000-7dc78000	Deferred        libk5crypto.so.3
ELF	7dc78000-7dd05000	Deferred        libkrb5.so.3
ELF	7dd05000-7dd2e000	Deferred        libgssapi_krb5.so.2
ELF	7dd2e000-7dd61000	Deferred        libcups.so.2
ELF	7dd79000-7dd8d000	Deferred        midimap<elf>
  \-PE	7dd80000-7dd8d000	\               midimap
ELF	7dd8d000-7de50000	Deferred        libasound.so.2
ELF	7de51000-7de68000	Deferred        msacm32<elf>
  \-PE	7de60000-7de68000	\               msacm32
ELF	7de68000-7de9d000	Deferred        winealsa<elf>
  \-PE	7de70000-7de9d000	\               winealsa
ELF	7decb000-7dece000	Deferred        libcom_err.so.2
ELF	7dee1000-7df14000	Deferred        uxtheme<elf>
  \-PE	7def0000-7df14000	\               uxtheme
ELF	7df14000-7df1d000	Deferred        libxcursor.so.1
ELF	7df1d000-7df22000	Deferred        libxfixes.so.3
ELF	7df22000-7df25000	Deferred        libxcomposite.so.1
ELF	7df25000-7df2b000	Deferred        libxrandr.so.2
ELF	7df2b000-7df33000	Deferred        libxrender.so.1
ELF	7df33000-7df38000	Deferred        libxxf86vm.so.1
ELF	7df38000-7df3b000	Deferred        libxinerama.so.1
ELF	7df3b000-7df5b000	Deferred        imm32<elf>
  \-PE	7df40000-7df5b000	\               imm32
ELF	7df5b000-7df60000	Deferred        libxdmcp.so.6
ELF	7df60000-7df78000	Deferred        libxcb.so.1
ELF	7df78000-7df7b000	Deferred        libxau.so.6
ELF	7df7b000-7e062000	Deferred        libx11.so.6
ELF	7e062000-7e070000	Deferred        libxext.so.6
ELF	7e070000-7e088000	Deferred        libice.so.6
ELF	7e088000-7e090000	Deferred        libsm.so.6
ELF	7e0a8000-7e140000	Deferred        winex11<elf>
  \-PE	7e0c0000-7e140000	\               winex11
ELF	7e17f000-7e1a0000	Deferred        libexpat.so.1
ELF	7e1a0000-7e1ca000	Deferred        libfontconfig.so.1
ELF	7e1ca000-7e1df000	Deferred        libz.so.1
ELF	7e1df000-7e24c000	Deferred        libfreetype.so.6
ELF	7e24c000-7e24e000	Deferred        libxcb-xlib.so.0
ELF	7e264000-7e28b000	Deferred        msacm32<elf>
  \-PE	7e270000-7e28b000	\               msacm32
ELF	7e28b000-7e2a0000	Deferred        psapi<elf>
  \-PE	7e290000-7e2a0000	\               psapi
ELF	7e2a0000-7e2eb000	Deferred        dbghelp<elf>
  \-PE	7e2b0000-7e2eb000	\               dbghelp
ELF	7e2eb000-7e323000	Deferred        dinput<elf>
  \-PE	7e2f0000-7e323000	\               dinput
ELF	7e323000-7e33b000	Deferred        dinput8<elf>
  \-PE	7e330000-7e33b000	\               dinput8
ELF	7e33b000-7e422000	Deferred        oleaut32<elf>
  \-PE	7e350000-7e422000	\               oleaut32
ELF	7e422000-7e4ce000	Deferred        comdlg32<elf>
  \-PE	7e430000-7e4ce000	\               comdlg32
ELF	7e4ce000-7e503000	Deferred        winspool<elf>
  \-PE	7e4e0000-7e503000	\               winspool
ELF	7e503000-7e525000	Deferred        mpr<elf>
  \-PE	7e510000-7e525000	\               mpr
ELF	7e525000-7e574000	Deferred        wininet<elf>
  \-PE	7e530000-7e574000	\               wininet
ELF	7e574000-7e58e000	Deferred        wsock32<elf>
  \-PE	7e580000-7e58e000	\               wsock32
ELF	7e58e000-7e5a7000	Deferred        crtdll<elf>
  \-PE	7e590000-7e5a7000	\               crtdll
ELF	7e5a7000-7e639000	Deferred        winmm<elf>
  \-PE	7e5b0000-7e639000	\               winmm
ELF	7e639000-7e665000	Deferred        ws2_32<elf>
  \-PE	7e640000-7e665000	\               ws2_32
ELF	7e665000-7e684000	Deferred        d3dx8<elf>
  \-PE	7e670000-7e684000	\               d3dx8
ELF	7e684000-7e6a3000	Deferred        d3dx9_36<elf>
  \-PE	7e690000-7e6a3000	\               d3dx9_36
ELF	7e6a3000-7e6bc000	Deferred        d3dx9_25<elf>
  \-PE	7e6b0000-7e6bc000	\               d3dx9_25
ELF	7e6bc000-7e7cc000	Deferred        wined3d<elf>
  \-PE	7e6d0000-7e7cc000	\               wined3d
ELF	7e7cc000-7e7fc000	Deferred        d3d9<elf>
  \-PE	7e7d0000-7e7fc000	\               d3d9
ELF	7e7fc000-7e866000	Deferred        msvcrt<elf>
  \-PE	7e810000-7e866000	\               msvcrt
ELF	7e866000-7e879000	Deferred        libresolv.so.2
ELF	7e87d000-7e891000	Deferred        oleacc<elf>
  \-PE	7e880000-7e891000	\               oleacc
ELF	7e891000-7e8b0000	Deferred        iphlpapi<elf>
  \-PE	7e8a0000-7e8b0000	\               iphlpapi
ELF	7e8b0000-7e915000	Deferred        rpcrt4<elf>
  \-PE	7e8c0000-7e915000	\               rpcrt4
ELF	7e915000-7ea1e000	Deferred        ole32<elf>
  \-PE	7e930000-7ea1e000	\               ole32
ELF	7ea1e000-7eadf000	Deferred        comctl32<elf>
  \-PE	7ea30000-7eadf000	\               comctl32
ELF	7eadf000-7eb39000	Deferred        shlwapi<elf>
  \-PE	7eaf0000-7eb39000	\               shlwapi
ELF	7eb39000-7ec53000	Deferred        shell32<elf>
  \-PE	7eb50000-7ec53000	\               shell32
ELF	7ec53000-7eca7000	Deferred        advapi32<elf>
  \-PE	7ec60000-7eca7000	\               advapi32
ELF	7eca7000-7ed45000	Deferred        gdi32<elf>
  \-PE	7ecc0000-7ed45000	\               gdi32
ELF	7ed45000-7ee8e000	Deferred        user32<elf>
  \-PE	7ed60000-7ee8e000	\               user32
ELF	7efae000-7efb9000	Deferred        libnss_files.so.2
ELF	7efb9000-7efc3000	Deferred        libnss_nis.so.2
ELF	7efc3000-7efe8000	Deferred        libm.so.6
ELF	7efe8000-7f000000	Deferred        libnsl.so.1
ELF	b7ce1000-b7cea000	Deferred        libnss_compat.so.2
ELF	b7ceb000-b7cef000	Deferred        libdl.so.2
ELF	b7cef000-b7e3e000	Deferred        libc.so.6
ELF	b7e3f000-b7e57000	Deferred        libpthread.so.0
ELF	b7e6f000-b7fa5000	Deferred        libwine.so.1
ELF	b7fa7000-b7fc3000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) H:\maxddark\games\heroes5\bin\H5_Game.exe
	0000001a    0
	00000019    0
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
00000017 
	00000018    0
Backtrace:
=>1 0x00576e12 in h5_game (+0x176e12) (0x0032fc44)
  2 0x1052f32e (0x1052f318)
  3 0x5f4a424f (0x5f564441)


---

### Post by asdfoo on 2008-09-22
> **MaximB said:**
> No luck here either.
I get :

Read my earlier response which you have ignored.

---

### Post by MaximB on 2008-09-22
> **asdfoo said:**
> Read my earlier response which you have ignored.

You can download the demo here : 
[http://www.heroesofmightandmagic.com/heroes5/download_heroes_5_demo.shtml](http://www.heroesofmightandmagic.com/heroes5/download_heroes_5_demo.shtml)

Note that I have installed patches up to patch 5 and I also trying to use the No-Cd crack - but still no good.

---

### Post by cireland0307 on 2008-09-22
> **MaximB said:**
> You can download the demo here : 
[http://www.heroesofmightandmagic.com/heroes5/download_heroes_5_demo.shtml](http://www.heroesofmightandmagic.com/heroes5/download_heroes_5_demo.shtml)

Note that I have installed patches up to patch 5 and I also trying to use the No-Cd crack - but still no good.

Hmm...weird, but wine is weird. I can get games to work sometimes and other times not.

Did you install DirectX9? I know people say you don't need it, but a lot of games want it..also the Visual C++ Redistributable should be installed. Try installing both of those from winetricks.

---

### Post by asdfoo on 2008-09-23
> **MaximB said:**
> You can download the demo here : 
[http://www.heroesofmightandmagic.com/heroes5/download_heroes_5_demo.shtml](http://www.heroesofmightandmagic.com/heroes5/download_heroes_5_demo.shtml)

Note that I have installed patches up to patch 5 and I also trying to use the No-Cd crack - but still no good.

MaximB, I downloaded the demo to try for myself.

I think I have found the issue...

Try starting it by doing:

cd ~/.wine/drive_c/Program\ Files\Heroes5\bin
wine H5_Game.exe

---

### Post by MaximB on 2008-09-23
Man....
You have installed heroes5 in the ~/.wine/drive_c/Program Files\Heroes5\ directory.
I have installed it on a different directory.
It's still the same issue.
It won't matter where I install it.

The problem must be elswhere .

---

### Post by asdfoo on 2008-09-23
> **MaximB said:**
> Man....
You have installed heroes5 in the ~/.wine/drive_c/Program Files\Heroes5\ directory.
I have installed it on a different directory.
It's still the same issue.
It won't matter where I install it.

The problem must be elswhere .


The demo works if you run it from the bin directory, if you run it from anywhere else the program gets confused and crashes.

---

### Post by TimothyLuke on 2008-09-23
Just to confirm asdfoo's comment,

I installed the demo in /home/timothy/h5 to do a test

when I used "wine /home/timothy/h5/bin/H5_Game.exe" it failed

when I tried "cd /home/timothy/h5/" and then tried "wine bin/H5_Game.exe" it failed.

when I tried "cd /home/timothy/h5/bin" and then tried "wine H5_Game.exe" it WORKED.

---

### Post by MaximB on 2008-09-24
> **TimothyLuke said:**
> Just to confirm asdfoo's comment,

I installed the demo in /home/timothy/h5 to do a test

when I used "wine /home/timothy/h5/bin/H5_Game.exe" it failed

when I tried "cd /home/timothy/h5/" and then tried "wine bin/H5_Game.exe" it failed.

when I tried "cd /home/timothy/h5/bin" and then tried "wine H5_Game.exe" it WORKED.

Ok, I'll try it with a different program when I get home.
I never tried to install the Demo of Heroes5, but I run the full game the same way you did, from the bin directory.

Maybe it because you use Nvidia and I use ATI ?
I'm really out of suggestions here.

---

### Post by TimothyLuke on 2008-09-24
Could be I have pretty much always used NVidia cards as I have not had a lot of success with ATI cards under linux.  I know ATI is supposed to be more Linux friendly these days....

---

### Post by MaximB on 2008-09-25
> **TimothyLuke said:**
> Could be I have pretty much always used NVidia cards as I have not had a lot of success with ATI cards under linux.  I know ATI is supposed to be more Linux friendly these days....

So I thought ....
That's why I bought an ATI card with my new PC about a month ago.

But it seems like it's an AMD/ATI bug here, a guy at wine forums told me.

Thanks for trying to help me.

---

### Post by Almito on 2008-09-28
Hi,

I had a lot of trouble launching Heroes 5 a few weeks ago (I also have an ATI card).
Though, the problem "solved itself" when I updated the software with the last patches. I was running version 1.41, so I applied patches 1.41 to 1.5 and 1.5 to 1.6.

In the wine configuration, you might also have to make sure that the pixel shader is *not* activated (it made the game not launch at all on my computer).
Plus, I had to overload d3dx9_25 - maybe you already do this.

Let me know if that works for you! :)

---

### Post by MaximB on 2008-09-29
> **Almito said:**
> Hi,

I had a lot of trouble launching Heroes 5 a few weeks ago (I also have an ATI card).
Though, the problem "solved itself" when I updated the software with the last patches. I was running version 1.41, so I applied patches 1.41 to 1.5 and 1.5 to 1.6.

In the wine configuration, you might also have to make sure that the pixel shader is *not* activated (it made the game not launch at all on my computer).
Plus, I had to overload d3dx9_25 - maybe you already do this.

Let me know if that works for you! :)


Thank you very much.
The 1.6 patch did the trick !

But it runs so slow considering the fact that my PC is brand new with ATI Radeon HD 4870 that should run any game without a glitch.

---

### Post by asdfoo on 2008-09-29
> **MaximB said:**
> Thank you very much.
The 1.6 patch did the trick !

But it runs so slow considering the fact that my PC is brand new with ATI Radeon HD 4870 that should run any game without a glitch.


I might be jumping the gun, but it could be those good old linux ATI drivers offering worse performance than nVidia.

You could try setting this registry key which helps some games:

from the commandline, run:

regedit

Now browse to the HKEY_CURRENT_USER / Software / Wine / Direct3D folder.

If the Direct3D key folder does not exist then you can create it yourself:

    * 1. Right-click on the Wine folder icon.
    * 2. Select New > Key from the pop-up menu.
    * 3. Name the new 'folder' key "Direct3D" without the quotes.

Once you find or create the Direct3D key you can enable shaders in Wine:

    * 1. Select the Direct3D key folder icon.
    * 2. Right-click the mouse in the pane to the right to open the right-click menu.
    * 3. Use the right-click menu command New > String Value

Type in: OffscreenRenderingMode

Set its value to: fbo

exit regedit then try to start the game again

---

### Post by Jcas on 2009-03-03
hello
Can you help me too? I understand haw I will start heroes, but he is output*error direct 3d*. But I instaled direct 3d and I did 
*sh winetrick.sh* too.
```
[jirka@amisek bin]$ wine H5_Game.exe 
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
fixme:win:EnumDisplayDevicesW ((null),0,0x1c8f8cc,0x00000000), stub!
[jirka@amisek bin]$ 

```
now i testing with d3d9* in the winecfg/library and there ins`t *error direct3d* in the output, but the game stoping alone.
Where can I download the patch?
How will I known, where is patch for me?
How can I patch will install?
thank

---

