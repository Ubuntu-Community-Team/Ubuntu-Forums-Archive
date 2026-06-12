---
title: "Spore Galactic Adventures Wine"
date: 2012-01-27
forum: Wine
---

### Post by mnorgate on 2012-01-27
I am trying to get Spore to work under WINE. I have installed the game plus the Galactic Adventures expansion without any problems, but when I try to run it I get a black screen and an error box stating 

"The program SporeApp.exe has encountered a serious problem and need to exit"

Below is the output from the terminal. Any ideas on what might be causing this. I have update the graphics drivers already to the latest version available on the NVidia site

```

fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
fixme:advapi:RegisterTraceGuidsW (0x3d24d0, 0x3dd6e8, {7c830ece-5fb3-417a-a1bd-508f45277356}, 1, 0x33fac4, (null), (null), 0x3dd6f0,): stub
fixme:thread:SetThreadIdealProcessor (0x8c): stub
fixme:thread:SetThreadIdealProcessor (0x94): stub
fixme:thread:SetThreadIdealProcessor (0x9c): stub
fixme:thread:SetThreadIdealProcessor (0xa4): stub
fixme:mountmgr:harddisk_ioctl returning zero-filled buffer for IOCTL_VOLUME_GET_VOLUME_DISK_EXTENTS
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:wtsapi:WTSQuerySessionInformationW Stub (nil) 0xffffffff 5 0xddd780 0xddd784
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0xb55ad8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0xdde990)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\Origin\\Logs\\EALogReader.html" 1 4 (nil) (nil) 0xb5c700 (nil)
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 4124 (SPI_GETMOUSESONAR)
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee30,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:thread:SetThreadIdealProcessor (0x118): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x3004a, 0x14f110): stub
fixme:dbghelp:elf_search_auxv can't find symbol in module
wine: Unhandled page fault on read access to 0x00000000 at address 0x7f0738 (thread 0022), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x007f0738).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:007f0738 ESP:0033f414 EBP:00000000 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:07e2c2f0 ECX:00000000 EDX:00000000
 ESI:07e410a0 EDI:07e41230
Stack dump:
0x0033f414:  00000000 07e410a0 07d7224c 0262c12c
0x0033f424:  07e410a0 007ef4b3 00000000 0033fdcc
0x0033f434:  0262c0f0 02624358 07e3d9c0 00000400
0x0033f444:  00000300 00000000 00000000 00000001
0x0033f454:  00000000 3fcce460 3f800000 00f1c3e1
0x0033f464:  0033fe90 00000000 0033fdcc 0262c0f0
Backtrace:
0x007f0738: movl	0x0(%ecx),%eax
Modules:
Module	Address			Debug info	Name (126 modules)
PE	  3d0000-  3e2000	Deferred        xinput9_1_0
PE	  400000- 1cc6000	Export          sporeapp
PE	 1cd0000- 1f1f000	Deferred        d3dx9_27
PE	10000000-10055000	Deferred        dmcmdportalclient
PE	78000000-78044000	Deferred        msvcrt
PE	78520000-785c3000	Deferred        msvcr90
ELF	79bec000-7b800000	Deferred        libnvidia-glcore.so.290.10
ELF	7b800000-7b9a8000	Deferred        kernel32<elf>
  \-PE	7b810000-7b9a8000	\               kernel32
ELF	7bc00000-7bcc3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7cbdf000-7cbf3000	Deferred        msimg32<elf>
  \-PE	7cbe0000-7cbf3000	\               msimg32
ELF	7d580000-7d657000	Deferred        libgl.so.1
ELF	7d657000-7d692000	Deferred        dinput<elf>
  \-PE	7d660000-7d692000	\               dinput
ELF	7d7d6000-7d7f4000	Deferred        libgcc_s.so.1
ELF	7d801000-7d81c000	Deferred        rasapi32<elf>
  \-PE	7d810000-7d81c000	\               rasapi32
ELF	7d81c000-7d90e000	Deferred        oleaut32<elf>
  \-PE	7d830000-7d90e000	\               oleaut32
ELF	7d90e000-7d929000	Deferred        spoolss<elf>
  \-PE	7d910000-7d929000	\               spoolss
ELF	7d929000-7d932000	Deferred        librt.so.1
ELF	7d932000-7d937000	Deferred        libgpg-error.so.0
ELF	7d937000-7d93b000	Deferred        libkeyutils.so.1
ELF	7d93b000-7d984000	Deferred        libdbus-1.so.3
ELF	7d984000-7da09000	Deferred        libgcrypt.so.11
ELF	7da09000-7da1b000	Deferred        libtasn1.so.3
ELF	7da1b000-7da44000	Deferred        libk5crypto.so.3
ELF	7da44000-7db0d000	Deferred        libkrb5.so.3
ELF	7db0d000-7db20000	Deferred        libavahi-client.so.3
ELF	7db20000-7dbd0000	Deferred        libgnutls.so.26
ELF	7dbd0000-7dc0e000	Deferred        libgssapi_krb5.so.2
ELF	7dc0e000-7dc60000	Deferred        libcups.so.2
ELF	7dc63000-7dc67000	Deferred        libnvidia-tls.so.290.10
ELF	7dc67000-7dc88000	Deferred        localspl<elf>
  \-PE	7dc70000-7dc88000	\               localspl
ELF	7dc88000-7dcc1000	Deferred        winspool<elf>
  \-PE	7dc90000-7dcc1000	\               winspool
ELF	7dcc1000-7dd25000	Deferred        setupapi<elf>
  \-PE	7dcd0000-7dd25000	\               setupapi
ELF	7ddf2000-7de26000	Deferred        uxtheme<elf>
  \-PE	7de00000-7de26000	\               uxtheme
ELF	7de26000-7de2c000	Deferred        libxfixes.so.3
ELF	7de2c000-7de37000	Deferred        libxcursor.so.1
ELF	7de37000-7de47000	Deferred        libxi.so.6
ELF	7de47000-7de4b000	Deferred        libxcomposite.so.1
ELF	7de4b000-7de54000	Deferred        libxrandr.so.2
ELF	7de54000-7de5f000	Deferred        libxrender.so.1
ELF	7de5f000-7de65000	Deferred        libxxf86vm.so.1
ELF	7de65000-7de69000	Deferred        libxinerama.so.1
ELF	7de69000-7de70000	Deferred        libxdmcp.so.6
ELF	7de70000-7de8f000	Deferred        libxcb.so.1
ELF	7de8f000-7de95000	Deferred        libuuid.so.1
ELF	7de95000-7dfcb000	Deferred        libx11.so.6
ELF	7dfcb000-7dfe5000	Deferred        libice.so.6
ELF	7dfe5000-7dfee000	Deferred        libsm.so.6
ELF	7dff0000-7dff9000	Deferred        libkrb5support.so.0
ELF	7dff9000-7e007000	Deferred        libavahi-common.so.3
ELF	7e010000-7e014000	Deferred        libcom_err.so.2
ELF	7e016000-7e0bd000	Deferred        winex11<elf>
  \-PE	7e020000-7e0bd000	\               winex11
ELF	7e127000-7e151000	Deferred        libexpat.so.1
ELF	7e151000-7e186000	Deferred        libfontconfig.so.1
ELF	7e186000-7e19b000	Deferred        libz.so.1
ELF	7e19b000-7e232000	Deferred        libfreetype.so.6
ELF	7e234000-7e247000	Deferred        libxext.so.6
ELF	7e25a000-7e38e000	Deferred        wined3d<elf>
  \-PE	7e270000-7e38e000	\               wined3d
ELF	7e38e000-7e3c6000	Deferred        d3d9<elf>
  \-PE	7e390000-7e3c6000	\               d3d9
ELF	7e3c6000-7e40d000	Deferred        dsound<elf>
  \-PE	7e3d0000-7e40d000	\               dsound
ELF	7e40d000-7e46a000	Deferred        dbghelp<elf>
  \-PE	7e410000-7e46a000	\               dbghelp
ELF	7e46a000-7e49b000	Deferred        usp10<elf>
  \-PE	7e470000-7e49b000	\               usp10
ELF	7e49b000-7e4bd000	Deferred        imm32<elf>
  \-PE	7e4a0000-7e4bd000	\               imm32
ELF	7e4bd000-7e4d8000	Deferred        dinput8<elf>
  \-PE	7e4c0000-7e4d8000	\               dinput8
ELF	7e4d8000-7e5cd000	Deferred        comctl32<elf>
  \-PE	7e4e0000-7e5cd000	\               comctl32
ELF	7e5cd000-7e636000	Deferred        shlwapi<elf>
  \-PE	7e5e0000-7e636000	\               shlwapi
ELF	7e636000-7e846000	Deferred        shell32<elf>
  \-PE	7e640000-7e846000	\               shell32
ELF	7e846000-7e85d000	Deferred        libresolv.so.2
ELF	7e871000-7e885000	Deferred        psapi<elf>
  \-PE	7e880000-7e885000	\               psapi
ELF	7e885000-7e8a7000	Deferred        iphlpapi<elf>
  \-PE	7e890000-7e8a7000	\               iphlpapi
ELF	7e8a7000-7e8d9000	Deferred        ws2_32<elf>
  \-PE	7e8b0000-7e8d9000	\               ws2_32
ELF	7e8d9000-7e8f4000	Deferred        wsock32<elf>
  \-PE	7e8e0000-7e8f4000	\               wsock32
ELF	7e8f4000-7e91d000	Deferred        msacm32<elf>
  \-PE	7e900000-7e91d000	\               msacm32
ELF	7e91d000-7e992000	Deferred        rpcrt4<elf>
  \-PE	7e930000-7e992000	\               rpcrt4
ELF	7e992000-7ea98000	Deferred        ole32<elf>
  \-PE	7e9b0000-7ea98000	\               ole32
ELF	7ea98000-7eaf8000	Deferred        advapi32<elf>
  \-PE	7eaa0000-7eaf8000	\               advapi32
ELF	7eaf8000-7eb9d000	Deferred        gdi32<elf>
  \-PE	7eb00000-7eb9d000	\               gdi32
ELF	7eb9d000-7ecda000	Deferred        user32<elf>
  \-PE	7ebb0000-7ecda000	\               user32
ELF	7ecda000-7ed7c000	Deferred        winmm<elf>
  \-PE	7ece0000-7ed7c000	\               winmm
ELF	7ed7c000-7ed89000	Deferred        libnss_files.so.2
ELF	7ed89000-7ed95000	Deferred        libnss_nis.so.2
ELF	7ed95000-7edae000	Deferred        libnsl.so.1
ELF	7efae000-7efd8000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f73fa000-f73ff000	Deferred        libdl.so.2
ELF	f73ff000-f7579000	Deferred        libc.so.6
ELF	f757a000-f7595000	Deferred        libpthread.so.0
ELF	f7595000-f7599000	Deferred        libxau.so.6
ELF	f75b2000-f75bc000	Deferred        libnss_compat.so.2
ELF	f75bd000-f76ff000	Dwarf           libwine.so.1
ELF	f7701000-f7721000	Deferred        ld-linux.so.2
ELF	f7721000-f7722000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 explorer.exe
	00000009    0
0000000e services.exe
	0000001b    0
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000013    0
	00000012    0
00000018 plugplay.exe
	0000001c    0
	0000001a    0
	00000019    0
00000021 (D) C:\Program Files\Electronic Arts\SPORE_EP1\SporebinEP1\SporeApp.exe
	00000035    0
	00000034    0
	00000026    0
	00000025    0
	00000024    0
	00000023    0
	00000022    0 <==
0000002a EACoreServer.exe
	00000031    1
	00000030    1
	0000002f    0
	0000002e    2
	0000002d    2
	0000002b    0
Backtrace:
fixme:dbghelp:elf_search_auxv can't find symbol in module
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xf74769f6
wine client error:22: write: Bad file descriptor


```

---

