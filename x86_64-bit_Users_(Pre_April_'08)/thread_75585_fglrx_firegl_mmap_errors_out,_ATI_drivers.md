---
title: "fglrx: firegl_mmap errors out, ATI drivers"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by tarkus on 2005-10-13
**Edit: This problem is now fixed.  Use [either of the how-to's]("http://ubuntuforums.org/showthread.php?t=75382") to install the driver on 64-bit.**

Hi there everyone,
I'm running Breezy on an AMD64 with a Radeon X700. I've installed the ATI fglrx drivers, and it actually worked for a while. However, when I did an apt-get upgrade recently (before the final release), it broke!

I think that the Xorg driver is still ok, because in the Xorg.0.log it complains that the ATI driver couldn't enable acceleration because of a broken kernel module. Sure enough, dmesg says:
[ 227.421078] [fglrx:firegl_mmap] *ERROR* No map found!
I can't find any information about this error on Google. I've tried this under both Ubuntu 2.6.12-9-amd64-generic and my own homebrew 2.6.13.4 kernel. Both exhibit the same problem. This is rather strange, because the upgrade did not involve a kernel change yet it seems to have broken a module.

Running a GL program causes: libGL error: drmMap of framebuffer failed
fglrxinfo shows:
> steven@godzilla:~$ fglrxinfo
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

dmesg has this to say:
> [   48.375487] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   48.411837] [fglrx] Maximum main memory to use for locked dma buffers: 918 MBytes.
[   48.418035] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 16
[   48.425111] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[   48.691821] input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
[   49.194345] ts: Compaq touchscreen protocol output
[   51.307888] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   52.181240] kjournald starting.  Commit interval 5 seconds
[   52.183291] EXT3-fs: mounted filesystem with ordered data mode.
[   54.586696] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   54.589911] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   58.227316] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   69.735924] [fglrx] free  PCIe = 51118080
[   69.735930] [fglrx] max   PCIe = 51118080
[   69.735932] [fglrx] free  LFB = 108908544
[   69.735934] [fglrx] max   LFB = 108908544
[   69.735936] [fglrx] free  Inv = 134217728
[   69.735938] [fglrx] max   Inv = 134217728
[   69.735940] [fglrx] total Inv = 134217728
[   69.735942] [fglrx] total TIM = 0
[   69.735943] [fglrx] total FB  = 0
[   69.735945] [fglrx] total PCIe = 16384
[  587.698760] [fglrx:firegl_mmap] *ERROR* No map found!
[  589.049772] ISO 9660 Extensions: Microsoft Joliet Level 1
[  589.050373] ISOFS: changing to secondary root
[ 2017.166639] [fglrx:firegl_mmap] *ERROR* No map found!
[ 2317.629803] [fglrx:firegl_mmap] *ERROR* No map found!
[ 2619.103260] [fglrx:firegl_mmap] *ERROR* No map found!


Any ideas? Or, if there's nobody here that can, anywhere I can go to get help?

Thanks a million,
Steven

---

### Post by ibthomson on 2005-10-13
I've experienced the exact same situation. I've tried reinstalling the drivers from repositories, ATI (both automatic and alien rpm) and still gives the same output. The recent apt-get upgrade killed it.

---

### Post by ToastedToad on 2005-10-13
```
scott@black:~$ fglrxinfo
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

Same issue here. Tried the ATI Installer, same thing. Haven't had any luck so far finding the fix.

---

### Post by tarkus on 2005-10-13
Well, nice to know I'm not the only one with this problem :p
Additionally, I've fiddled with the MTRR settings, adding an additional MTRR where my video memory appears to be (according to lspci)

Needless to say, no luck :p

I did manage to, in deleting the default mtrr, cause a ten minute reboot as the system struggled at 100% CPU to refresh the screen and stuff :p

A little knowledge and root is a dangerous combination...

---

### Post by wzzrd on 2005-10-14
Gentoo doesn't even allow for the installation of 8.16.20. Maybe we just should go back to the previous release. Needless, to say, I suffer the same problem...

---

### Post by xthaparian on 2005-10-14
[QUOTE=tarkus]Hi there everyone,
I'm running Breezy on an AMD64 with a Radeon X700. I've installed the ATI fglrx drivers, and it actually worked for a while. However, when I did an apt-get upgrade recently (before the final release), it broke!

I think that the Xorg driver is still ok, because in the Xorg.0.log it complains that the ATI driver couldn't enable acceleration because of a broken kernel module. Sure enough, dmesg says:
[ 227.421078] [fglrx:firegl_mmap] *ERROR* No map found!
I can't find any information about this error on Google. I've tried this under both Ubuntu 2.6.12-9-amd64-generic and my own homebrew 2.6.13.4 kernel. Both exhibit the same problem. This is rather strange, because the upgrade did not involve a kernel change yet it seems to have broken a module.

Running a GL program causes: libGL error: drmMap of framebuffer failed
fglrxinfo shows:


dmesg has this to say:



Any ideas? Or, if there's nobody here that can, anywhere I can go to get help?

Thanks a million,
Steven[/QUOTE]


Well could you please let me know how did you manage to install the 64 bit driver at first place???

---

### Post by Corvash on 2005-10-14
```
apt-get install linux-restricted-modules-$(uname -r) xorg-driver-fglrx
```

BTW, one more having the same driver issue

---

### Post by loupy on 2005-10-14
I'm stuck with the Mesa.  With all the research I've done it seems as if fglrx won't support wide screens (I have a 1280x800), and I cannot get the ATI driver to install. 

I hope someone tells me I'm wrong, but for now I'm in 2D :(

---

### Post by Kay on 2005-10-14
Do I need to say I have the same problem too? :( I tried with today's new drivers too, 8.18.6, but still the same problem.. Gonna try the i386 edition now, hopefully the problem is nonexistant there, I don't really need the 64-bit support :) It wasn't that much faster, was it? Btw, the 8.18.6 driver does solve the 1280x800 res not working problem :D

---

### Post by Pablo_Escobar on 2005-10-14
Another victim of ATI frivers :( 64bit Breezy :(

---

### Post by archiesteel on 2005-10-14
Same problem here. I'm almost 100% certain that this is a xorg issue, as the problems started happening after I upgraded the xorg packages. :mad: 

This may also be related: installing the drivers using ati's installers breaks GL applications, which complain that they cannot find libGL.so.1 (even though it's there).

I guess we'll have to wait until the next xorg upgrade to find out...after spending a couple of days trying to see if they could be fixed by hand, I've thrown in the towel!

---

### Post by Kay on 2005-10-14
[QUOTE=archiesteel]Same problem here. I'm almost 100% certain that this is a xorg issue, as the problems started happening after I upgraded the xorg packages. :mad: 

This may also be related: installing the drivers using ati's installers breaks GL applications, which complain that they cannot find libGL.so.1 (even though it's there).

I guess we'll have to wait until the next xorg upgrade to find out...after spending a couple of days trying to see if they could be fixed by hand, I've thrown in the towel![/QUOTE]

I saw a broken symlink with libGL.so.1 when trying to solve the problem.. maybe u should relink them to libGL.so.1.2, but probably that wouldnt solve the problem =( Btw, anyone tried these ones: [http://r300.sourceforge.net/](http://r300.sourceforge.net/) ??

---

### Post by archiesteel on 2005-10-14
[QUOTE=Kay]I saw a broken symlink with libGL.so.1 when trying to solve the problem.. maybe u should relink them to libGL.so.1.2, but probably that wouldnt solve the problem =([/QUOTE]

Nah, the symlinks are there, I tried many combinations and still no joy.

BTW, my device doesn't seem to be recognized by the kernel.

```
elie@anaxana:~$ lspci | grep ATI
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
```

I have an ATI RADEON® XPRESS 200M IGP with 128MB (laptop motherboard) with an AMD64 system, for what it's worth...

[QUOTE=Kay]Btw, anyone tried these ones: [http://r300.sourceforge.net/](http://r300.sourceforge.net/) ??[/QUOTE]

Well, the big red warning on the page is kinda disheartening:

[COLOR="Red"][I]The source code on this website may damage your hardware.
It is *UNTESTED* and *BROKEN* ![/I]
[/COLOR]
If you try it, tell us how it went... ;)

---

### Post by pwarren on 2005-10-14
[QUOTE=Kay] I don't really need the 64-bit support :) It wasn't that much faster, was it?[/QUOTE]

I've found that some operations a quite a bit faster,  vorbis encoding almost doubles(!) in speed.  and Video encoding is much faster. but you're correct, 64bit doesn't give much of an advantage for the 'average' desktop usage patterns like firefox and thunderbird.

Cheers
Paul Warren
[http://pwarren.homelinux.org]("http://pwarren.homelinux.org")

---

### Post by Jiilik on 2005-10-14
I also experience the same errors. The fglrx worked normally in breezy in the days leading up to the release, but sometime near release day, it broke.

Bug 17614 is "NEW" related to this issue.

---

### Post by mlomker on 2005-10-15
[QUOTE=loupy]I'm stuck with the Mesa.  With all the research I've done it seems as if fglrx won't support wide screens (I have a 1280x800), and I cannot get the ATI driver to install. 
[/QUOTE]

That's true for certain monitors.  Has to do with dri.  It is fixed in 8.18.6 but that won't install on amd64...I spent about a day trying to get it to work.

I ended up going 32-bit and I wrote a [how-to]("http://ubuntuforums.org/showthread.php?p=411503") for driver installation on that platform.

---

### Post by alexandre1982 on 2005-10-15
[QUOTE=Jiilik]I also experience the same errors. The fglrx worked normally in breezy in the days leading up to the release, but sometime near release day, it broke.

Bug 17614 is "NEW" related to this issue.[/QUOTE]

me too,

When I upgrade from breezy to 5.10 yesteday, my configuration of my ati failed and become:
hera-m:~# fglrxinfo
libGL error: drmMap of framebuffer failed
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

... no3D and very slow.
in Xorg.0.log:
(II) fglrx(0): UMM Bus area: 0xf05e9000 (size=0x07a07000)
(II) fglrx(0): UMM area: 0xf05e9000 (size=0x07a07000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card9
... etc.
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x001d8000
(II) fglrx(0): [drm] mapped SAREA 0x001d8000 to 0x2aaaaab35000
(II) fglrx(0): [drm] framebuffer handle = 0xf0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0): Name: fglrx
(II) fglrx(0): Version: 8.16.20
(II) fglrx(0): Date: Aug 16 2005
(II) fglrx(0): Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0): Build-Kernel UTS_RELEASE: 2.6.12-9-amd64-k8
(II) fglrx(0): Build-Kernel MODVERSIONS: no
(II) fglrx(0): Build-Kernel __SMP__: no
(II) fglrx(0): Build-Kernel PAGE_SIZE: 0x1000
(II) fglrx(0): [drm] register handle = 0xfbef0000
(II) fglrx(0): [pcie] 65536 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00354000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x005e9000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1210)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 800)
(II) fglrx(0): Largest offscreen area available: 1280 x 402
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
Screen to screen bit blits
Solid filled rectangles
8x8 mono pattern filled rectangles
Solid Lines
Dashed Lines
Offscreen Pixmaps
Setting up tile and stipple cache:
30 128x128 slots
(II) fglrx(0): Acceleration enabled
...etc

before this upgrade, that run very well. I have try to reinstall all drivers, restricted modules, directly ati drivers script and more but nothing...

that's all.

If anybody find a solution.

Alexandre

-- 
[http://www.hera.cc](http://www.hera.cc)

---

### Post by zupermanz on 2005-10-15
Am having the same problems with alexander...this must be an amd64 issue. In 5,04 worked though...

---

### Post by mlomker on 2005-10-15
> Am having the same problems with alexander...this must be an amd64 issue. In 5,04 worked though...

The 8.16.20 driver that comes with Breezy worked for me after the upgrade from Hoary to Breezy.  It's the 8.18.6 driver that I couldn't figure out how to install.  

I'm not sure if the people having trouble with the driver are using an ATI installed package or Breezy's.

You can try [completely removing]("http://ubuntuforums.org/showpost.php?p=408876&postcount=6") your ATI package and using Breezy's if you haven't already.

---

### Post by Corvash on 2005-10-15
The firegl_mmap / drmMap failures are occuring using the xorg-driver-fglrx package provided by Ubuntu.

Using the ATi installer results in 'unable to find libGL.so.1' errors instead. Although I have noticed one promising lead, the ATi website mentions you need to install the 32-bit drivers aswell. Currently seeing if that helps any.

---

### Post by mlomker on 2005-10-15
> Using the ATi installer results in 'unable to find libGL.so.1' errors instead.


I just caught wind of [this patch]("http://ati.cchtml.com/show_bug.cgi?id=198").  I don't know if it'll work or not but it's a lead.

---

### Post by Corvash on 2005-10-15
Tried it, Still not going.

No more libGL.so errors, just still using MesaGL.

---

### Post by mlomker on 2005-10-15
> No more libGL.so errors, just still using MesaGL.

What does **ldd /usr/X11R6/bin/fglrxinfo** give you?  Pointing at the correct libGL.so.1?

---

### Post by Corvash on 2005-10-15
Ok, noticed in the xorg log it was still using the Ubuntu kernel module, despite me having compiled and installed a later one.

Uninstalled the linux-restricted-modules and xorg-driver-fglrx packages, then re-ran the installer. Error disappeared from the xlogs, but still no accelleration.

After a bit more tinkering, I'm now back to square one, drmMap. Just now it's with newer drivers.

There are a few warnings reported when building the module. I'll post them to this board tommorow - right now I must sleep.

---

### Post by archiesteel on 2005-10-15
[QUOTE=Corvash]The firegl_mmap / drmMap failures are occuring using the xorg-driver-fglrx package provided by Ubuntu.

Using the ATi installer results in 'unable to find libGL.so.1' errors instead. Although I have noticed one promising lead, the ATi website mentions you need to install the 32-bit drivers aswell. Currently seeing if that helps any.[/QUOTE]

This describes my problems as well. GL apps work the Ubuntu xorg-driver-fglrx package, but no 3D acceleration (and with the drmMap errors). Using official packages, GL apps no longer works. This is on an amd64 system.

I can confirm that this was working up to about four days before the Breezy release. I remember there being a big xorg update that day...

I don't think it is a kernel issue, because I was still using 2.6.12-8 at that time and I got the same errors. Updating to 2.6.12-9 (by doing a complete system reinstall) didn't solve anything.

Did installing the 32-bit drivers alongside the 64-bit ones work?

---

### Post by archiesteel on 2005-10-15
[QUOTE=Corvash]After a bit more tinkering, I'm now back to square one, drmMap. Just now it's with newer drivers.

There are a few warnings reported when building the module. I'll post them to this board tommorow - right now I must sleep.[/QUOTE]

Was this using the patched installer, as per post #21?

---

### Post by Jiilik on 2005-10-15
[QUOTE=mlomker]The 8.16.20 driver that comes with Breezy worked for me after the upgrade from Hoary to Breezy.  It's the 8.18.6 driver that I couldn't figure out how to install.  

I'm not sure if the people having trouble with the driver are using an ATI installed package or Breezy's.

You can try [completely removing]("http://ubuntuforums.org/showpost.php?p=408876&postcount=6") your ATI package and using Breezy's if you haven't already.[/QUOTE]
I'm using the official breezy packages only.

---

### Post by Jiilik on 2005-10-15
[QUOTE=mlomker]What does **ldd /usr/X11R6/bin/fglrxinfo** give you?  Pointing at the correct libGL.so.1?[/QUOTE]

```

$ ldd /usr/bin/fglrxinfo
        libGL.so.1 => /usr/lib/libGL.so.1 (0x00002aaaaabc2000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaaad94000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002aaaaaf6e000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaab07f000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002aaaab2b7000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaab3cc000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaab4ce000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaab5d2000)
        /lib64/ld-linux-x86-64.so.2 (0x00002aaaaaaab000)
```

---

### Post by mlomker on 2005-10-15
> 
        libGL.so.1 => /usr/lib/libGL.so.1 (0x00002aaaaabc2000)


On 32-bit systems the correct file is **libGL.so.1 => /usr/X11R6/lib/libGL.so.1**, but that's all that I can tell you.  I couldn't get the driver to work until I went 32-bit.

---

### Post by Jiilik on 2005-10-16
[QUOTE=mlomker]On 32-bit systems the correct file is **libGL.so.1 => /usr/X11R6/lib/libGL.so.1**, but that's all that I can tell you.  I couldn't get the driver to work until I went 32-bit.[/QUOTE]

If I follow the symlinks, it is the same thing... /usr/lib/libGL.so.* points at /usr/X11R6/lib/libGL.so.* -- this is not the issue methinks

---

### Post by mlomker on 2005-10-16
> this is not the issue methinks

I think it is a library problem, but perhaps something that a developer will have to fix.  On 32-bit installs (which do work) those are different files.  ATI mentions on their webpage that there are 32 and 64-bit components to their driver package and that you need both for it to work.  I think something is borked with the dynamic linking on the 64-bit systems.

For the record, I did have the included 8.16.20 drivers working on 64-bit Breezy.  It was simply a matter of [thoroughly removing]("http://www.ubuntuforums.org/showthread.php?t=75378") my ATI-packaged Hoary drivers and reinstalling them.  What I absolutely couldn't get to work was the new 8.18.6 driver, which I need to fix my widescreen resolution problem.

Maybe I'll back up my 32-bit install and put 64-bit back on this week.  I might be able to figure it out, given what I've learned from the 32-bit side.

---

### Post by Corvash on 2005-10-17
I'm inclined to suspect a kernel issue, as:
* dmesg afaik reports kernel messages, 
* both drmMap and firegl_mmap speak of memory allocation (specifically of the framebuffer, which is the on-card memory in which the rendered output is constructed)
* The compile log for the fglrx module (if compiled manually) contains a significant number of warning messages regarding depreciated system calls.

Attached is my Xorg.log and the compile log (make.sh.log) for the fglrx module. I'm gonna try downgrading to kernel 2.6.11 sometime in the next few days (can't do it right now, got other stuff that needs doing), and seeing if that makes a difference.

Also, out of curiosity, what's everyone running? Might help someone figure out what the issue is.

I'm on an Acer Ferrari 3400 laptop.

EDIT: Can't upload xorg log, too large. It wasn't all that informative anyhow.

---

### Post by archiesteel on 2005-10-17
[QUOTE=Corvash]I'm inclined to suspect a kernel issue [...]

Also, out of curiosity, what's everyone running? Might help someone figure out what the issue is.[/QUOTE]

I'm not sure it's a kernel issue. For me, it broke after a xorg update, while still running 2.6.12-8.

I'm running a Compaq Presario V2310, amd64 (Turion). It starting to look as if this is only affecting 64-bit users...

Today I'm going to try substituting the libs in my 32-bit chroot with the "alleged" 64-bit libraries, just to see if they were correctly compiled...

---

### Post by Kaja on 2005-10-17
It's definitely 64-bit issue. I have both 32/64bit installations of Breezy. 32-bit work 64-bit not. During kernel module compiling are many warnings, but only 3 differences. It seem not to be our problem.

/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_put_user_ptr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1149: warning: cast from pointer to integer of different size
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_register_ioctl32_conversion':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2220: warning: `register_ioctl32_conversion' is deprecated (declared at include/linux/ioctl32.h:29)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_unregister_ioctl32_conversion':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2225: warning: `unregister_ioctl32_conversion' is deprecated (declared at include/linux/ioctl32.h:30)

---

### Post by Schizoid on 2005-10-18
I've been over this, as far as I can tell its an issue with libGL version not being the one that atiogl_a_dri.so was linked against,  I've isolated the error t that points this out. This makes alot of sense seeing as everything looks fine, but everything is slow do to falling back to software OpenGL.

```
 [COLOR="DarkOrange"]$ LIBGL_DEBUG=verbose fglrxinfo [/COLOR]
libGL: XF86DRIGetClientDriverName: 8.16.20 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/atiogl_a_dri.so
**[COLOR="Red"]fglrx: libGL version does not match - OpenGL module is using glapi fallback[/COLOR]**
libGL: XF86DRIGetClientDriverName: 8.16.20 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

 To get these results just make sure you set LIBGL_DEBUG=verbose either export or add to you bash line. Note this also works with glxinfo.

Schizoid

---

### Post by Cosmic_Crusader on 2005-10-18
I've noticed a similar problem created this thread: [**Failing to locate shared libraries - missing 32bit/64bit versions**]("http://ubuntuforums.org/showthread.php?p=422074").

I've noticed that there are usually duplicate versions of 32bit and 64bit libraries, however there are some missing that cause these errors.

For example:> ldd `locate fglrx_xgamma`
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002aaaaabc2000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaaacd7000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002aaaaaeb1000)
        libm.so.6 => /lib/libm.so.6 (0x00002aaaaafc2000)
        libfglrx_gamma.1 => not found
        libc.so.6 => /lib/libc.so.6 (0x00002aaaab148000)
        /lib64/ld-linux-x86-64.so.2 (0x00002aaaaaaab000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaab37f000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaab483000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaab586000) 
Notice that the libfglrx_gamma.1 is not found, and yet:> locate libfglrx_gamma.1
/usr/X11R6/lib/libfglrx_gamma.1 
Checking the linking on this file shows:> ldd /usr/X11R6/lib/libfglrx_gamma.1
        libc.so.6 => /lib/libc.so.6 (0x00002aaaaabbc000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)

If I try it on one of the working libraries:> ldd `locate libXpm.so.4`
/usr/lib/libXpm.so.4.11.0:
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaaabd0000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaaadab000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaaaead000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaab0e4000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaab1e8000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)
/usr/lib/libXpm.so.4:
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaaabd0000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaaadab000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaaaead000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaab0e4000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaab1e8000)
        /lib64/ld-linux-x86-64.so.2 (0x0000555555554000)
/usr/lib32/libXpm.so.4.11.0:
        linux-gate.so.1 =>  (0xffffe000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x5557a000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5563a000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x5563d000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x5576b000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x5576e000)
        /lib/ld-linux.so.2 (0x56555000)
/usr/lib32/libXpm.so.4:
        linux-gate.so.1 =>  (0xffffe000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x5557a000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5563a000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x5563d000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x5576b000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x5576e000)
        /lib/ld-linux.so.2 (0x56555000)
There are versions of both 32bit and 64bit in the relevant directories.

Does this shed some light or turn on a light for anyone?

---

### Post by Kaja on 2005-10-18
IMHO "libGL version does not match" is another issue. I tried this:

> 
LIBGL_DEBUG=verbose /usr/X11R6/bin/fglrxinfo

libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


no libGL problem, but still drmMap error

and let's continue ...

> 
file /usr/X11R6/lib/libGL.so.1
  /usr/X11R6/lib/libGL.so.1: symbolic link to `libGL.so.1.2'

file /usr/X11R6/lib/libGL.so.1.2
  /usr/X11R6/lib/libGL.so.1.2: ELF 64-bit LSB shared object, AMD x86-64, version 1 (SYSV), not stripped

dpkg -S /usr/X11R6/lib/libGL.so.1.2
  fglrx64-6-8-0: /usr/X11R6/lib/libGL.so.1.2


It looks right.

---

### Post by Schizoid on 2005-10-18
its the same error just more verbose please read the whole error message
heh nevemind I see what your saying, ok I'll look into what your saying there.

---

### Post by Schizoid on 2005-10-18
[QUOTE=Kaja]IMHO "libGL version does not match" is another issue. I tried this:



no libGL problem, but still drmMap error

and let's continue ...



It looks right.[/QUOTE]

your not using the Ubuntu package thats a conversion from the either the ATI installer or the ATI rpm. so you test doesnt help me.

---

### Post by Kaja on 2005-10-18
I use converted (by alien) ATI rpm package fglrx 8.18.6, because 8.16.20 isn't able to use the resolution 1280x800. Nevertheless, you can see that drmMap error is same without reference to libGL issue. Nevermind.

---

### Post by pgarciagon on 2005-10-18
Having the same problem here.
On an accer ferrari 4000
amd64, ati x700.
ubuntu 5.10

Here some infos:

######

pgarcia@claudia5:~$ uname -a
Linux claudia5 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64 GNU/Linux

######

pgarcia@claudia5:~$ fglrxinfo
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

############

############

pgarcia@claudia5:~$ ldd `locate fglrxinfo`
        libGL.so.1 => /usr/lib/libGL.so.1 (0x00002aaaaabc2000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaaad94000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002aaaaaf6e000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaab07f000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002aaaab2b7000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaab3cc000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaab4ce000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaab5d2000)
        /lib64/ld-linux-x86-64.so.2 (0x00002aaaaaaab000)

################

Here a link to the corresponding x server log file section:

[http://www.fiopa.com/xserver.txt]("http://www.fiopa.com/xserver.txt")

---

### Post by Septor on 2005-10-18
I installed Breezy on my AMD64 system last night, so I'm going to work on the ati-installer Ubuntu scripts this week (I am the maintainer) and see if I can't get something working for us... I think some of the library paths are off, including possibly hard-coded paths inside of the binary files themselves.

---

### Post by Schizoid on 2005-10-18
Let me know if you need a hand with anything , I'm in the process of breaking down all the packages also. If I find anything that stands out I'll let you know.

---

### Post by archiesteel on 2005-10-18
[QUOTE=Septor]I installed Breezy on my AMD64 system last night, so I'm going to work on the ati-installer Ubuntu scripts this week (I am the maintainer) and see if I can't get something working for us... I think some of the library paths are off, including possibly hard-coded paths inside of the binary files themselves.[/QUOTE]

Yay!

You're probably aware of this already, but just in case:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17614](http://bugzilla.ubuntu.com/show_bug.cgi?id=17614)

---

### Post by Schizoid on 2005-10-18
Correct, so I just got the impression that this was a amd64 issue, and I've been looking at it on and off over the last couple of days.

 Are there any offcial docs for building the fglrx drivers from ubunto sources? my version is hacked  to heck, and it would help to know the right way of doing it. If there are none, dont worry about it I'll just do it the schizoid way :P

my way... apt-get sources, build packages, apt-get install packages, then I muck around with the fglrx tar.gz file.

---

### Post by Septor on 2005-10-18
After running the ATI installer, try setting the environment variables before
running a GL program:

export LIBGL_DRIVER_PATH="/usr/X11R6/lib64/modules/dri:/usr/X11R6/lib32/modules/dri"
export LD_LIBRARY_PATH="/usr/X11R6/lib64:/usr/X11R6/lib32"

Let me know if this helps.

---

### Post by Septor on 2005-10-18
[QUOTE=Schizoid]Correct, so I just got the impression that this was a amd64 issue, and I've been looking at it on and off over the last couple of days.

 Are there any offcial docs for building the fglrx drivers from ubunto sources? my version is hacked  to heck, and it would help to know the right way of doing it. If there are none, dont worry about it I'll just do it the schizoid way :P

my way... apt-get sources, build packages, apt-get install packages, then I muck around with the fglrx tar.gz file.[/QUOTE]


Well you could just run "sh ./ati-driver-installer-8.18.6-x86_64.run --buildpkg Ubuntu/breezy" to make all the packages.  But I'd recommend you read [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198) first.

---

### Post by Schizoid on 2005-10-18
ok when you say installer do you mean the ati installer? or just apt-getting the ubuntu binaries ie linux-restricted-modules-2.6.12-9-amd64-k8 and xorg-driver-fglrx? basically I just need to know what you mean by ati-installer. Either way I'll go ahead and run these test while I wait for a response

disregard this makes alot more sense after reading that bug.. ok I'll run these test and post the results, should I still be applying the ubuntu patch?

---

### Post by Septor on 2005-10-18
[QUOTE=Schizoid]ok when you say installer do you mean the ati installer? or just apt-getting the ubuntu binaries ie linux-restricted-modules-2.6.12-9-amd64-k8 and xorg-driver-fglrx? basically I just need to know what you mean by ati-installer. Either way I'll go ahead and run these test while I wait for a response[/QUOTE]

I meant run the ati-driver-installer-8.18.6-x86_64.run program to install fglrx.  But if you do that apt won't know about the packages.  Anyways, if you use the linux-restricted-modules version, then you might have to modify the paths I listed above.  LD_LIBRARY_PATH should contain the paths to both the 64bit and 32bit versions of libGL.so.1.2 from the fglrx packages.  LIBGL_DRIVER_PATH should contain the paths to both the 64bit and 32bit versions of fglrx_dri.so. Find where you have those files and set those variables accordingly for testing.

---

### Post by archiesteel on 2005-10-19
[QUOTE=Septor]After running the ATI installer, try setting the environment variables before
running a GL program:

export LIBGL_DRIVER_PATH="/usr/X11R6/lib64/modules/dri:/usr/X11R6/lib32/modules/dri"
export LD_LIBRARY_PATH="/usr/X11R6/lib64:/usr/X11R6/lib32"

Let me know if this helps.[/QUOTE]

I get the same error as if I don't:

```
elie@anaxana:~$ export LIBGL_DRIVER_PATH="/usr/X11R6/lib64/modules/dri:/usr/X11R6/lib32/modules/dri"
elie@anaxana:~$ export LD_LIBRARY_PATH="/usr/X11R6/lib64:/usr/X11R6/lib32"
elie@anaxana:~$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

The library is there and the symlinks are correct, but somehow the GL apps don't see it.

```
elie@anaxana:~$ ldd /usr/X11R6/bin/fglrxinfo
        libGL.so.1 => not found
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaaabc2000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002aaaaad9c000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaaaead000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaab0e5000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaab1e8000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaab2eb000)
        /lib64/ld-linux-x86-64.so.2 (0x00002aaaaaaab000)
```

---

### Post by Corvash on 2005-10-19
[QUOTE=Septor]After running the ATI installer, try setting the environment variables before
running a GL program:

export LIBGL_DRIVER_PATH="/usr/X11R6/lib64/modules/dri:/usr/X11R6/lib32/modules/dri"
export LD_LIBRARY_PATH="/usr/X11R6/lib64:/usr/X11R6/lib32"

Let me know if this helps.[/QUOTE]


Still get these errors:
aravi@aegis:~$ fglrxinfo libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib64/modules/dri/fglrx_dri.so failed (/usr/X11R6 /lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or  directory)
libGL error: unable to find driver: fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib64/modules/dri/fglrx_dri.so failed (/usr/X11R6 /lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or  directory)
libGL error: unable to find driver: fglrx_dri.so
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I've verified that the fglrx_dri.so exists in those locations, but it still can't find it. Two things I notice, 

1. lib64 is a symlink to lib, could this be interfering with ld finding the libraries.

2. Using file to check the library shows it to be a 32-bit binary.
/usr/X11R6/lib64/modules/dri/fglrx_dri.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), not stripped

---

### Post by Kaja on 2005-10-19
Is it necessary to have both (32/64) libraries (libGL, fglrx_dri, ...) for running 64-bit flgrxinfo?

---

### Post by Septor on 2005-10-19
[QUOTE=Corvash]
2. Using file to check the library shows it to be a 32-bit binary.
/usr/X11R6/lib64/modules/dri/fglrx_dri.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), not stripped[/QUOTE]

Wow that's not right... there should be 32bit libs in /usr/X11R6/lib32 and 64bit libs in /usr/X11R6/lib64...  the reason you are getting "library not found" is because a 64bit app cannot open a 32bit library.  The problem is with the ATI installer that assumes /usr/X11R6/lib is lib32, not lib64 as it is in Breezy.  So Breezy amd64 users cannot use the ati-installer as is.  We should have better luck with the Breezy packages, so I'll try to get some working scripts for 8.18.6.

---

### Post by Septor on 2005-10-19
[QUOTE=Kaja]Is it necessary to have both (32/64) libraries (libGL, fglrx_dri, ...) for running 64-bit flgrxinfo?[/QUOTE]

I believe so.  I don't know why, but I am pretty sure you'll need both sets of libs installed, and in the correct place.

---

### Post by Kaja on 2005-10-19
[QUOTE=Septor]I believe so.  I don't know why, but I am pretty sure you'll need both sets of libs installed, and in the correct place.[/QUOTE]

IMHO no.
I straced fglrxinfo and there are opening 64-bit libs only.

But I find one interested point. Fglrxinfo fail on this:
> 
mmap(NULL, 134152192, PROT_READ|PROT_WRITE, MAP_SHARED, 4, 0xc8000000c8000000) = -1 EINVAL (Invalid argument)


and compare with strace from working 32-bit version:
> 
mmap2(NULL, 134152192, PROT_READ|PROT_WRITE, MAP_SHARED, 4, 0xc8000) = 0xaf46d000


IMHO: According to DMESG, it is calling from kernel module fglrx in function firegl_mmap. This function is external (look to firegl_public.h) and it is in binary file vm.o in archive libfglrx_ip.a.GCC3. (ATI binary driver 8.18.6)

I guess that with 8.16.20 from ubuntu package it'll be same. Can anyone try this? 
I can't believe that it worked with another Xorg.

---

### Post by Corvash on 2005-10-19
Manually moved the libraries, so the 64-bit libs are in lib64, and the 32-bit libs are in lib32. Still doesn't work, I still get the drmMap error (but no other errors).

```
aravi@aegis:~$ fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.
```

---

### Post by Septor on 2005-10-19
I fixed up the package generation scripts, but alas I am now stuck with the drmMap problem.  Apparently the same problem is occuring with SuSE, so it looks likely to be an ATI problem.  I'm waiting on an answer from them for now.

---

### Post by archiesteel on 2005-10-19
[QUOTE=Septor]I fixed up the package generation scripts, but alas I am now stuck with the drmMap problem.  Apparently the same problem is occuring with SuSE, so it looks likely to be an ATI problem.  I'm waiting on an answer from them for now.[/QUOTE]

Could it be a combo between ATI and the recent Xorg update? Because it worked up until the Xorg update that occured a few days before release.

I'm not sure I'm brave enough to reinstall the Breezy Preview CD, but I did manage to get 3D working before the final release updates...

---

### Post by Septor on 2005-10-19
[QUOTE=archiesteel]Could it be a combo between ATI and the recent Xorg update? Because it worked up until the Xorg update that occured a few days before release.

I'm not sure I'm brave enough to reinstall the Breezy Preview CD, but I did manage to get 3D working before the final release updates...[/QUOTE]

I got a message from Daniel Stone (xorg Ubuntu maintainer) and he said that it might work to reinstall the xserver-xorg-core 6.8.2-70 or earlier package.  Basically it seems that the /usr/X11R6/lib/extensions/modules/libdri.a might be incompatible with fglrx due to some changes made recently.  If you can get an older libdri.a and replace your current one (make backups of the original though!) then you might be able to get it working.  I'm going to try this tonight when I get home to verify the fix/problem.

---

### Post by archiesteel on 2005-10-20
[QUOTE=Septor]I got a message from Daniel Stone (xorg Ubuntu maintainer) and he said that it might work to reinstall the xserver-xorg-core 6.8.2-70 or earlier package.  Basically it seems that the /usr/X11R6/lib/extensions/modules/libdri.a might be incompatible with fglrx due to some changes made recently.  If you can get an older libdri.a and replace your current one (make backups of the original though!) then you might be able to get it working.  I'm going to try this tonight when I get home to verify the fix/problem.[/QUOTE]

I tried with xserver-xorg-core 6.8.2-60. Using the ati-installer I still get the "libGL.so.1 missing" error, while using it with the Ubuntu xorg-driver-fglrx package I get this:

```
elie@anaxana:~/Download$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I could try 6.8.2-70 but I don't know where to get it (I got -60 from the Breezy preview CD).

---

### Post by Septor on 2005-10-20
[QUOTE=archiesteel]I tried with xserver-xorg-core 6.8.2-60. Using the ati-installer I still get the "libGL.so.1 missing" error, while using it with the Ubuntu xorg-driver-fglrx package I get this:

```
elie@anaxana:~/Download$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I could try 6.8.2-70 but I don't know where to get it (I got -60 from the Breezy preview CD).[/QUOTE]

-60 should be okay.  Can you extract just the libdri.a file and try it out with the latest Breezy xserver-xorg-core release, and my Ubuntu packages?

---

### Post by archiesteel on 2005-10-20
[QUOTE=Septor]-60 should be okay.  Can you extract just the libdri.a file and try it out with the latest Breezy xserver-xorg-core release, and my Ubuntu packages?[/QUOTE]

I've extracted the libdri.a and will overwrite the one from the latest xserver-xorg-core with it.

Where can I find your Ubuntu packages?

---

### Post by Septor on 2005-10-20
[QUOTE=archiesteel]I've extracted the libdri.a and will overwrite the one from the latest xserver-xorg-core with it.

Where can I find your Ubuntu packages?[/QUOTE]

Get the latest ati-driver-installer for 8.18.6 (you probably have it already) then follow the instructions at [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198) for patching and building the packages.  You'll need to install a few other packages if you haven't built .deb packages before... the details can be found in:

[http://ubuntuforums.org/showthread.php?p=423589&posted=1](http://ubuntuforums.org/showthread.php?p=423589&posted=1)
  and in 
[http://ubuntuforums.org/showthread.php?t=76116](http://ubuntuforums.org/showthread.php?t=76116)

---

### Post by paperinacup on 2005-10-20
well its not JUST a AMD 64 problem. I am running a Pentium M 770 with an ATI Radeon X700 with the SAME exact problem.

---

### Post by Septor on 2005-10-20
[QUOTE=paperinacup]well its not JUST a AMD 64 problem. I am running a Pentium M 770 with an ATI Radeon X700 with the SAME exact problem.[/QUOTE]

The Pentium M 770 isn't a 64bit CPU is it?  I think you are having a different problem.  Are you running the latest Breezy?  There seems to be no drmMap problems with i386 versions of Breezy.

---

### Post by Schizoid on 2005-10-20
Septor,

I ran some tests useing the ati installer, there were problems with pathing, but not to get side tracked with that now, I jut worked around it. once that was resolved I was still getting a drmmap issue. I'm currently working on a slim custom kernel, its complete I just have to rebuild the ati-installer packages against the kernel, I'll do this when I have some time. This might help determine if its a kernel relatad issue, ie  no drm in my kernel at all and no console framebuffer stuff.

Only other thing I can think of it there is a issue with mesa, since even drm radeon doesnt work for me, I dont know if thas the case for anyone else?

If you can think up some othere test or something else I can look at let me know.

---

### Post by Septor on 2005-10-20
Okay, I made a fix (i.e. workaround) for everyone.  Instructions and files are available at the bugzilla entry: [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

I have tested it myself (Radeon X550, amd64 3000+, Breezy) and it works fine:

```

$ LIBGL_DEBUG=verbose fgl_glxgears -fbo
Using GL_EXT_framebuffer_object
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
Can't open configuration file /etc/fglrxrc: No such file or directory.
Can't open configuration file /etc/drirc: No such file or directory.
Error in /home/acyr/.drirc line 1, column 0: no element found.
2762 frames in 5.0 seconds = 552.400 FPS
2981 frames in 5.0 seconds = 596.200 FPS
2975 frames in 5.0 seconds = 595.000 FPS
2991 frames in 5.0 seconds = 598.200 FPS

```

---

### Post by Téragone on 2005-10-20
Septor: 

Which Breezy ? i386 or AMD64


thanks

OUPS AMD64 I think since the path include lib64

---

### Post by Schizoid on 2005-10-20
ok good stuff working for me.

```

jupiter% LIBGL_DEBUG=verbose glxgears
libGL: XF86DRIGetClientDriverName: 8.16.20 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.16.20 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
```

thanks for all the work on this.

---

### Post by Corvash on 2005-10-20
Working, Acer Ferrari 3400, Radeon Mobility 9700

Thanks for all the work.

---

### Post by Kuolio on 2005-10-20
I have this bug too.. thanks for the workaround, I'll try it out later today. This should be fixed ASAP byt the devels, hope you all have made bugreports like mad on this ;)

---

### Post by Septor on 2005-10-20
[QUOTE=Téragone]Septor: 

Which Breezy ? i386 or AMD64


thanks

OUPS AMD64 I think since the path include lib64[/QUOTE]

Yup this is an AMD64 only problem. i386 users do not have a problem with libdri.a at all.

---

### Post by archiesteel on 2005-10-20
Yay! It works!

Thanks Septor for you hard work, it is greatly appreciated!

---

### Post by DRF on 2005-10-20
Thanks Septor!

Replacing the 'libdri.a' file worked here also. Very good timing as my new monitor arrived today :) 

Hopefully it won't be too long before they add this fix into the packages in the repositories.

Daniel

(My system is a Radeon 9800 and AMD64 3400)

---

### Post by mumbly58 on 2005-10-20
**[SIZE="4"]CHAMPAGNE !!![/SIZE]**

It works great !

Thanx !!!!!!!!!!!! :) 

My System :
Acer Aspire 5024 - Turion ML-34 64 bits (1.8 Ghz) - ATI Radeon Mobilty X700 PCIE (RV410)

---

### Post by n6mod on 2005-10-20
All good here:

Acer Ferrari 3200: Athlon64 2800+/Radeon 9[6|7]00 (depends who you ask)

-Zandr

---

### Post by archiesteel on 2005-10-20
As a side note...I just found out that, now that DRI works, I can no longer suspend-to-RAM (well, to be more precise, I cannot resume from suspend-to-RAM). This is a well-known problem, for which I don't think there's a workaround. It seems I have to choose between 3D acceleration or swsusp!

Linux Laptops: not for the faint of heart!! :D

---

### Post by mlomker on 2005-10-20
> Okay, I made a fix (i.e. workaround) for everyone.  Instructions and files are available at the bugzilla entry: [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)


Septor, 

I just confirmed that the libdri downgrade also fixes Breezy's included 8.16.20 drivers.  I have updated my how-to for 8.16.20 and will now build the .debs for amd64 and make them available.

Thanks a million for your work!  I know that there are going to be a lot of happy 64-bit users now.

---

### Post by pgarciagon on 2005-10-20
Open GL accel. working  now!

accer ferrari 4000/amd turion 64/ati x700128

Thank you very much for your hardwork!

---

### Post by chabadoo on 2005-10-20
Hi All,

As far I did the following:
1) extract the ati-installer files: sh ati-driver-installer-8.18.6-i386.run
--extract
   (or the 64bit version if that is what you are using).
2) apply the patch: patch -p0 < /path/to/this/ubuntu.patch
3) change into the installer directory: cd fglrx-install
4) build the packages: ./ati-installer 8.18.6 --buildpkg Ubuntu/breezy

but during step 4 I got the following output

```
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
/tmp/fglrx ~/Download/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.18.6-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
        cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
dh_testdir
make: dh_testdir: Kommando nicht gefunden
make: *** [configure] Fehler 127
~/Download/fglrx-install
```

kernel-headers, libstdc++5, and gcc are installed!

Does anybody write a howto for this?
I have an ACER 5022WLMI

@mumbly58 maybe your help would be most usefull

But of course I am thankfull for any helping hands

---

### Post by Septor on 2005-10-20
[QUOTE=chabadoo]
dh_testdir
make: dh_testdir: Kommando nicht gefunden
make: *** [configure] Fehler 127
~/Download/fglrx-install[/CODE]
[/QUOTE]

Well I don't speak german, but that looks like "command not found" to me :)

You need to install the "debhelper" package for the dh_* tools in order to build the packages.  You'll also need: fakeroot, build-essential, gcc, and module-assistant, if you don't have them already.  mlomker said he was going to make amd64 .debs and post them somewhere, so you could probably just wait for them if you don't want to go through the trouble of building them yourself.

---

### Post by mlomker on 2005-10-20
> mlomker said he was going to make amd64 .debs and post them somewhere, so you could probably just wait for them if you don't want to go through the trouble of building them yourself.

Yup.  I just made them available at the USA link on my [how-to.]("http://ubuntuforums.org/showthread.php?t=78466")  I'll send a PM to moccah in the hopes that he'll host them for Europe.

---

### Post by eightysix on 2005-10-21
I did everything on the instructions, but I still get this:

```
$ LIBGL_DEBUG=verbose fgl_glxgears -fbo
Using GL_EXT_framebuffer_object
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
Segmentation fault

```

---

### Post by eightysix on 2005-10-21
[QUOTE=eightysix]I did everything on the instructions, but I still get this:

```
$ LIBGL_DEBUG=verbose fgl_glxgears -fbo
Using GL_EXT_framebuffer_object
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
Segmentation fault

```[/QUOTE]

And when I try using the fglrx driver, X crashes when I try to start it up after reboot.

---

### Post by mlomker on 2005-10-21
> And when I try using the fglrx driver, X crashes when I try to start it up after reboot.

If you updated the libdri.a file and installed using the .deb approach then it might be time to try a fresh reload on your machine.  I tested the install three times on my machine and it works perfectly.  You may have a unique problem with your hardware combination but you won't know for sure unless you do a clean load.

If you have more than one partition then you could boot up a copy of Knoppix and use partimage to back-up your existing install.  That's what I do now and I can 'reload' my operating system in 5 minutes to test things...very handy.

---

### Post by Schizoid on 2005-10-21
[QUOTE=mlomker]Septor, 

I just confirmed that the libdri downgrade also fixes Breezy's included 8.16.20 drivers.  I have updated my how-to for 8.16.20 and will now build the .debs for amd64 and make them available.

Thanks a million for your work!  I know that there are going to be a lot of happy 64-bit users now.[/QUOTE]

If your makeing deb packages just with the libdri fix, can you make sure that its noted that it will break the radeon/drm driver support, radeon driver doenst seem to work for me could be related to the same problem as the ati dirvers, but if its not an isolated case then libdri version mismatches and radeon with complain, and disable drm.

---

### Post by mlomker on 2005-10-21
[QUOTE=Schizoid]If your makeing deb packages just with the libdri fix, can you make sure that its noted that it will break the radeon/drm driver support, radeon driver doenst seem to work for me could be related to the same problem as the ati dirvers, but if its not an isolated case then libdri version mismatches and radeon with complain, and disable drm.[/QUOTE]

Ubuntu has to fix that issue because libdri.a is a part of the xserver-xorg-core package.  My how-to has it as a separate file.  If you aren't running the fglrx driver on 64-bit then there's no reason to change it.

---

### Post by Schizoid on 2005-10-21
hehe sorry to bug you again buddy :) also I was thinking that it would be better to direct people to just use the ubuntu packages instead of the ati drivers so there is less confusion. I notice that you mention it in this thread and I noted it myself and should have posted something in that regards

---

### Post by mlomker on 2005-10-21
>  I was thinking that it would be better to direct people to just use the ubuntu packages instead of the ati drivers so there is less confusion. 

I'm not sure who this is directed at.  The top of my 8.18.6 how-to clearly states that you should use Ubuntu's drivers unless you are experiencing the widescreen resolution problem.

---

### Post by Schizoid on 2005-10-21
[QUOTE=mlomker]Ubuntu has to fix that issue because libdri.a is a part of the xserver-xorg-common package.  My how-to has it as a separate file.  If you aren't running the fglrx driver on 64-bit then there's no reason to change it.[/QUOTE]

oh for sure I agree, but if people do want to use the radeon/drm driver ... I dont know switch back and forth this fix will break radeon support. Its just something I thought was worth noting in the faq.

---

### Post by mlomker on 2005-10-21
[QUOTE=Schizoid]oh for sure I agree, but if people do want to use the radeon/drm driver ... I dont know switch back and forth this fix will break radeon support. Its just something I thought was worth noting in the faq.[/QUOTE]

I suppose, but I can't imagine why anyone would switch back to the Radeon driver.  The people that install fglrx in the first place are doing so to play games and are concerned about 3D performance.

You could **sudo apt-get install --reinstall xserver-xorg-core** to overwrite the libdri.a file again.

---

### Post by Schizoid on 2005-10-21
both packages are supported by ubuntu, so they should both work, seeing as how this a quick fix for the ati drivers. But it also breaks another package in the process it should be noted that is does do that, even more so if we are aware of it.  

Either way its no big deal I agree its likely that someone wont switch back and forth.

---

### Post by mlomker on 2005-10-21
> both packages are supported by ubuntu, so they should both work, seeing as how this a quick fix for the ati drivers. 

I updated the how-to to suggest backing up the file.  The fact of the matter is that the fglrx drivers *are not* currently supported by Ubuntu, otherwise we wouldn't need this hack of a fix.  Whoever's in charge of the xorg packages needs to come up with a permanent solution.  I'd assume that Septor's already in touch or has filed a bug report for them.

---

### Post by Schizoid on 2005-10-21
great thanks alot buddy, and thanks for the great howto. 

edit.

Ah also sorry I wasnt aware that the ati driver are not supported by Ubuntu my bad. please for give me.

---

### Post by eightysix on 2005-10-21
[QUOTE=mlomker]If you updated the libdri.a file and installed using the .deb approach then it might be time to try a fresh reload on your machine.  I tested the install three times on my machine and it works perfectly.  You may have a unique problem with your hardware combination but you won't know for sure unless you do a clean load.

If you have more than one partition then you could boot up a copy of Knoppix and use partimage to back-up your existing install.  That's what I do now and I can 'reload' my operating system in 5 minutes to test things...very handy.[/QUOTE]

I'd rather not do that yet again. But, I think this is the root of the problem:

```
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

Fatal server error:
Module load failure
```

---

### Post by Schizoid on 2005-10-21
you need to comment out this line

 #Load    "int10"

in your xorg.conf file

---

### Post by mlomker on 2005-10-21
>  #Load    "int10"


Correct.  I was under the (apparently false) impression that eightsix was using my [how-to]("http://ubuntuforums.org/showthread.php?p=408111"), where that is already documented.

---

### Post by eightysix on 2005-10-21
[QUOTE=Schizoid]you need to comment out this line

 #Load    "int10"

in your xorg.conf file[/QUOTE]

I got it to work, but to my dissatisfaction. Everything was buggy under my Radeon 8500 so I switched back to the ati driver. I wonder if it's my dual monitor setup. I'll probably do more testing later. In any case, I'm just glad the driver works now. 

Thanks for the help guys!

---

### Post by ToastedToad on 2005-10-21
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)
```


Thanks to all who made this work. It's you guys that make ubuntu the top dog on the block......Great Job!!!!!!!!

---

### Post by zupermanz on 2005-10-22
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)
 :smile: :smile: :smile: :smile: :smile: :smile: :smile: 
Thanks!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by chabadoo on 2005-10-23
Hello,

chabadoo@LanCaster:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)

everything fine :razz: - thank you so much
--------------------------------------------------------------------------
but I still have a problem with the controlpanel

chabadoo@LanCaster:~$ fireglcontrolpanel
fireglcontrolpanel: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

Does anybody know the reason?

---

### Post by mlomker on 2005-10-23
> Does anybody know the reason?

Go into Synaptic and confirm that **libexpat1** is installed.

---

### Post by chabadoo on 2005-10-23
the packet is installed!

```
ldd /usr/bin/fireglcontrolpanel
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x55582000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0x55628000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x5563d000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x5568b000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x556a4000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x556ab000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x556ae000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x556bc000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x5577c000)
        **libexpat.so.0 => not found**
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0x557aa000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0x557ad000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0x557b5000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0x557b9000)
      **  libXxf86vm.so.1 => not found**
        libXft.so.2 => /usr/lib32/libXft.so.2 (0x55823000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0x55835000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x5583e000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x558f8000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x5591b000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x55926000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x55a54000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55a65000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x55a68000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x55a6d000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x55a81000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0x55aa0000)
```

```
ldd /usr/bin/fireglcontrolpanel|grep libexpat
        libexpat.so.0 => not found
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x55a81000)
```

[B]The real file is libexpat.so.1.0.0 with ~so.1 being linked to it and ~so.0
being linked to ~so.1

I've tried changing the links so both links point to the file. The libraries
are also in /usr/lib, and I've tried adding this to ld.so.conf and running
ldconfig. [/B]

Please help me - It would be so nice to have everything working on my laptop

Another thread about that @linuxquestions.org
[http://www.linuxquestions.org/questions/showthread.php?s=&postid=1903799#post1903799](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1903799#post1903799)

---

### Post by chabadoo on 2005-10-24
I solved the problem with the first while via downloading the lib file from [http://membled.com/lib](http://membled.com/lib) - I inserted it directly for the so.0 link

but it does NOT solve the problem with libXxf86vm.so.1 - It seemes that something is wrong with the files they are pointing to.

Can anybody send me another version of this file (I have libXxf86vm.so.1.1.0 Size 20032)?
[B]
@mlomker
The file that comes with breezy does not work - so please send me your file![/B]

---

### Post by mlomker on 2005-10-24
> The file that comes with breezy does not work - so please send me your file![/B]

Are you running 32-bit?  I don't have any non-Breezy files on my system.  Try reinstalling the libxxf86vm1 package.

```

sudo apt-get install --reinstall libxxf86vm1
sudo ldconfig

```

---

### Post by chabadoo on 2005-10-24
i am running 64-bit system with your great 64 bit deb packages

already tried to reinstall - it seemes, that the link is ok, but the control center want's a different version of the file!!!

That's what worked for me with the other lib!

---

### Post by mlomker on 2005-10-24
[QUOTE=chabadoo]i am running 64-bit system with your great 64 bit deb packages
[/QUOTE]

Oh, then you probably just need to point at the 32-bit libraries that are already installed....that's what we did in Hoary.  Take a look at this [script.]("http://www.ubuntuforums.org/attachment.php?attachmentid=2567&d=1127497569")

You'll probably just have to edit the path to point to /usr/bin.  It's the export command prior to running the thing that matters.

---

### Post by psusi on 2005-11-02
So the conclusion then is that the firegl mmap errors are caused by breakage in recent versions of xserver-xorg-core?  I currently have 6.8.2-77 installed but I can't figure out how to go back to the older version that supposedly works.  The versions tab only shows that version, and package->force version is disabled.

---

### Post by mlomker on 2005-11-02
[QUOTE=psusi]So the conclusion then is that the firegl mmap errors are caused by breakage in recent versions of xserver-xorg-core? [/QUOTE]

No, the fix is to downgrade the libdri.a file...assuming you're running 64-bit.  The process is in the [how-to's]("http://ubuntuforums.org/showthread.php?t=75382") for both versions of the driver.

---

### Post by beppo on 2005-12-17
[QUOTE=mlomker]Oh, then you probably just need to point at the 32-bit libraries that are already installed....that's what we did in Hoary.  Take a look at this [script.]("http://www.ubuntuforums.org/attachment.php?attachmentid=2567&d=1127497569")

You'll probably just have to edit the path to point to /usr/bin.  It's the export command prior to running the thing that matters.[/QUOTE]

This does not solve the problem. As far as I could understand from 

 strace fireglcontrolpanel

the problem is that the 32bit version of the library is needed. It is however nowhere on the system. (I also did the above recommened reinstall of the package containing the library; according to synaptic it only contains the 64 bit version of the library!) :confused:

---

