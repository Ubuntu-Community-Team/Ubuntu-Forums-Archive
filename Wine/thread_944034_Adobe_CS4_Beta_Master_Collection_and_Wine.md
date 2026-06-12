---
title: "Adobe CS4 Beta Master Collection and Wine"
date: 2008-10-10
forum: Wine
---

### Post by AmbientOcclusion on 2008-10-10
Hi.

I have been beta testing for Adobe, primarily on After Effects (end user stuff). I had heard that it would work on Wine and in the testing boards people had mentioned this is possible, but the documentation and methodology is scarce. I think this is for legal reasons. They won't officially support it but will mention, even via their sales dept. that it will run in Wine.

I wanted to post some of the failures here as I have a couple of questions. I think that this will be a very popular topic here fairly soon...

In attempting to install CS4 Master Collection Beta Here are the error results reported in Terminal (it doesn't install):

*(I have 64bit Ubuntu and this looks like it is 32 bit is this a problem?)

```
loginname@Comp:~/Desktop/cs4$ wine Setup.exe
fixme:console:AttachConsole stub ffffffff
Begin Adobe Setup
UI mode: Full GUI
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 003b), starting debugger...
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0032f8dc EBP:0032fb08 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:00000000 ECX:0032f904 EDX:00000079
 ESI:00000006 EDI:00000000
Stack dump:
0x0032f8dc:  00432b78 00000006 00000000 00000000
0x0032f8ec:  00000000 0032f904 393b95f5 006756b0
0x0032f8fc:  0032fd58 00000000 008011c8 0032f958
0x0032f90c:  7bc433cf 008034a0 00801240 0032f968
0x0032f91c:  7bc433cf 008011d0 007f03e0 0000011c
0x0032f92c:  00000006 00000000 00001770 00000002
Backtrace:
=>1 0x00000000 (0x0032fb08)
  2 0x00455347 in setup (+0x55347) (0x0032fb50)
  3 0x00429b49 in setup (+0x29b49) (0x0032fbc8)
  4 0x536e6957 (0x02020002)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (88 modules)
PE	  400000-  6d7000	Export          setup
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e0de000-7e0e2000	Deferred        libgpg-error.so.0
ELF	7e0e2000-7e12f000	Deferred        libgcrypt.so.11
ELF	7e12f000-7e13f000	Deferred        libtasn1.so.3
ELF	7e13f000-7e142000	Deferred        libkeyutils.so.1
ELF	7e142000-7e14a000	Deferred        libkrb5support.so.0
ELF	7e14a000-7e17c000	Deferred        libcrypt.so.1
ELF	7e17c000-7e1f1000	Deferred        libgnutls.so.13
ELF	7e1f1000-7e214000	Deferred        libk5crypto.so.3
ELF	7e214000-7e2a1000	Deferred        libkrb5.so.3
ELF	7e2a1000-7e2ca000	Deferred        libgssapi_krb5.so.2
ELF	7e2ca000-7e2fd000	Deferred        libcups.so.2
ELF	7e343000-7e346000	Deferred        libcom_err.so.2
ELF	7e359000-7e38c000	Deferred        uxtheme<elf>
  \-PE	7e360000-7e38c000	\               uxtheme
ELF	7e38c000-7e395000	Deferred        libxcursor.so.1
ELF	7e395000-7e39a000	Deferred        libxfixes.so.3
ELF	7e39a000-7e39d000	Deferred        libxcomposite.so.1
ELF	7e39d000-7e3a3000	Deferred        libxrandr.so.2
ELF	7e3a3000-7e3ab000	Deferred        libxrender.so.1
ELF	7e3ab000-7e3ae000	Deferred        libxinerama.so.1
ELF	7e3ae000-7e3ce000	Deferred        imm32<elf>
  \-PE	7e3b0000-7e3ce000	\               imm32
ELF	7e3ce000-7e3d3000	Deferred        libxdmcp.so.6
ELF	7e3d3000-7e3eb000	Deferred        libxcb.so.1
ELF	7e3eb000-7e3ee000	Deferred        libxau.so.6
ELF	7e3ee000-7e4d5000	Deferred        libx11.so.6
ELF	7e4d5000-7e4e3000	Deferred        libxext.so.6
ELF	7e4e3000-7e4e8000	Deferred        libxxf86vm.so.1
ELF	7e4ff000-7e596000	Deferred        winex11<elf>
  \-PE	7e510000-7e596000	\               winex11
ELF	7e5dd000-7e5fe000	Deferred        libexpat.so.1
ELF	7e5fe000-7e628000	Deferred        libfontconfig.so.1
ELF	7e628000-7e63d000	Deferred        libz.so.1
ELF	7e63d000-7e6ad000	Deferred        libfreetype.so.6
ELF	7e6ad000-7e6af000	Deferred        libxcb-xlib.so.0
ELF	7e6c4000-7e6d9000	Deferred        psapi<elf>
  \-PE	7e6d0000-7e6d9000	\               psapi
ELF	7e6d9000-7e6f2000	Deferred        version<elf>
  \-PE	7e6e0000-7e6f2000	\               version
ELF	7e6f2000-7e794000	Deferred        oleaut32<elf>
  \-PE	7e700000-7e794000	\               oleaut32
ELF	7e794000-7e7f5000	Deferred        rpcrt4<elf>
  \-PE	7e7a0000-7e7f5000	\               rpcrt4
ELF	7e7f5000-7e899000	Deferred        ole32<elf>
  \-PE	7e800000-7e899000	\               ole32
ELF	7e899000-7e8c0000	Deferred        oledlg<elf>
  \-PE	7e8a0000-7e8c0000	\               oledlg
ELF	7e8c0000-7e8f6000	Deferred        winspool<elf>
  \-PE	7e8d0000-7e8f6000	\               winspool
ELF	7e8f6000-7e9b5000	Deferred        comctl32<elf>
  \-PE	7e900000-7e9b5000	\               comctl32
ELF	7e9b5000-7eac8000	Deferred        shell32<elf>
  \-PE	7e9d0000-7eac8000	\               shell32
ELF	7eac8000-7eb73000	Deferred        comdlg32<elf>
  \-PE	7ead0000-7eb73000	\               comdlg32
ELF	7eb73000-7eb86000	Deferred        libresolv.so.2
ELF	7eb86000-7eba4000	Deferred        iphlpapi<elf>
  \-PE	7eb90000-7eba4000	\               iphlpapi
ELF	7eba4000-7ebd0000	Deferred        ws2_32<elf>
  \-PE	7ebb0000-7ebd0000	\               ws2_32
ELF	7ebd0000-7ebea000	Deferred        wsock32<elf>
  \-PE	7ebe0000-7ebea000	\               wsock32
ELF	7ebea000-7ec3c000	Deferred        advapi32<elf>
  \-PE	7ec00000-7ec3c000	\               advapi32
ELF	7ec3c000-7ecd7000	Deferred        gdi32<elf>
  \-PE	7ec50000-7ecd7000	\               gdi32
ELF	7ecd7000-7ee1e000	Deferred        user32<elf>
  \-PE	7ecf0000-7ee1e000	\               user32
ELF	7ee1e000-7ee77000	Deferred        shlwapi<elf>
  \-PE	7ee30000-7ee77000	\               shlwapi
ELF	7ef97000-7efa2000	Deferred        libnss_files.so.2
ELF	7efa2000-7efac000	Deferred        libnss_nis.so.2
ELF	7efac000-7efc4000	Deferred        libnsl.so.1
ELF	7efc4000-7efe9000	Deferred        libm.so.6
ELF	7efec000-7f000000	Deferred        lz32<elf>
  \-PE	7eff0000-7f000000	\               lz32
ELF	f7cd6000-f7cdf000	Deferred        libnss_compat.so.2
ELF	f7ce0000-f7ce4000	Deferred        libdl.so.2
ELF	f7ce4000-f7e33000	Deferred        libc.so.6
ELF	f7e34000-f7e4c000	Deferred        libpthread.so.0
ELF	f7e63000-f7f99000	Deferred        libwine.so.1
ELF	f7f9b000-f7fba000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
	0000000b    0
0000000c 
	0000000e    0
	0000000d    0
0000001e (D) H:\Desktop\cs4\Setup.exe
	0000003b    0 <==
00000047 
	00000009    0
Backtrace:
=>1 0x00000000 (0x0032fb08)
  2 0x00455347 in setup (+0x55347) (0x0032fb50)
  3 0x00429b49 in setup (+0x29b49) (0x0032fbc8)
  4 0x536e6957 (0x02020002)

```
Any ideas of what the general problem is here would be helpful. Thanks!

---

### Post by asdfoo on 2008-10-10
> **AmbientOcclusion said:**
> Hi.

I have been beta testing for Adobe, primarily on After Effects (end user stuff). I had heard that it would work on Wine and in the testing boards people had mentioned this is possible, but the documentation and methodology is scarce. I think this is for legal reasons. They won't officially support it but will mention, even via their sales dept. that it will run in Wine.

I wanted to post some of the failures here as I have a couple of questions. I think that this will be a very popular topic here fairly soon...

In attempting to install CS4 Master Collection Beta Here are the error results reported in Terminal (it doesn't install):

*(I have 64bit Ubuntu and this looks like it is 32 bit is this a problem?)

```
loginname@Comp:~/Desktop/cs4$ wine Setup.exe
fixme:console:AttachConsole stub ffffffff
Begin Adobe Setup
UI mode: Full GUI
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 003b), starting debugger...
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0032f8dc EBP:0032fb08 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:00000000 ECX:0032f904 EDX:00000079
 ESI:00000006 EDI:00000000
Stack dump:
0x0032f8dc:  00432b78 00000006 00000000 00000000
0x0032f8ec:  00000000 0032f904 393b95f5 006756b0
0x0032f8fc:  0032fd58 00000000 008011c8 0032f958
0x0032f90c:  7bc433cf 008034a0 00801240 0032f968
0x0032f91c:  7bc433cf 008011d0 007f03e0 0000011c
0x0032f92c:  00000006 00000000 00001770 00000002
Backtrace:
=>1 0x00000000 (0x0032fb08)
  2 0x00455347 in setup (+0x55347) (0x0032fb50)
  3 0x00429b49 in setup (+0x29b49) (0x0032fbc8)
  4 0x536e6957 (0x02020002)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (88 modules)

Threads:
process  tid      prio (all id:s are in hex)
0000000a 
	0000000b    0
0000000c 
	0000000e    0
	0000000d    0
0000001e (D) H:\Desktop\cs4\Setup.exe
	0000003b    0 <==
00000047 
	00000009    0
Backtrace:
=>1 0x00000000 (0x0032fb08)
  2 0x00455347 in setup (+0x55347) (0x0032fb50)
  3 0x00429b49 in setup (+0x29b49) (0x0032fbc8)
  4 0x536e6957 (0x02020002)

```
Any ideas of what the general problem is here would be helpful. Thanks!

hi, no the problem is not 64bit vs 32, Wine is only 32bit. 

Which version of Wine are you using? 1.1.6 installs CS3 fine I hear, so perhaps try with 1.1.6 and report back?

---

### Post by MaindotC on 2008-10-11
What do you mean wine is only 32 bit ??

---

### Post by asdfoo on 2008-10-11
> **strAlan said:**
> What do you mean wine is only 32 bit ??

All versions of Wine are compiled as 32bit.  There is no 64bit Wine yet.  64bit support will come in the future after more pressing issues have been sorted out.

---

### Post by MaindotC on 2008-10-11
I'm sure you can understand why I asked this.  After doing a site-search of winehq.org for "64-bit" I read and see evidence of your statement.  I use Wine on my 64-bit Hardy so naturally I was aroused at this remark.  I learn something new everyday :)

---

### Post by AmbientOcclusion on 2008-10-11
Hey asdfoo,

thanks for the tip in updating wine...

I have the latest version now, but I still have install problems.

```
loginame@Comp:/media/cs4$ wine Setup.exe
fixme:advapi:LookupAccountNameW L"" L"the2" 0x33ec0c 0x33e970 0x1327c8 0x33e968 0x33e974 - stub
fixme:module:NtLoadDriver (0x33ee60), stub!
fixme:module:NtLoadDriver (0x33ed2c), stub!
fixme:module:NtLoadDriver (0x33ebe4), stub!
fixme:console:AttachConsole stub ffffffff
Begin Adobe Setup
UI mode: Full GUI
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0032f8dc EBP:0032fb08 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:00000000 ECX:0032f904 EDX:00000079
 ESI:00000006 EDI:00000000
Stack dump:
0x0032f8dc:  00432b78 00000006 00000000 00000000
0x0032f8ec:  00000000 0032f904 579a227e 006756b0
0x0032f8fc:  0032fd58 00000000 00801188 0032f958
0x0032f90c:  7bc43ddf 00803468 00801200 0032f968
0x0032f91c:  7bc43ddf 00801190 007f03e0 0000011c
0x0032f92c:  00000006 00000000 00001770 00000002
Backtrace:
=>1 0x00000000 (0x0032fb08)
  2 0x00455347 in setup (+0x55347) (0x0032fb50)
  3 0x00429b49 in setup (+0x29b49) (0x0032fbc8)
  4 0x536e6957 (0x02020002)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (88 modules)
PE	  400000-  6d7000	Export          setup
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e00d000-7e011000	Deferred        libgpg-error.so.0
ELF	7e011000-7e05e000	Deferred        libgcrypt.so.11
ELF	7e05e000-7e06e000	Deferred        libtasn1.so.3
ELF	7e06e000-7e071000	Deferred        libkeyutils.so.1
ELF	7e071000-7e079000	Deferred        libkrb5support.so.0
ELF	7e079000-7e0ab000	Deferred        libcrypt.so.1
ELF	7e0ab000-7e120000	Deferred        libgnutls.so.13
ELF	7e120000-7e143000	Deferred        libk5crypto.so.3
ELF	7e143000-7e1d0000	Deferred        libkrb5.so.3
ELF	7e1d0000-7e1f9000	Deferred        libgssapi_krb5.so.2
ELF	7e1f9000-7e22c000	Deferred        libcups.so.2
ELF	7e271000-7e274000	Deferred        libcom_err.so.2
ELF	7e287000-7e2ba000	Deferred        uxtheme<elf>
  \-PE	7e290000-7e2ba000	\               uxtheme
ELF	7e2ba000-7e2c3000	Deferred        libxcursor.so.1
ELF	7e2c3000-7e2c8000	Deferred        libxfixes.so.3
ELF	7e2c8000-7e2cb000	Deferred        libxcomposite.so.1
ELF	7e2cb000-7e2d1000	Deferred        libxrandr.so.2
ELF	7e2d1000-7e2d9000	Deferred        libxrender.so.1
ELF	7e2d9000-7e2de000	Deferred        libxxf86vm.so.1
ELF	7e2de000-7e2e1000	Deferred        libxinerama.so.1
ELF	7e2e1000-7e301000	Deferred        imm32<elf>
  \-PE	7e2f0000-7e301000	\               imm32
ELF	7e301000-7e306000	Deferred        libxdmcp.so.6
ELF	7e306000-7e31e000	Deferred        libxcb.so.1
ELF	7e31e000-7e320000	Deferred        libxcb-xlib.so.0
ELF	7e320000-7e323000	Deferred        libxau.so.6
ELF	7e323000-7e40a000	Deferred        libx11.so.6
ELF	7e40a000-7e418000	Deferred        libxext.so.6
ELF	7e42f000-7e4c7000	Deferred        winex11<elf>
  \-PE	7e440000-7e4c7000	\               winex11
ELF	7e511000-7e532000	Deferred        libexpat.so.1
ELF	7e532000-7e55c000	Deferred        libfontconfig.so.1
ELF	7e55c000-7e571000	Deferred        libz.so.1
ELF	7e571000-7e5e1000	Deferred        libfreetype.so.6
ELF	7e5f8000-7e60d000	Deferred        psapi<elf>
  \-PE	7e600000-7e60d000	\               psapi
ELF	7e60d000-7e621000	Deferred        lz32<elf>
  \-PE	7e610000-7e621000	\               lz32
ELF	7e621000-7e63a000	Deferred        version<elf>
  \-PE	7e630000-7e63a000	\               version
ELF	7e63a000-7e721000	Deferred        oleaut32<elf>
  \-PE	7e650000-7e721000	\               oleaut32
ELF	7e721000-7e786000	Deferred        rpcrt4<elf>
  \-PE	7e730000-7e786000	\               rpcrt4
ELF	7e786000-7e88f000	Deferred        ole32<elf>
  \-PE	7e7a0000-7e88f000	\               ole32
ELF	7e88f000-7e8b7000	Deferred        oledlg<elf>
  \-PE	7e890000-7e8b7000	\               oledlg
ELF	7e8b7000-7e8ec000	Deferred        winspool<elf>
  \-PE	7e8c0000-7e8ec000	\               winspool
ELF	7e8ec000-7e9ad000	Deferred        comctl32<elf>
  \-PE	7e8f0000-7e9ad000	\               comctl32
ELF	7e9ad000-7eac7000	Deferred        shell32<elf>
  \-PE	7e9c0000-7eac7000	\               shell32
ELF	7eac7000-7eb74000	Deferred        comdlg32<elf>
  \-PE	7ead0000-7eb74000	\               comdlg32
ELF	7eb74000-7eb93000	Deferred        iphlpapi<elf>
  \-PE	7eb80000-7eb93000	\               iphlpapi
ELF	7eb93000-7ebbf000	Deferred        ws2_32<elf>
  \-PE	7eba0000-7ebbf000	\               ws2_32
ELF	7ebbf000-7ebd9000	Deferred        wsock32<elf>
  \-PE	7ebc0000-7ebd9000	\               wsock32
ELF	7ebd9000-7ec2d000	Deferred        advapi32<elf>
  \-PE	7ebf0000-7ec2d000	\               advapi32
ELF	7ec2d000-7eccb000	Deferred        gdi32<elf>
  \-PE	7ec40000-7eccb000	\               gdi32
ELF	7eccb000-7ee14000	Deferred        user32<elf>
  \-PE	7ecf0000-7ee14000	\               user32
ELF	7ee14000-7ee6e000	Deferred        shlwapi<elf>
  \-PE	7ee20000-7ee6e000	\               shlwapi
ELF	7ef8e000-7ef99000	Deferred        libnss_files.so.2
ELF	7ef99000-7efa3000	Deferred        libnss_nis.so.2
ELF	7efa3000-7efbb000	Deferred        libnsl.so.1
ELF	7efbb000-7efc4000	Deferred        libnss_compat.so.2
ELF	7efc4000-7efe9000	Deferred        libm.so.6
ELF	7efeb000-7effe000	Deferred        libresolv.so.2
ELF	f7cc2000-f7cc6000	Deferred        libdl.so.2
ELF	f7cc6000-f7e15000	Deferred        libc.so.6
ELF	f7e16000-f7e2e000	Deferred        libpthread.so.0
ELF	f7e45000-f7f7b000	Deferred        libwine.so.1
ELF	f7f7d000-f7f9c000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\cs4\Setup.exe
	00000009    0 <==
0000000a 
	0000000b    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
00000017 
	00000018    0
Backtrace:
=>1 0x00000000 (0x0032fb08)
  2 0x00455347 in setup (+0x55347) (0x0032fb50)
  3 0x00429b49 in setup (+0x29b49) (0x0032fbc8)
  4 0x536e6957 (0x02020002)

```

Not really sure what's going on here. Looks like Wine starts up and then a page fault error, same as before.

I will try CS3. I am wondering if this is a beta problem and that the full release will work. The reps and salespeople swear it works fine.

---

### Post by asdfoo on 2008-10-11
> **AmbientOcclusion said:**
> Hey asdfoo,

thanks for the tip in updating wine...

I have the latest version now, but I still have install problems.

```
loginame@Comp:/media/cs4$ wine Setup.exe
fixme:advapi:LookupAccountNameW L"" L"the2" 0x33ec0c 0x33e970 0x1327c8 0x33e968 0x33e974 - stub
fixme:module:NtLoadDriver (0x33ee60), stub!
fixme:module:NtLoadDriver (0x33ed2c), stub!
fixme:module:NtLoadDriver (0x33ebe4), stub!
fixme:console:AttachConsole stub ffffffff
Begin Adobe Setup
UI mode: Full GUI
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).

Backtrace:
=>1 0x00000000 (0x0032fb08)
  2 0x00455347 in setup (+0x55347) (0x0032fb50)
  3 0x00429b49 in setup (+0x29b49) (0x0032fbc8)
  4 0x536e6957 (0x02020002)

```

Not really sure what's going on here. Looks like Wine starts up and then a page fault error, same as before.

I will try CS3. I am wondering if this is a beta problem and that the full release will work. The reps and salespeople swear it works fine.


Yeah, hard to tell without a full log, your backtrace doesn't help much.  It would probably be a good idea to file a bug report at [http://bugs.winehq.org](http://bugs.winehq.org).

To get a full log, you could run: WINEDEBUG=+relay,+seh,+tid wine setup 2> log.txt

Then if you look at the log (it might be anywhere from a few MB to tens of MB) you should see the crash at the end, but perhaps some of the preceeding lines will provide a clue.   


As for the reps swearing it works, perhaps they did something differently, such as installing in Windows first then copying the files to their linux partition (which kinda defeats the purpose of Wine) or maybe they tried a different version of the software.  Can't say for sure.

---

### Post by AmbientOcclusion on 2008-10-12
I emailed one of the beta team leads and he mentioned that the Beta will NOT work in Wine but the full release does. So this sort of answers the question.

Just out of curiosity, what files would you need to copy from a windows install to wine?

---

### Post by asdfoo on 2008-10-12
> **AmbientOcclusion said:**
> I emailed one of the beta team leads and he mentioned that the Beta will NOT work in Wine but the full release does. So this sort of answers the question.

Just out of curiosity, what files would you need to copy from a windows install to wine?

The Adobe program files...  it may or may not work, it might need registry keys setup as part of the install.

---

### Post by MasterNetra on 2008-10-18
Idk how wine handles the programs individually but the CS3 Master Collection doesn't install at least not for me.

---

### Post by asdfoo on 2008-10-18
> **MasterNetra said:**
> Idk how wine handles the programs individually but the CS3 Master Collection doesn't install at least not for me.

I think it was working but a recent change in the development branch of Wine caused a regression in the installer.  I think you have to apply this patch for it to work:

There is a bug report filed here: [http://bugs.winehq.org/show_bug.cgi?id=15652](http://bugs.winehq.org/show_bug.cgi?id=15652) (Please remember that bugzilla is not a support forum, ask your questions here on the ubuntu forums or [http://forum.winehq.org](http://forum.winehq.org))

---

### Post by cybercow222 on 2008-11-05
as i understood neither CS3 and CS4 are installable from the setup execuable because it crashez. i readed google pushed adobe to adapt photoshop to work with wine. i saw people installed either photoshop, fireworks, flash and dreamweaver on ubuntu with success but with some minor bugs. the method is to install the desidered programs on windows platform then copy the whole /Adobe folder to ubuntu, the one is not enough and need some aditional fine tuning like copying some things from user settings or such ... i readed about it somewhere, the instruction was for dw but is worth for ps though ...

---

### Post by asdfoo on 2008-11-06
> **cybercow222 said:**
> as i understood neither CS3 and CS4 are installable from the setup execuable because it crashez. i readed google pushed adobe to adapt photoshop to work with wine. i saw people installed either photoshop, fireworks, flash and dreamweaver on ubuntu with success but with some minor bugs. the method is to install the desidered programs on windows platform then copy the whole /Adobe folder to ubuntu, the one is not enough and need some aditional fine tuning like copying some things from user settings or such ... i readed about it somewhere, the instruction was for dw but is worth for ps though ...

The CS4 installer should work:

> 
First, it downloads gecko, but hangs afterwards; you have to ^C and
restart the installer.

Second, dialogs are often painted with three-quarters of the content missing,
and the remaining quarter misplaced.  Moving the dialog offscreen and back
on usually fixes this.  So this is both a showtopper for the
average user and a cosmetic problem.

Third, the very first dialog that is shown is mostly blank.  Jacek
knows why: our gecko engine is out of date, and can't handle negative
values on some css properties.  He came up with a simple workaround:
when this happens, kill the installer (with wineserver -k), 
then edit 
.wine/drive_c/Program Files/Common
Files/Adobe/Installers/d6da2ba33e237f559e70b443726029b/resources/media/css/main.css
and replace the line
       z-index:-10;
with the line
       z-index:0;



---

### Post by magcius on 2008-11-09
> **asdfoo said:**
> The CS4 installer should work:

For everyone wondering, you will need to install msxml3.

Run the commands in with "$" in front.

```

$ wineserver -k
$ wget http://www.kegel.com/wine/winetricks
Resolving www.kegel.com... 216.92.86.126
Connecting to www.kegel.com|216.92.86.126|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 62682 (61K) [text/plain]
Saving to: `winetricks'

100%[======================================>] 62,682       175K/s   in 0.3s    

2008-11-09 14:20:36 (175 KB/s) - `winetricks' saved [62682/62682]

$ gksudo mv winetricks /usr/local/bin
$ gksudo chmod a+x /usr/local/bin/winetricks
$ winetricks msxml3

... a Windows installer will pop up after a while. Follow it through.

```
then run the Setup.exe file like so:

```

$ wine start Setup.exe &

```

When the installer finally pops up a blank window that says "Loading Setup" at the top, run the command:

```

$ wineserver -k

```

This will kill all running WINE applications.

Next, run this command. This will apply the fix said in the last post. This is a long, one, so select the entire thing and use the middle-mouse button to paste it in. I didn't include the dollar for convenience purposes. 

```

perl -e "s/z-index:-10;/z-index:0;/" -p -i ~/.wine/drive_c/Program\ Files/Common\ Files/Adobe/Installers/`basename \`ls | grep *.ico\` .ico`/resources/media/css/main.css

```

Next, run the setup again. Paste the next command in if you need to, just don't select the dollar.

```

$ cd ~/.wine/drive_c/Program\ Files/Common\ Files/Adobe/Installers/`basename \`ls | grep *.ico\` .ico`/
$ wine Setup.exe

```

This is where I got stuck, as everything worked, except the installation just hung at "Loading Setup..." on the screen.

If you get a similar issue, paste the output of this command here (another long one...):

```

$ tail -20 ~/.wine/drive_c/Program\ Files/Common\ Files/Adobe/Installers/Adobe\ Creative\ Suite\ 4\ Master\ Collection\ 4.0\ `date +%m-%d-%Y`.log

```

My result is below:

```

{"OS":{"Macintosh":{"Require":[{"@lowerBound":1,
"Version":"10.4.11","Need64Bit":"0","NeedServer":"0"}],"Exclude":[{"@upperBound":1,
"Version":"10.4.10","Only64Bit":"0","OnlyServer":"0"}]},"Windows":{"XP":{"Require":{"@lowerBound":1,
"MinServicePack":"3","@servicePack64Bit":1
,"Need64Bit":"0"},"Exclude":{"@upperBound":1,
"MaxServicePack":"1","@servicePack64Bit":"0"
}},"Vista":{"Require":{"@lowerBound":1,
"MinServicePack":"1","@servicePack64Bit":1
,"Need64Bit":"0"},"Exclude":{"@upperBound":1,
"MaxServicePack":"0","@servicePack64Bit":"0"
,"Only64Bit":"0"}}}},
						"Memory":{"System":{"Default":{"Require":"2048"}}},
						"Display":{"Default":{"Require":{"Width":"1024","Height":"768"}}}
	}
]

[       9] Sun Nov 09 12:53:25 2008  WARN
The minimum system requirements listed below are recommended in order to run Adobe Creative Suite 4 Master Collection properly and are not met:
[       9] Sun Nov 09 12:53:25 2008 FATAL
Critical errors were found in setup

```

Thanks again.

---

### Post by AmbientOcclusion on 2008-11-11
Magcius, thanks for this. I am going to try this in a bit. I have been in a similar predicament.

---

### Post by lakersforce on 2008-11-11
Also, try to install the ia32libs

---

### Post by magcius on 2008-11-11
> **lakersforce said:**
> Also, try to install the ia32libs

I don't understand how this would help. I am running on an x86 processor, and this seems completely unrelated to what I'm doing.

---

### Post by talofo on 2008-11-15
If you will make it work, I definitly go for Ubuntu and leave XP or other Ms Os.

I'm newbie on all this, so I'm not such a help. :(

Good luck, and please report any progresses, cas I'm really glad that this may work.


Regards,
MEM

---

### Post by Atro on 2008-11-15
Same here
the only thing preventing me from completely switching to Ubuntu is Adobe. If I see that CS4 runs on Ubuntu with not much problems, I will delete every single Microsoft made file from my computers

---

### Post by magcius on 2008-11-16
Atro, CS4 works wonderfully under Wine after installation. (Photoshop CS4 has a Platinum rating on AppDB). It's just Adobe Setup that is stupid.

EDIT: AppDB accepted my app results: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514)

---

### Post by talofo on 2008-11-16
> **magcius said:**
> Atro, CS4 works wonderfully under Wine after installation. (Photoshop CS4 has a Platinum rating on AppDB). It's just Adobe Setup that is stupid.

EDIT: AppDB accepted my app results: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514)

Magcius, thanks a lot for your reply that seams to be great news, but you are saying that all Adobe CS4 version works?
Even shortcuts and all? 
I'm using Illustrator, Dreamweaver, Fireworks and Photoshop, all of them will work fine?

If yes, can you please tell us what should we do to make it work cas, if that's the case, I will get out from M$ in no time. :D:D:D:D

Regards,
MEM

---

### Post by magcius on 2008-11-16
According to the sales reps at Adobe (which usually can be trusted), everything but the installer works.

---

### Post by abrichr on 2008-11-17
Following these instructions, I've managed to get the installation halfway several times.  The problem I'm having is that the installer always hangs on Adobe Air -- I've even left it on overnight with no progress.  I've removed and reinstalled Wine several times -- even compiled from source.

I don't know if it's possible to disable Adobe Air from installing, since the screen that allows you to choose which components to install displays very poorly.

I'm going to try installing it in Virtualbox, and copy the files over as I did with CS3.

---

### Post by talofo on 2008-11-17
Ok. So the possibility may be, install everything another way and them copy the already installed filed to Ubunto. Is there a differemce of I use Kubuntu with KDE instead of Gnome Ubuntu?

As your CS3 installion work well, I mean, all programes from adobe and a nice speed?


Regards, and thanks a lot for your comments,
MEM

---

### Post by barx on 2008-11-19
What can I say . . . seems to be less requirements than Adobe CS3

I dowloaded Flash CS4 with serial number and a Patch, that patch is a dll

is the **amtlib.dll**  that tells me something the usual Flash has something wrong also for WIndows users . .. 

I run Macromedia Flash 8 and runs pretty well, I want to try helping you, but I don't have the most recent version of wine. I have the 1.01, the one is in Repository of Synaptic. When I try to install the deb for mi AMD64 arquitecture it says that I libasound is not compatible and if I uninstall it will eliminate many of my aplications.

Is there a way to install the latest version of wine without problems?

I'm interested on cs4 also I can pass the direction of the torrent if interest you. I do this first (download), because I don't want to spend money into the trash buying the original, that's why I din't bought CS3. 

There's no a Linux version already, so, that's why we do that things

Another question. Is not easier to do a program for Mac installers alike wine for linux?

Because, Mac OS is Unix like, and I'm not sure if now is Unix Based, there must be a way if Adobe don't want to make a Linux version, or there is a way to do it?:confused:

---

### Post by abrichr on 2008-11-19
To install the latest version of wine, follow these steps:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

As for the OSX version of Wine, I'm no expert, but I believe the main reason why such an application doesn't exist is simply because there isn't as high demand for it.  Put another way, there are more linux users who wish to run windows applications than there are linux users who wish to run mac applications.

[Cocotron]("http://www.cocotron.org") is one app that I know of in very early stages of development, but as they say on their website (at the time of writing):

> The general goal is to provide complete support on any viable platform, the project is intended to be as portable as possible. However, most of the work at this time is focused on providing support for Microsoft Windows. In particular the NT based versions, 2000 up to Vista.

---

### Post by AmbientOcclusion on 2008-11-23
So I have the full version of CS4 now and I too am having a problem with Air. You can deselect it in the install. 

Currently I can get it to install but it crashes on load. Sometimes the splash screen just hangs.

---

### Post by sputty01 on 2008-11-30
> **magcius said:**
> Atro, CS4 works wonderfully under Wine after installation. (Photoshop CS4 has a Platinum rating on AppDB). It's just Adobe Setup that is stupid.

EDIT: AppDB accepted my app results: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14514)

I don't know how CS4 could be classed as platinum by anyone, the program does start but the text tool and various other features just crash the program instantaneously, this also means you cant load any old photoshop documents containing vector based text layers. Ive tried all the mentioned techniques but to no avail :(

For anyone else wanting to try it out you will need to first run the installation on windows and then follow these steps listed in the comments section of the AppDB entry:
> 
copy %windir%/WinSxS to ~/.wine/drive_c/windows/
copy %appdata%/Adobe to ~/.wine/drive_c/windows/profiles/All Users/Application Data/
copy %appdata%/FLEXnet to ~/.wine/drive_c/windows/profiles/All Users/Application Data/

copy c:/Program Files/Adobe to ~/.wine/drive_c/Program Files/
copy c:/Program Files/Common Files/Adobe to ~/.wine/drive_c/Program Files/Common Files/
copy c:/Program Files/Common Files/Macrovision Shared to ~/.wine/drive_c/Program Files/Common Files/

From windows registry backup HKEY_LOCAL_MACHINE\SOFTWARE\Adobe and HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\FLEXnet Licensing Service and restore both to wine registry

now open up your Photoshop CS4 and have fun

Its very close to working, but without the text tool its useless for the majority of its users :( CS2 is still the only option for the moment.

---

### Post by talofo on 2008-12-07
how... :( bad news. :( What about virtualization? Is that a possibility?

---

### Post by talofo on 2008-12-15
Anyone succeed having DREAMWEAVER CS4 running on UBUNTU with Wine?


:(

MEM

---

### Post by alex.rayu on 2008-12-16
I have just managed to install Photoshop CS3 under wine 1.10 - maybe cs4 will now install as well?

---

### Post by talofo on 2008-12-16
Yes... I'm trying with CS4 lets see...

---

### Post by alex.rayu on 2008-12-16
How did it go?

---

### Post by talofo on 2008-12-16
Hi. I've just finnish it. How did you know? :p

Well, I've tried the Dreamweaver CS4 Trial and it opens. :):):):)

Now we must have some bugs already reported on wineHQ.
Update: Like in here: [http://bugs.winehq.org/show_bug.cgi?id=16430](http://bugs.winehq.org/show_bug.cgi?id=16430)


Here's the HOW TO:

1)
Install Wine 1.1.10:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)



2)
Install cabextract:
sudo apt-get install cabextract



3)
Install Wine Gecko Package.



4)
Install Winetricks:
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

chmod +x winetricks


5) 
Install native gdiplus:
$ sh winetricks gdiplus 



6) And Native msxml3:
$ sh winetricks msxml3 



7) The IE6 libs are needed for splash screen:
./winetricks corefonts ie6

#######################################################################
Go to a native windows system32 directory and copy: odbc32.dll
then Paste on wine/system32/

do: winecfg
In New Override for Library option choose: odbc32
Click Add. Make sure you have something like this: odbc32(native, builtin)
Click Apply then OK to exit.
########################################################################

8) Repeat last step for: odbcint.dll


Now we are ready to try:
Go to Dreamweaver Setup Directory, and running not with double click BUT, from the command line. wine Dreamweaver.exe

gl.


Notes:
If doing the trial, you might get lost finding the radio button to select it. It is... invisible! Just click to the left of the "I want to install and use..." line where you'd think it would be. A box will appear.



All this info is just compiled infos from here and there, that i've put together and make it to work, I have no credits from this.


Regards,
MEM

---

### Post by alex.rayu on 2008-12-16
Congrats!
I wonder if Photoshop CS4 will run well?
See, CS3 runs ok but their GDI+ interface becomes blank and sometimes does not redraw even if you click it. It appeared they have different one in PS4?

---

### Post by talofo on 2008-12-16
Well the GUI of CS4 is totally different, but, for now, the Dreamweaver CS4 has a bug exactly on that area. the drop down menus of Dreamweaver don't refresh. Hopefully we can get the patch that is on WineHQ to work with Ubuntu.


After this we can try all the others. I've just not tried the Adobe Collection Trial because I don't have much space, and well, to debug errors, maybe it's better to go one program at the time. ;)

Maybe Photoshop:
suffers from the same problem of the menus.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318)


Maybe someone else able to help us on this? :D


MEM

---

### Post by PHOTOG on 2009-01-19
Any new news.....I am totally not any type of coder, so wil not be of any help.....I am just looking to Ditch all M$ OS and other software (office + anything I can) and get over here to the OPen side of life.
But job requires Photoshop 7 and CS4.....I know that sounds strange but I have way toooo many PS7 plug-ins to dump it and I cannot afford to upgrade them to CS4.

Will be watching for progress reports on this.

Thanx for all the hard work guys!!!!!

---

### Post by alex.rayu on 2009-01-21
Neither PS3 nor PS4 run in wine 1.1.13
I managed to install PS CS4 but it hung at splash

---

### Post by donkyhotay on 2009-01-21
The menu bug is known and a patch for it is already available, unfortunately it requires manual patching/compiling in order to use it at this time. Currently any cs4 application except illustrator and acrobat can be installed (though not necessarily run) by installing ie6 and msxml6 with winetricks and manually installing the 0.9 gecko engine (winetricks version is out of date).

---

### Post by alex.rayu on 2009-01-21
Will they include that patch into the next release?

---

### Post by donkyhotay on 2009-01-21
> **alex.rayu said:**
> Will they include that patch into the next release?

They're planning on doing so for version 1.2 but it currently isn't in the GIT repository yet for compiling from source.

---

### Post by alex.rayu on 2009-01-21
On my bug request page I received a patch and was asked to apply it. [http://bugs.winehq.org/show_bug.cgi?id=17062#add_comment](http://bugs.winehq.org/show_bug.cgi?id=17062#add_comment)

How do I do it? It lists more than one file. I would prefer not to mess with the code manually in implementing the patch.

---

### Post by donkyhotay on 2009-01-21
I don't know myself, although I do occasionally compile the GIT version of wine from source I don't mess with the patches or anything since I try to test the current 'official' versions. Some patches you have to run a script and some you just replace the files in the correct locations. I'm not planning on messing with that patch until it gets integrated into the official GIT repository at which point it will be already integrated. Someone else here may know more about it but I would recommend posting your question onto the wine bugzilla for that specific bug. The people posting there are the ones that use/made the patch and will know much more about it.

---

### Post by lecelte on 2009-01-25
Hi,

I've Photoshop CS4 32 installed in a VirtualBox (Win XP) with an Ubuntu 8.10.

1/ I've copy/paste C:\Program files\Adobe to wine directory.
2/ I've exported registry key HKLM/Adobe and launch :

$ recode ucs-2..ascii adobe.reg
$ wine regedit adobe.reg

Bridge's WORK fine :D  :
* performances are better than using VirtualBox
* but Bridge can't read my CR2 files (Canon Raw) => Camera RAW is not working
* and Bridge can't open Photoshop

When I launch Photoshop, I've an error from a missing DLL, but this DLL is in Bridge directory, It seem to be a wine config problem :

> yle@fixe2008-ubuntu:~/.wine/drive_c/Program Files/adobe-cs4/Adobe Bridge CS4$ wine ../Adobe\ Photoshop\ CS4/Photoshop.exe 
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\adobe-cs4\\Adobe Photoshop CS4\\Photoshop.exe") not found

Any idea ?

Yann

---

### Post by alex.rayu on 2009-01-27
I gave up on it. Using CS2 and CS4 in VirtualBox "just in case".

---

### Post by MasterNetra on 2009-01-28
How is Flash CS3 or Flash CS4 working in the new wine release (1.1.13) ? The priors Flash CS3 (at least) was highly buggy. Has that changed any with 1.1.13? I would like to switch back to Ubuntu but thats whats pretty much has been holding me back and i wouldn't want to have to try re-installing ubuntu and adobe stuff just to find it still doesn't work correctly...

---

### Post by alex.rayu on 2009-01-28
Neither of CS3 installs. CS4 they say installs but Flash does not work, and Photoshop has Text tool freeze the wine upon selection. But for me, CS4 does not install at all. Nobody knows why.

---

### Post by MasterNetra on 2009-01-28
What version of wine ya using?

---

### Post by alex.rayu on 2009-01-29
I am using the latest - 1.1.13. But I tried it with all previous versions as they came out. ANY of CS3 products, be it Photoshop, Flash, or DreamWeaver, after installing some of the Shared Components, then says, that an error occured, and some of the Shared components and the product proper (Flash/Photoshop/DW) are failed to install.

---

### Post by happinesskills on 2009-01-31
they've come out with 1.1.14 now. I don't know when they did it.

---

### Post by AllRadioisDead on 2009-01-31
Hi, sorry to bump into the conversation, but I'm looking to install photoshop and dreamweaver on my ubuntu PC. On the wine AP DB, it claims that photoshop works.
> CS4 runs great after being patched. Patching Wine requires compiling Wine from source and applying the patches while doing so (Of course). I haven't noticed any changes in any of my other Windows applications. I can say the patches worked great on my system and they haven't broke any other applications. Let's hope the same thing can be said about KDE 4.2 *crosses fingers*

Where can I find this patch?
Thanks :)

---

### Post by alex.rayu on 2009-01-31
The patch is tricky. You will have to install GIT version manager, copy the git sources to your computer, and apply a patch to the latest git sources. That is at least for me is too much.

I have not tested the Wine 1.1.14 yet.

---

### Post by alex.rayu on 2009-01-31
Tried with 1.1.14. The old error for me persists. With native gdiplus, it hangs when splash appears, and with builtin gdiplus it hangs in the end, when it says" initializing the panels".

---

### Post by AllRadioisDead on 2009-01-31
That sounds brutal, I don't think I'll be trying it. Good luck with your adventures.

---

### Post by alex.rayu on 2009-01-31
> **ihermit said:**
> That sounds brutal, I don't think I'll be trying it. Good luck with your adventures.

Why, don't want to learn to patch and compile from git? Oh well. Force be with you!

---

### Post by s3kt0r on 2009-01-31
> **alex.rayu said:**
> Why, don't want to learn to patch and compile from git? Oh well. Force be with you!

This is an interesting topic. Although I don't have need for any of those programs -work or hobby reasons- I do have an interest on getting things working, especially by emulation.
Going to find me some materials and learn something about compiling using GIT, been reading those three letters for sometime and have become curious.
Any good links for a seeker of the force?
Tried installing CS2 (ps) in wine 1.1.2 and it worked. But messing around with my previous install of hardy eventually required the install of intrepid, so now I don't know if it will work. Also kernel was 2.6.26 I guess. I now have 2.6.28.

---

### Post by AllRadioisDead on 2009-01-31
> **alex.rayu said:**
> Why, don't want to learn to patch and compile from git? Oh well. Force be with you!

To be honest, I'm fairly new to ubuntu and I would have no idea where to start, and it doesn't look like anyone's having much luck with this.

---

### Post by alex.rayu on 2009-01-31
> **ihermit said:**
> To be honest, I'm fairly new to ubuntu and I would have no idea where to start, and it doesn't look like anyone's having much luck with this.

You see, the steps Wine made recently have been gigantic. But there are things that it can not do yet. I am very happy with Ubuntu as a system. I like it much more than I do Windows. But I use Photoshop and Flash for web design. I can't afford making sites with GIMP =)

So, I now use Photoshop CS2 and Flash 8. I also have Windows in another boot partition and a Windows in VirtualBox. I only go there when I need to use Darker color and Lighter color blending modes in CS4. I expect that they will fix wine any time now. 

But yes - for me, "go there, and patch and compile yourself" is not an answer even though I can do that. (Actually I did that and it did not help me =) ) When they fix it they fix it. I expect that will be soon. I wish they would spend more time fixing CS4 support than WOW and other games though.

I recommend to use Windows - either on VirtualBox or in another partition, or not just switch to Ubuntu - until the issue gets resolved.

---

### Post by AllRadioisDead on 2009-01-31
> **alex.rayu said:**
> You see, the steps Wine made recently have been gigantic. But there are things that it can not do yet. I am very happy with Ubuntu as a system. I like it much more than I do Windows. But I use Photoshop and Flash for web design. I can't afford making sites with GIMP =)

So, I now use Photoshop CS2 and Flash 8. I also have Windows in another boot partition and a Windows in VirtualBox. I only go there when I need to use Darker color and Lighter color blending modes in CS4. I expect that they will fix wine any time now. 

But yes - for me, "go there, and patch and compile yourself" is not an answer even though I can do that. (Actually I did that and it did not help me =) ) When they fix it they fix it. I expect that will be soon. I wish they would spend more time fixing CS4 support than WOW and other games though.

I recommend to use Windows - either on VirtualBox or in another partition, or not just switch to Ubuntu - until the issue gets resolved.

I'm a 16 year old student, and I'm starting to get into web design as well. Recently I also started picking up on C++, which I'm trying to learn. Ontop of that, I'm also a gamer (Maplestory, La Tale, Gunbound, Atlantica, WoW.) And finally, I'm a zune user, so there are a few reasons I can't switch to Ubuntu as my main OS.

 I'd love, to, as I love everything about Ubuntu (Customization, UI, Compiz-Fusion, Package manager), and it's a shame really. I could always buy an ipod, but I'm in the market for a new cell phone right now and I don't have a job. I could use CS3 for time being, which I'll probably attempt to install, but I still love how much cleaner CS4 looks. None of the games work except for WOW, which still apparently isn't perfect. I agree that Wine is able to do amazing things, but it's not quite there for me yet. 

I hate running virtual machines, I'm not sure why, maybe because I don't like running a seperate computer in a window, or having to start up a second OS just to run a program. The support of the amazing Ubuntu community has made my linux experience a lot easier though, so I'm thankfull for that.:p

---

### Post by alex.rayu on 2009-02-01
Yes, community here is wonderful and helpful. Just as the whole Ubuntu project.

---

### Post by Romi on 2009-02-02
But the fix is in the GIT, so it will be in the next release, won't it?

---

### Post by alex.rayu on 2009-02-02
If it were so, it would have made into this release. The fix for *me* was only a suggested patch for git version.

---

### Post by AllRadioisDead on 2009-02-02
Hmm, so there will be no fix?

---

### Post by alex.rayu on 2009-02-03
There will be a fix, and I hope soon. I am checking the wine web site regularly for the reports. The issue wine weekly, and any new issue can fix it. They are definitely working on the Text tool, and my issue with gdiplus crashing does not seem to be spread significantly.

---

### Post by ttlnb on 2009-02-06
i tried to install with hardy and latest wine 1.1.4, the installation went ok, but the program fails to run. now i can't uninstall it either, it just hangs. :(

how can i at least uninstall it? deletign the libraries seems wrong somehow.

---

### Post by alex.rayu on 2009-02-06
The report is that it should work. You should have unstalled gdiplus and msxml3. It does not work for me though. The reason I have discovered is the intel x3100 drivers.

You can't delete it well. It's safe to remove the whole .wine folder unless you have something else you need installed there.

---

### Post by donkyhotay on 2009-02-06
> **alex.rayu said:**
> The report is that it should work. You should have unstalled gdiplus and msxml3. It does not work for me though. The reason I have discovered is the intel x3100 drivers.

You can't delete it well. It's safe to remove the whole .wine folder unless you have something else you need installed there.

You also have to install ie6 with winetricks and gecko manually [http://wiki.winehq.org/Gecko](http://wiki.winehq.org/Gecko) in order to install cs4 programs. I have recently tested out the patch that fixes the persistent menu problem that many cs4 programs have. It works really well and I hope it gets implemented into GIT soon but of course requires manual patching and compiling which isn't for everybody. I might try creating a script or howto over the weekend if I have time though.

---

### Post by alex.rayu on 2009-02-06
From what I heard it should already have been implemented in 1.1.14.

---

### Post by donkyhotay on 2009-02-06
Nope, just downloaded and compiled wine from the GIT repositories just now. The problem with menus vanishing came right back so the patch is not currently in the GIT repository.

//edit: just now being 02/06/09

---

### Post by rfkrocktk on 2009-02-25
I'm definitely all ears on this one. I already cast my vote for Flash CS3 and CS4 support. I'm a Flash developer, so I can usually use Flex, but for throwing together skins and animation, the Flash IDE is near invaluable. I have CS3 running on Wine at the moment, but it's a no-install version and it takes just about 10 minutes to start, and it has the whole "invisible panels" thing, but that can be worked around :P

Like stated in previous posts, as soon as Wine can claim platinum status on all CS products (or even just Flash, Dreamweaver, and Photoshop), I will not use Windows anymore. It's the only thing holding me back from complete Ubuntu migration. I've got basically everything I need except Flash and Photoshop. The sooner I can say goodbye to Micro$oft, the better, I have to work on Vista at my job and I'm about to just reformat my computer and install Ubuntu. I've already got Ubuntu 8.04 on my personal laptop and I am extremely happy with it. Like I said, everything I need, eg: Eclipse and Firefox, works just fine on Ubuntu.

Everything except for CS3/CS4, which hopefully will soon be patched! Here's hoping that Adobe will compile their next CS version in Mono so there'll be ONE version for Windows, Mac, AND LINUX!

---

### Post by alex.rayu on 2009-02-26
Absolutely! I do Photoshop and Flash as well (not Flex though). And yes, It's very hard for me in Ubuntu. I like Ubuntu very much, and it's quite itchy to have to sacrifice safety and intuitiveness in Ubuntu for being able to work in Photoshop and Flash. There is no alternative for Flash or Photoshop currently. At least, not the ones that would make one competitive on the wider market.

---

### Post by CK05 on 2009-03-27
Hi, thanks to this wonderful post

[http://ubuntuforums.org/showpost.php?p=6935335&postcount=31](http://ubuntuforums.org/showpost.php?p=6935335&postcount=31)

I was able to get PS4 running but has anyone else noticed that the menus won't go away? When you use the menus they kind of "build up" and won't go away!

---

### Post by Rackstar on 2009-04-17
There is a patch for the menu's that won't go away.

The installer won't work for me. I tried to do all like in above post, but it starts by saying:
Checking system profile (in Adobe Installer screen), Then gives Adobe error: Could not install, please contact adobe support.

(Loosely translated from dutch)

Can anyone help? I really tried everything, as a photographer, I need photoshop bad.

Or should I make a new thread?

---

### Post by alex.rayu on 2009-04-17
No no fix so far. They have assigned "Gold" to it again though, even tho it won't even install!

---

### Post by Rackstar on 2009-06-14
> **rmausser said:**
> I have created a working version of Flash CS3... its not CS4 but I can't get that to work yet.

download here

<snip>

and unzip to a folder. No need to install, run flash.exe with Wine. 

There are still minor cosmetic issues, and you need a fairly fast PC to run it, but everything works.

Is this legal?

---

### Post by viktor489 on 2009-07-15
Something new!
I love Ubuntu, but my work depend totally of Adobe Master Suite CS4, i have been reading all the conversations in the forums and I want to ask if **somebody know how to run the suite CS4, specially Illustrator CS4 and Flash CS4**. I'm starting to use Inkscape in place of Illustrator and it work fine, but my leader team want everything in Illustrator (Because we use the 3D feature too much).
I'm using Virtual Box now days, but is too slow when you are working with heavy vectors, I hope find how to fix this problem, because I dont want to use another Microsoft software in my life.
Thankyou!

(This is the first time that I use this kind of tools in internet, I never use the forums because I feel it doesn't work)


PD: Sorry for my english, I'm from a little town in the middle of Mexico)

---

### Post by codyxx on 2009-07-23
Try VMWare. 'Tis much faster than VirtualBox from my experience.

---

### Post by dannymichel on 2009-07-26
> **viktor489 said:**
> Something new!
I love Ubuntu, but my work depend totally of Adobe Master Suite CS4, i have been reading all the conversations in the forums and I want to ask if **somebody know how to run the suite CS4, specially Illustrator CS4 and Flash CS4**. I'm starting to use Inkscape in place of Illustrator and it work fine, but my leader team want everything in Illustrator (Because we use the 3D feature too much).
I'm using Virtual Box now days, but is too slow when you are working with heavy vectors, I hope find how to fix this problem, because I dont want to use another Microsoft software in my life.
Thankyou!

(This is the first time that I use this kind of tools in internet, I never use the forums because I feel it doesn't work)


PD: Sorry for my english, I'm from a little town in the middle of Mexico)

i will pray with u

---

### Post by cosmophobia on 2010-03-19
> **talofo said:**
> Hi. I've just finnish it. How did you know? :p

Well, I've tried the Dreamweaver CS4 Trial and it opens. :):):):)

Now we must have some bugs already reported on wineHQ.
Update: Like in here: [http://bugs.winehq.org/show_bug.cgi?id=16430](http://bugs.winehq.org/show_bug.cgi?id=16430)


Here's the HOW TO:

1)
Install Wine 1.1.10:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)



2)
Install cabextract:
sudo apt-get install cabextract



3)
Install Wine Gecko Package.



4)
Install Winetricks:
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

chmod +x winetricks


5) 
Install native gdiplus:
$ sh winetricks gdiplus 



6) And Native msxml3:
$ sh winetricks msxml3 



7) The IE6 libs are needed for splash screen:
./winetricks corefonts ie6

#######################################################################
Go to a native windows system32 directory and copy: odbc32.dll
then Paste on wine/system32/

do: winecfg
In New Override for Library option choose: odbc32
Click Add. Make sure you have something like this: odbc32(native, builtin)
Click Apply then OK to exit.
########################################################################

8) Repeat last step for: odbcint.dll


Now we are ready to try:
Go to Dreamweaver Setup Directory, and running not with double click BUT, from the command line. wine Dreamweaver.exe

gl.


Notes:
If doing the trial, you might get lost finding the radio button to select it. It is... invisible! Just click to the left of the "I want to install and use..." line where you'd think it would be. A box will appear.



All this info is just compiled infos from here and there, that i've put together and make it to work, I have no credits from this.


Regards,
MEM

I am following the HOWTO, but on the step where i should override odbcint.dll i am stuck. In my winecfg menu, where i have to choose odbcint.dll file to be overrided, the file is not present. I don't know ( but i suppose ) if it is critical to my installation. Actually the file is present in the .wine/drive_c/windows/system32 directory, but is not present in the wine.cfg.

Please reply with solution or direction what should i do

---

### Post by nickthrolson on 2010-04-13
VM Ware is quick fix for users that need cs4 master collection on there ubuntu os. I hope in the future adobe will support linux not just osx & windows.

---

### Post by joshua121 on 2010-10-31
Thanks to multiple forums and tutorials I've found, I have some of the Adobe stuff working in Ubuntu 10.04.... Photoshop CS5 & CS4, Dreamweaver CS5 & CS4, Flash CS5, Fireworks CS5 & CS4, InDesign CS5 & CS4 and Soundbooth CS5 loads but it says it's missing the proper codecs. 

This doesn't work for Illustrator CS4 or CS5, so if you know a way to make that work, I'm all ears.


Anyway, I'll lay out what I did.

Make sure you have a fresh copy of wine by deleting anything that is there now. Open up terminal and paste in these values... you'll be asked for your password.

[COLOR="Red"]sudo apt-get autoremove wine[/COLOR]

That will remove wine

[COLOR="Red"]rm -r -v .wine[/COLOR]

removes the wine directory



Now that you're clean.

Let's set up and install wine, 
run these 5 commands in terminal in sequence.

[COLOR="Red"]sudo add-apt-repository ppa:ubuntu-wine/ppa 

sudo apt-get update 

sudo apt-get install wine1.3

winetricks vcrun2008 msxml3 atmlib gdiplus (this one takes a while)

winecfg
[/COLOR]




Now boot into windows (I'm running win7 ultimate, but most of the tutorials I read people were using XP, so I'm not sure if that matters.)

Install all of the adobe stuff in windows normally.


Once you have installed everything in windows, you need to open regedit and export the registry/Keys for "local machine -  software - adobe" and copy that file to your home folder in Ubuntu

You will also need to copy these files to your ubuntu wine directories as well.

&#8220;C:\Program Files\Adobe\" to "$HOME/.wine/drive_c/Program Files/Adobe"
&#8220;C:\Program Files\Common Files\Adobe" to &#8220;$HOME/.wine/drive_c/Program Files/Common Files/Adobe"
&#8220;C:\Documents and Settings\All Users\Application Data\Adobe\CS5&#8221; to &#8220;$HOME/.wine/drive_c/users/Public/Application Data/Adobe/CS5&#8221;

We are almost there.




Back in Ubuntu make sure the adobe.reg file is in your home folder, open terminal and run:

[COLOR="red"]wine regedit adobe.reg
[/COLOR]

Now run winecfg, goto Library, select rpcrt4 then Edit and select Builtin then Native.

Then in terminal run:

[COLOR="red"]sh winetricks vcrun2005sp1 [/COLOR]

(once or twice I got an error with this command and had to run)

[COLOR="red"]sudo winetricks vcrun2005sp1[/COLOR]

Run the config one more time for good measure.

[COLOR="red"]winecfg[/COLOR]

Now you should be able to load you're adobe programs from the terminal... 

[COLOR="red"]cd .wine/drive_c/Program\ Files/Adobe/Adobe\ Dreamweaver\ CS5/

wine Dreamweaver.exe[/COLOR]

(to run the other programs you will just go to their directories instead and call their exe)

you will see this error 

[IMG]http://lh5.ggpht.com/_47w2iQ8-NcE/TGZISZ2dZrI/AAAAAAAACpE/ycA5YAxW6T8/Program%20Error_008%5B4%5D.png?imgmax=800[/IMG]

but worry not, you can close it and continue anyway.


Many thanks to the peoples who helped me get this far, Firefly2005, Vehuel, and Thanh Tran.

here are the original tutorials that I used.

[http://int3ractive.blogspot.com/2010/08/how-to-run-flash-cs5-on-ubuntu-with.html]("http://int3ractive.blogspot.com/2010/08/how-to-run-flash-cs5-on-ubuntu-with.html")

[http://ubuntuforums.org/showthread.php?t=1484552]("http://ubuntuforums.org/showthread.php?t=1484552")

I hope that this helps lots of people, If you have questions... I'm not sure if I'll really be able to help, but I will definitely try.

Joshua

---

### Post by kmarinis88 on 2010-11-02
TNX SO MUCH man! I've seen some tutorials but only for Photoshop! Never though you could run the whole suite in Ubuntu.

However I am mostly interested in Photoshop, Flash and Flash Catalyst. From your sayings Photoshop and Flash are ok. What about Flash Catalyst? Tried that out yet?

If it can ran Catalyst I'm ditching MS and switching to Ubuntu forever...

---

