---
title: "32 bit Legends game causes Segmentation fault (core dumped)"
date: 2007-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-06-04
Can anyone figure out why this game won't work? I have all the 32 bit libs it wants.

```
chris@ubuntu:/usr/local/games/legends$ ldd LinLegends
        linux-gate.so.1 =>  (0xffffe000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ed3000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7ecf000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7ddd000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7dcf000)
        librt.so.1 => /lib32/librt.so.1 (0xf7dc6000)
        libSDL-1.3.so.0 => ./libSDL-1.3.so.0 (0xf7d54000)
        libm.so.6 => /lib32/libm.so.6 (0xf7d2d000)
        libc.so.6 => /lib32/libc.so.6 (0xf7bec000)
        /lib/ld-linux.so.2 (0xf7efe000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7be8000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7be3000)
chris@ubuntu:/usr/local/games/legends$ ldd LinLegends | grep not
chris@ubuntu:/usr/local/games/legends$ runlegends 
chris@ubuntu:/usr/local/games/legends$ ./LinLegends 
Segmentation fault (core dumped)
chris@ubuntu:/usr/local/games/legends$
chris@ubuntu:/usr/local/games/legends$ linux32 runlegends
chris@ubuntu:/usr/local/games/legends$ linux32 ./LinLegends 
Segmentation fault (core dumped)
chris@ubuntu:/usr/local/games/legends$ 
 
```

---

### Post by pappapump on 2007-06-04
did you try the update yet?
It's a shell script.

---

### Post by fakie_flip on 2007-06-04
> **pappapump said:**
> did you try the update yet?
It's a shell script.

The game starts from the loki gui installer. After the game is finished installing, I have the choice to start the game from the installer gui, and it works, but any other way does not. Why is that? If I kept playing the game that way, I would have to reinstall it every time I wanted to play.

---

### Post by fakie_flip on 2007-06-04
> **pappapump said:**
> did you try the update yet?
It's a shell script.

Here is what I get from running the update script.

```
chris@ubuntu:/usr/local/games/legends$ sudo ./update 
Password:
rsync --progress --stats -zrvc rsync://update.legendsthegame.net/commonlegends .
receiving file list ... 
27 files to consider

Number of files: 27
Number of files transferred: 0
Total file size: 141930411 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 953
File list generation time: 0.567 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 83
Total bytes received: 993

sent 83 bytes  received 993 bytes  195.64 bytes/sec
total size is 141930411  speedup is 131905.59
rsync --progress --stats -zrvc rsync://update.legendsthegame.net/lin32legends .
receiving file list ... 
13 files to consider
runlegends
         180 100%  175.78kB/s    0:00:00 (xfer#1, to-check=1/13)

Number of files: 13
Number of files transferred: 1
Total file size: 15600767 bytes
Total transferred file size: 180 bytes
Literal data: 180 bytes
Matched data: 0 bytes
File list size: 487
File list generation time: 0.062 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 109
Total bytes received: 703

sent 109 bytes  received 703 bytes  324.80 bytes/sec
total size is 15600767  speedup is 19212.77

Update completed succesfully.
chris@ubuntu:/usr/local/games/legends$ runlegends
chris@ubuntu:/usr/local/games/legends$ linux32 ./runlegends 
chris@ubuntu:/usr/local/games/legends$ ./LinLegends 
./LinLegends: error while loading shared libraries: libSDL-1.3.so.0: cannot open shared object file: No such file or directory
chris@ubuntu:/usr/local/games/legends$ echo $LD_LIBRARY_PATH 
/home/chris/.32bitLibs
chris@ubuntu:/usr/local/games/legends$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:./
chris@ubuntu:/usr/local/games/legends$ ./LinLegends Segmentation fault (core dumped)
chris@ubuntu:/usr/local/games/legends$ linux32 ./LinLegends 
Segmentation fault (core dumped)
chris@ubuntu:/usr/local/games/legends$ 
```

---

### Post by fakie_flip on 2007-06-04
I have all of these libs that it says it needs, so why does it say I need them?

```
chris@ubuntu:/usr/local/games/legends$ objdump -x LinLegends | grep NEEDED
  NEEDED      libpthread.so.0
  NEEDED      libdl.so.2
  NEEDED      libX11.so.6
  NEEDED      libXext.so.6
  NEEDED      librt.so.1
  NEEDED      libSDL-1.3.so.0
  NEEDED      libm.so.6
  NEEDED      libc.so.6
chris@ubuntu:/usr/local/games/legends$ locate libpthread.so.0
/lib32/libpthread.so.0
/lib/libpthread.so.0
chris@ubuntu:/usr/local/games/legends$ locate libdl.so.2
/lib32/libdl.so.2
/lib/libdl.so.2
chris@ubuntu:/usr/local/games/legends$ locate libX11.so.6
/usr/lib32/libX11.so.6.2.0
/usr/lib32/libX11.so.6
/usr/lib/libX11.so.6.2.0
/usr/lib/libX11.so.6
chris@ubuntu:/usr/local/games/legends$ locate libXext.so.6
/usr/lib32/libXext.so.6.4.0
/usr/lib32/libXext.so.6
/usr/lib/libXext.so.6.4.0
/usr/lib/libXext.so.6
chris@ubuntu:/usr/local/games/legends$
```

---

### Post by Cappy on 2007-06-04
I was playing around with this "objdump -x" command.
```

$ objdump -x gridwars | grep NEEDED
  NEEDED      libX11.so.6
  NEEDED      libGL.so.1
  NEEDED      libGLU.so.1
  NEEDED      libXxf86vm.so.1
  NEEDED      libstdc++.so.5
  NEEDED      libm.so.6
  NEEDED      libpthread.so.0
  NEEDED      libc.so.6

$ objdump -x ut2004-bin-linux-amd64 | grep NEEDED
  NEEDED      libdl.so.2
  NEEDED      libpthread.so.0
  NEEDED      ./libSDL-1.2.so.0
  NEEDED      libstdc++.so.5
  NEEDED      libm.so.6
  NEEDED      libgcc_s.so.1
  NEEDED      libc.so.6

$ objdump -x ut2004-bin | grep NEEDED  
  NEEDED      libdl.so.2
  NEEDED      libpthread.so.0
  NEEDED      ./libSDL-1.2.so.0
  NEEDED      libstdc++.so.5
  NEEDED      libm.so.6
  NEEDED      libgcc_s.so.1
  NEEDED      libc.so.6

```

These play just fine when I run them.
Maybe these are just libraries that are REQUIRED, not necessarily missing.

---

### Post by fakie_flip on 2007-06-04
> **Cappy said:**
> I was playing around with this "objdump -x" command.
```

$ objdump -x gridwars | grep NEEDED
  NEEDED      libX11.so.6
  NEEDED      libGL.so.1
  NEEDED      libGLU.so.1
  NEEDED      libXxf86vm.so.1
  NEEDED      libstdc++.so.5
  NEEDED      libm.so.6
  NEEDED      libpthread.so.0
  NEEDED      libc.so.6

$ objdump -x ut2004-bin-linux-amd64 | grep NEEDED
  NEEDED      libdl.so.2
  NEEDED      libpthread.so.0
  NEEDED      ./libSDL-1.2.so.0
  NEEDED      libstdc++.so.5
  NEEDED      libm.so.6
  NEEDED      libgcc_s.so.1
  NEEDED      libc.so.6

$ objdump -x ut2004-bin | grep NEEDED  
  NEEDED      libdl.so.2
  NEEDED      libpthread.so.0
  NEEDED      ./libSDL-1.2.so.0
  NEEDED      libstdc++.so.5
  NEEDED      libm.so.6
  NEEDED      libgcc_s.so.1
  NEEDED      libc.so.6

```

These play just fine when I run them.
Maybe these are just libraries that are REQUIRED, not necessarily missing.

I know I have all the 32 bit libs, or else the game wouldn't have started from the gui loki installer, so why is it not working when I try to run it any other way? What can I do to find out?

---

### Post by fakie_flip on 2007-06-04
Problem solved. I figured it out. The game would only run as the root user. The configuration files in my directory were owned by the root user, so my user did not have permissions to them. Here is what I did to correct the problem, and now the games works.

```
chris@ubuntu:~$ chown -Rc chris:chris .legends/
chown: `.legends/': Permission denied
chris@ubuntu:~$ sudo chown -Rc chris:chris .legends/
changed ownership of `.legends/legends/prefs/prefs.cs' to chris:chris
changed ownership of `.legends/legends/prefs/keyConfig.cs' to chris:chris
changed ownership of `.legends/legends/prefs' to chris:chris
changed ownership of `.legends/legends/scripts/server' to chris:chris
changed ownership of `.legends/legends/scripts/client/admin' to chris:chris
changed ownership of `.legends/legends/scripts/client/ui' to chris:chris
changed ownership of `.legends/legends/scripts/client' to chris:chris
changed ownership of `.legends/legends/scripts' to chris:chris
changed ownership of `.legends/legends/data/terrains' to chris:chris
changed ownership of `.legends/legends/data/textures/guiProfiles/bluePigment' to chris:chris
changed ownership of `.legends/legends/data/textures/guiProfiles' to chris:chris
changed ownership of `.legends/legends/data/textures' to chris:chris
changed ownership of `.legends/legends/data' to chris:chris
changed ownership of `.legends/legends' to chris:chris
changed ownership of `.legends/common/cache/Arial Bold_15.gft' to chris:chris
changed ownership of `.legends/common/cache/Arial_12.gft' to chris:chris
changed ownership of `.legends/common/cache/Lucidia Console_14.gft' to chris:chris
changed ownership of `.legends/common/cache/Arial_16.gft' to chris:chris
changed ownership of `.legends/common/cache/Arial Bold_14.gft' to chris:chris
changed ownership of `.legends/common/cache/Arial_14.gft' to chris:chris
changed ownership of `.legends/common/cache/Arial_13.gft' to chris:chris
changed ownership of `.legends/common/cache/Arial Bold_12.gft' to chris:chris
changed ownership of `.legends/common/cache' to chris:chris
changed ownership of `.legends/common/server' to chris:chris
changed ownership of `.legends/common/edit/particleEditor' to chris:chris
changed ownership of `.legends/common/edit/mapEditor' to chris:chris
changed ownership of `.legends/common/edit/guiEditor' to chris:chris
changed ownership of `.legends/common/edit' to chris:chris
changed ownership of `.legends/common/client/shell' to chris:chris
changed ownership of `.legends/common/client' to chris:chris
changed ownership of `.legends/common' to chris:chris
changed ownership of `.legends/console.log' to chris:chris
changed ownership of `.legends/' to chris:chris
chris@ubuntu:~$ runlegends 
chris@ubuntu:~$ grab_native: (path /dev/dsp fd 14)
set_fd in: bufsiz 4096 fmt 0x10 speed 44100 channels 2
set_fd out: bufsiz 1024 fmt 0x10 speed 44100 channels 2
```

---

