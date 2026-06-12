---
title: "Problems with wine &amp; World of Warcraft"
date: 2009-10-05
forum: x86 64-bit Users
---

### Post by Morimando on 2009-10-05
Hey there.
I searched around for a bit, but didn't come across anything useful. I am running Karmic Koala w/ a NVIDIA Geforce 8800GT ad a Dualcore 3Ghz with 6 GB of RAM.
I installed Karmic yesterday and before that, I've been using Gentoo. Now with Gentoo I had Wine & WoW running smoothly, but now I am getting errors :(
Could be that I need some Options in my xorg.conf, I forgot to back that up and so only have the standard settings there. If anyone knows where to find the list of settings, I'd be thankful.
Now for the error: When trying to start Launcher, I get
```
wine: Unhandled page fault on read access to 0x004a670c at address 0x4a670c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x004a670c in 32-bit code (0x004a670c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:004a670c ESP:0032feac EBP:0032fee8 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7b8c5ff4 ECX:ed85ba8c EDX:0032ff10
 ESI:7ffdf000 EDI:004a670c
Stack dump:
0x0032feac:  7b8778c4 7ffdf000 00000000 00000000
0x0032febc:  00000000 00000000 00000000 00000000
0x0032fecc:  00000000 00000000 00000000 00000000
0x0032fedc:  7bc9eff4 ffc255a4 7ffdf000 0032fef8
0x0032feec:  7bc6c0b4 7ffdf000 ffc255a4 0032ffc8
0x0032fefc:  7bc6c2c0 7b877870 7ffdf000 00000000
Backtrace:
=>0 0x004a670c EntryPoint() in launcher (0x0032fee8)
  1 0x7bc6c0b4 call_thread_func+0xc() in ntdll (0x0032fef8)
  2 0x7bc6c2c0 call_thread_entry_point+0x70() in ntdll (0x0032ffc8)
  3 0x7bc482da in ntdll (+0x382da) (0x0032ffe8)
  4 0xf7e74ebd wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
0x004a670c EntryPoint in launcher: call	0x004b1676
Modules:
Module	Address			Debug info	Name (95 modules)
PE	  400000-  538000	Export          launcher
ELF	7b800000-7b983000	Deferred        kernel32<elf>
  \-PE	7b820000-7b983000	\               kernel32
ELF	7bc00000-7bcbb000	Export          ntdll<elf>
  \-PE	7bc10000-7bcbb000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7dd1f000-7dd24000	Deferred        libgpg-error.so.0
ELF	7dd24000-7dd2d000	Deferred        librt.so.1
ELF	7dd2d000-7dd6f000	Deferred        libdbus-1.so.3
ELF	7dd6f000-7ddeb000	Deferred        libgcrypt.so.11
ELF	7ddeb000-7ddfd000	Deferred        libtasn1.so.3
ELF	7ddfd000-7de01000	Deferred        libkeyutils.so.1
ELF	7de01000-7de0a000	Deferred        libkrb5support.so.0
ELF	7de0a000-7de35000	Deferred        libk5crypto.so.3
ELF	7de35000-7dee7000	Deferred        libkrb5.so.3
ELF	7dee7000-7def8000	Deferred        libavahi-client.so.3
ELF	7def8000-7df05000	Deferred        libavahi-common.so.3
ELF	7df05000-7dfad000	Deferred        libgnutls.so.26
ELF	7dfad000-7dfda000	Deferred        libgssapi_krb5.so.2
ELF	7dfda000-7e024000	Deferred        libcups.so.2
ELF	7e081000-7e0b5000	Deferred        uxtheme<elf>
  \-PE	7e090000-7e0b5000	\               uxtheme
ELF	7e0b5000-7e0c0000	Deferred        libxcursor.so.1
ELF	7e0c0000-7e0c6000	Deferred        libxfixes.so.3
ELF	7e0c6000-7e0ca000	Deferred        libxcomposite.so.1
ELF	7e0ca000-7e0d3000	Deferred        libxrandr.so.2
ELF	7e0d3000-7e0dd000	Deferred        libxrender.so.1
ELF	7e0dd000-7e0e3000	Deferred        libxxf86vm.so.1
ELF	7e0e3000-7e0e6000	Deferred        libxinerama.so.1
ELF	7e0e6000-7e108000	Deferred        imm32<elf>
  \-PE	7e0f0000-7e108000	\               imm32
ELF	7e108000-7e10d000	Deferred        libxdmcp.so.6
ELF	7e10d000-7e12b000	Deferred        libxcb.so.1
ELF	7e12b000-7e12f000	Deferred        libxau.so.6
ELF	7e12f000-7e134000	Deferred        libuuid.so.1
ELF	7e134000-7e263000	Deferred        libx11.so.6
ELF	7e263000-7e273000	Deferred        libxext.so.6
ELF	7e273000-7e28e000	Deferred        libice.so.6
ELF	7e28e000-7e297000	Deferred        libsm.so.6
ELF	7e297000-7e29b000	Deferred        libcom_err.so.2
ELF	7e2b3000-7e358000	Deferred        winex11<elf>
  \-PE	7e2c0000-7e358000	\               winex11
ELF	7e383000-7e3aa000	Deferred        libexpat.so.1
ELF	7e3aa000-7e3d7000	Deferred        libfontconfig.so.1
ELF	7e3d7000-7e456000	Deferred        libfreetype.so.6
ELF	7e472000-7e486000	Deferred        lz32<elf>
  \-PE	7e480000-7e486000	\               lz32
ELF	7e486000-7e4aa000	Deferred        mpr<elf>
  \-PE	7e490000-7e4aa000	\               mpr
ELF	7e4aa000-7e4c0000	Deferred        libz.so.1
ELF	7e4c1000-7e4dc000	Deferred        version<elf>
  \-PE	7e4d0000-7e4dc000	\               version
ELF	7e4dc000-7e536000	Deferred        wininet<elf>
  \-PE	7e4f0000-7e536000	\               wininet
ELF	7e536000-7e566000	Deferred        ws2_32<elf>
  \-PE	7e540000-7e566000	\               ws2_32
ELF	7e566000-7e65b000	Deferred        oleaut32<elf>
  \-PE	7e580000-7e65b000	\               oleaut32
ELF	7e65b000-7e6cd000	Deferred        rpcrt4<elf>
  \-PE	7e670000-7e6cd000	\               rpcrt4
ELF	7e6cd000-7e7df000	Deferred        ole32<elf>
  \-PE	7e6f0000-7e7df000	\               ole32
ELF	7e7df000-7e809000	Deferred        oledlg<elf>
  \-PE	7e7e0000-7e809000	\               oledlg
ELF	7e809000-7e841000	Deferred        winspool<elf>
  \-PE	7e810000-7e841000	\               winspool
ELF	7e841000-7e910000	Deferred        comctl32<elf>
  \-PE	7e850000-7e910000	\               comctl32
ELF	7e910000-7e973000	Deferred        shlwapi<elf>
  \-PE	7e920000-7e973000	\               shlwapi
ELF	7e973000-7eb0d000	Deferred        shell32<elf>
  \-PE	7e980000-7eb0d000	\               shell32
ELF	7eb0d000-7ebc2000	Deferred        comdlg32<elf>
  \-PE	7eb10000-7ebc2000	\               comdlg32
ELF	7ebc2000-7ec6e000	Deferred        gdi32<elf>
  \-PE	7ebd0000-7ec6e000	\               gdi32
ELF	7ec6e000-7edcb000	Deferred        user32<elf>
  \-PE	7ec90000-7edcb000	\               user32
ELF	7edcb000-7ee26000	Deferred        advapi32<elf>
  \-PE	7ede0000-7ee26000	\               advapi32
ELF	7ee26000-7ee3c000	Deferred        libresolv.so.2
ELF	7ee44000-7ee58000	Deferred        msimg32<elf>
  \-PE	7ee50000-7ee58000	\               msimg32
ELF	7ee58000-7ee78000	Deferred        iphlpapi<elf>
  \-PE	7ee60000-7ee78000	\               iphlpapi
ELF	7efa4000-7efb1000	Deferred        libnss_files.so.2
ELF	7efb1000-7efbc000	Deferred        libnss_nis.so.2
ELF	7efbc000-7efe4000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        libnsl.so.1
ELF	f7cd0000-f7cd9000	Deferred        libnss_compat.so.2
ELF	f7cda000-f7cde000	Deferred        libdl.so.2
ELF	f7cde000-f7e36000	Deferred        libc.so.6
ELF	f7e37000-f7e51000	Deferred        libpthread.so.0
ELF	f7e6d000-f7faa000	Export          libwine.so.1
ELF	f7fac000-f7fcb000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) E:\Spiele\World of Warcraft\Launcher.exe
	00000009    0 <==
0000000e 
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
0000001a 
	0000001b    0
Backtrace:
=>0 0x004a670c EntryPoint() in launcher (0x0032fee8)
  1 0x7bc6c0b4 call_thread_func+0xc() in ntdll (0x0032fef8)
  2 0x7bc6c2c0 call_thread_entry_point+0x70() in ntdll (0x0032ffc8)
  3 0x7bc482da in ntdll (+0x382da) (0x0032ffe8)
  4 0xf7e74ebd wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x4a670c

```
and when trying to start Wow.exe, I get
```

err:module:attach_process_dlls "DivxDecoder.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"E:\\Spiele\\World of Warcraft\\Wow.exe" failed, status c0000005

```

here's my xorg.conf:
```

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "RenderAccel"   "true"
EndSection

```
Using wine 1.1.30

---

### Post by khelben1979 on 2009-10-05
Your xorg.conf looks very small. I suspect that you haven't installed the graphics drivers from nVidia and this is the source of your problem.
[URL="http://www.nvidia.com/Download/index.aspx?lang=en-us"]
nVidia drivers on nVidia.com[/URL].

---

### Post by Morimando on 2009-10-05
> **khelben1979 said:**
> Your xorg.conf looks very small. I suspect that you haven't installed the graphics drivers from nVidia and this is the source of your problem.
[URL="http://www.nvidia.com/Download/index.aspx?lang=en-us"]
nVidia drivers on nVidia.com[/URL].
Have installed the 185 driver from the repositories. The module name "nvidia" in the xorg.conf indicates that this proprietary driver is used. The open-source driver initially supplied with Ubuntu has a different module name.
The problem seems to be the DivxDecoder.dll mentioned in the error wine gives me, which - from what i found on google - seems to be an amd64 issue. Unfortunately I haven't found a solution yet. The issue doesn't have to do with the Config.wtf, I'd say, since I modified that and it was running with Gentoo very nicely.
I tweaked the Xorg.conf a little, meanwhile, but, alas, to no avail :(
new xorg.conf:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "DisableGLXRootClipping" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "DamageEvents" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by Morimando on 2009-10-05
Argh!
I found it...
Apparently, one needs "exec" permissions on the drive, which were missing. Pretty basic error and thus the harder to find.
So for all others out there having the same issue... try the following mount options in /etc/fstab:
```
/dev/sdb5	/media/Media    ext3    defaults,user,auto,exec        0       2
```
The option "user" might be implied by "defaults", "exec" however is not.
When you've corrected your fstab, remount the partition in question (you need to do that for the corresponding partition where YOUR WoW is installed, not necessarily sdb5!) using 
```
mount -o remount /dev/<partition>
```

---

### Post by 11hjpphty76lkjj on 2009-10-09
I can confirm that this fixed this problem for me as well.  Not sure why exactly..might be interesting to know.

---

