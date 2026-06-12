---
title: "NVIDIA GTX 285 fans stuck at 2402RPM"
date: 2009-09-10
forum: x86 64-bit Users
---

### Post by Bekul on 2009-09-10
Hey, just built my first new computer in over four years, Intel Core i7, with an NVIDIA GTX 285, and of course, the 64 bit version of Ubuntu (which only sees 3.8GB of my 6GB of RAM, but that's another thread)

The point of /this/ thread, is that, even while doing /nothing/, just looking at the desktop, graphics card fans are maxed out, at almost 2500RPM.

That isn't right.

The 'NVIDIA X Server Settings' program doesn't have any fan control settings, and this is loud.

I installed nvclock in the terminal, but after going nvclock -i, I get, after a second, '*** stack smashing detected ***: nvclock terminated', which sounds really bad and dangerous.

Questions: How do I calm this raging 2402RPM fan speed? nvclock doesn't seem to want to work, and I'm leery of forcing it when simply trying to get card info causes '*** stack smashing detected ***: nvclock terminated'.

What can I safely do to make the fan speed run, at best automatically, or at the very least, at less than 2402RPM?

Full output of nvclock -i pasted below:

:~$ nvclock -i
Unhandled init script entry with id '&#65533;' at e9d6
Unhandled init script entry with id '&#65533;' at e9f9
Unhandled init script entry with id '&#65533;' at ea1c
Unhandled init script entry with id '&#65533;' at ea3f
-- General info --
Card: 		nvidia GeForce GTX 285
Architecture: 	GT200 B1
PCI id: 	0x5e3
GPU clock: 	300.856 MHz
Bustype: 	PCI-Express

-- Shader info --
Clock: 1296.000 MHz
Stream units: 240 (11111111b)
ROP units: 32 (11111111b)
-- Memory info --
Amount: 	1024 MB
Type: 		512 bit DDR3
Clock: 		1188.000 MHz

-- PCI-Express info --
Current Rate: 	16X
Maximum rate: 	16X

-- Sensor info --
Sensor: Analog Devices ADT7473
Board temperature: 39C
GPU temperature: 48C
Fanspeed: 2402 RPM
Fanspeed mode: auto
PWM duty cycle: 97.6%

-- VideoBios information --
Version: 62.00.50.00.01
Signon message: GT200 P892 SKU 0052 VGA BIOS
Performance level 0: gpu 300MHz/shader 600MHz/memory 100MHz/1.05V/100%
Performance level 1: gpu 400MHz/shader 800MHz/memory 300MHz/1.05V/100%
Performance level 2: gpu 680MHz/shader 1476MHz/memory 1250MHz/1.15V/100%
VID mask: 1
Voltage level 0: 1.05V, VID: 1
Voltage level 1: 1.15V, VID: 0

*** stack smashing detected ***: nvclock terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f6444a5a2c7]
/lib/libc.so.6(__fortify_fail+0x0)[0x7f6444a5a290]
nvclock[0x4031e0]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f64449795a6]
nvclock[0x4019a9]
======= Memory map: ========
00400000-00420000 r-xp 00000000 08:11 15591145                           /usr/local/bin/nvclock
0061f000-00620000 r--p 0001f000 08:11 15591145                           /usr/local/bin/nvclock
00620000-00621000 rw-p 00020000 08:11 15591145                           /usr/local/bin/nvclock
00621000-00622000 rw-p 00621000 00:00 0 
021d5000-021f6000 rw-p 021d5000 00:00 0                                  [heap]
7f6443f1b000-7f6443f31000 r-xp 00000000 08:11 49971261                   /lib/libgcc_s.so.1
7f6443f31000-7f6444131000 ---p 00016000 08:11 49971261                   /lib/libgcc_s.so.1
7f6444131000-7f6444132000 r--p 00016000 08:11 49971261                   /lib/libgcc_s.so.1
7f6444132000-7f6444133000 rw-p 00017000 08:11 49971261                   /lib/libgcc_s.so.1
7f6444133000-7f6444138000 r-xp 00000000 08:11 15509050                   /usr/lib/libXdmcp.so.6.0.0
7f6444138000-7f6444337000 ---p 00005000 08:11 15509050                   /usr/lib/libXdmcp.so.6.0.0
7f6444337000-7f6444338000 rw-p 00004000 08:11 15509050                   /usr/lib/libXdmcp.so.6.0.0
7f6444338000-7f644433a000 r-xp 00000000 08:11 15509039                   /usr/lib/libXau.so.6.0.0
7f644433a000-7f6444539000 ---p 00002000 08:11 15509039                   /usr/lib/libXau.so.6.0.0
7f6444539000-7f644453a000 r--p 00001000 08:11 15509039                   /usr/lib/libXau.so.6.0.0
7f644453a000-7f644453b000 rw-p 00002000 08:11 15509039                   /usr/lib/libXau.so.6.0.0
7f644453b000-7f644453d000 r-xp 00000000 08:11 49971253                   /lib/libdl-2.9.so
7f644453d000-7f644473d000 ---p 00002000 08:11 49971253                   /lib/libdl-2.9.so
7f644473d000-7f644473e000 r--p 00002000 08:11 49971253                   /lib/libdl-2.9.so
7f644473e000-7f644473f000 rw-p 00003000 08:11 49971253                   /lib/libdl-2.9.so
7f644473f000-7f644475a000 r-xp 00000000 08:11 15509623                   /usr/lib/libxcb.so.1.1.0
7f644475a000-7f6444959000 ---p 0001b000 08:11 15509623                   /usr/lib/libxcb.so.1.1.0
7f6444959000-7f644495a000 r--p 0001a000 08:11 15509623                   /usr/lib/libxcb.so.1.1.0
7f644495a000-7f644495b000 rw-p 0001b000 08:11 15509623                   /usr/lib/libxcb.so.1.1.0
7f644495b000-7f6444ac3000 r-xp 00000000 08:11 49971239                   /lib/libc-2.9.so
7f6444ac3000-7f6444cc3000 ---p 00168000 08:11 49971239                   /lib/libc-2.9.so
7f6444cc3000-7f6444cc7000 r--p 00168000 08:11 49971239                   /lib/libc-2.9.so
7f6444cc7000-7f6444cc8000 rw-p 0016c000 08:11 49971239                   /lib/libc-2.9.so
7f6444cc8000-7f6444ccd000 rw-p 7f6444cc8000 00:00 0 
7f6444ccd000-7f6444cde000 r-xp 00000000 08:11 15509052                   /usr/lib/libXext.so.6.4.0
7f6444cde000-7f6444edd000 ---p 00011000 08:11 15509052                   /usr/lib/libXext.so.6.4.0
7f6444edd000-7f6444ede000 r--p 00010000 08:11 15509052                   /usr/lib/libXext.so.6.4.0
7f6444ede000-7f6444edf000 rw-p 00011000 08:11 15509052                   /usr/lib/libXext.so.6.4.0
7f6444edf000-7f6444fe1000 r-xp 00000000 08:11 15509033                   /usr/lib/libX11.so.6.2.0
7f6444fe1000-7f64451e1000 ---p 00102000 08:11 15509033                   /usr/lib/libX11.so.6.2.0
7f64451e1000-7f64451e2000 r--p 00102000 08:11 15509033                   /usr/lib/libX11.so.6.2.0
7f64451e2000-7f64451e6000 rw-p 00103000 08:11 15509033                   /usr/lib/libX11.so.6.2.0
7f64451e6000-7f6445206000 r-xp 00000000 08:11 49971219                   /lib/ld-2.9.so
7f64452a2000-7f64452a3000 rw-p 7f64452a2000 00:00 0 
7f64452a3000-7f64452a4000 rw-s de088000 00:0f 8227                       /dev/nvidia0
7f64452a4000-7f64452b4000 rw-s de300000 00:0f 8227                       /dev/nvidia0
7f64452b4000-7f64453b4000 rw-s de700000 00:0f 8227                       /dev/nvidia0
7f64453b4000-7f64453e4000 rw-s de000000 00:0f 8227                       /dev/nvidia0
7f64453e4000-7f64453e8000 rw-p 7f64453e4000 00:00 0 
7f64453eb000-7f64453ec000 rw-s de088000 00:0f 8227                       /dev/nvidia0
7f64453ec000-7f64453ee000 rw-s de680000 00:0f 8227                       /dev/nvidia0
7f64453ee000-7f64453fe000 rw-s de610000 00:0f 8227                       /dev/nvidia0
7f64453fe000-7f6445400000 rw-s de601000 00:0f 8227                       /dev/nvidia0
7f6445400000-7f6445401000 rw-s de100000 00:0f 8227                       /dev/nvidia0
7f6445401000-7f6445402000 rw-s de101000 00:0f 8227                       /dev/nvidia0
7f6445402000-7f6445405000 rw-p 7f6445402000 00:00 0 
7f6445405000-7f6445406000 r--p 0001f000 08:11 49971219                   /lib/ld-2.9.so
7f6445406000-7f6445407000 rw-p 00020000 08:11 49971219                   /lib/ld-2.9.so
7fff4d3f2000-7fff4d407000 rw-p 7ffffffea000 00:00 0                      [stack]
7fff4d5ff000-7fff4d600000 r-xp 7fff4d5ff000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

---

### Post by DecipherXX on 2009-09-11
If you can, Try to boot into windows and change the speed. If you cant, your only option is eithe replace the card or buy an inline fan speed controller i'm afraid. =[

---

