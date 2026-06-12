---
title: "X-Plane help"
date: 2006-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by arjunsharma on 2006-02-23
So I installed X-Plane 8.00 on my computer. a) with an AMD 64 3600 which should I run? :
> 
X-Plane-800-athlon-xp
X-Plane-800-athlon-xp-dev
X-Plane-800-i586
X-Plane-800-i586-dev
X-Plane-800-i686
X-Plane-800-i686-dev


b) when I try to run any of them, I get this error:
./X-Plane-800-*whichever*: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

then I did ldd `which ./X-Plane-800-*whichever*` and got:> 
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x5557b000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0x5561a000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x55690000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x5569d000)
        libopenal.so.0 => not found
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x5575d000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5576e000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x55772000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x55794000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0x558c2000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x559a6000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x559b1000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x559b4000)
        /lib/ld-linux.so.2 (0x55555000)

 
then I did "locate libopenal" and got:
> 
/var/lib/dpkg/info/libopenal0.shlibs
/var/lib/dpkg/info/libopenal0.list
/var/lib/dpkg/info/libopenal0.postinst
/var/lib/dpkg/info/libopenal0.postrm
/var/lib/dpkg/info/libopenal0.md5sums
/var/lib/dpkg/info/libopenal-dev.postinst
/var/lib/dpkg/info/libopenal-dev.list
/var/lib/dpkg/info/libopenal-dev.prerm
/var/lib/dpkg/info/libopenal-dev.md5sums
/var/cache/apt/archives/libopenal0_0.2004090900-1.1build1_amd64.deb
/var/cache/apt/archives/libopenal-dev_0.2004090900-1.1build1_amd64.deb
/var/cache/apt/archives/libopenalpp-cvsc2_20041206-2ubuntu2_amd64.deb
/var/cache/apt/archives/libopenalpp-cvs-dev_20041206-2ubuntu2_amd64.deb
/usr/share/doc/libopenal0
/usr/share/doc/libopenal0/changelog.gz
/usr/share/doc/libopenal0/copyright
/usr/share/doc/libopenal0/changelog.Debian.gz
/usr/share/doc/libopenal-dev
/usr/share/doc/libopenal-dev/PLATFORM
/usr/share/doc/libopenal-dev/CREDITS
/usr/share/doc/libopenal-dev/TODO
/usr/share/doc/libopenal-dev/README.Debian
/usr/share/doc/libopenal-dev/NOTES
/usr/share/doc/libopenal-dev/changelog.gz
/usr/share/doc/libopenal-dev/copyright
/usr/share/doc/libopenal-dev/changelog.Debian.gz
/usr/lib/libopenal.so.0.0.7
/usr/lib/libopenal.so.0
/usr/lib/libopenal.a
/usr/lib/libopenal.so


I copied the last four to the /usr/lib32 folder, but even when I do locate again it doesn't see them... although when I do "ls /usr/lib32" it shows them...

any help? I went to Synaptic, and it says the libopenal is installed... I really want to get X-Plane installed, help is MUCH appreciated!

Thanks,
Arjun

---

### Post by procras on 2006-02-23
> I copied the last four to the /usr/lib32 folder, but even when I do locate again it doesn't see them... although when I do "ls /usr/lib32" it shows them...

You need to run updatedb to refresh the locate database after you make new files or move things around

$ sudo updatedb
$ locate file_you_are_interested_in

Cant help with your main problem though! Has anyone got this running in the 32 bit distro, if they have you could try that :(

---

### Post by cash4elvis on 2006-03-13
Did you get it to work?  I'm trying to install the x-plane linux installer 1.0.7 and it give me the same error... libopenal.so.0 cannot share: no file or directory. 

I have copied it to every lib I can find and still it won't find it.  I'v run updatedb also.

AMD sempron 64bit
nVidia 6600 OC

-Stan

---

### Post by ssmaxss on 2006-09-14
Download 32-bit libopenal0 deb, extract it and use libopenal.so.0 from there (place it in /usr/lib32)

---

