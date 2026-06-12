---
title: "IceS segment fault"
date: 2008-12-28
forum: x86 64-bit Users
---

### Post by Funnnny on 2008-12-28
I installed IceS for a shourcast server, complied it and tried to run. But there's a error message that say "invalid pointer".
Sometimes I get that problem when I compile a program under Ubuntu 64bit ( never got this when I used 32bit version)

here the error log
> *** glibc detected *** ices: free(): invalid pointer: 0x00007f45df510a60 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f45df21c938]
/lib/libc.so.6(cfree+0x76)[0x7f45df21ef86]
ices[0x409ace]
ices[0x4096ba]
ices[0x409789]
ices[0x409512]
ices[0x40457d]
ices[0x40361e]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f45df1c1466]
ices[0x403549]
======= Memory map: ========
00400000-0040e000 r-xp 00000000 08:07 482386                             /usr/local/bin/ices
0060d000-0060e000 r--p 0000d000 08:07 482386                             /usr/local/bin/ices
0060e000-0060f000 rw-p 0000e000 08:07 482386                             /usr/local/bin/ices
0060f000-006c5000 rw-p 0060f000 00:00 0 
020dc000-020fd000 rw-p 020dc000 00:00 0                                  [heap]
7f45d8000000-7f45d8021000 rw-p 7f45d8000000 00:00 0 
7f45d8021000-7f45dc000000 ---p 7f45d8021000 00:00 0 
7f45deb67000-7f45deb7d000 r-xp 00000000 08:07 3229581                    /lib/libgcc_s.so.1
7f45deb7d000-7f45ded7d000 ---p 00016000 08:07 3229581                    /lib/libgcc_s.so.1
7f45ded7d000-7f45ded7e000 r--p 00016000 08:07 3229581                    /lib/libgcc_s.so.1
7f45ded7e000-7f45ded7f000 rw-p 00017000 08:07 3229581                    /lib/libgcc_s.so.1
7f45ded7f000-7f45ded8a000 r-xp 00000000 08:07 3229605                    /lib/libnss_files-2.8.90.so
7f45ded8a000-7f45def89000 ---p 0000b000 08:07 3229605                    /lib/libnss_files-2.8.90.so
7f45def89000-7f45def8a000 r--p 0000a000 08:07 3229605                    /lib/libnss_files-2.8.90.so
7f45def8a000-7f45def8b000 rw-p 0000b000 08:07 3229605                    /lib/libnss_files-2.8.90.so
7f45def8b000-7f45defa2000 r-xp 00000000 08:07 2976259                    /usr/lib/libz.so.1.2.3.3
7f45defa2000-7f45df1a1000 ---p 00017000 08:07 2976259                    /usr/lib/libz.so.1.2.3.3
7f45df1a1000-7f45df1a3000 rw-p 00016000 08:07 2976259                    /usr/lib/libz.so.1.2.3.3
7f45df1a3000-7f45df30c000 r-xp 00000000 08:07 3229558                    /lib/libc-2.8.90.so
7f45df30c000-7f45df50b000 ---p 00169000 08:07 3229558                    /lib/libc-2.8.90.so
7f45df50b000-7f45df50f000 r--p 00168000 08:07 3229558                    /lib/libc-2.8.90.so
7f45df50f000-7f45df510000 rw-p 0016c000 08:07 3229558                    /lib/libc-2.8.90.so
7f45df510000-7f45df515000 rw-p 7f45df510000 00:00 0 
7f45df515000-7f45df599000 r-xp 00000000 08:07 3229592                    /lib/libm-2.8.90.so
7f45df599000-7f45df798000 ---p 00084000 08:07 3229592                    /lib/libm-2.8.90.so
7f45df798000-7f45df799000 r--p 00083000 08:07 3229592                    /lib/libm-2.8.90.so
7f45df799000-7f45df79a000 rw-p 00084000 08:07 3229592                    /lib/libm-2.8.90.so
7f45df79a000-7f45df79f000 r-xp 00000000 08:07 2960404                    /usr/lib/libogg.so.0.5.3
7f45df79f000-7f45df99e000 ---p 00005000 08:07 2960404                    /usr/lib/libogg.so.0.5.3
7f45df99e000-7f45df99f000 r--p 00004000 08:07 2960404                    /usr/lib/libogg.so.0.5.3
7f45df99f000-7f45df9a0000 rw-p 00005000 08:07 2960404                    /usr/lib/libogg.so.0.5.3
7f45df9a0000-7f45df9bf000 r-xp 00000000 08:07 2976207                    /usr/lib/libvorbis.so.0.4.0
7f45df9bf000-7f45dfbbe000 ---p 0001f000 08:07 2976207                    /usr/lib/libvorbis.so.0.4.0
7f45dfbbe000-7f45dfbbf000 r--p 0001e000 08:07 2976207                    /usr/lib/libvorbis.so.0.4.0
7f45dfbbf000-7f45dfbcd000 rw-p 0001f000 08:07 2976207                    /usr/lib/libvorbis.so.0.4.0
7f45dfbcd000-7f45dfbd4000 r-xp 00000000 08:07 2976211                    /usr/lib/libvorbisfile.so.3.2.0
7f45dfbd4000-7f45dfdd3000 ---p 00007000 08:07 2976211                    /usr/lib/libvorbisfile.so.3.2.0
7f45dfdd3000-7f45dfdd4000 r--p 00006000 08:07 2976211                    /usr/lib/libvorbisfile.so.3.2.0
7f45dfdd4000-7f45dfdd5000 rw-p 00007000 08:07 2976211                    /usr/lib/libvorbisfile.so.3.2.0
7f45dfdd5000-7f45dfe1b000 r-xp 00000000 08:07 2960602                    /usr/lib/libmp3lame.so.0.0.0
7f45dfe1b000-7f45e001b000 ---p 00046000 08:07 2960602                    /usr/lib/libmp3lame.so.0.0.0
7f45e001b000-7f45e001c000 r--p 00046000 08:07 2960602                    /usr/lib/libmp3lame.so.0.0.0
7f45e001c000-7f45e001d000 rw-p 00047000 08:07 2960602                    /usr/lib/libmp3lame.so.0.0.0
7f45e001d000-7f45e004e000 rw-p 7f45e001d000 00:00 0 
7f45e004e000-7f45e0050000 r-xp 00000000 08:07 3229662                    /lib/libutil-2.8.90.so
7f45e0050000-7f45e024f000 ---p 00002000 08:07 3229662                    /lib/libutil-2.8.90.so
7f45e024f000-7f45e0250000 r--p 00001000 08:07 3229662                    /lib/libutil-2.8.90.so
7f45e0250000-7f45e0251000 rw-p 00002000 08:07 3229662                    /lib/libutil-2.8.90.so
7f45e0251000-7f45e0253000 r-xp 00000000 08:07 3229573                    /lib/libdl-2.8.90.so
7f45e0253000-7f45e0453000 ---p 00002000 08:07 3229573                    /lib/libdl-2.8.90.so
7f45e0453000-7f45e0454000 r--p 00002000 08:07 3229573                    /lib/libdl-2.8.90.so
7f45e0454000-7f45e0455000 rw-p 00003000 08:07 3229573                    /lib/libdl-2.8.90.so
7f45e0455000-7f45e046c000 r-xp 00000000 08:07 3229635                    /lib/libpthread-2.8.90.so
7f45e046c000-7f45e066b000 ---p 00017000 08:07 3229635                    /lib/libpthread-2.8.90.so
7f45e066b000-7f45e066c000 r--p 00016000 08:07 3229635                    /lib/libpthread-2.8.90.so
7f45e066c000-7f45e066d000 rw-p 00017000 08:07 3229635                    /lib/libpthread-2.8.90.so
7f45e066d000-7f45e0671000 rw-p 7f45e066d000 00:00 0 
7f45e0671000-7f45e07ad000 r-xp 00000000 08:07 2976084                    /usr/lib/libpython2.5.so.1.0
7f45e07ad000-7f45e09ad000 ---p 0013c000 08:07 2976084                    /usr/lib/libpython2.5.so.1.0
7f45e09ad000-7f45e09ae000 r--p 0013c000 08:07 2976084                    /usr/lib/libpython2.5.so.1.0
7f45e09ae000-7f45e09e0000 rw-p 0013d000 08:07 2976084                    /usr/lib/libpython2.5.so.1.0
7f45e09e0000-7f45e09e8000 rw-p 7f45e09e0000 00:00 0 
7f45e09e8000-7f45e0b3b000 r-xp 00000000 08:07 2282742                    /usr/lib/libxml2.so.2.6.32
7f45e0b3b000-7f45e0d3a000 ---p 00153000 08:07 2282742                    /usr/lib/libxml2.so.2.6.32
7f45e0d3a000-7f45e0d42000 r--p 00152000 08:07 2282742                    /usr/lib/libxml2.so.2.6.32
7f45e0d42000-7f45e0d44000 rw-p 0015a000 08:07 2282742                    /usr/lib/libxml2.so.2.6.32
7f45e0d44000-7f45e0d45000 rw-p 7f45e0d44000 00:00 0 
7f45e0d45000-7f45e0d5d000 r-xp 00000000 08:07 2976150                    /usr/lib/libspeex.so.1.4.0
7f45e0d5d000-7f45e0f5d000 ---p 00018000 08:07 2976150                    /usr/lib/libspeex.so.1.4.0
7f45e0f5d000-7f45e0f5e000 r--p 00018000 08:07 2976150                    /usr/lib/libspeex.so.1.4.0
7f45e0f5e000-7f45e0f5f000 rw-p 00019000 08:07 2976150                    /usr/lib/libspeex.so.1.4.0
7f45e0f5f000-7f45e0fa5000 r-xp 00000000 08:07 2976175                    /usr/lib/libtheora.so.0.3.3
7f45e0fa5000-7f45e11a4000 ---p 00046000 08:07 2976175                    /usr/lib/libtheora.so.0.3.3
7f45e11a4000-7f45e11a6000 rw-p 00045000 08:07 2976175                    /usr/lib/libtheora.so.0.3.3
7f45e11a6000-7f45e11b5000 r-xp 00000000 08:07 2281533                    /usr/lib/libshout.so.3.2.0
7f45e11b5000-7f45e13b5000 ---p 0000f000 08:07 2281533                    /usr/lib/libshout.so.3.2.0
7f45e13b5000-7f45e13b6000 r--p 0000f000 08:07 2281533                    /usr/lib/libshout.so.3.2.0
7f45e13b6000-7f45e13b7000 rw-p 00010000 08:07 2281533                    /usr/lib/libshout.so.3.2.0
7f45e13b7000-7f45e13d6000 r-xp 00000000 08:07 3229538                    /lib/ld-2.8.90.so
7f45e15ae000-7f45e15b5000 rw-p 7f45e15ae000 00:00 0 
7f45e15cf000-7f45e15d5000 rw-p 7f45e15cf000 00:00 0 
7f45e15d5000-7f45e15d6000 r--p 0001e000 08:07 3229538                    /lib/ld-2.8.90.so
7f45e15d6000-7f45e15d7000 rw-p 0001f000 08:07 3229538                    /lib/ld-2.8.90.so
7fffe95c2000-7fffe95d7000 rw-p 7ffffffea000 00:00 0                      [stack]
7fffe95ff000-7fffe9600000 r-xp 7fffe95ff000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

btw, I'm using IceS 0.4, Ubuntu 8.10 64bit.
Any help ?

---

### Post by cariboo on 2008-12-28
Wouldn't it be a lot easier to install ices from the repositories?

```
sudo apt-get install ices
```

Jim

---

### Post by Funnnny on 2008-12-28
Tried to install IceS from repo but the problem still remain :(

---

### Post by cariboo on 2008-12-29
You will have to completely remove your self  compiled version and all it's configuration files as well as the version from the repositories. To remove the version from the repositories in a terminal type:

```
sudo apt-get purge ices
```

Then remove any left over configuration files, then install ices again.

Jim

---

### Post by Funnnny on 2008-12-29
I removed IceS, delete the old IceS configuration, executable file and symbolic link as well, reinstall IceS from repo again but the problem still there.
I searched through their forum, it seems Ices2 had that problem with some pointer and they already fixed it.

---

