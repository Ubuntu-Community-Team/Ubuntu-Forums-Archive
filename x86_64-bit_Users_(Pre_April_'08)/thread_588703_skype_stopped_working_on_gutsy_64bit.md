---
title: "skype stopped working on gutsy 64bit"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by keitsi on 2007-10-23
Hello,

I am having a problem with skype on gutsy amd64 platform.
I have installed the libraries required by skype, and actually skype worked fine for a couple of weeks (been using gutsy since the beta).

I don't yet know what caused it, but now when I start skype, it just halts after login. Before the problem I had the skype window open for a long time, so I can't know what change has caused this. I have tried reverting everything back but can't seem to make it work. It is also possible that some update broke it.

Running the static oss version of skype starts, but it just says "problem with sound device" whenever I try to call someone.

Running the alsa version halts when I should be hearing the starting sound (bzzzzzzziiiip or something like that).

I have tried removing ~/.Skype directory with no help. Also tried the static alsa version.

Sound works perfectly in every other program that uses alsa (at least amarok, wine, flash, vlc, kde/artsd).

Here, I run a backtrace on it with gdb:
```

keitsi@keitsi:~$ gdb skype
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(gdb) start
Function "main" not defined.
Make breakpoint pending on future shared library load? (y or [n])
Starting program: /usr/bin/skype
(no debugging symbols found)
warning: Lowest section in system-supplied DSO at 0xffffe000 is .hash at ffffe0b4
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 4141365456 (LWP 9500)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[New Thread 4139617168 (LWP 9503)]
[New Thread 4137978768 (LWP 9505)]
[New Thread 4137450384 (LWP 9506)]
[New Thread 4129057680 (LWP 9507)]
[New Thread 4128529296 (LWP 9508)]
[New Thread 4122733456 (LWP 9509)]
[New Thread 4118793104 (LWP 9510)]
[New Thread 4110400400 (LWP 9511)]
[Thread 4118793104 (LWP 9510) exited]
[Thread 4110400400 (LWP 9511) exited]
[New Thread 4126145424 (LWP 9513)]
[Thread 4126145424 (LWP 9513) exited]

Program received signal SIGINT, Interrupt.
[Switching to Thread 4141365456 (LWP 9500)]
0xffffe405 in __kernel_vsyscall ()
(gdb) backtrace
#0  0xffffe405 in __kernel_vsyscall ()
#1  0xf725d2db in semop () from /lib32/libc.so.6
#2  0xf7e9eb38 in snd_pcm_dsnoop_open () from /usr/lib32/libasound.so.2
#3  0xf7e9f438 in _snd_pcm_dsnoop_open () from /usr/lib32/libasound.so.2
#4  0xf7e69c65 in ?? () from /usr/lib32/libasound.so.2
#5  0xffeef0a8 in ?? ()
#6  0x09276b88 in ?? ()
#7  0x09244cd0 in ?? ()
#8  0x09276708 in ?? ()
#9  0x00000001 in ?? ()
#10 0x00000003 in ?? ()
#11 0x09276b8f in ?? ()
#12 0x00000000 in ?? ()
(gdb)

```

My system information:
```

keitsi@keitsi:~$ dpkg -l|grep skype
ii  skype                                      1.4.0.118-1                          Skype - Take a deep breath
keitsi@keitsi:~$ uname -a
Linux keitsi 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
keitsi@keitsi:~$ dpkg -l|grep asound
ii  lib32asound2                               1.0.14-1ubuntu8                      ALSA library (32bit)
ii  libasound2                                 1.0.14-1ubuntu8                      ALSA library
ii  libasound2-dev                             1.0.14-1ubuntu8                      ALSA library development files
ii  libasound2-plugins                         1.0.14-1ubuntu3                      ALSA library additional plugins
keitsi@keitsi:~$ ldd `which skype`
        linux-gate.so.1 =>  (0xffffe000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7e87000)
        librt.so.1 => /lib32/librt.so.1 (0xf7e7e000)
        libQtDBus.so.4 => /usr/lib32/libQtDBus.so.4 (0xf7e2b000)
        libQtGui.so.4 => /usr/lib32/libQtGui.so.4 (0xf7690000)
        libQtNetwork.so.4 => /usr/lib32/libQtNetwork.so.4 (0xf7600000)
        libQtCore.so.4 => /usr/lib32/libQtCore.so.4 (0xf7480000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7468000)
        libsigc-2.0.so.0 => /lib32/libsigc-2.0.so.0 (0xf7462000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf736e000)
        libm.so.6 => /lib32/libm.so.6 (0xf7349000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf733d000)
        libc.so.6 => /lib32/libc.so.6 (0xf71f3000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7102000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf70fe000)
        /lib/ld-linux.so.2 (0xf7f6a000)
        libdbus-1.so.3 => /usr/lib32/libdbus-1.so.3 (0xf70c8000)
        libQtXml.so.4 => /usr/lib32/libQtXml.so.4 (0xf706f000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf7044000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf702f000)
        libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf702a000)
        libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf6f6d000)
        libaudio.so.2 => /usr/lib32/libaudio.so.2 (0xf6f56000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0xf6f05000)
        libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf6ee2000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf6eda000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf6ec2000)
        libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6eb9000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6eb1000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6eab000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6ea6000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf6e9d000)
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf6e9a000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf6e29000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6e1b000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6e18000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6e13000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf6df2000)
keitsi@keitsi:~$ lspci|grep -i audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
keitsi@keitsi:~$ aplay -L
default:CARD=CK804
    NVidia CK804, NVidia CK804
    Default Audio Device
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=UART
    MPU-401 UART
    Default Audio Device
keitsi@keitsi:~$

```

Hardware:
- Asus A8N-SLI Premium
- AMD Athlon64 X2 3800+
- 2GB DDR

Any hints where to look at?

---

### Post by keitsi on 2007-10-24
Here's a screenshot:
[http://keitsi.minttupuffet.net/misc/gutsy_amd64_skype_hangs.png](http://keitsi.minttupuffet.net/misc/gutsy_amd64_skype_hangs.png)

(my WM painted the skype window dark when it stopped working)

---

### Post by ddave01 on 2007-10-26
Just want to advise that sound on my Skype (64Bit) stopped working when I upgraded to gutsy (kubuntu 7.10)

ddave

---

### Post by ddave01 on 2007-10-26
I do not know why but sound is now working in skype.  

Not sure what is going on when rebooting machine and getting different result. 

 I will monitor application over time,  there seems to be some instability in 7.10.   I did the version upgrade.

---

### Post by keitsi on 2007-11-04
Hello,

It seems that the following steps fixed my sound:
- Log into a GNOME session (I normally use KDE)
- Choose sound settings (or similar, the page where you select which device to use)
- Change every sound device in the dropdown boxes, and then change them back.
- Save settings.

After this, sound also works properly in KDE sessions, including skype.
Before the steps I also noticed some similar, random problems with amarok. Weirdly, some programs worked fine.

I hope this helps anyone having similar symptoms.

---

