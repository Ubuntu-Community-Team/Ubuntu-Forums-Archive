---
title: "Wine, EQ2, and DirectX oh my!"
date: 2008-03-23
forum: Wine
---

### Post by javafiend on 2008-03-23
I'm trying to get my crack, EQ2, running in Wine.  I've had varying results and the most recent headache is now I'm being told that "EverQuest II requires DirectX 9.0c."  I was under the impression that DirectX was included in Wine. 

I've tried installing the DirectX redistributable, but it doesn't seem to be installing completely.  Dxdiag.exe is nowhere to be found and EQ2 is still not recognizing DirectX.

I'm not sure what to try next.  I've uninstalled Wine, deleted the .wine directory and ran "sudo aptitude purge wine", rebooted and reinstalled numerous times.  Can anyone help?

I'm running Hardy 64-bit beta and Wine 0.9.58.

---

### Post by Chad.S on 2008-03-23
If it's like regular Everquest, it's just checking if a dll is present and throwing that error if it isn't. I fixed this with reg Everquest by downloading and copying d3dx9_30.dll to the main eq game directory.

---

### Post by Faud on 2008-03-24
Nope, dont install directX9.0c, that will screw up Wine. EQ2 should work in WINE out of the box.
When are you getting the error ?

---

### Post by Faud on 2008-03-24
Try here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=358](http://appdb.winehq.org/objectManager.php?sClass=version&iId=358)

---

### Post by javafiend on 2008-03-24
I've been getting the error after the patcher runs or when I just run EverQuest2.exe.  When the game seems to start up, it throws the error.

---

### Post by javafiend on 2008-03-24
Here is the exact error text I get when I try to run wine EverQuest2.exe in terminal:

```

err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"dxdiagn.dll"
err:ole:CoGetClassObject no class object {a65b8071-3bfe-4213-9a5b-491da4461ca7} could be created for context 0x1

```

---

### Post by javafiend on 2008-03-24
Grr...  I got past the dxdiagn.dll problem, sort of, only to get this:

```

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:reg:GetNativeSystemInfo (0x339688) using GetSystemInfo()
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecfc,0x00000000), stub!
wine: Unhandled page fault on read access to 0x00000000 at address 0x7f97c3 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x007f97c3).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:007f97c3 ESP:0033dc54 EBP:00000005 EFLAGS:00210202(   - 00      - -RI1)
 EAX:0033dc64 EBX:04000500 ECX:00000000 EDX:00000500
 ESI:016a1e00 EDI:00010026
Stack dump:
0x0033dc54:  0040e929 0033dc64 00000000 00415501
0x0033dc64:  00000000 04000500 0041568f 004159da
0x0033dc74:  00010026 04000500 0033dccc 7ee023ec
0x0033dc84:  00000001 00581a00 7d835f80 7b88e9ff
0x0033dc94:  0033dcac 00000000 0033dcf4 7eddecca
0x0033dca4:  00010026 00000005 00000000 04000500
Backtrace:
=>1 0x007f97c3 in everquest2 (+0x3f97c3) (0x00000005)
  2 0x00000000 (0x00000000)
0x007f97c3: movl	0x0(%ecx),%eax
Modules:
Module	Address			Debug info	Name (116 modules)
PE	  340000-  3a8000	Deferred        js3250
PE	  3b0000-  3b8000	Deferred        plc4
PE	  3c0000-  3c6000	Deferred        plds4
PE	  400000- 10e4000	Export          everquest2
PE	 3620000- 37d5000	Deferred        dxdiagn
PE	10000000-1063b000	Deferred        xul
PE	21100000-2118c000	Deferred        mss32
PE	30000000-30028000	Deferred        nspr4
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
ELF	7d077000-7db8c000	Deferred        libglcore.so.1
ELF	7db8c000-7dc30000	Deferred        libgl.so.1
ELF	7dc30000-7dc79000	Deferred        dsound<elf>
  \-PE	7dc40000-7dc79000	\               dsound
ELF	7ddef000-7de04000	Deferred        psapi<elf>
  \-PE	7ddf0000-7de04000	\               psapi
ELF	7de04000-7de4e000	Deferred        dbghelp<elf>
  \-PE	7de10000-7de4e000	\               dbghelp
ELF	7de4e000-7de52000	Deferred        libgpg-error.so.0
ELF	7de52000-7de9f000	Deferred        libgcrypt.so.11
ELF	7de9f000-7deaf000	Deferred        libtasn1.so.3
ELF	7deaf000-7deb7000	Deferred        libkrb5support.so.0
ELF	7deb7000-7dee9000	Deferred        libcrypt.so.1
ELF	7dee9000-7df5e000	Deferred        libgnutls.so.13
ELF	7df5e000-7df82000	Deferred        libk5crypto.so.3
ELF	7df82000-7e012000	Deferred        libkrb5.so.3
ELF	7e012000-7e03b000	Deferred        libgssapi_krb5.so.2
ELF	7e03b000-7e06f000	Deferred        libcups.so.2
ELF	7e06f000-7e083000	Deferred        midimap<elf>
  \-PE	7e070000-7e083000	\               midimap
ELF	7e083000-7e0a9000	Deferred        msacm32<elf>
  \-PE	7e090000-7e0a9000	\               msacm32
ELF	7e0a9000-7e0c0000	Deferred        msacm32<elf>
  \-PE	7e0b0000-7e0c0000	\               msacm32
ELF	7e0c0000-7e183000	Deferred        libasound.so.2
ELF	7e196000-7e1cc000	Deferred        winealsa<elf>
  \-PE	7e1a0000-7e1cc000	\               winealsa
ELF	7e216000-7e248000	Deferred        uxtheme<elf>
  \-PE	7e220000-7e248000	\               uxtheme
ELF	7e248000-7e251000	Deferred        libxcursor.so.1
ELF	7e251000-7e256000	Deferred        libxfixes.so.3
ELF	7e256000-7e259000	Deferred        libxcomposite.so.1
ELF	7e259000-7e25f000	Deferred        libxrandr.so.2
ELF	7e25f000-7e267000	Deferred        libxrender.so.1
ELF	7e267000-7e26a000	Deferred        libxinerama.so.1
ELF	7e26a000-7e26f000	Deferred        libxdmcp.so.6
ELF	7e26f000-7e287000	Deferred        libxcb.so.1
ELF	7e287000-7e289000	Deferred        libxcb-xlib.so.0
ELF	7e289000-7e28c000	Deferred        libxau.so.6
ELF	7e28c000-7e377000	Deferred        libx11.so.6
ELF	7e377000-7e385000	Deferred        libxext.so.6
ELF	7e385000-7e38a000	Deferred        libxxf86vm.so.1
ELF	7e38a000-7e38d000	Deferred        libkeyutils.so.1
ELF	7e396000-7e398000	Deferred        libnvidia-tls.so.1
ELF	7e398000-7e39b000	Deferred        libcom_err.so.2
ELF	7e39d000-7e42d000	Deferred        winex11<elf>
  \-PE	7e3b0000-7e42d000	\               winex11
ELF	7e465000-7e486000	Deferred        libexpat.so.1
ELF	7e486000-7e4b0000	Deferred        libfontconfig.so.1
ELF	7e4b0000-7e4c5000	Deferred        libz.so.1
ELF	7e4c5000-7e535000	Deferred        libfreetype.so.6
ELF	7e535000-7e5d7000	Deferred        oleaut32<elf>
  \-PE	7e550000-7e5d7000	\               oleaut32
ELF	7e5d7000-7e5f4000	Deferred        imm32<elf>
  \-PE	7e5e0000-7e5f4000	\               imm32
ELF	7e5f4000-7e6ec000	Deferred        wined3d<elf>
  \-PE	7e610000-7e6ec000	\               wined3d
ELF	7e6ec000-7e71c000	Deferred        d3d9<elf>
  \-PE	7e6f0000-7e71c000	\               d3d9
ELF	7e71c000-7e7be000	Deferred        comdlg32<elf>
  \-PE	7e720000-7e7be000	\               comdlg32
ELF	7e7be000-7e7f3000	Deferred        winspool<elf>
  \-PE	7e7d0000-7e7f3000	\               winspool
ELF	7e7f3000-7e853000	Deferred        rpcrt4<elf>
  \-PE	7e800000-7e853000	\               rpcrt4
ELF	7e853000-7e8f7000	Deferred        ole32<elf>
  \-PE	7e860000-7e8f7000	\               ole32
ELF	7e8f7000-7e985000	Deferred        winmm<elf>
  \-PE	7e900000-7e985000	\               winmm
ELF	7e985000-7e998000	Deferred        libresolv.so.2
ELF	7e9ab000-7e9c9000	Deferred        iphlpapi<elf>
  \-PE	7e9b0000-7e9c9000	\               iphlpapi
ELF	7e9c9000-7e9f5000	Deferred        ws2_32<elf>
  \-PE	7e9d0000-7e9f5000	\               ws2_32
ELF	7e9f5000-7ea0f000	Deferred        wsock32<elf>
  \-PE	7ea00000-7ea0f000	\               wsock32
ELF	7ea0f000-7eace000	Deferred        comctl32<elf>
  \-PE	7ea20000-7eace000	\               comctl32
ELF	7eace000-7eb27000	Deferred        shlwapi<elf>
  \-PE	7eae0000-7eb27000	\               shlwapi
ELF	7eb27000-7ec2f000	Deferred        shell32<elf>
  \-PE	7eb40000-7ec2f000	\               shell32
ELF	7ec2f000-7ec7b000	Deferred        advapi32<elf>
  \-PE	7ec40000-7ec7b000	\               advapi32
ELF	7ec7b000-7ed16000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed16000	\               gdi32
ELF	7ed16000-7ee58000	Deferred        user32<elf>
  \-PE	7ed30000-7ee58000	\               user32
ELF	7ee58000-7ee6c000	Deferred        lz32<elf>
  \-PE	7ee60000-7ee6c000	\               lz32
ELF	7ee6c000-7ee85000	Deferred        version<elf>
  \-PE	7ee70000-7ee85000	\               version
ELF	7efa5000-7efb0000	Deferred        libnss_files.so.2
ELF	7efb0000-7efc8000	Deferred        libnsl.so.1
ELF	7efc8000-7efed000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	f7c81000-f7c8a000	Deferred        libnss_compat.so.2
ELF	f7c8b000-f7c8f000	Deferred        libdl.so.2
ELF	f7c8f000-f7dde000	Deferred        libc.so.6
ELF	f7ddf000-f7df7000	Deferred        libpthread.so.0
ELF	f7e0a000-f7f1f000	Deferred        libwine.so.1
ELF	f7f21000-f7f40000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Sony\EverQuest II\EverQuest2.exe
	00000013    0
	00000009    0 <==
0000000a 
	0000000b    0
0000000c 
	0000000f    0
	0000000e    0
	0000000d    0
00000010 
	00000012    0
	00000011    0
Backtrace:
=>1 0x007f97c3 in everquest2 (+0x3f97c3) (0x00000005)
  2 0x00000000 (0x00000000)

```

Would this have anything to do with running 64-bit OS?

---

### Post by javafiend on 2008-03-24
Woohoo!!! It's finally working!

There are some problems, however.  It crashes whenever I try to update any of the graphic settings.

I did end up installing DirectX with Wine-Doors and then deleted my eq2.ini, eq2_default.ini, and eq2_recent.ini files.  Then I did a full file scan with the patcher.

Does any of that help pin down my current problem?

---

