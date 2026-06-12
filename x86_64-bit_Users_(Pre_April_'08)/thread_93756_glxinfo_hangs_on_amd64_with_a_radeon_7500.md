---
title: "glxinfo hangs on amd64 with a radeon 7500"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by bpow on 2005-11-22
3D accelleration was working for me under hoary, but now is not working since I upgraded to breezy. Oh, and it works when I boot to an ubuntu 32 bit install, just not under 64bit.

Hardware:
[LIST]
[*]Shuttle SK83G
[*]AMD Athlon64 2800+
[*]ATI Radeon 7500
[/LIST]

Kernel version is 2.6.12-9-amd64-k8

Symptoms:
[LIST]
[*]Things which would use 3D (screensavers, bzflag, tuxkart) run with near-100% CPU but don't actually do anything
[*]glxinfo just hangs, using near-100% CPU.
[/LIST]

So I have tried going through [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)

'dmesg | grep drm' shows:
> [   73.193717] [drm] Initialized drm 1.0.0 20040925
[   73.220919] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]


'dmesg | grep agp' shows:
> 
[   24.758250] agpgart: Detected AGP bridge 0
[   24.760357] agpgart: AGP aperture is 64M @ 0xe8000000
[   24.775711] Linux agpgart interface v0.101 (c) Dave Jones
[   73.221656] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   73.221667] agpgart: Device is in legacy mode, falling back to 2.x
[   73.221672] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   73.221723] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode


Xorg.cond contains no '(EE)' lines. There are some (WW) lines but they are not relevant to dri.

Xorg.0.log does contain the line > (II) RADEON(0): Direct rendering enabled[QUOTE].

If I run
'LIBGL_DEBUG=verbose glxinfo', I get:
[QUOTE]
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 4.0.1 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0

... and the glxinfo process hangs using 99% CPU.

The last several lines of 'LIBGL_DEBUG=verbose strace glxinfo' are:
> 
munmap(0x2aaab0c53000, 113160)          = 0
brk(0x579000)                           = 0x579000
mmap(NULL, 806912, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaab0c53000
brk(0x59c000)                           = 0x59c000
brk(0x5bf000)                           = 0x5bf000
brk(0x5e2000)                           = 0x5e2000
brk(0x609000)                           = 0x609000
brk(0x62c000)                           = 0x62c000
brk(0x64f000)                           = 0x64f000
brk(0x673000)                           = 0x673000
brk(0x696000)                           = 0x696000
brk(0x6ba000)                           = 0x6ba000
brk(0x6dd000)                           = 0x6dd000
mmap(NULL, 184320, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaab0d18000
write(3, "\220\3\6\0\4\0\240\2#\0\0\0\0\0\0\0\0\0\0\0\1B_d\200\7"..., 36) = 36
read(3, "\1\0\31\0\0\0\0\0\0\0\0\0\0\0\0\0\4\0\240\2\0\0\0\0\226"..., 32) = 3


So I'm not sure where to go from here... Please help-- my two-year-old has been asking to see "race cars" (tuxkart) and "tanks" (bzflag).

---

### Post by rossigee on 2005-12-03
I had the same problem. After looking carefully at my /var/log/Xorg.0.log file, I spotted it having trouble opening /dev/dri/card0, because the /dev/dri directory was set to root-only writable. I fixed it to with:

sudo chmod 770 /dev/dri
sudo chown root:video

My user is already a member of the video group, and those are the perms on the /dev/dri/card0 file. After this, my glxinfo magically started working. Hope this helps.

---

### Post by rossigee on 2005-12-03
[QUOTE=rossigee]After this, my glxinfo magically started working. Hope this helps.[/QUOTE]

Sorry, I had glxgears running for a couple of minutes while I wrote that smug reply. After that, I couldn't get anything GL-related to work again. All back to the old 'read(3,' hanging problem while reading from /tmp/.X11 blah. I'm guessing that this is a 64-bit issue. BTW, my card is a Radeon 9200SE.

---

