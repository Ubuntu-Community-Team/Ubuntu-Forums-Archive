---
title: "[SOLVED] How can I make Ragnarok working?"
date: 2008-02-29
forum: Wine
---

### Post by Lukasz Tarkowski on 2008-02-29
I would like to know how I can get ragnarok to work in Ubuntu/Gutsy 7.10?
I tried with wine and I get an direct3d error
I have Ati Radeon 200m Intergrated MotherBoard Amd Athlon :)
I hope that there are free applications for that game or whatever it is called hehe :)

---

### Post by Lukasz Tarkowski on 2008-02-29
By the way if I try to install WineCVS I get test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected

/home/lukasz/WineCVS

---

### Post by Kilz on 2008-03-01
> **Lukasz Tarkowski said:**
> By the way if I try to install WineCVS I get test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected

/home/lukasz/WineCVS

[http://appdb.winehq.org/appview.php?iVersionId=928](http://appdb.winehq.org/appview.php?iVersionId=928)

---

### Post by Lukasz Tarkowski on 2008-03-01
That link didn't help much I get this
```
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0040e8c2 ESP:0034fabc EBP:003e0b80 EFLAGS:00010202(   - 00      - -RI1)
 EAX:003e0b80 EBX:7b820000 ECX:00000001 EDX:00090b80
 ESI:7b820040 EDI:00350000
Stack dump:
0x0034fabc:  0065011c 0034fd01 00000186 004001f0
0x0034facc:  00090b80 7b865090 00411601 00109000
0x0034fadc:  0000027b 0034fb0c 0034fd7c 00000000
0x0034faec:  00000001 0041176b 0034fb18 00411788
0x0034fafc:  0034fb0c 00400000 0065011c 0041425c
0x0034fb0c:  0034fd44 004140b5 0042169d 0034fef8
Backtrace:
=>1 0x0040e8c2 in rebirthro (+0xe8c2) (0x003e0b80)
  2 0x00000000 (0x00000000)
0x0040e8c2: movl        0x1c(%ebp),%edx
Modules:
Module  Address                 Debug info      Name (54 modules)
PE        400000-  42c000       Export          rebirthro
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c80d000-7c812000       Deferred        libxfixes.so.3
ELF     7c812000-7c81b000       Deferred        libxcursor.so.1
ELF     7c81b000-7c838000       Deferred        imm32<elf>
  \-PE  7c820000-7c838000       \               imm32
ELF     7c838000-7c840000       Deferred        libxrender.so.1
ELF     7cba6000-7cbac000       Deferred        libxrandr.so.2
ELF     7d6b7000-7d6c0000       Deferred        librt.so.1
ELF     7d6c0000-7e6f6000       Deferred        fglrx_dri.so
ELF     7e6f6000-7e701000       Deferred        libgcc_s.so.1
ELF     7e701000-7e77b000       Deferred        libgl.so.1
ELF     7e77b000-7e780000       Deferred        libxdmcp.so.6
ELF     7e780000-7e783000       Deferred        libxau.so.6
ELF     7e783000-7e874000       Deferred        libx11.so.6
ELF     7e874000-7e882000       Deferred        libxext.so.6
ELF     7e882000-7e887000       Deferred        libxxf86vm.so.1
ELF     7e887000-7e89f000       Deferred        libice.so.6
ELF     7e89f000-7e8a7000       Deferred        libsm.so.6
ELF     7e8b5000-7e940000       Deferred        winex11<elf>
  \-PE  7e8c0000-7e940000       \               winex11
ELF     7e9b8000-7e9d8000       Deferred        libexpat.so.1
ELF     7e9d8000-7ea03000       Deferred        libfontconfig.so.1
ELF     7ea03000-7ea18000       Deferred        libz.so.1
ELF     7ea18000-7ea88000       Deferred        libfreetype.so.6
ELF     7ea88000-7ea9b000       Deferred        libresolv.so.2
ELF     7eaa9000-7eac7000       Deferred        iphlpapi<elf>
  \-PE  7eab0000-7eac7000       \               iphlpapi
ELF     7eac7000-7eb20000       Deferred        rpcrt4<elf>
  \-PE  7ead0000-7eb20000       \               rpcrt4
ELF     7eb20000-7ebc1000       Deferred        ole32<elf>
  \-PE  7eb30000-7ebc1000       \               ole32
ELF     7ebc1000-7ec5f000       Deferred        oleaut32<elf>
  \-PE  7ebd0000-7ec5f000       \               oleaut32
ELF     7ec5f000-7eca8000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca8000       \               advapi32
ELF     7eca8000-7ed43000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed43000       \               gdi32
ELF     7ed43000-7ee81000       Deferred        user32<elf>
  \-PE  7ed60000-7ee81000       \               user32
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca8000-b7cac000       Deferred        libdl.so.2
ELF     b7cac000-b7df6000       Deferred        libc.so.6
ELF     b7df7000-b7e0f000       Deferred        libpthread.so.0
ELF     b7e1d000-b7f31000       Deferred        libwine.so.1
ELF     b7f33000-b7f4f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000039 
        0000003a    0
00000037 (D) C:\Program Files\RebirthRO\RebirthRO.exe
        00000038    0 <==
00000033 
        00000034    0
00000027 
        00000028    0
00000021 
        00000022    0
0000001b 
        0000001c    0
00000016 
        00000018    0
        00000017    0
00000010 
        00000011    0
0000000a 
        0000000b    0

```
WINEDEBUG=-all wine RebrithRO.exe Didn't work

---

### Post by Major_Kong on 2008-03-05
Same here.

But decided to try running RebirthRO.bin and got this output:

> fixme:win:EnumDisplayDevicesW ((null),0,0x34f5f4,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:d3d7:IDirect3DImpl_7_CreateDevice The application wants to create a Direct3D device, but non-opengl surfaces are set in the registry. Please set the surface implementation to opengl or autodetection to allow 3D rendering


And a error box saying: "Cannot init d3d OR grf file has problem."

---

### Post by Major_Kong on 2008-03-08
bump

---

### Post by Major_Kong on 2008-04-12
Still nothing ?

Apart from the patcher, the only error trying to run the client is this:
> err:d3d7:IDirect3DImpl_7_CreateDevice The application wants to create a Direct3D device, but non-opengl surfaces are set in the registry. Please set the surface implementation to opengl or autodetection to allow 3D rendering


---

### Post by Lukasz Tarkowski on 2008-04-12
Sorry 
I had uninstalled Ubuntu.
I had to take a break.
I installed Ubuntu again from clean install hehe.
I am getting a new laptop soon with Vista, I am gonna still have Ubuntu on External Hdd just different graphic card.
I have Ati 128mb not enough at this moment
Not sure when I will be able to install Ragnarok again hehe

---

### Post by Lukasz Tarkowski on 2008-04-13
It doesn't work now :(
I get d3d init error on BlackOut RO

---

### Post by Major_Kong on 2008-05-13
RESOLVED THE D3D ERROR !

You have to run regedit, and then go to HKEY_CURRENT_USER > Software > Wine > Direct3D, and change the value of DirectDrawRenderer to 'opengl' or 'autodetection' (without the apostrophe).

Now if i only could get it to connect to the server... Any ideas ???

EDIT: I'm using the RebirthRO client, so results may differ.

---

### Post by Lukasz Tarkowski on 2008-05-13
Well For now I am gonna use the disk for something else so sorry but good to know :)
Maybe once they fix those errors hehe.
I am not sure when I will install Ubuntu again
Thank You

---

### Post by Major_Kong on 2008-05-14
Well, the 'error' is fixed in the client. The problem now *only* lies in the patcher.
Apart from the client not connecting... but that could be a RebirthRO specific problem.

---

### Post by danielmaiarn on 2008-07-02
Well, i'm trying to get Ragnarok to do a simple update, but the only thing that i got is my cursor blink once and puff the Wine window closes....when a run on terminal i see this msg:

wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x402052 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x7bc457ec).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc457ec ESP:0032e6a4 EBP:0032e708 EFLAGS:00000206(   - 00      - -IP1)
 EAX:0000194e EBX:7bc88444 ECX:0013ab58 EDX:0011004c
 ESI:0032e6b0 EDI:00000001
Stack dump:
0x0032e6a4:  0001002a 00000000 00000000 80000100
0x0032e6b4:  00000001 00000000 00402052 00000002
0x0032e6c4:  0041c8aa 0000194e 00000002 00000001
0x0032e6d4:  7eddae80 7edbb568 00110014 7e97b640
0x0032e6e4:  ffffffff 00000001 0032e70c 7e95da67
0x0032e6f4:  00110000 00000000 000004c8 7ec63620
Backtrace:
=>1 0x7bc457ec in ntdll (+0x357ec) (0x0032e708)
0x7bc457ec: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (66 modules)
PE	  400000-  424000	Deferred        ragnarok
PE	5f400000-5f4ed000	Deferred        mfc42
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b930000	Deferred        kernel32<elf>
  \-PE	7b820000-7b930000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e445000-7e458000	Deferred        libresolv.so.2
ELF	7e46c000-7e48a000	Deferred        iphlpapi<elf>
  \-PE	7e470000-7e48a000	\               iphlpapi
ELF	7e48a000-7e4ec000	Deferred        rpcrt4<elf>
  \-PE	7e4a0000-7e4ec000	\               rpcrt4
ELF	7e4ec000-7e590000	Deferred        ole32<elf>
  \-PE	7e500000-7e590000	\               ole32
ELF	7e5b8000-7e5eb000	Deferred        uxtheme<elf>
  \-PE	7e5c0000-7e5eb000	\               uxtheme
ELF	7e5eb000-7e5f4000	Deferred        libxcursor.so.1
ELF	7e5f4000-7e5f9000	Deferred        libxfixes.so.3
ELF	7e5f9000-7e5fc000	Deferred        libxcomposite.so.1
ELF	7e5fc000-7e602000	Deferred        libxrandr.so.2
ELF	7e602000-7e60a000	Deferred        libxrender.so.1
ELF	7e60a000-7e60d000	Deferred        libxinerama.so.1
ELF	7e60d000-7e62d000	Deferred        imm32<elf>
  \-PE	7e610000-7e62d000	\               imm32
ELF	7e62d000-7e632000	Deferred        libxdmcp.so.6
ELF	7e632000-7e64a000	Deferred        libxcb.so.1
ELF	7e64a000-7e64d000	Deferred        libxau.so.6
ELF	7e64d000-7e734000	Deferred        libx11.so.6
ELF	7e734000-7e742000	Deferred        libxext.so.6
ELF	7e742000-7e747000	Deferred        libxxf86vm.so.1
ELF	7e75b000-7e7f2000	Deferred        winex11<elf>
  \-PE	7e770000-7e7f2000	\               winex11
ELF	7e835000-7e856000	Deferred        libexpat.so.1
ELF	7e856000-7e880000	Deferred        libfontconfig.so.1
ELF	7e894000-7e8a9000	Deferred        libz.so.1
ELF	7e8a9000-7e919000	Deferred        libfreetype.so.6
ELF	7e92d000-7e997000	Deferred        msvcrt<elf>
  \-PE	7e940000-7e997000	\               msvcrt
ELF	7e9b1000-7ea70000	Deferred        comctl32<elf>
  \-PE	7e9c0000-7ea70000	\               comctl32
ELF	7ea70000-7eb85000	Deferred        shell32<elf>
  \-PE	7ea80000-7eb85000	\               shell32
ELF	7eb85000-7ebde000	Deferred        shlwapi<elf>
  \-PE	7eb90000-7ebde000	\               shlwapi
ELF	7ebde000-7ec30000	Deferred        advapi32<elf>
  \-PE	7ebf0000-7ec30000	\               advapi32
ELF	7ec30000-7ecce000	Deferred        gdi32<elf>
  \-PE	7ec40000-7ecce000	\               gdi32
ELF	7ecce000-7ee15000	Deferred        user32<elf>
  \-PE	7ecf0000-7ee15000	\               user32
ELF	7ee15000-7ee36000	Deferred        mpr<elf>
  \-PE	7ee20000-7ee36000	\               mpr
ELF	7ee36000-7ee84000	Deferred        wininet<elf>
  \-PE	7ee40000-7ee84000	\               wininet
ELF	7efa4000-7efaf000	Deferred        libnss_files.so.2
ELF	7efaf000-7efc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7efed000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7c40000-f7c42000	Deferred        libxcb-xlib.so.0
ELF	f7c47000-f7c4b000	Deferred        libdl.so.2
ELF	f7c4b000-f7d9a000	Deferred        libc.so.6
ELF	f7d9a000-f7db2000	Deferred        libpthread.so.0
ELF	f7dc7000-f7efd000	Deferred        libwine.so.1
ELF	f7eff000-f7f1e000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Arquivos de programas\Gravity\RO\Ragnarok.exe
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
=>1 0x7bc457ec in ntdll (+0x357ec) (0x0032e708)
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting

===================================================================================
any idea??? I already try install even DX 10 for XP....nothing worked

---

### Post by Lukasz Tarkowski on 2009-01-21
I don't think you can patch the Ragnarok in Ubuntu :(
You have to patch it in Windows and copy the extracted files to Ubuntu somehow :D

---

