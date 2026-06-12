---
title: "System randomly freezes"
date: 2007-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cirdan7 on 2007-01-11
This is *really* making me mad. My system always seems to freeze, randomly. It randomly freezes, I can restart and do the same exact thing and it'll do it fine, my computer just seems to randomly freeze. ctrl-alt-backspace, escape or anything doesn't work. The mouse freezes and I can't do anything to fix it beside restart the computer. Is there anything I can do to try and stabilize this thing? It also freezes with the live CD so its not something I installed. I have Edgy with all the updates, and beryl. 

Pentium 4 3.0 Ghz Dual Core Hyper Threaded
1 gig of ram
Radeon 9700

I tried turning off hyper threading in the BIOS but that didn't seem to help. I have a feeling I might need to recompile the kernel for my computer, how do I go about doing this or is there anything else I should try?

---

### Post by Cirdan7 on 2007-01-12
Here is a log I found in /var/crash. Any help would be great, I am getting tiered of this thing randomly crashing.

_usr_sbin_synaptic.0.crash

```

ProblemType: Crash
Date: Wed Jan 10 17:58:35 2007
ExecutablePath: /usr/sbin/synaptic
ProcCmdline: /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 41943043 --progress-str Please\ wait,\ this\ can\ take\ some\ time. --finish-str Update\ is\ complete --set-selections-file /tmp/tmp6WBdoX
ProcCwd: /home/ryan
ProcEnviron:
 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
 LANG=en_US.UTF-8
 SHELL=/bin/bash
ProcMaps:
 08048000-080fb000 r-xp 00000000 03:41 1914634    /usr/sbin/synaptic
 080fb000-080fe000 rw-p 000b3000 03:41 1914634    /usr/sbin/synaptic
 080fe000-083a6000 rw-p 080fe000 00:00 0          [heap]
 b667c000-b668b000 r-xp 00000000 03:41 97961      /lib/libbz2.so.1.0.3
 b668b000-b668c000 rw-p 0000f000 03:41 97961      /lib/libbz2.so.1.0.3
 b668c000-b66bc000 r-xp 00000000 03:41 1911059    /usr/lib/libcroco-0.6.so.3.0.1
 b66bc000-b66bf000 rw-p 0002f000 03:41 1911059    /usr/lib/libcroco-0.6.so.3.0.1
 b66bf000-b66e8000 r-xp 00000000 03:41 1911309    /usr/lib/libgsf-1.so.114.0.1
 b66e8000-b66eb000 rw-p 00028000 03:41 1911309    /usr/lib/libgsf-1.so.114.0.1
 b66eb000-b66ec000 rw-p b66eb000 00:00 0 
 b66ec000-b671b000 r-xp 00000000 03:41 1911571    /usr/lib/librsvg-2.so.2.16.0
 b671b000-b671c000 rw-p 0002f000 03:41 1911571    /usr/lib/librsvg-2.so.2.16.0
 b6726000-b6727000 r-xp 00000000 03:41 1913576    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
 b6727000-b6728000 rw-p 00001000 03:41 1913576    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
 b6728000-b6788000 rw-s 00000000 00:08 720910     /SYSV00000000 (deleted)
 b6788000-b678e000 r-xp 00000000 03:41 1913575    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
 b678e000-b678f000 rw-p 00005000 03:41 1913575    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
 b678f000-b67fb000 r--p 00000000 03:41 2170712    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
 b67fb000-b6982000 r--p 00000000 03:41 2256938    /usr/share/icons/hicolor/icon-theme.cache
 b6982000-b6fde000 r--p 00000000 03:41 2256657    /usr/share/icons/gnome/icon-theme.cache
 b6fde000-b6fe7000 r--p 00000000 03:41 2256650    /usr/share/icons/Mist/icon-theme.cache
 b6fe7000-b6fe9000 r-xp 00000000 03:41 2041406    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
 b6fe9000-b6fea000 rw-p 00001000 03:41 2041406    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
 b6fea000-b705b000 r--p 00000000 03:41 2170716    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
 b705b000-b7065000 r-xp 00000000 03:41 1913542    /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
 b7065000-b7066000 rw-p 00009000 03:41 1913542    /usr/lib/gtk-2.0/2.10.0/engines/libmist.so
 b7066000-b706f000 r-xp 00000000 03:41 101018     /lib/tls/i686/cmov/libnss_files-2.4.so
 b706f000-b7071000 rw-p 00008000 03:41 101018     /lib/tls/i686/cmov/libnss_files-2.4.so
 b7071000-b7079000 r-xp 00000000 03:41 101022     /lib/tls/i686/cmov/libnss_nis-2.4.so
 b7079000-b707b000 rw-p 00007000 03:41 101022     /lib/tls/i686/cmov/libnss_nis-2.4.so
 b707b000-b708d000 r-xp 00000000 03:41 101012     /lib/tls/i686/cmov/libnsl-2.4.so
 b708d000-b708f000 rw-p 00011000 03:41 101012     /lib/tls/i686/cmov/libnsl-2.4.so
 b708f000-b7091000 rw-p b708f000 00:00 0 
 b7091000-b7098000 r-xp 00000000 03:41 101014     /lib/tls/i686/cmov/libnss_compat-2.4.so
 b7098000-b709a000 rw-p 00006000 03:41 101014     /lib/tls/i686/cmov/libnss_compat-2.4.so
 b709b000-b709f000 r-xp 00000000 03:41 1913568    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
 b709f000-b70a0000 rw-p 00003000 03:41 1913568    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
 b70a1000-b70a2000 r-xp 00000000 03:41 1912997    /usr/lib/gconv/ISO8859-1.so
 b70a2000-b70a4000 rw-p 00001000 03:41 1912997    /usr/lib/gconv/ISO8859-1.so
 b70a4000-b70a5000 r-xp 00000000 03:41 1911824    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
 b70a5000-b70a6000 rw-p 00000000 03:41 1911824    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
 b70a6000-b70d9000 r--p 00000000 03:41 1975976    /usr/lib/locale/en_US.utf8/LC_CTYPE
 b70d9000-b70da000 r--p 00000000 03:41 1975981    /usr/lib/locale/en_US.utf8/LC_NUMERIC
 b70da000-b70db000 r--p 00000000 03:41 1975984    /usr/lib/locale/en_US.utf8/LC_TIME
 b70db000-b71b2000 r--p 00000000 03:41 1975975    /usr/lib/locale/en_US.utf8/LC_COLLATE
 b71b2000-b71b3000 r--p 00000000 03:41 1975979    /usr/lib/locale/en_US.utf8/LC_MONETARY
 b71b3000-b71b4000 r--p 00000000 03:41 1975985    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
 b71b4000-b71b5000 r--p 00000000 03:41 1975982    /usr/lib/locale/en_US.utf8/LC_PAPER
 b71b5000-b71b6000 r--p 00000000 03:41 1975980    /usr/lib/locale/en_US.utf8/LC_NAME
 b71b6000-b71b7000 r--p 00000000 03:41 1975974    /usr/lib/locale/en_US.utf8/LC_ADDRESS
 b71b7000-b71ba000 rw-p b71b7000 00:00 0 
 b71ba000-b71cf000 r-xp 00000000 03:41 1910910    /usr/lib/libICE.so.6.3.0
 b71cf000-b71d0000 rw-p 00014000 03:41 1910910    /usr/lib/libICE.so.6.3.0
 b71d0000-b71d2000 rw-p b71d0000 00:00 0 
 b71d2000-b71da000 r-xp 00000000 03:41 1910928    /usr/lib/libSM.so.6.0.0
 b71da000-b71db000 rw-p 00007000 03:41 1910928    /usr/lib/libSM.so.6.0.0
 b71db000-b71e2000 r-xp 00000000 03:41 101031     /lib/tls/i686/cmov/librt-2.4.so
 b71e2000-b71e4000 rw-p 00006000 03:41 101031     /lib/tls/i686/cmov/librt-2.4.so
 b71e4000-b71e5000 rw-p b71e4000 00:00 0 
 b71e5000-b71e9000 r-xp 00000000 03:41 1910947    /usr/lib/libXdmcp.so.6.0.0
 b71e9000-b71ea000 rw-p 00003000 03:41 1910947    /usr/lib/libXdmcp.so.6.0.0
 b71ea000-b720c000 r-xp 00000000 03:41 1911544    /usr/lib/libpng12.so.0.1.2.8
 b720c000-b720d000 rw-p 00021000 03:41 1911544    /usr/lib/libpng12.so.0.1.2.8
 b720d000-b720f000 r-xp 00000000 03:41 1910938    /usr/lib/libXau.so.6.0.0
 b720f000-b7210000 rw-p 00001000 03:41 1910938    /usr/lib/libXau.so.6.0.0
 b7210000-b722c000 r-xp 00000000 03:41 1911132    /usr/lib/libexpat.so.1.0.0
 b722c000-b722e000 rw-p 0001c000 03:41 1911132    /usr/lib/libexpat.so.1.0.0
 b722e000-b7295000 r-xp 00000000 03:41 1911148    /usr/lib/libfreetype.so.6.3.10
 b7295000-b7298000 rw-p 00067000 03:41 1911148    /usr/lib/libfreetype.so.6.3.10
 b7298000-b7299000 rw-p b7298000 00:00 0 
 b7299000-b72ac000 r-xp 00000000 03:41 1911678    /usr/lib/libz.so.1.2.3
 b72ac000-b72ad000 rw-p 00012000 03:41 1911678    /usr/lib/libz.so.1.2.3
 b72ad000-b73da000 r-xp 00000000 03:41 101001     /lib/tls/i686/cmov/libc-2.4.so
 b73da000-b73dc000 r--p 0012c000 03:41 101001     /lib/tls/i686/cmov/libc-2.4.so
 b73dc000-b73de000 rw-p 0012e000 03:41 101001     /lib/tls/i686/cmov/libc-2.4.so
 b73de000-b73e1000 rw-p b73de000 00:00 0 
 b73e1000-b73eb000 r-xp 00000000 03:41 97987      /lib/libgcc_s.so.1
 b73eb000-b73ec000 rw-p 00009000 03:41 97987      /lib/libgcc_s.so.1
 b73ec000-b74c0000 r-xp 00000000 03:41 1911621    /usr/lib/libstdc++.so.6.0.8
 b74c0000-b74c3000 r--p 000d4000 03:41 1911621    /usr/lib/libstdc++.so.6.0.8
 b74c3000-b74c5000 rw-p 000d7000 03:41 1911621    /usr/lib/libstdc++.so.6.0.8
 b74c5000-b74cb000 rw-p b74c5000 00:00 0 
 b74cb000-b74da000 r-xp 00000000 03:41 101027     /lib/tls/i686/cmov/libpthread-2.4.so
 b74da000-b74dc000 rw-p 0000f000 03:41 101027     /lib/tls/i686/cmov/libpthread-2.4.so
 b74dc000-b74df000 rw-p b74dc000 00:00 0 
 b74df000-b74e2000 r-xp 00000000 03:41 1911426    /usr/lib/liblaunchpad-integration.so.0.0.0
 b74e2000-b74e3000 rw-p 00002000 03:41 1911426    /usr/lib/liblaunchpad-integration.so.0.0.0
 b74e3000-b750d000 r-xp 00000000 03:41 1911523    /usr/lib/libpangoft2-1.0.so.0.1400.5
 b750d000-b750e000 rw-p 00029000 03:41 1911523    /usr/lib/libpangoft2-1.0.so.0.1400.5
 b750e000-b7532000 r-xp 00000000 03:41 101009     /lib/tls/i686/cmov/libm-2.4.so
 b7532000-b7534000 rw-p 00023000 03:41 101009     /lib/tls/i686/cmov/libm-2.4.so
 b7534000-b753e000 r-xp 00000000 03:41 1911527    /usr/lib/libpangox-1.0.so.0.1400.5
 b753e000-b753f000 rw-p 00009000 03:41 1911527    /usr/lib/libpangox-1.0.so.0.1400.5
 b753f000-b7545000 r-xp 00000000 03:41 1911529    /usr/lib/libpangoxft-1.0.so.0.1400.5
 b7545000-b7546000 rw-p 00005000 03:41 1911529    /usr/lib/libpangoxft-1.0.so.0.1400.5
 b7546000-b7557000 r-xp 00000000 03:41 1910957    /usr/lib/libXft.so.2.1.2
 b7557000-b7558000 rw-p 00010000 03:41 1910957    /usr/lib/libXft.so.2.1.2
 b7558000-b7559000 rw-p b7558000 00:00 0 
 b7559000-b7590000 r-xp 00000000 03:41 97997      /lib/libncurses.so.5.5
 b7590000-b7598000 rw-p 00037000 03:41 97997      /lib/libncurses.so.5.5
 b7598000-b7599000 rw-p b7598000 00:00 0 
 b7599000-b7646000 r-xp 00000000 03:41 1911649    /usr/lib/libvte.so.9.1.6
 b7646000-b7649000 rw-p 000ad000 03:41 1911649    /usr/lib/libvte.so.9.1.6
 b7649000-b76da000 r-xp 00000000 03:41 1911239    /usr/lib/libglib-2.0.so.0.1200.4
 b76da000-b76db000 rw-p 00091000 03:41 1911239    /usr/lib/libglib-2.0.so.0.1200.4
 b76db000-b76dd000 r-xp 00000000 03:41 101007     /lib/tls/i686/cmov/libdl-2.4.so
 b76dd000-b76df000 rw-p 00001000 03:41 101007     /lib/tls/i686/cmov/libdl-2.4.so
 b76df000-b76e2000 r-xp 00000000 03:41 1911251    /usr/lib/libgmodule-2.0.so.0.1200.4
 b76e2000-b76e3000 rw-p 00002000 03:41 1911251    /usr/lib/libgmodule-2.0.so.0.1200.4
 b76e3000-b771c000 r-xp 00000000 03:41 1911291    /usr/lib/libgobject-2.0.so.0.1200.4
 b771c000-b771d000 rw-p 00038000 03:41 1911291    /usr/lib/libgobject-2.0.so.0.1200.4
 b771d000-b771e000 rw-p b771d000 00:00 0 
 b771e000-b7756000 r-xp 00000000 03:41 1911519    /usr/lib/libpango-1.0.so.0.1400.5
 b7756000-b7758000 rw-p 00037000 03:41 1911519    /usr/lib/libpango-1.0.so.0.1400.5
 b7758000-b781e000 r-xp 00000000 03:41 1910932    /usr/lib/libX11.so.6.2.0
 b781e000-b7821000 rw-p 000c5000 03:41 1910932    /usr/lib/libX11.so.6.2.0
 b7821000-b7881000 r-xp 00000000 03:41 1911043    /usr/lib/libcairo.so.2.9.2
 b7881000-b7883000 rw-p 0005f000 03:41 1911043    /usr/lib/libcairo.so.2.9.2
 b7883000-b7887000 r-xp 00000000 03:41 1910953    /usr/lib/libXfixes.so.3.1.0
 b7887000-b7888000 rw-p 00003000 03:41 1910953    /usr/lib/libXfixes.so.3.1.0
 b7888000-b7890000 r-xp 00000000 03:41 1910943    /usr/lib/libXcursor.so.1.0.2
 b7890000-b7891000 rw-p 00007000 03:41 1910943    /usr/lib/libXcursor.so.1.0.2
 b7891000-b7893000 r-xp 00000000 03:41 1910971    /usr/lib/libXrandr.so.2.0.0
 b7893000-b7894000 rw-p 00002000 03:41 1910971    /usr/lib/libXrandr.so.2.0.0
 b7894000-b7895000 rw-p b7894000 00:00 0 
 b7895000-b789c000 r-xp 00000000 03:41 1910959    /usr/lib/libXi.so.6.0.0
 b789c000-b789d000 rw-p 00006000 03:41 1910959    /usr/lib/libXi.so.6.0.0
 b789d000-b789f000 r-xp 00000000 03:41 1910961    /usr/lib/libXinerama.so.1.0.0
 b789f000-b78a0000 rw-p 00001000 03:41 1910961    /usr/lib/libXinerama.so.1.0.0
 b78a0000-b78a7000 r-xp 00000000 03:41 1910973    /usr/lib/libXrender.so.1.3.0
 b78a7000-b78a8000 rw-p 00006000 03:41 1910973    /usr/lib/libXrender.so.1.3.0
 b78a8000-b78b4000 r-xp 00000000 03:41 1910951    /usr/lib/libXext.so.6.4.0
 b78b4000-b78b5000 rw-p 0000c000 03:41 1910951    /usr/lib/libXext.so.6.4.0
 b78b5000-b78de000 r-xp 00000000 03:41 1911138    /usr/lib/libfontconfig.so.1.0.4
 b78de000-b78e3000 rw-p 00028000 03:41 1911138    /usr/lib/libfontconfig.so.1.0.4
 b78e3000-b78e4000 rw-p b78e3000 00:00 0 
 b78e4000-b78eb000 r-xp 00000000 03:41 1911521    /usr/lib/libpangocairo-1.0.so.0.1400.5
 b78eb000-b78ec000 rw-p 00006000 03:41 1911521    /usr/lib/libpangocairo-1.0.so.0.1400.5
 b78ec000-b78ed000 rw-p b78ec000 00:00 0 
 b78ed000-b7902000 r-xp 00000000 03:41 1911192    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
 b7902000-b7903000 rw-p 00015000 03:41 1911192    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
 b7903000-b791b000 r-xp 00000000 03:41 1911010    /usr/lib/libatk-1.0.so.0.1213.0
 b791b000-b791d000 rw-p 00017000 03:41 1911010    /usr/lib/libatk-1.0.so.0.1213.0
 b791d000-b799e000 r-xp 00000000 03:41 1911190    /usr/lib/libgdk-x11-2.0.so.0.1000.6
 b799e000-b79a1000 rw-p 00081000 03:41 1911190    /usr/lib/libgdk-x11-2.0.so.0.1000.6
 b79a1000-b7ab4000 r-xp 00000000 03:41 1911666    /usr/lib/libxml2.so.2.6.26
 b7ab4000-b7ab9000 rw-p 00113000 03:41 1911666    /usr/lib/libxml2.so.2.6.26
 b7ab9000-b7aba000 rw-p b7ab9000 00:00 0 
 b7aba000-b7e03000 r-xp 00000000 03:41 1911346    /usr/lib/libgtk-x11-2.0.so.0.1000.6
 b7e03000-b7e09000 rw-p 00349000 03:41 1911346    /usr/lib/libgtk-x11-2.0.so.0.1000.6
 b7e09000-b7e0a000 rw-p b7e09000 00:00 0 
 b7e0a000-b7e21000 r-xp 00000000 03:41 1911235    /usr/lib/libglade-2.0.so.0.0.7
 b7e21000-b7e22000 rw-p 00016000 03:41 1911235    /usr/lib/libglade-2.0.so.0.0.7
 b7e22000-b7e23000 rw-p b7e22000 00:00 0 
 b7e23000-b7e36000 r-xp 00000000 03:41 1910995    /usr/lib/libapt-inst-libc6.4-6.so.1.1.0
 b7e36000-b7e37000 rw-p 00013000 03:41 1910995    /usr/lib/libapt-inst-libc6.4-6.so.1.1.0
 b7e37000-b7f05000 r-xp 00000000 03:41 1910997    /usr/lib/libapt-pkg-libc6.4-6.so.3.51.0
 b7f05000-b7f07000 rw-p 000ce000 03:41 1910997    /usr/lib/libapt-pkg-libc6.4-6.so.3.51.0
 b7f07000-b7f08000 r--p 00000000 03:41 1975983    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
 b7f08000-b7f09000 r--p 00000000 03:41 1975978    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
 b7f09000-b7f10000 r--s 00000000 03:41 1913049    /usr/lib/gconv/gconv-modules.cache
 b7f10000-b7f11000 r--p 00000000 03:41 1975977    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
 b7f11000-b7f13000 rw-p b7f11000 00:00 0 
 b7f13000-b7f2c000 r-xp 00000000 03:41 97942      /lib/ld-2.4.so
 b7f2c000-b7f2e000 rw-p 00018000 03:41 97942      /lib/ld-2.4.so
 bfb95000-bfbaa000 rw-p bfb95000 00:00 0          [stack]
 ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
ProcStatus:
 Name:	synaptic
 State:	D (disk sleep)
 SleepAVG:	97%
 Tgid:	5044
 Pid:	5044
 PPid:	5043
 TracerPid:	0
 Uid:	0	0	0	0
 Gid:	0	0	0	0
 FDSize:	32
 Groups:	0 
 VmPeak:	   28776 kB
 VmSize:	   28772 kB
 VmLck:	       0 kB
 VmHWM:	   12284 kB
 VmRSS:	   12284 kB
 VmData:	    2852 kB
 VmStk:	      84 kB
 VmExe:	     716 kB
 VmLib:	   14136 kB
 VmPTE:	      36 kB
 Threads:	1
 SigQ:	0/4294967295
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000000
 SigIgn:	0000000021001000
 SigCgt:	0000000180000200
 CapInh:	0000000000000000
 CapPrm:	00000000fffffeff
 CapEff:	00000000fffffeff
 Cpus_allowed:	ff
 Mems_allowed:	1
```

---

### Post by juyanith on 2007-01-12
I doubt this is much help, but are you running beryl? This is exactly what happens to me when I run beryl. Everything will be fine for a random amount of time, then the display freezes and mouse and keyboard input seems blocked (eg. ctrl+alt+bs doesn't work). The system is still up as I can ssh in from another machine, but otherwise I have to do a hard reset. The only "fix" I have is to stick with metacity. :(

---

### Post by alek66 on 2007-01-12
Check for some temperature problems. Cheack acpi...

---

### Post by Cirdan7 on 2007-01-12
Yes I am running beryl, but it was doing to before I had it.

---

### Post by alek66 on 2007-01-14
> **Cirdan7 said:**
> Yes I am running beryl, but it was doing to before I had it.

When I had beryl installed on, it demanded a lot my computer, causing temp raises an that shutted down my laptop.

good luck
let me know how you solved the problem if you do

---

