---
title: "ArcSoft ShowBiz DVD 2 Crashes"
date: 2008-05-11
forum: Wine
---

### Post by anthonyiacono on 2008-05-11
Hey all,
Was trying to install my good ol' ShowBiz DVD 2 on Ubuntu with the latest wine, but this is dumped upon launching.

```
phillip@PHILLIP-UBUNTU:~/.wine/drive_c/Program Files/ArcSoft/ShowBiz DVD 2$ wine ./ShowBiz
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
wine: Unhandled page fault on read access to 0x00000000 at address 0x403829 (thread 0009), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00403829).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00403829 ESP:7f21f744 EBP:7f003af9 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7b8b2888 ECX:00000000 EDX:7f21f764
 ESI:7c73e660 EDI:7f21f8ec
Stack dump:
0x7f21f744:  7f21f760 7f21f8ec 0067a09e 00000000
0x7f21f754:  00000000 b7dad160 7f21f778 b7ccecad
0x7f21f764:  b7dad160 00000008 7e0358bc 7c090448
0x7f21f774:  7c037d50 7e0358bc 7e0273f8 7f21f948
0x7f21f784:  7c090448 000000a0 7e0358bc 7c037d50
0x7f21f794:  7f21f7ec 7c038e0c 7c037de4 000000a0
Backtrace:
=>1 0x00403829 in showbiz (+0x3829) (0x7f003af9)
0x00403829: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (156 modules)
PE	  400000-  67e000	Export          showbiz
PE	10000000-1000f000	Deferred        editwin
PE	66700000-66855000	Deferred        ~df394b.tmp
PE	73dd0000-73ec2000	Deferred        mfc42
PE	76080000-760e1000	Deferred        msvcp60
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c72d000-7c740000	Deferred        sti<elf>
  \-PE	7c730000-7c740000	\               sti
PE	7d250000-7d33f000	Deferred        slshowrc
ELF	7d341000-7d360000	Deferred        imm32<elf>
  \-PE	7d350000-7d360000	\               imm32
ELF	7dc28000-7dc3c000	Deferred        midimap<elf>
  \-PE	7dc30000-7dc3c000	\               midimap
ELF	7dc3c000-7dc53000	Deferred        msacm32<elf>
  \-PE	7dc40000-7dc53000	\               msacm32
ELF	7dc53000-7dd16000	Deferred        libasound.so.2
ELF	7dd16000-7dd4c000	Deferred        winealsa<elf>
  \-PE	7dd20000-7dd4c000	\               winealsa
ELF	7dd4c000-7dd50000	Deferred        libgpg-error.so.0
ELF	7dd50000-7dd9d000	Deferred        libgcrypt.so.11
ELF	7dd9d000-7ddad000	Deferred        libtasn1.so.3
ELF	7ddad000-7ddb0000	Deferred        libkeyutils.so.1
ELF	7ddb0000-7ddb8000	Deferred        libkrb5support.so.0
ELF	7ddb8000-7ddea000	Deferred        libcrypt.so.1
ELF	7ddea000-7de5f000	Deferred        libgnutls.so.13
ELF	7de5f000-7de82000	Deferred        libk5crypto.so.3
ELF	7de82000-7df0f000	Deferred        libkrb5.so.3
ELF	7df0f000-7df38000	Deferred        libgssapi_krb5.so.2
ELF	7df38000-7df6b000	Deferred        libcups.so.2
ELF	7dfc5000-7dff7000	Deferred        uxtheme<elf>
  \-PE	7dfd0000-7dff7000	\               uxtheme
ELF	7dff7000-7e000000	Deferred        libxcursor.so.1
ELF	7e000000-7e005000	Deferred        libxfixes.so.3
ELF	7e005000-7e008000	Deferred        libxcomposite.so.1
ELF	7e008000-7e00e000	Deferred        libxrandr.so.2
ELF	7e00e000-7e016000	Deferred        libxrender.so.1
ELF	7e016000-7e019000	Deferred        libxinerama.so.1
ELF	7e019000-7e01e000	Deferred        libxdmcp.so.6
ELF	7e01e000-7e036000	Deferred        libxcb.so.1
ELF	7e036000-7e039000	Deferred        libxau.so.6
ELF	7e039000-7e120000	Deferred        libx11.so.6
ELF	7e120000-7e12e000	Deferred        libxext.so.6
ELF	7e12e000-7e146000	Deferred        libice.so.6
ELF	7e146000-7e14e000	Deferred        libsm.so.6
ELF	7e15a000-7e15d000	Deferred        libcom_err.so.2
ELF	7e15f000-7e1f0000	Deferred        winex11<elf>
  \-PE	7e170000-7e1f0000	\               winex11
ELF	7e218000-7e239000	Deferred        libexpat.so.1
ELF	7e239000-7e263000	Deferred        libfontconfig.so.1
ELF	7e263000-7e278000	Deferred        libz.so.1
ELF	7e278000-7e2e8000	Deferred        libfreetype.so.6
ELF	7e2e8000-7e2fb000	Deferred        msimg32<elf>
  \-PE	7e2f0000-7e2fb000	\               msimg32
ELF	7e2fb000-7e360000	Deferred        setupapi<elf>
  \-PE	7e310000-7e360000	\               setupapi
ELF	7e360000-7e374000	Deferred        avicap32<elf>
  \-PE	7e370000-7e374000	\               avicap32
ELF	7e374000-7e387000	Deferred        shfolder<elf>
  \-PE	7e380000-7e387000	\               shfolder
ELF	7e387000-7e3a8000	Deferred        mpr<elf>
  \-PE	7e390000-7e3a8000	\               mpr
ELF	7e3a8000-7e3f6000	Deferred        wininet<elf>
  \-PE	7e3b0000-7e3f6000	\               wininet
ELF	7e3f6000-7e435000	Deferred        urlmon<elf>
  \-PE	7e400000-7e435000	\               urlmon
ELF	7e435000-7e47f000	Deferred        dsound<elf>
  \-PE	7e440000-7e47f000	\               dsound
ELF	7e47f000-7e4a7000	Deferred        msvfw32<elf>
  \-PE	7e490000-7e4a7000	\               msvfw32
ELF	7e4a7000-7e4cd000	Deferred        msacm32<elf>
  \-PE	7e4b0000-7e4cd000	\               msacm32
ELF	7e4cd000-7e507000	Deferred        avifil32<elf>
  \-PE	7e4d0000-7e507000	\               avifil32
ELF	7e507000-7e524000	Deferred        msvcirt<elf>
  \-PE	7e510000-7e524000	\               msvcirt
ELF	7e524000-7e58d000	Deferred        msvcrt<elf>
  \-PE	7e530000-7e58d000	\               msvcrt
ELF	7e58d000-7e5e3000	Deferred        ddraw<elf>
  \-PE	7e590000-7e5e3000	\               ddraw
ELF	7e5e3000-7e671000	Deferred        winmm<elf>
  \-PE	7e5f0000-7e671000	\               winmm
ELF	7e671000-7e713000	Deferred        oleaut32<elf>
  \-PE	7e680000-7e713000	\               oleaut32
ELF	7e713000-7e726000	Deferred        libresolv.so.2
ELF	7e728000-7e72d000	Deferred        libxxf86vm.so.1
ELF	7e737000-7e755000	Deferred        iphlpapi<elf>
  \-PE	7e740000-7e755000	\               iphlpapi
ELF	7e755000-7e7b5000	Deferred        rpcrt4<elf>
  \-PE	7e760000-7e7b5000	\               rpcrt4
ELF	7e7b5000-7e859000	Deferred        ole32<elf>
  \-PE	7e7c0000-7e859000	\               ole32
ELF	7e859000-7e88f000	Deferred        winspool<elf>
  \-PE	7e860000-7e88f000	\               winspool
ELF	7e88f000-7e94e000	Deferred        comctl32<elf>
  \-PE	7e8a0000-7e94e000	\               comctl32
ELF	7e94e000-7e9a7000	Deferred        shlwapi<elf>
  \-PE	7e960000-7e9a7000	\               shlwapi
ELF	7e9a7000-7eab1000	Deferred        shell32<elf>
  \-PE	7e9c0000-7eab1000	\               shell32
ELF	7eab1000-7eb5a000	Deferred        comdlg32<elf>
  \-PE	7eac0000-7eb5a000	\               comdlg32
ELF	7eb5a000-7eb6e000	Deferred        lz32<elf>
  \-PE	7eb60000-7eb6e000	\               lz32
ELF	7eb6e000-7eb87000	Deferred        version<elf>
  \-PE	7eb70000-7eb87000	\               version
ELF	7eb87000-7eccd000	Deferred        user32<elf>
  \-PE	7eba0000-7eccd000	\               user32
ELF	7eccd000-7ed68000	Deferred        gdi32<elf>
  \-PE	7ece0000-7ed68000	\               gdi32
ELF	7ed68000-7edb9000	Deferred        advapi32<elf>
  \-PE	7ed70000-7edb9000	\               advapi32
ELF	7efa7000-7efb2000	Deferred        libnss_files.so.2
ELF	7efb2000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
PE	7f220000-7f28f000	Deferred        dgui
PE	7f290000-7f2e8000	Deferred        albumbase
PE	7f2f0000-7f3d1000	Deferred        ezdll
PE	7f3e0000-7f44e000	Deferred        fpxlib
PE	7f450000-7f463000	Deferred        dxpubtool
PE	7f470000-7f763000	Deferred        vdibtool
PE	7f780000-7f786000	Deferred        cdisplayer
PE	7f790000-7f7aa000	Deferred        mediaimport
PE	7f7b0000-7f7c5000	Deferred        mediaexport
PE	7f7d0000-7f7d7000	Deferred        audiofmt
PE	7f7e0000-7f7ec000	Deferred        arctitlemgr
PE	7f7f0000-7f7f8000	Deferred        arcpluginmgr
PE	7f800000-7f809000	Deferred        cdplay
PE	7f810000-7f819000	Deferred        cdrip
PE	7f820000-7f827000	Deferred        wmawriter
PE	7f830000-7f841000	Deferred        dvcombine
PE	7f850000-7f8bf000	Deferred        slideshow
PE	7f8c0000-7f98d000	Deferred        slide
PE	7f990000-7f999000	Deferred        dvrmssave
PE	7f9a0000-7f9d1000	Deferred        panzoom
PE	7f9e0000-7fa2c000	Deferred        capturewdm
PE	7fa30000-7fa51000	Deferred        mpegapi
PE	7fa60000-7fa8c000	Deferred        padusdll
PE	7fa90000-7fb1c000	Deferred        pfc
PE	7fb20000-7fb5d000	Deferred        discapi
PE	7fb60000-7fb7c000	Deferred        vobapi
PE	7fb80000-7fb8b000	Deferred        mpegcheck
PE	7fb90000-7fb97000	Deferred        file2frame
PE	7fdc0000-7fdc9000	Deferred        panzoom_res
PE	7fdd0000-7fde0000	Deferred        pfc1033
ELF	b7c50000-b7c52000	Deferred        libxcb-xlib.so.0
ELF	b7c53000-b7c5c000	Deferred        libnss_compat.so.2
ELF	b7c5d000-b7c61000	Deferred        libdl.so.2
ELF	b7c61000-b7db0000	Deferred        libc.so.6
ELF	b7db1000-b7dc9000	Deferred        libpthread.so.0
ELF	b7dda000-b7eef000	Deferred        libwine.so.1
ELF	b7ef1000-b7f0d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\ArcSoft\ShowBiz DVD 2\ShowBiz.exe
	00000009    0 <==
0000000c 
	00000023    0
	00000022    0
	00000016    0
	00000014    0
	00000010    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000013    0
	00000012    0
00000017 
	00000019    0
	00000018    0
0000001a 
	0000001f    0
	0000001b    0
0000001d 
	00000027    0
	00000026    0
	00000025    0
	00000021    0
	00000020    0
	0000001e    0
Backtrace:
=>1 0x00403829 in showbiz (+0x3829) (0x7f003af9)
```

I am a programmer, but since I have no access to the sourcecode whatsoever, I was wondering if anyone would be able to diagnose the crash. It happens whenever the program is launched.

Thanks,
Anthony

---

