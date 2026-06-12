---
title: "ati fglrx problems"
date: 2005-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by frenzy909 on 2005-12-15
Hi,

I hope somebody can help me out here. I got a Radeon 9600XT under ubuntu 5.10. And can't get the 3D accelleration to work.
I first tried using the fglrx package available through synaptic, but that didn't work. Although I did adapt my xorg.conf. (both manually as indicated in the ubuntu help and with fglrxconfig. and i also tried manual combinations)
It seemed that the libGL remained the mesa lib? or at least fglrxinfo kept returning mesa in combination with opengl?

Therefore I downloaded the latest driver installer from the ati site (ati-driver-installer-8.20.8-x86_64.run) and tried to install that. The installation seemed to go alright, but the log file says:

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.

Still, the kernel module doesn't seem to be the problem: Now I got library problems... On investigation I found that /etc/ld.so.conf only listed the 32 bit libraries? So I added the regular (read 64bit) libraries. Now it reads:
root@frenzy:/etc# cat /etc/ld.so.conf
/lib32
/usr/lib32
/usr/X11R6/lib32
/lib
/usr/lib
/usr/X11R6/lib

Still I have the library problems:
 fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

To make it even stranger, it doesn't find it for fglrxinfo, but does find it for fireglcontrolpanel:

root@frenzy:/etc#  ldd `which fglrxinfo`
        libGL.so.1 => not found
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaaabc2000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002aaaaad9c000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaaaead000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaab0e5000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaab1e8000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaab2eb000)
        /lib64/ld-linux-x86-64.so.2 (0x00002aaaaaaab000)
root@frenzy:/etc# ldd /usr/X11R6/bin/fireglcontrolpanel
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0x5557b000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0x5561a000)
        ....
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x556ae000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x5576e000)
        libexpat.so.0 => not found
        ....

As you can see, for fireglcontrolpanel it won't find some other library. 
(which of course also is present:
/usr/X11R6/lib$ locate libexpat.so.0
/usr/lib/libexpat.so.0
/usr/lib32/libexpat.so.0 )

Well, I hope someone can make sense of this, as I am completely lost at this point. Thanks!

gr. Frans

---

### Post by OOpabloOO on 2005-12-16
Hi
Look at here:

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

It solved my issues.

fireglcontrolpanel is a 32bit application and needs libexpat compiled for i386. It is not in the breezy/AMD64 rep, you should install it manually from i386 package and then using  a script like this:

#!/bin/sh
  LD_LIBRARY_PATH=/usr/lib32/
  export LD_LIBRARY_PATH
  exec /usr/bin/fireglcontrolpanel


see ya

---

