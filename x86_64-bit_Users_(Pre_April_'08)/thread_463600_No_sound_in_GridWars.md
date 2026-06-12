---
title: "No sound in GridWars"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-06-03
I downloaded the game from here [http://gridwars.marune.de/](http://gridwars.marune.de/) and it plays fine except that I do not have sound. I am using the 32 bit version because that is all that's available. I tried running the game from a terminal and got no errors. I was hoping to get some errors about the sound, so that I would know what is missing. I need help to get the sound working. Thanks.

---

### Post by Kilz on 2007-06-03
> **fakie_flip said:**
> I downloaded the game from here [http://gridwars.marune.de/](http://gridwars.marune.de/) and it plays fine except that I do not have sound. I am using the 32 bit version because that is all that's available. I tried running the game from a terminal and got no errors. I was hoping to get some errors about the sound, so that I would know what is missing. I need help to get the sound working. Thanks.

Do you have the ia32 libs installed?

---

### Post by fakie_flip on 2007-06-03
> **Kilz said:**
> Do you have the ia32 libs installed?

```
chris@ubuntu:~$ dpkg -l | grep ia32
ii  ia32-libs                                  1.5ubuntu9                             ia32 shared libraries for use on amd64 and i
ii  ia32-libs-gtk                              25                                     gtk+ ia32 shared libraries for with OpenOffi
ii  ia32-libs-kde                              12                                     KDE ia32 shared libraries for with OpenOffic
ii  ia32-libs-sdl                              1.0ubuntu3                             ia32 shared libraries of sdl related package
chris@ubuntu:~$ 
```

---

### Post by fakie_flip on 2007-06-03
The sound files for the game are wav, so they should be able to play without any special codec.

---

### Post by Cappy on 2007-06-03
Maybe 
```
sudo apt-get install lib32asound2 
```

Perhaps you could run ```
ldd /path/to/application
```
It will list out the 32-bit libraries the application uses.

Edit:
Here is the output
```

linux-gate.so.1 =>  (0xffffe000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7e70000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7ddc000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7d5b000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0xf7d56000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0xf7c9c000)
        libm.so.6 => /lib32/libm.so.6 (0xf7c75000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7c5e000)
        libc.so.6 => /lib32/libc.so.6 (0xf7b1d000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7b19000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7b14000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7b10000)
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf719e000)
        libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf719c000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf718d000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf70a3000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7097000)
        /lib/ld-linux.so.2 (0xf7f75000)

```

Sound works for me and man it is a freaking sweet game!

Have you tried
```

sudo apt-get install alsa-oss
aoss gridwars
``` ?

---

### Post by fakie_flip on 2007-06-03
> **Cappy said:**
> Maybe 
```
sudo apt-get install lib32asound2 
```

Perhaps you could run ```
ldd /path/to/application
```
It will list out the 32-bit libraries the application uses.

```
chris@ubuntu:~$ sudo apt-get install lib32asound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lib32asound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@ubuntu:~$ ldd /usr/local/games/gridwars_lin/gridwars 
        linux-gate.so.1 =>  (0xffffe000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7ebc000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7e30000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7daf000)
        libXxf86vm.so.1 => /usr/lib32/libXxf86vm.so.1 (0xf7daa000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0xf7cf0000)
        libm.so.6 => /lib32/libm.so.6 (0xf7cc9000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7cb2000)
        libc.so.6 => /lib32/libc.so.6 (0xf7b71000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7b6d000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7b68000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7b64000)
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf72de000)
        libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf72dc000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf72cd000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf71e3000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf71d7000)
        /lib/ld-linux.so.2 (0xf7fc1000)
chris@ubuntu:~$ 
```

---

### Post by fakie_flip on 2007-06-03
Nvm, I got sound working. Thanks.

---

