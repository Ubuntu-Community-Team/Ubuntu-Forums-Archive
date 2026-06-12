---
title: "kindle in wine"
date: 2016-04-29
forum: Wine
---

### Post by wyndlass on 2016-04-29
i have an amazon account and just installed kindle in wine but it won't let me connect to download all of my books. i got around this problem before but can recall what i did. i keeps telling me to try again when i use my amazon account login in stuff. kind of like i don't have an account, i guess. any help is greatly appreciated. thanx


jadaja.

---

### Post by wyndlass on 2016-04-29
btw i'm on a hp pavilon g7 2017us running wily using the newest stable version of wine.

---

### Post by QDR06VV9 on 2016-04-29
I am trying to remember something to effect of setting Wineconfig to windows 7?
I will check for sure or maybe this will jog your memory.
Here was the link that I used [http://askubuntu.com/questions/144463/how-can-i-get-kindle-for-pc-working-on-ubuntu-12-04](http://askubuntu.com/questions/144463/how-can-i-get-kindle-for-pc-working-on-ubuntu-12-04)
And i used Calibre and still use it (not using kindle now though).

---

### Post by wyndlass on 2016-05-03
runrickus, i got past the registration part by using a different kindle app version but i ran into a problem that i had before, some of the books won't open to read and the app shuts down.  i get this window



which lead me to this,


```


Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00557ef2).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00557ef2 ESP:0033d7cc EBP:065751c4 EFLAGS:00210202(  R- --  I   - - - )
 EAX:0033d7dc EBX:121e8788 ECX:00000000 EDX:0033d7dc
 ESI:065751a8 EDI:ffffffff
Stack dump:
0x0033d7cc:  c7f6ff10 ffffffff 065751a8 121e8788
0x0033d7dc:  00000000 00000000 00b7c49b ffffffff
0x0033d7ec:  0055b1b0 121e8700 06603ad0 12323f38
0x0033d7fc:  c7f6f000 0033d834 00b7ab80 ffffffff
0x0033d80c:  0055b1d9 c7f6f0d4 065b5ea8 121e8788
0x0033d81c:  06b63e18 00000001 65505b00 ffffff00
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x00557ef2 in kindle (+0x157ef2) (0x065751c4)
  1 0x12323f38 (0x06603ad0)
  2 0x06bd0bd0 (0x0271adc4)
  3 0x0079d530 in kindle (+0x39d52f) (0x0079d670)
  4 0xc0851840 (0x8b04418b)
0x00557ef2: movl	0x0(%ecx),%edx
Modules:
Module	Address			Debug info	Name (153 modules)
PE	  340000-  37d000	Deferred        ssleay32
PE	  380000-  3ba000	Deferred        webcoreviewer
PE	  3c0000-  3d0000	Deferred        pthreadvc2
PE	  400000- 2c48000	Export          kindle
PE	 2d60000- 2e7c000	Deferred        libeay32
PE	 2e80000- 2fc0000	Deferred        qtscript4
PE	 2fc0000- 30b5000	Deferred        libxml2
PE	 30c0000- 31e7000	Deferred        javascriptcore
PE	 31f0000- 3294000	Deferred        cflite
PE	 32a0000- 39bb000	Deferred        libwebcore
PE	 39c0000- 39fd000	Deferred        libjpeg
PE	 3a10000- 3a1a000	Deferred        qgif4
PE	 4830000- 4864000	Deferred        qjpeg4
PE	 6da0000- 6dea000	Deferred        kloplugin
PE	 7b30000- 7bf2000	Deferred        flashcardsplugin
PE	 7c00000- 7f66000	Deferred        keduftueplugin
PE	 7f70000- 7f9f000	Deferred        notebookexportplugin
PE	 7fa0000- 804e000	Deferred        sqlcipherplugin
PE	10000000-10c2f000	Deferred        qtwebkit4
PE	4a800000-4a8eb000	Deferred        icuuc46
PE	4a900000-4aa36000	Deferred        icuin46
PE	4ad00000-4bb80000	Deferred        icudt46
PE	5a4c0000-5a4d4000	Deferred        zlib1
PE	61000000-61058000	Deferred        qtxml4
PE	62000000-6209a000	Deferred        qtsql4
PE	64000000-640f9000	Deferred        qtnetwork4
PE	65000000-657da000	Deferred        qtgui4
PE	67000000-67269000	Deferred        qtcore4
PE	78050000-780b9000	Deferred        msvcp100
PE	78aa0000-78b5e000	Deferred        msvcr100
ELF	7b800000-7ba55000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba55000	\               kernel32
ELF	7bc00000-7bcd9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcd9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c42c000-7c467000	Deferred        winhttp<elf>
  \-PE	7c430000-7c467000	\               winhttp
ELF	7c467000-7c46e000	Deferred        libnss_dns.so.2
ELF	7c496000-7c520000	Deferred        gdiplus<elf>
  \-PE	7c4a0000-7c520000	\               gdiplus
ELF	7cecc000-7cf0e000	Deferred        rsaenh<elf>
  \-PE	7ced0000-7cf0e000	\               rsaenh
ELF	7cf0e000-7cf28000	Deferred        imagehlp<elf>
  \-PE	7cf10000-7cf28000	\               imagehlp
ELF	7cf28000-7cf46000	Deferred        wintab32<elf>
  \-PE	7cf30000-7cf46000	\               wintab32
ELF	7d068000-7d07d000	Deferred        libgpg-error.so.0
ELF	7d07d000-7d09b000	Deferred        libgcc_s.so.1
ELF	7d09b000-7d14a000	Deferred        libgcrypt.so.20
ELF	7d14a000-7d170000	Deferred        liblzma.so.5
ELF	7d170000-7d179000	Deferred        librt.so.1
ELF	7d179000-7d205000	Deferred        libsystemd.so.0
ELF	7d205000-7d20f000	Deferred        libffi.so.6
ELF	7d20f000-7d227000	Deferred        libresolv.so.2
ELF	7d227000-7d22c000	Deferred        libkeyutils.so.1
ELF	7d22c000-7d286000	Deferred        libdbus-1.so.3
ELF	7d286000-7d312000	Deferred        libgmp.so.10
ELF	7d312000-7d346000	Deferred        libhogweed.so.4
ELF	7d346000-7d382000	Deferred        libnettle.so.6
ELF	7d382000-7d396000	Deferred        libtasn1.so.6
ELF	7d396000-7d3fa000	Deferred        libp11-kit.so.0
ELF	7d3fa000-7d42b000	Deferred        libk5crypto.so.3
ELF	7d42b000-7d502000	Deferred        libkrb5.so.3
ELF	7d502000-7d645000	Deferred        libgnutls-deb0.so.28
ELF	7d645000-7d6cc000	Deferred        libcups.so.2
ELF	7d72c000-7d739000	Deferred        libkrb5support.so.0
ELF	7d739000-7d73e000	Deferred        libcom_err.so.2
ELF	7d73e000-7d790000	Deferred        libgssapi_krb5.so.2
ELF	7d7b8000-7d7ee000	Deferred        uxtheme<elf>
  \-PE	7d7c0000-7d7ee000	\               uxtheme
ELF	7d7ee000-7d7f5000	Deferred        libxfixes.so.3
ELF	7d7f5000-7d800000	Deferred        libxcursor.so.1
ELF	7d800000-7d812000	Deferred        libxi.so.6
ELF	7d812000-7d816000	Deferred        libxcomposite.so.1
ELF	7d816000-7d823000	Deferred        libxrandr.so.2
ELF	7d823000-7d82f000	Deferred        libxrender.so.1
ELF	7d82f000-7d836000	Deferred        libxxf86vm.so.1
ELF	7d836000-7d83a000	Deferred        libxinerama.so.1
ELF	7d83a000-7d841000	Deferred        libxdmcp.so.6
ELF	7d841000-7d845000	Deferred        libxau.so.6
ELF	7d845000-7d86a000	Deferred        libxcb.so.1
ELF	7d86a000-7d9b5000	Deferred        libx11.so.6
ELF	7d9b5000-7d9ca000	Deferred        libxext.so.6
ELF	7d9ce000-7d9e2000	Deferred        libavahi-client.so.3
ELF	7d9e2000-7d9f0000	Deferred        libavahi-common.so.3
ELF	7d9f2000-7da7f000	Deferred        winex11<elf>
  \-PE	7da00000-7da7f000	\               winex11
ELF	7dac6000-7daef000	Deferred        libexpat.so.1
ELF	7daef000-7db32000	Deferred        libfontconfig.so.1
ELF	7db32000-7db5e000	Deferred        libpng12.so.0
ELF	7db5e000-7dc0b000	Deferred        libfreetype.so.6
ELF	7dc33000-7dc58000	Deferred        iphlpapi<elf>
  \-PE	7dc40000-7dc58000	\               iphlpapi
ELF	7dc58000-7dc74000	Deferred        wsock32<elf>
  \-PE	7dc60000-7dc74000	\               wsock32
ELF	7dc74000-7dcaa000	Deferred        wintrust<elf>
  \-PE	7dc80000-7dcaa000	\               wintrust
ELF	7dcaa000-7dd75000	Deferred        crypt32<elf>
  \-PE	7dcb0000-7dd75000	\               crypt32
ELF	7dd75000-7dda2000	Deferred        msvcr90<elf>
  \-PE	7dd80000-7dda2000	\               msvcr90
ELF	7dda2000-7de4f000	Deferred        msvcrt<elf>
  \-PE	7ddc0000-7de4f000	\               msvcrt
ELF	7de4f000-7df85000	Deferred        msvcp90<elf>
  \-PE	7de90000-7df85000	\               msvcp90
ELF	7df85000-7dfa9000	Deferred        imm32<elf>
  \-PE	7df90000-7dfa9000	\               imm32
ELF	7dfa9000-7e0d4000	Deferred        oleaut32<elf>
  \-PE	7dfc0000-7e0d4000	\               oleaut32
ELF	7e0d4000-7e110000	Deferred        winspool<elf>
  \-PE	7e0e0000-7e110000	\               winspool
ELF	7e110000-7e1f5000	Deferred        comdlg32<elf>
  \-PE	7e120000-7e1f5000	\               comdlg32
ELF	7e1f5000-7e21f000	Deferred        msacm32<elf>
  \-PE	7e200000-7e21f000	\               msacm32
ELF	7e21f000-7e2d7000	Deferred        winmm<elf>
  \-PE	7e230000-7e2d7000	\               winmm
ELF	7e2d7000-7e353000	Deferred        rpcrt4<elf>
  \-PE	7e2e0000-7e353000	\               rpcrt4
ELF	7e353000-7e480000	Deferred        ole32<elf>
  \-PE	7e370000-7e480000	\               ole32
ELF	7e480000-7e578000	Deferred        comctl32<elf>
  \-PE	7e490000-7e578000	\               comctl32
ELF	7e578000-7e7a1000	Deferred        shell32<elf>
  \-PE	7e590000-7e7a1000	\               shell32
ELF	7e7a1000-7e817000	Deferred        shlwapi<elf>
  \-PE	7e7b0000-7e817000	\               shlwapi
ELF	7e817000-7e885000	Deferred        advapi32<elf>
  \-PE	7e820000-7e885000	\               advapi32
ELF	7e885000-7e99d000	Deferred        gdi32<elf>
  \-PE	7e890000-7e99d000	\               gdi32
ELF	7e99d000-7eaeb000	Deferred        user32<elf>
  \-PE	7e9b0000-7eaeb000	\               user32
ELF	7eaeb000-7eb12000	Deferred        mpr<elf>
  \-PE	7eaf0000-7eb12000	\               mpr
ELF	7eb12000-7eb2d000	Deferred        libz.so.1
ELF	7eb2d000-7eba4000	Deferred        wininet<elf>
  \-PE	7eb40000-7eba4000	\               wininet
ELF	7eba4000-7ebd9000	Deferred        ws2_32<elf>
  \-PE	7ebb0000-7ebd9000	\               ws2_32
ELF	7ef4b000-7ef59000	Deferred        libnss_files.so.2
ELF	7ef59000-7ef66000	Deferred        libnss_nis.so.2
ELF	7ef66000-7ef81000	Deferred        libnsl.so.1
ELF	7ef81000-7ef8b000	Deferred        libnss_compat.so.2
ELF	7ef8b000-7efd8000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f73ea000-f73ef000	Deferred        libdl.so.2
ELF	f73ef000-f75aa000	Deferred        libc.so.6
ELF	f75ab000-f75c8000	Deferred        libpthread.so.0
ELF	f75f0000-f77a6000	Dwarf           libwine.so.1
ELF	f77a8000-f77cc000	Deferred        ld-linux.so.2
ELF	f77ce000-f77cf000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files (x86)\Amazon\Kindle\Kindle.exe
	00000033    0
	00000032    0
	00000030    0
	0000002f    0
	0000002e    0
	0000002b    0
	0000002a    0
	00000029    0
	00000028    0
	00000009    0 <==
0000000e services.exe
	0000002d    0
	0000001e    0
	00000019    0
	00000018    0
	00000016    0
	00000014    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001d    0
	0000001a    0
	00000017    0
	00000013    0
0000001b plugplay.exe
	00000021    0
	00000020    0
	0000001c    0
00000025 explorer.exe
	00000027    0
	00000026    0
System information:
    Wine build: wine-1.6.2
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 4.2.0-35-generic


```

can you or anyone else help me with this?  thanx again

---

### Post by wyndlass on 2016-05-03
oops it put the screenshot at the bottom, leaning curve.

---

