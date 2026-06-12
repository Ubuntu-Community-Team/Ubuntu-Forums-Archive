---
title: "starcraft bw crashes upon connecting to battle.net"
date: 2008-07-24
forum: Wine
---

### Post by ryan86corolla on 2008-07-24
i had starcraft working fine, but i reinstalled ubuntu and when i installed starcraft again, now it doesn't work. :(

i installed starcraft, installed broodwar, and installed the latest update (1.15.2). starcraft starts fine, but when i connect to battle.net, as soon as it gets to the login page it crashes. here's what terminal says:

```
$ wine .wine/drive_c/Program\ Files/Starcraft/StarCraft.exe 
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f410,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x128f00)->(1,(nil)): Stub
fixme:ras:RasEnumConnectionsA (0x1fa0094,0x33f7cc,0x33f7e0),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
wine: Unhandled page fault on write access to 0x011bc000 at address 0x1b40148 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x011bc000 in 32-bit code (0x01b40148).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:01b40148 ESP:0033e434 EBP:0033e540 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00cff200 EBX:00000000 ECX:00000001 EDX:00000000
 ESI:026c796f EDI:011bc000
Stack dump:
0x0033e434:  003e01cc 00000003 0033e50c 00000000
0x0033e444:  000001d8 0033e494 0000005a 1505ed34
0x0033e454:  1505ed34 0000005a 026c5fd8 00000005
0x0033e464:  00000000 150291c0 7e186abb 7e1efc84
0x0033e474:  00000002 150291c0 150291e0 00000029
0x0033e484:  00000002 000002a2 000000a6 003a1be0
Backtrace:
=>1 0x01b40148 (0x0033e540)
0x01b40148: movb	%al,0x0(%edi)
Modules:
Module	Address			Debug info	Name (113 modules)
PE	  400000-  6ec000	Deferred        starcraft
PE	 2000000- 2011000	Deferred        local
PE	10000000-1001a000	Deferred        smackw32
PE	15000000-15069000	Deferred        storm
PE	19000000-19089000	Deferred        battle.snp
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c2df000-7c2ea000	Deferred        libgcc_s.so.1
ELF	7c3fb000-7c414000	Deferred        rasapi32<elf>
  \-PE	7c400000-7c414000	\               rasapi32
ELF	7c414000-7c440000	Deferred        ws2_32<elf>
  \-PE	7c420000-7c440000	\               ws2_32
ELF	7c7a8000-7c7ae000	Deferred        libnss_dns.so.2
ELF	7c7b9000-7c7d3000	Deferred        wsock32<elf>
  \-PE	7c7c0000-7c7d3000	\               wsock32
ELF	7c7d3000-7c7e7000	Deferred        midimap<elf>
  \-PE	7c7e0000-7c7e7000	\               midimap
ELF	7c7e7000-7c80d000	Deferred        msacm32<elf>
  \-PE	7c7f0000-7c80d000	\               msacm32
ELF	7c80d000-7c8d0000	Deferred        libasound.so.2
ELF	7c8d0000-7c962000	Deferred        winmm<elf>
  \-PE	7c8e0000-7c962000	\               winmm
ELF	7cf5b000-7cf91000	Deferred        winealsa<elf>
  \-PE	7cf60000-7cf91000	\               winealsa
ELF	7cf98000-7cfaf000	Deferred        msacm32<elf>
  \-PE	7cfa0000-7cfaf000	\               msacm32
ELF	7cfaf000-7cff9000	Deferred        dsound<elf>
  \-PE	7cfc0000-7cff9000	\               dsound
ELF	7d7df000-7e065000	Deferred        libglcore.so.1
ELF	7e065000-7e0f1000	Deferred        libgl.so.1
ELF	7e0f1000-7e1f4000	Deferred        wined3d<elf>
  \-PE	7e100000-7e1f4000	\               wined3d
ELF	7e1f4000-7e24b000	Deferred        ddraw<elf>
  \-PE	7e200000-7e24b000	\               ddraw
ELF	7e35c000-7e360000	Deferred        libgpg-error.so.0
ELF	7e360000-7e3ad000	Deferred        libgcrypt.so.11
ELF	7e3ad000-7e3bd000	Deferred        libtasn1.so.3
ELF	7e3bd000-7e3c5000	Deferred        libkrb5support.so.0
ELF	7e3c5000-7e3f7000	Deferred        libcrypt.so.1
ELF	7e3f7000-7e46d000	Deferred        libgnutls.so.13
ELF	7e46d000-7e490000	Deferred        libk5crypto.so.3
ELF	7e490000-7e51d000	Deferred        libkrb5.so.3
ELF	7e51d000-7e546000	Deferred        libgssapi_krb5.so.2
ELF	7e546000-7e579000	Deferred        libcups.so.2
ELF	7e57b000-7e57e000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e5a8000-7e5bb000	Deferred        libresolv.so.2
ELF	7e5c6000-7e5e4000	Deferred        iphlpapi<elf>
  \-PE	7e5d0000-7e5e4000	\               iphlpapi
ELF	7e5e4000-7e645000	Deferred        rpcrt4<elf>
  \-PE	7e5f0000-7e645000	\               rpcrt4
ELF	7e645000-7e6e9000	Deferred        ole32<elf>
  \-PE	7e650000-7e6e9000	\               ole32
ELF	7e711000-7e744000	Deferred        uxtheme<elf>
  \-PE	7e720000-7e744000	\               uxtheme
ELF	7e744000-7e74d000	Deferred        libxcursor.so.1
ELF	7e74d000-7e752000	Deferred        libxfixes.so.3
ELF	7e752000-7e755000	Deferred        libxcomposite.so.1
ELF	7e755000-7e75b000	Deferred        libxrandr.so.2
ELF	7e75b000-7e763000	Deferred        libxrender.so.1
ELF	7e763000-7e766000	Deferred        libxinerama.so.1
ELF	7e766000-7e76b000	Deferred        libxdmcp.so.6
ELF	7e76b000-7e783000	Deferred        libxcb.so.1
ELF	7e783000-7e86a000	Deferred        libx11.so.6
ELF	7e86a000-7e878000	Deferred        libxext.so.6
ELF	7e878000-7e87d000	Deferred        libxxf86vm.so.1
ELF	7e87d000-7e895000	Deferred        libice.so.6
ELF	7e895000-7e89d000	Deferred        libsm.so.6
ELF	7e89e000-7e8a0000	Deferred        libnvidia-tls.so.1
ELF	7e8a0000-7e8a3000	Deferred        libkeyutils.so.1
ELF	7e8a3000-7e8a6000	Deferred        libcom_err.so.2
ELF	7e8a8000-7e93f000	Deferred        winex11<elf>
  \-PE	7e8c0000-7e93f000	\               winex11
ELF	7e945000-7e966000	Deferred        libexpat.so.1
ELF	7e966000-7e990000	Deferred        libfontconfig.so.1
ELF	7e990000-7e9a5000	Deferred        libz.so.1
ELF	7e9a5000-7ea15000	Deferred        libfreetype.so.6
ELF	7ea16000-7ea19000	Deferred        libxau.so.6
ELF	7ea20000-7ea56000	Deferred        winspool<elf>
  \-PE	7ea30000-7ea56000	\               winspool
ELF	7ea56000-7eb01000	Deferred        comdlg32<elf>
  \-PE	7ea60000-7eb01000	\               comdlg32
ELF	7eb01000-7ebc0000	Deferred        comctl32<elf>
  \-PE	7eb10000-7ebc0000	\               comctl32
ELF	7ebc0000-7ec19000	Deferred        shlwapi<elf>
  \-PE	7ebd0000-7ec19000	\               shlwapi
ELF	7ec19000-7ed2c000	Deferred        shell32<elf>
  \-PE	7ec30000-7ed2c000	\               shell32
ELF	7ed2c000-7ed40000	Deferred        lz32<elf>
  \-PE	7ed30000-7ed40000	\               lz32
ELF	7ed40000-7ed59000	Deferred        version<elf>
  \-PE	7ed50000-7ed59000	\               version
ELF	7ed59000-7ed79000	Deferred        imm32<elf>
  \-PE	7ed60000-7ed79000	\               imm32
ELF	7ed79000-7edcb000	Deferred        advapi32<elf>
  \-PE	7ed90000-7edcb000	\               advapi32
ELF	7edcb000-7ee66000	Deferred        gdi32<elf>
  \-PE	7ede0000-7ee66000	\               gdi32
ELF	7ee66000-7efad000	Deferred        user32<elf>
  \-PE	7ee80000-7efad000	\               user32
ELF	7efad000-7efb8000	Deferred        libnss_files.so.2
ELF	7efb8000-7efd0000	Deferred        libnsl.so.1
ELF	7efd0000-7eff5000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d00000-b7d09000	Deferred        libnss_compat.so.2
ELF	b7d0a000-b7d0e000	Deferred        libdl.so.2
ELF	b7d0e000-b7e5d000	Deferred        libc.so.6
ELF	b7e5e000-b7e76000	Deferred        libpthread.so.0
ELF	b7e76000-b7e78000	Deferred        libxcb-xlib.so.0
ELF	b7e81000-b7fb7000	Deferred        libwine.so.1
ELF	b7fb9000-b7fd5000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) H:\.wine\drive_c\Program Files\Starcraft\StarCraft.exe
	00000024    0
	00000023    0
	00000021    0
	00000020    2
	0000001f    2
	0000001c    2
	0000001b    0
	0000001a   15
	00000017    1
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
00000018 
	00000019    0
Backtrace:
=>1 0x01b40148 (0x0033e540)
err:seh:setup_exception_record stack overflow 820 bytes in thread 0024 eip 7bc3ab33 esp 7baefffc stack 0x7baef000-0x7baf0000-0x7bc00000
err:seh:setup_exception_record stack overflow 828 bytes in thread 0023 eip 7bc72c62 esp 7bcdeff4 stack 0x7bcde000-0x7bcdf000-0x7bdef000
err:seh:setup_exception_record stack overflow 876 bytes in thread 0021 eip b7e68a1f esp 7bdeffc4 stack 0x7bdef000-0x7bdf0000-0x7bf00000

```




edit: installing msttcorefonts fixed it. :)

---

### Post by Golevel on 2008-08-10
Having the exact same problem, any ideas?

Edit:

This fixed it:

sudo apt-get update
sudo apt-get install msttcorefonts

---

