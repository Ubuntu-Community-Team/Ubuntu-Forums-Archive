---
title: "Problem getting x-plane 8.40 running under 64bit Edgy"
date: 2006-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Saubazi on 2006-11-21
First problem - installation. I did not find any installation script so I don't know what to put where. 

DVD had something like this on it 
$ ls /media/cdrom1/
dvd_version.txt     installation.pdf     Installer_Windows.exe  X-Plane.ico
how to install.rtf  Installer Macintosh  X-Plane 8.40

 and
$ ls /media/cdrom1/X-Plane\ 8.40/
All                Linux Athlon XP    Linux Pentium 3  Windows
directory.txt.zip  Linux Generic x86  Macintosh

under Linux directories it looks like:
$ ls /media/cdrom1/X-Plane\ 8.40/Linux\ Generic\ x86/
Airfoil-Maker-i586.zip  Plane-Maker-i586.zip  World-Maker-i586.zip
Briefer-i586.zip        README.zip            X-Plane-i586.zip


and under All it looks like:
$ ls /media/cdrom1/X-Plane\ 8.40/All/
Aircraft  Airfoils  Custom Scenery  Instructions  Resources  Weapons

So some creativity and I copied binaries from the linux generic directory to /home/user/tmp and below it all these directories from "All"
It looks:
~/tmp$ ls
Aircraft                 Cycle Dump.txt         README
Airfoil-Maker-athlon-xp  Data.txt               Resources
Airfoil-Maker-i586       directory.txt          Weapons
Airfoils                 Instructions           World-Maker-athlon-xp
Briefer-athlon-xp        Log.txt                World-Maker-i586
Briefer-i586             Plane-Maker-athlon-xp  X-Plane-athlon-xp
Custom Scenery           Plane-Maker-i586       X-Plane-i586


and now for example:
~/tmp$ ldd X-Plane-i586 
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e43000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7dc9000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7dbb000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7cf2000)
        libopenal.so.0 => /usr/lib32/libopenal.so.0 (0xf7c52000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7c3f000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7c3b000)
        libm.so.6 => /lib32/libm.so.6 (0xf7c15000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7c09000)
        libc.so.6 => /lib32/libc.so.6 (0xf7ad5000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf79f6000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf79f3000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf79ee000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf792e000)
        libartsc.so.0 => /usr/lib32/libartsc.so.0 (0xf7928000)
        libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf7924000)
        libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf791f000)
        libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf788d000)
        libesd.so.0 => /usr/lib32/libesd.so.0 (0xf7883000)
        libaudiofile.so.0 => /usr/lib32/libaudiofile.so.0 (0xf7863000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf77da000)
        libvorbis.so.0 => /usr/lib32/libvorbis.so.0 (0xf77b2000)
        libvorbisfile.so.3 => /usr/lib32/libvorbisfile.so.3 (0xf77aa000)
        libsmpeg-0.4.so.0 => /usr/lib32/libsmpeg-0.4.so.0 (0xf7752000)
        /lib/ld-linux.so.2 (0xf7efd000)
        librt.so.1 => /lib32/librt.so.1 (0xf7749000)
        libogg.so.0 => /usr/lib32/libogg.so.0 (0xf7743000)

I don't know if this is not ok /lib/ld-linux.so.2 looks odd but otherwise I guess it is ok? (that gate entry I don't know but somewhere I read that it is normal!?!)

The when I try to launch I get:
$ ./X-Plane-i586 
X-System Error:
Cannot open the keys file!

Instructions:keys:X-Plane.txt





Sorry.
Aborted (core dumped)


I'd really appreciate if someone can confirm my directory structure or give any further help to get over with this...

---

### Post by Saubazi on 2006-11-21
Never mind - found this:

[http://ubuntuforums.org/showthread.php?p=1750488](http://ubuntuforums.org/showthread.php?p=1750488)

Going along with that insaller - I'll report what happened when I am done...

---

### Post by Saubazi on 2006-11-22
Got the installer running and the program installed. 
Funnily it is complaining about missing OpenGL and 
the x-plane itself crashes while loading. 

I will join this discussion, for the matter:

[http://www.ubuntuforums.org/showthread.php?t=254812](http://www.ubuntuforums.org/showthread.php?t=254812)

---

