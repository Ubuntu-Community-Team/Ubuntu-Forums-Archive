---
title: "Unable to install Postal 2 demo in amd64 Feisty"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-06-06
I can't get the game to install. Here is what happens. I tried installing it many different ways, and after each time, I still didn't have the game installed. My games menu in Gnome doesn't show the game. I can't find it installed anywhere, and I can't find any commands to start the game. Any ideas? I tried getting the 32 bit gtklibs-1.2 and its dependencies.

```
chris@ubuntu:~/Desktop$ ./postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop$ sudo ./postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop$ sh postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop$
```

```
chris@ubuntu:~/Desktop/POSTAL$ LD_LIBRARY_PATH=/home/chris/.32bitLibs ./postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop/POSTAL$ ls ~/.32bitLibs
et-sdl-sound.so           libgthread-1.2.so.0.0.10  libphysfs-1.0.so.0.0.0
ld-2.5.so                 libgtk-1.2.so.0           libSDL-1.3.so.0
ld-linux.so.2             libgtk-1.2.so.0.9.1       libSDL_image-1.2.so.0
libgdk-1.2.so.0           libmad.so.0               libSDL_image-1.2.so.0.1.4
libgdk-1.2.so.0.9.1       libmad.so.0.2.1           libsmpeg-0.4.so.0
libglib-1.2.so.0          libogg.so.0               libsmpeg-0.4.so.0.1.4
libglib-1.2.so.0.0.10     libogg.so.0.5.3           libvorbisfile.so.3
libgmodule-1.2.so.0       libopenal.so.0            libvorbisfile.so.3.1.1
libgmodule-1.2.so.0.0.10  libopenal.so.0.0.0        libvorbis.so.0
libgthread-1.2.so.0       libphysfs-1.0.so.0        libvorbis.so.0.3.1
chris@ubuntu:~/Desktop/POSTAL$ 
```

---

### Post by Kilz on 2007-06-06
Ummmm have you tried, maybe, possibly, opening a terminal and typing postal2? Have you tried to get support or information from the site you got the install file from?

---

### Post by fakie_flip on 2007-06-06
```
chris@ubuntu:/etc/X11$ postal2
bash: postal2: command not found
chris@ubuntu:/etc/X11$
```

Yes, I have. There are no new commands to start the game. Here is how I know there isn't, and I know it is not installed.

```
chris@ubuntu:~$ sudo find / -iname '*postal*'
Password:
/home/chris/Desktop/POSTAL/postal2mpdemo-lnx-1407.run
/home/chris/Desktop/POSTAL/postal2mpdemo-lnx-1407.tar.bz2
chris@ubuntu:~$
```

---

### Post by Kilz on 2007-06-06
> **fakie_flip said:**
> ```
chris@ubuntu:/etc/X11$ postal2
bash: postal2: command not found
chris@ubuntu:/etc/X11$
```

Yes, I have. There are no new commands to start the game. Here is how I know there isn't, and I know it is not installed.

```
chris@ubuntu:~$ sudo find / -iname '*postal*'
Password:
/home/chris/Desktop/POSTAL/postal2mpdemo-lnx-1407.run
/home/chris/Desktop/POSTAL/postal2mpdemo-lnx-1407.tar.bz2
chris@ubuntu:~$
```

You may want to ask questions of the people who supplied you the install file.

---

### Post by fakie_flip on 2007-06-25
Problem solved. I deleted those demos and tried the real game. It's working great in 64 bit. I'm not sure why the demos wouldnt work, but the full version does.

---

### Post by shane4stef on 2007-12-14
Can you tell me how you got installed?...I have the fudge pack. Had installed but hdd went dead. Now cant  seem to install. tried sudo sh /media/cdrom0/linux_installer.sh. not working. This is how i installed before though. Thanks for any help.

---

