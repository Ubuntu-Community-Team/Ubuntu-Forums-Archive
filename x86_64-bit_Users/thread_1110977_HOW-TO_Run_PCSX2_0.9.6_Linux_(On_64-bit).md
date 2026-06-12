---
title: "HOW-TO: Run PCSX2 0.9.6 Linux (On 64-bit)"
date: 2009-03-30
forum: x86 64-bit Users
---

### Post by falkTX on 2009-03-30
The PCSX2 Team just released a new version of PCSX2, but it runs only on 32bit.
I decided to look for a solution. First I tried to compile the SVN version, with no sucess (although I was able to compile all plugins).
So maybe using some 32bit libs it could work. And it did!
I created a deb package for this, so now you just have to install it and play.

EDIT:
Here it is:
[http://www.mediafire.com/download.php?zzyjzf15yjd](http://www.mediafire.com/download.php?zzyjzf15yjd)

---

### Post by skymera on 2009-03-30
Slightly related.

How well does this PCSX2 work?
I've never got it to run a PS2 game using Ubuntu or Windows :(

---

### Post by falkTX on 2009-03-30
On my hardware (nv7400, 1800hz-dualcore), extremly slow...
My friend has a nvidia9600 and it runs "normal" (which means great).

---

### Post by falkTX on 2009-03-30
I forgot to tell, I was playing Tekken5 yesterday.. in his laptop!

---

### Post by falkTX on 2009-03-30
The same link as 1st post:
[http://www.mediafire.com/download.php?zzyjzf15yjd](http://www.mediafire.com/download.php?zzyjzf15yjd)

Download, install and run PCSX2

---

### Post by chris062689 on 2009-04-14
I wish someone would step up and start building deb's for all of the popular emulators.  It's a sad state of affairs.
I would, but I have no idea how to.  :mad:

w00t 500 posts!

---

### Post by falkTX on 2009-04-15
> **chris062689 said:**
> I wish someone would step up and start building deb's for all of the popular emulators.  It's a sad state of affairs.
I would, but I have no idea how to.  :mad:

w00t 500 posts!

I would do it if I had net access at home.
My plan is to create an Ubuntu repo trough FTP, contains some large games, emulators, x64 hack stuff, and 'games-ready-for-wine-in-deb'.

But that may take a ot of time...

---

### Post by gametime25 on 2009-07-05
> **chris062689 said:**
> I wish someone would step up and start building deb's for all of the popular emulators.  It's a sad state of affairs.
I would, but I have no idea how to.  :mad:

w00t 500 posts!

I know what you mean.

---

### Post by s0la on 2009-07-19
Hi.. First, thnx for sharing with us your .deb package, I installed it on my Ubuntu Jaunty(9.04) x86(64), but I don't know how to run it.. I tried from the shell, but it can't run it.. Any help..

---

### Post by falkTX on 2009-07-20
> **s0la said:**
> Hi.. First, thnx for sharing with us your .deb package, I installed it on my Ubuntu Jaunty(9.04) x86(64), but I don't know how to run it.. I tried from the shell, but it can't run it.. Any help..

The deb file just install the needed dependencies for PCSX2 0.9.6.
You have to install the package, then run the PCSX2.

---

### Post by szenith on 2009-08-18
Could someone make a 32 bit version of this, and make a thread? Also, it would help if someone could tell me exactly what dependencies I should install (for pcsx2 on 32 bit) because the list on the site is a bit outdated/inexact.

---

### Post by szenith on 2009-08-18
oops didn't notice this was posted directly in the 64 bit forum... so scratch that maybe ,I just found this thread by googling. hehe. I'll make a thread about it somewhere else.

---

### Post by int2ag0n on 2009-09-07
Thanks dude , you helped me a lot . the application starts and finds the ZeroGS plugin.

 However , i was hoping that after using your deb i could compile pcsx2 from source but no luck.

Thanks

---

### Post by falkTX on 2009-09-07
> **int2ag0n said:**
> Thanks dude , you helped me a lot . the application starts and finds the ZeroGS plugin.

 However , i was hoping that after using your deb i could compile pcsx2 from source but no luck.

Thanks

I've compile it recently (about 1 week ago) - [http://falktx.xtreemhost.com/outro/pcsx2-bin-trunk.7z]("http://falktx.xtreemhost.com/outro/pcsx2-bin-trunk.7z")

But it doesn't run on my PC, due to Intel driver missing FBO support... :(

---

### Post by int2ag0n on 2009-09-09
> **falkTX said:**
> I've compile it recently (about 1 week ago) - [http://falktx.xtreemhost.com/outro/pcsx2-bin-trunk.7z]("http://falktx.xtreemhost.com/outro/pcsx2-bin-trunk.7z")

But it doesn't run on my PC, due to Intel driver missing FBO support... :(

Before i installed your deb , the compilation had been complaining that ld couldn't find compatible library -lCg (libCg.so) . After i installed your deb (current situation) , the compilation fails to complete because it cannot find a compatible -lSDL (libSDL.so).

```
 /usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libSDL.so when searching for -lSDL
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libSDL.a when searching for -lSDL
/usr/bin/ld: skipping incompatible /usr/lib/libSDL.so when searching for -lSDL
/usr/bin/ld: skipping incompatible /usr/lib/libSDL.a when searching for -lSDL
/usr/bin/ld: cannot find -lSDL
collect2: &#951; ld &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#949;&#958;&#972;&#948;&#959;&#965; 1(greek <-> english: ld return 1)
make: *** [libZeroPAD.so.0.3.0] Error 1
Error with building plugins

```

all this happens when i run the command :$ sh build.sh all

when i run the ruby installer :$ ./build.sh all
it says something else :

```

---------------
Building Zzogl
---------------
./build.rb:114:in `chdir': No such file or directory - /home/internat/briefcase/programs/pcsx2-read-only/plugins/zzogl/opengl (Errno::ENOENT)
	from ./build.rb:114:in `build'
	from ./build.rb:167
	from ./build.rb:166:in `each'
	from ./build.rb:166

```

Unless i dont understand it right , this means that a directory is missing from the source tree. I downloaded the tar file twice just in case ... but the same problem exists.

As i mentioned before after using your deb the application started with no problems , however i did not managed to play any game , i tried gran turismo 3 (the image & the sound is crap , and when it finishes the loading just before a race , the game freezes) the rating of gt3 is in-game , and i also tried terminator 3 redemtion (flawless sound and image -that's good i thought at first , but the game freezes after loading just before entering the mission) the rating of t3 is also in-game.

I think that this are platform specific problems , because the same games are reported to playable in numerous forums in winblows. Maybe i'll give a shot it to winblows Vista in my brothers laptop with the same games.

---

### Post by falkTX on 2009-09-09
-lSDL is not compatible in 64bit.

Or you get a full 32bit chroot environment, or a 32bit OS.

My choise was installing Ubuntu Jaunty 32bit on VirtualBox. It compiled fine there

---

### Post by cest on 2009-10-20
Hello! 
    
      I have installed your .deb package and I succeded to compile the source code obtained through subversion without error. But when I start the program I get the following:
 
```
stefano@desk:~/.instal/pcsx2/bin$ ./pcsx2

*** buffer overflow detected ***: ./pcsx2 terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f9d15a552c7]
/lib/libc.so.6[0x7f9d15a53170]
plugins/libSPU2null.so(_Z8InitADSRv+0x1c)[0x7f9d02c7be5c]
plugins/libSPU2null.so(SPU2init+0xc8)[0x7f9d02c7e058]
./pcsx2[0x4506d3]
./pcsx2[0x4555b5]
./pcsx2[0x41c919]
./pcsx2[0x41ceed]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f9d159745a6]
./pcsx2[0x4068b9]
======= Memory map: ========
00400000-0061b000 r-xp 00000000 08:12 174950                             /home/stefano/.instal/pcsx2/bin/pcsx2
0081a000-0081b000 r-xp 0021a000 08:12 174950                             /home/stefano/.instal/pcsx2/bin/pcsx2
0081b000-00844000 rwxp 0021b000 08:12 174950                             /home/stefano/.instal/pcsx2/bin/pcsx2
00844000-0091c000 rwxp 00844000 00:00 0 
00bfb000-00d37000 rwxp 00bfb000 00:00 0                                  [heap]
0c000000-0c800000 rwxp 0c000000 00:00 0 
0d000000-0e000000 rwxp 0d000000 00:00 0 
0f000000-0f800000 rwxp 0f000000 00:00 0 
31000000-31200000 rwxp 31000000 00:00 0 
32000000-32010000 rwxp 32000000 00:00 0 
34000000-34010000 rwxp 34000000 00:00 0 
34800000-34810000 rwxp 34800000 00:00 0 
40c6e000-40c70000 rwxp 00000000 00:0f 733                                /dev/zero
7f9d0204f000-7f9d02250000 rwxp 7f9d0204f000 00:00 0 
7f9d02250000-7f9d02252000 r-xp 00000000 08:12 196930                     /home/stefano/.instal/pcsx2/bin/plugins/libFWnull.so
7f9d02252000-7f9d02451000 ---p 00002000 08:12 196930                     /home/stefano/.instal/pcsx2/bin/plugins/libFWnull.so
7f9d02451000-7f9d02452000 r-xp 00001000 08:12 196930                     /home/stefano/.instal/pcsx2/bin/plugins/libFWnull.so
7f9d02452000-7f9d02453000 rwxp 00002000 08:12 196930                     /home/stefano/.instal/pcsx2/bin/plugins/libFWnull.so
7f9d02453000-7f9d02455000 r-xp 00000000 08:12 197868                     /home/stefano/.instal/pcsx2/bin/plugins/libUSBnull.so
7f9d02455000-7f9d02654000 ---p 00002000 08:12 197868                     /home/stefano/.instal/pcsx2/bin/plugins/libUSBnull.so
7f9d02654000-7f9d02655000 r-xp 00001000 08:12 197868                     /home/stefano/.instal/pcsx2/bin/plugins/libUSBnull.so
7f9d02655000-7f9d02656000 rwxp 00002000 08:12 197868                     /home/stefano/.instal/pcsx2/bin/plugins/libUSBnull.so
7f9d02656000-7f9d02658000 r-xp 00000000 08:12 196901                     /home/stefano/.instal/pcsx2/bin/plugins/libDEV9null.so
7f9d02658000-7f9d02857000 ---p 00002000 08:12 196901                     /home/stefano/.instal/pcsx2/bin/plugins/libDEV9null.so
7f9d02857000-7f9d02858000 r-xp 00001000 08:12 196901                     /home/stefano/.instal/pcsx2/bin/plugins/libDEV9null.so
7f9d02858000-7f9d02859000 rwxp 00002000 08:12 196901                     /home/stefano/.instal/pcsx2/bin/plugins/libDEV9null.so
7f9d02859000-7f9d02868000 r-xp 00000000 08:12 269894                     /lib/libbz2.so.1.0.4
7f9d02868000-7f9d02a68000 ---p 0000f000 08:12 269894                     /lib/libbz2.so.1.0.4
7f9d02a68000-7f9d02a69000 r-xp 0000f000 08:12 269894                     /lib/libbz2.so.1.0.4
7f9d02a69000-7f9d02a6a000 rwxp 00010000 08:12 269894                     /lib/libbz2.so.1.0.4
7f9d02a6a000-7f9d02a72000 r-xp 00000000 08:12 196814                     /home/stefano/.instal/pcsx2/bin/plugins/libCDVDiso.so
7f9d02a72000-7f9d02c71000 ---p 00008000 08:12 196814                     /home/stefano/.instal/pcsx2/bin/plugins/libCDVDiso.so
7f9d02c71000-7f9d02c72000 r-xp 00007000 08:12 196814                     /home/stefano/.instal/pcsx2/bin/plugins/libCDVDiso.so
7f9d02c72000-7f9d02c73000 rwxp 00008000 08:12 196814                     /home/stefano/.instal/pcsx2/bin/plugins/libCDVDiso.so
7f9d02c73000-7f9d02c79000 rwxp 7f9d02c73000 00:00 0 
7f9d02c79000-7f9d02c7f000 r-xp 00000000 08:12 197866                     /home/stefano/.instal/pcsx2/bin/plugins/libSPU2null.so
7f9d02c7f000-7f9d02e7e000 ---p 00006000 08:12 197866                     /home/stefano/.instal/pcsx2/bin/plugins/libSPU2null.so
7f9d02e7e000-7f9d02e7f000 r-xp 00005000 08:12 197866                     /home/stefano/.instal/pcsx2/bin/plugins/libSPU2null.so
7f9d02e7f000-7f9d02e80000 rwxp 00006000 08:12 197866                     /home/stefano/.instal/pcsx2/bin/plugins/libSPU2null.so
7f9d02e80000-7f9d02e81000 rwxp 7f9d02e80000 00:00 0 
7f9d02e81000-7f9d02f5a000 r-xp 00000000 08:12 288094                     /usr/lib/libasound.so.2.0.0
7f9d02f5a000-7f9d0315a000 ---p 000d9000 08:12 288094                     /usr/lib/libasound.so.2.0.0
7f9d0315a000-7f9d0315d000 r-xp 000d9000 08:12 288094                     /usr/lib/libasound.so.2.0.0
7f9d0315d000-7f9d03161000 rwxp 000dc000 08:12 288094                     /usr/lib/libasound.so.2.0.0
7f9d03161000-7f9d031ca000 r-xp 00000000 08:12 288873                     /usr/lib/libSDL-1.2.so.0.11.2
7f9d031ca000-7f9d033ca000 ---p 00069000 08:12 288873                     /usr/lib/libSDL-1.2.so.0.11.2
7f9d033ca000-7f9d033cb000 r-xp 00069000 08:12 288873                     /usr/lib/libSDL-1.2.so.0.11.2
7f9d033cb000-7f9d033cd000 rwxp 0006a000 08:12 288873                     /usr/lib/libSDL-1.2.so.0.11.2
7f9d033cd000-7f9d033f9000 rwxp 7f9d033cd000 00:00 0 
7f9d033f9000-7f9d03407000 r-xp 00000000 08:12 197106                     /home/stefano/.instal/pcsx2/bin/plugins/libZeroPAD.so.0.2.0
7f9d03407000-7f9d03606000 ---p 0000e000 08:12 197106                     /home/stefano/.instal/pcsx2/bin/plugins/libZeroPAD.so.0.2.0
7f9d03606000-7f9d03607000 r-xp 0000d000 08:12 197106                     /home/stefano/.instal/pcsx2/bin/plugins/libZeroPAD.so.0.2.0
7f9d03607000-7f9d03608000 rwxp 0000e000 08:12 197106                     /home/stefano/.instal/pcsx2/bin/plugins/libZeroPAD.so.0.2.0
7f9d03608000-7f9d03a19000 rwxp 7f9d03608000 00:00 0 
7f9d03a19000-7f9d03a1c000 r-xp 00000000 08:12 269882                     /lib/libuuid.so.1.2
7f9d03a1c000-7f9d03c1c000 ---p 00003000 08:12 269882                     /lib/libuuid.so.1.2
7f9d03c1c000-7f9d03c1d000 r-xp 00003000 08:12 269882                     /lib/libuuid.so.1.2
7f9d03c1d000-7f9d03c1e000 rwxp 00004000 08:12 269882                     /lib/libuuid.so.1.2
7f9d03c1e000-7f9d03c35000 r-xp 00000000 08:12 288871                     /usr/lib/libICE.so.6.3.0
7f9d03c35000-7f9d03e34000 ---p 00017000 08:12 288871                     /usr/lib/libICE.so.6.3.0
7f9d03e34000-7f9d03e36000 rwxp 00016000 08:12 288871                     /usr/lib/libICE.so.6.3.0
7f9d03e36000-7f9d03e39000 rwxp 7f9d03e36000 00:00 0 
7f9d03e39000-7f9d03e41000 r-xp 00000000 08:12 286261                     /usr/lib/libSM.so.6.0.0
7f9d03e41000-7f9d04040000 ---p 00008000 08:12 286261                     /usr/lib/libSM.so.6.0.0
7f9d04040000-7f9d04041000 r-xp 00007000 08:12 286261                     /usr/lib/libSM.so.6.0.0
7f9d04041000-7f9d04042000 rwxp 00008000 08:12 286261                     /usr/lib/libSM.so.6.0.0
7f9d04042000-7f9d040a1000 r-xp 00000000 08:12 287163                     /usr/lib/libXt.so.6.0.0
7f9d040a1000-7f9d042a1000 ---p 0005f000 08:12 287163                     /usr/lib/libXt.so.6.0.0
7f9d042a1000-7f9d042a2000 r-xp 0005f000 08:12 287163                     /usr/lib/libXt.so.6.0.0
7f9d042a2000-7f9d042a7000 rwxp 00060000 08:12 287163                     /usr/lib/libXt.so.6.0.0
7f9d042a7000-7f9d042a8000 rwxp 7f9d042a7000 00:00 0 
7f9d042a8000-7f9d042c0000 r-xp 00000000 08:12 288939                     /usr/lib/libXmu.so.6.2.0
7f9d042c0000-7f9d044bf000 ---p 00018000 08:12 288939                     /usr/lib/libXmu.so.6.2.0
7f9d044bf000-7f9d044c1000 rwxp 00017000 08:12 288939                     /usr/lib/libXmu.so.6.2.0
7f9d044c1000-7f9d044c2000 r-xp 00000000 08:12 1136659                    /usr/lib/tls/libnvidia-tls.so.180.44
7f9d044c2000-7f9d045c2000 ---p 00001000 08:12 1136659                    /usr/lib/tls/libnvidia-tls.so.180.44
7f9d045c2000-7f9d045c3000 rwxp 00001000 08:12 1136659                    /usr/lib/tls/libnvidia-tls.so.180.44
7f9d045c3000-7f9d05365000 r-xp 00000000 08:12 289425                     /usr/lib/libGLcore.so.180.44
7f9d05365000-7f9d05464000 ---p 00da2000 08:12 289425                     /usr/lib/libGLcore.so.180.44
7f9d05464000-7f9d0589b000 rwxp 00da1000 08:12 289425                     /usr/lib/libGLcore.so.180.44
7f9d0589b000-7f9d058ad000 rwxp 7f9d0589b000 00:00 0 
7f9d058ad000-7f9d05904000 r-xp 00000000 08:12 289419                     /usr/lib/libCgGL.so
7f9d05904000-7f9d05a04000 ---p 00057000 08:12 289419                     /usr/lib/libCgGL.so
7f9d05a04000-7f9d05a09000 rwxp 00057000 08:12 289419                     /uAborted
```

Could you give me some help?

---

### Post by falkTX on 2009-10-21
Use their's pre-compiled binary.

They provide, for Linux, 0.9.6 ([http://pcsx2.net/files/18428](http://pcsx2.net/files/18428)) and 0.9.7 beta ([http://pcsx2.net/files/21118](http://pcsx2.net/files/21118))

---

### Post by Found on 2009-10-31
Error: Wrong architecture 'amd64'
:(

---

### Post by falkTX on 2009-10-31
> **Found said:**
> Error: Wrong architecture 'amd64'
:(

> HOW-TO: Run PCSX2 0.9.6 Linux (On 64-bit)Are you even running 64bit?

---

### Post by Yellow Pasque on 2009-11-01
> **falkTX said:**
> -lSDL is not compatible in 64bit. Or you get a full 32bit chroot environment, or a 32bit OS.

..or you use getlibs to install 32-bit version of libSDL (and whatever else you need): [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

