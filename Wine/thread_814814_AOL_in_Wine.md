---
title: "AOL in Wine?"
date: 2008-06-01
forum: Wine
---

### Post by kevin11951 on 2008-06-01
i need to use AOL 9.1 (or whatever the newest is) in ubuntu, meaning wine.

it installs okay, but when i run it i get this error:

Im running hardy 8.04, wine 1.0 rc3, and got it from the ubuntu repo in the wine page.

```
ksoviero@ksoviero-laptop:~$ wine "C:\Program Files\AOL 9.1\aol.exe"fixme:process:SetProcessShutdownParameters (0000012c, 00000001): partial stub.
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
wine: Unhandled page fault on read access to 0x00000008 at address 0x4000a01c (thread 0066), starting debugger...
Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x4000a01c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:4000a01c ESP:0060ecf0 EBP:0060ecf8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:0060ed24 EBX:00000000 ECX:00000000 EDX:0000006e
 ESI:00000000 EDI:0015c4c0
Stack dump:
0x0060ecf0:  6c04a010 0015c2e0 0060ed2c 6c006987
0x0060ed00:  0060ed24 00000004 0060ef3c 00000000
0x0060ed10:  0015ad37 0060ef3c 0060ef6c 00000000
0x0060ed20:  0060ed50 0060ef3c 00000000 0060ed50
0x0060ed30:  6c01142d 0015a2f8 0015c3b0 00000010
0x0060ed40:  00000004 5544524a 00000000 00000000
Backtrace:
=>1 0x4000a01c in xprt6 (+0xa01c) (0x0060ecf8)
  2 0x6c006987 in aolsvcmgr (+0x6987) (0x0060ed2c)
  3 0x6c01142d in aolsvcmgr (+0x1142d) (0x0060ed50)
  4 0x6c01178b in aolsvcmgr (+0x1178b) (0x0060ed5c)
  5 0x40015c4c in xprt6 (+0x15c4c) (0x0060edc0)
  6 0x40016153 in xprt6 (+0x16153) (0x0060ee1c)
  7 0x400177df in xprt6 (+0x177df) (0x0060ee5c)
  8 0x40017965 in xprt6 (+0x17965) (0x0060ee9c)
  9 0x6c016a01 in aolsvcmgr (+0x16a01) (0x0060eeb4)
  10 0x6c011bd5 in aolsvcmgr (+0x11bd5) (0x0060eee8)
  11 0x6c0145da in aolsvcmgr (+0x145da) (0x0060ef78)
  12 0x6c014876 in aolsvcmgr (+0x14876) (0x0060efac)
  13 0x6c014af5 in aolsvcmgr (+0x14af5) (0x0060f190)
  14 0x6c014bf7 in aolsvcmgr (+0x14bf7) (0x0060f1a4)
  15 0x6c014c67 in aolsvcmgr (+0x14c67) (0x0060f1f8)
  16 0x6c0178db in aolsvcmgr (+0x178db) (0x0060f244)
  17 0x6c01825f in aolsvcmgr (+0x1825f) (0x0060f2a0)
  18 0x6c0182c0 in aolsvcmgr (+0x182c0) (0x0060f2f4)
  19 0x6c01839f in aolsvcmgr (+0x1839f) (0x0060f310)
  20 0x6c010efc in aolsvcmgr (+0x10efc) (0x0060f34c)
  21 0x6c010fbc in aolsvcmgr (+0x10fbc) (0x0060f378)
  22 0x00374cb5 in waol (+0x24cb5) (0x0060f3a0)
  23 0x0035f772 in waol (+0xf772) (0x0060f3d8)
  24 0x00364374 in waol (+0x14374) (0x0060fa24)
  25 0x0040114b in waol (+0x114b) (0x0060fe60)
  26 0x004016cd in waol (+0x16cd) (0x0060ff08)
  27 0x7b877b27 in kernel32 (+0x57b27) (0x0060ffe8)
0x4000a01c: cmpl	%ebx,0x8(%esi)
Modules:
Module	Address			Debug info	Name (123 modules)
PE	  350000-  3ac000	Export          waol
PE	  400000-  40b000	Export          waol
PE	10000000-10014000	Deferred        xmltok
PE	20000000-2000d000	Deferred        xmlparse
PE	40000000-4003d000	Export          xprt6
PE	40100000-401bc000	Deferred        coolcore47
PE	60000000-60041000	Deferred        comm
PE	60580000-60629000	Deferred        supersub
PE	60a00000-60a16000	Deferred        proxymgr
PE	62100000-62109000	Deferred        synccore
PE	635c0000-635c7000	Deferred        appdata
PE	67180000-6726f000	Deferred        manager
PE	68000000-6800f000	Deferred        zlib
PE	6c000000-6c097000	Export          aolsvcmgr
PE	6f200000-6f20d000	Deferred        acfbase
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7de05000-7de2b000	Deferred        msacm32<elf>
  \-PE	7de10000-7de2b000	\               msacm32
ELF	7de2b000-7de42000	Deferred        msacm32<elf>
  \-PE	7de30000-7de42000	\               msacm32
ELF	7de42000-7df05000	Deferred        libasound.so.2
ELF	7df05000-7df3b000	Deferred        winealsa<elf>
  \-PE	7df10000-7df3b000	\               winealsa
ELF	7df3b000-7df3f000	Deferred        libgpg-error.so.0
ELF	7df3f000-7df8c000	Deferred        libgcrypt.so.11
ELF	7df8c000-7df9c000	Deferred        libtasn1.so.3
ELF	7df9c000-7dfa4000	Deferred        libkrb5support.so.0
ELF	7dfa4000-7dfd6000	Deferred        libcrypt.so.1
ELF	7dfd6000-7e04b000	Deferred        libgnutls.so.13
ELF	7e04b000-7e06e000	Deferred        libk5crypto.so.3
ELF	7e06e000-7e0fb000	Deferred        libkrb5.so.3
ELF	7e0fb000-7e124000	Deferred        libgssapi_krb5.so.2
ELF	7e124000-7e157000	Deferred        libcups.so.2
ELF	7e158000-7e16c000	Deferred        midimap<elf>
  \-PE	7e160000-7e16c000	\               midimap
ELF	7e1b8000-7e1eb000	Deferred        uxtheme<elf>
  \-PE	7e1c0000-7e1eb000	\               uxtheme
ELF	7e1eb000-7e1f4000	Deferred        libxcursor.so.1
ELF	7e1f4000-7e1f9000	Deferred        libxfixes.so.3
ELF	7e1f9000-7e1fc000	Deferred        libxcomposite.so.1
ELF	7e1fc000-7e202000	Deferred        libxrandr.so.2
ELF	7e202000-7e20a000	Deferred        libxrender.so.1
ELF	7e20a000-7e20d000	Deferred        libxinerama.so.1
ELF	7e20d000-7e212000	Deferred        libxdmcp.so.6
ELF	7e212000-7e22a000	Deferred        libxcb.so.1
ELF	7e22a000-7e22c000	Deferred        libxcb-xlib.so.0
ELF	7e22c000-7e22f000	Deferred        libxau.so.6
ELF	7e22f000-7e316000	Deferred        libx11.so.6
ELF	7e316000-7e324000	Deferred        libxext.so.6
ELF	7e324000-7e329000	Deferred        libxxf86vm.so.1
ELF	7e32c000-7e32f000	Deferred        libkeyutils.so.1
ELF	7e339000-7e33c000	Deferred        libcom_err.so.2
ELF	7e33e000-7e3d5000	Deferred        winex11<elf>
  \-PE	7e350000-7e3d5000	\               winex11
ELF	7e415000-7e436000	Deferred        libexpat.so.1
ELF	7e436000-7e460000	Deferred        libfontconfig.so.1
ELF	7e460000-7e475000	Deferred        libz.so.1
ELF	7e475000-7e4e5000	Deferred        libfreetype.so.6
ELF	7e4fa000-7e50e000	Deferred        lz32<elf>
  \-PE	7e500000-7e50e000	\               lz32
ELF	7e50e000-7e527000	Deferred        version<elf>
  \-PE	7e510000-7e527000	\               version
ELF	7e527000-7e566000	Deferred        urlmon<elf>
  \-PE	7e530000-7e566000	\               urlmon
ELF	7e566000-7e57f000	Deferred        rasapi32<elf>
  \-PE	7e570000-7e57f000	\               rasapi32
ELF	7e57f000-7e5a0000	Deferred        mpr<elf>
  \-PE	7e590000-7e5a0000	\               mpr
ELF	7e5a0000-7e5ee000	Deferred        wininet<elf>
  \-PE	7e5b0000-7e5ee000	\               wininet
ELF	7e5ee000-7e680000	Deferred        winmm<elf>
  \-PE	7e600000-7e680000	\               winmm
ELF	7e680000-7e6a0000	Deferred        imm32<elf>
  \-PE	7e690000-7e6a0000	\               imm32
ELF	7e6a0000-7e6d6000	Deferred        winspool<elf>
  \-PE	7e6b0000-7e6d6000	\               winspool
ELF	7e6d6000-7e795000	Deferred        comctl32<elf>
  \-PE	7e6e0000-7e795000	\               comctl32
ELF	7e795000-7e7ee000	Deferred        shlwapi<elf>
  \-PE	7e7a0000-7e7ee000	\               shlwapi
ELF	7e7ee000-7e8fe000	Deferred        shell32<elf>
  \-PE	7e800000-7e8fe000	\               shell32
ELF	7e8fe000-7e9a9000	Deferred        comdlg32<elf>
  \-PE	7e910000-7e9a9000	\               comdlg32
ELF	7e9a9000-7e9d5000	Deferred        ws2_32<elf>
  \-PE	7e9b0000-7e9d5000	\               ws2_32
ELF	7e9d5000-7e9ef000	Deferred        wsock32<elf>
  \-PE	7e9e0000-7e9ef000	\               wsock32
ELF	7e9ef000-7ea91000	Deferred        oleaut32<elf>
  \-PE	7ea00000-7ea91000	\               oleaut32
ELF	7ea91000-7eaa4000	Deferred        libresolv.so.2
ELF	7eaa4000-7eac2000	Deferred        iphlpapi<elf>
  \-PE	7eab0000-7eac2000	\               iphlpapi
ELF	7eac2000-7eb23000	Deferred        rpcrt4<elf>
  \-PE	7ead0000-7eb23000	\               rpcrt4
ELF	7eb23000-7ebc7000	Deferred        ole32<elf>
  \-PE	7eb30000-7ebc7000	\               ole32
ELF	7ebc7000-7ec31000	Deferred        msvcrt<elf>
  \-PE	7ebe0000-7ec31000	\               msvcrt
ELF	7ec31000-7eccc000	Deferred        gdi32<elf>
  \-PE	7ec40000-7eccc000	\               gdi32
ELF	7eccc000-7ee13000	Deferred        user32<elf>
  \-PE	7ecf0000-7ee13000	\               user32
ELF	7ee13000-7ee65000	Deferred        advapi32<elf>
  \-PE	7ee20000-7ee65000	\               advapi32
ELF	7ee65000-7ee70000	Deferred        libnss_files.so.2
ELF	7ee70000-7ee88000	Deferred        libnsl.so.1
ELF	7ee88000-7ee91000	Deferred        libnss_compat.so.2
ELF	7ee93000-7eea6000	Deferred        msimg32<elf>
  \-PE	7eea0000-7eea6000	\               msimg32
ELF	7efc6000-7efeb000	Deferred        libm.so.6
ELF	7eff2000-7effc000	Deferred        libnss_nis.so.2
ELF	f7c32000-f7c36000	Deferred        libdl.so.2
ELF	f7c36000-f7d85000	Deferred        libc.so.6
ELF	f7d86000-f7d9e000	Deferred        libpthread.so.0
ELF	f7db3000-f7ee9000	Deferred        libwine.so.1
ELF	f7eeb000-f7f0a000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
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
0000003c 
	00000020    0
	0000001a    0
	00000030    0
	00000046    0
	00000035    0
	00000038    0
	00000031    0
	00000029    0
	00000033    0
	00000042    0
	0000003e    0
	0000000b    0
	00000044    0
	00000013    0
	0000001b    0
	00000018    0
00000063 
	00000064    0
00000065 (D) C:\Program Files\AOL 9.1\waol.exe
	00000049    0
	00000067    0
	00000066    0 <==
Backtrace:
=>1 0x4000a01c in xprt6 (+0xa01c) (0x0060ecf8)
  2 0x6c006987 in aolsvcmgr (+0x6987) (0x0060ed2c)
  3 0x6c01142d in aolsvcmgr (+0x1142d) (0x0060ed50)
  4 0x6c01178b in aolsvcmgr (+0x1178b) (0x0060ed5c)
  5 0x40015c4c in xprt6 (+0x15c4c) (0x0060edc0)
  6 0x40016153 in xprt6 (+0x16153) (0x0060ee1c)
  7 0x400177df in xprt6 (+0x177df) (0x0060ee5c)
  8 0x40017965 in xprt6 (+0x17965) (0x0060ee9c)
  9 0x6c016a01 in aolsvcmgr (+0x16a01) (0x0060eeb4)
  10 0x6c011bd5 in aolsvcmgr (+0x11bd5) (0x0060eee8)
  11 0x6c0145da in aolsvcmgr (+0x145da) (0x0060ef78)
  12 0x6c014876 in aolsvcmgr (+0x14876) (0x0060efac)
  13 0x6c014af5 in aolsvcmgr (+0x14af5) (0x0060f190)
  14 0x6c014bf7 in aolsvcmgr (+0x14bf7) (0x0060f1a4)
  15 0x6c014c67 in aolsvcmgr (+0x14c67) (0x0060f1f8)
  16 0x6c0178db in aolsvcmgr (+0x178db) (0x0060f244)
  17 0x6c01825f in aolsvcmgr (+0x1825f) (0x0060f2a0)
  18 0x6c0182c0 in aolsvcmgr (+0x182c0) (0x0060f2f4)
  19 0x6c01839f in aolsvcmgr (+0x1839f) (0x0060f310)
  20 0x6c010efc in aolsvcmgr (+0x10efc) (0x0060f34c)
  21 0x6c010fbc in aolsvcmgr (+0x10fbc) (0x0060f378)
  22 0x00374cb5 in waol (+0x24cb5) (0x0060f3a0)
  23 0x0035f772 in waol (+0xf772) (0x0060f3d8)
  24 0x00364374 in waol (+0x14374) (0x0060fa24)
  25 0x0040114b in waol (+0x114b) (0x0060fe60)
  26 0x004016cd in waol (+0x16cd) (0x0060ff08)
  27 0x7b877b27 in kernel32 (+0x57b27) (0x0060ffe8)

```

---

### Post by doorknob60 on 2008-06-01
That means you won't get it to work. Don't worry, lots of programs simply don't work in Wine, because Wine isn't Windows. Also, why on earth do you need to use AOL, maybe there's an open source alternative that would suit?

---

### Post by kevin11951 on 2008-06-01
> **doorknob60 said:**
> That means you won't get it to work. Don't worry, lots of programs simply don't work in Wine, because Wine isn't Windows. Also, why on earth do you need to use AOL, maybe there's an open source alternative that would suit?

well... ive been using ubuntu for a while, and completely weaned myself off windows apps, but my mother is good for ubuntu, but is a die hard AOL (browser) user. so... aol in wine required, or no go.

---

### Post by bapoumba on 2008-06-01
Moved to the Wine subforum. You may get better exposure there.

---

### Post by jrusso2 on 2008-06-01
Have at look at what the WINE folks have to say about it.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=80](http://appdb.winehq.org/objectManager.php?sClass=application&iId=80)

---

### Post by KenBW2 on 2008-06-01
Eugh, AOL. I used to be on that. What does she want from the AOL browser? In my experience it was buggy, bloated, a resource hog, took too long to open and a waste of space (Screen & Disk).
Just convince her that Firefox/Opera is a great browser before she's exposed to Internet Explorer. Also, see if a Firefox/Opera theme would convince her

---

### Post by kevin11951 on 2008-06-01
> **KenBW2 said:**
> Eugh, AOL. I used to be on that. What does she want from the AOL browser? In my experience it was buggy, bloated, a resource hog, took too long to open and a waste of space (Screen & Disk).
Just convince her that Firefox/Opera is a great browser before she's exposed to Internet Explorer. Also, see if a Firefox/Opera theme would convince her

one problem she is very hard headed, when she opens a new window its slightly smaller than others, when she minimizes she has mini versions of those windows, she is just not going to give it up. i tried firefox, and she hated it, after that she wont try anything...

---

### Post by KenBW2 on 2008-06-01
> 
...when she opens a new window its slightly smaller than others, when she minimizes she has mini versions of those windows...


She doesn't like having multiple browser windows cluttering the taskbar?
That's what tabs were made for! If it's that sites' popups cause this, try Opera(.com). It's quite rigorous about keeping one instance, and only opens a new window if and when you explicitly tell it to.

Either way, on Linux or Windows, she needs weaning away from AOL (there's other ISPs you know - what if she decides to switch?).
I know it's probably a difficult task trying to convince your mum about AOL - I had the exact same problem of her being a die-hard AOL user when we were on it. Then we got free internet from her work so we switched. I even recently managed to get her from IE to Firefox!

You need to get from her exactly what is she (a) likes about the AOL browser, and (b) dislikes about the "alternatives". Post her reasons here and I'll do my damndest to find solutions to them. Why? I *hate* AOL, and I want to help every potential Ubuntu convert :D

Let me know...

---

### Post by Roryking on 2008-06-01
You might try finding AOL 8.0 or even 7.0. Also there is something called "Peng" but that is mostly for dialing in to the AOL network, not getting the interface you really want. As much as I hate to say it, you might be better off getting a skin for Firefox and trying to make it *look* like AOL.

Alternatively, I think there's a tutoral to make Virtualbox integrate the Windows desktop on to the Ubuntu desktop, creating a seamless interface... I might have to check that out myself :)

Also, to everyone who immediately started in with the "ZOMG why wud u use aol! aol is teh sux0rrz" - I'd like to remind you that he didn't ask "what do you think of aol," he asked "how can I get it to run on Linux."

---

### Post by KenBW2 on 2008-06-01
@Roryking
I agree with you - I once asked about using Macromedia Fireworks on Wine, and people were saying "oh use Gimp" etc (which I find useless, as it doesn't involve vector shapes). Incidentally I found Inkscape to be a better alternative to both. But anyway it had already been established that AOL would not work under WINE, and he wanted to get his PC converted to Ubuntu. So, in the absence of an alternative, I was attempting to find an alternative that fulfilled his mother's requirements. Just like Inkscape does for me.

---

### Post by Tea4all on 2009-05-04
Set Wine to run as Windows 98. Tested. Won't start though. Says it needs to install a driver.

---

