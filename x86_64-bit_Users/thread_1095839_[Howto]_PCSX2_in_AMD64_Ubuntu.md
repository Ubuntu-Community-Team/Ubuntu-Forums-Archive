---
title: "[Howto] PCSX2 in AMD64 Ubuntu"
date: 2009-03-14
forum: x86 64-bit Users
---

### Post by immolo on 2009-03-14
Right my first tutorial for Ubuntu but better late then never :P

This guide will show you how to run PCSX2 on your AMD64 computer without the need for a 32bit chroot.

First you need to download the Linux version of PCSX2 from the [website]("http://www.pcsx2.net/downloads.php") and unpack:

```

# tar zxvf PCSX2_0.9.6_linux.tar.gz
# cd pcsx2/
```

Next lets meet all the needed dependences:

```
# sudo apt-get install libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev libasound-dev nvidia-cg-toolkit libglu1-mesa-dev libglew1.5-dev;
```

Running PCSX2 now will result in the program running but not being able to show and graphic output due to the hard coding of looking for some 32bit libs so now we are going copy over some of the need libs.

Download the needed files:

```

# mkdir tmp
# cd tmp/
# wget http://mirrors.kernel.org/ubuntu/pool/main/g/glew/libglew1.5_1.5.0dfsg1-3ubuntu1_i386.deb
# wget http://mirrors.kernel.org/ubuntu/pool/main/g/glew/libglew1.5-dev_1.5.0dfsg1-3ubuntu1_i386.deb
# wget http://developer.download.nvidia.com/cg/Cg_2.1/2.1.0017/Cg-2.1_February2009_x86.tgz
```

Now we can extract the files:

```

# dpkg -x libglew1.5_1.5.0dfsg1-3ubuntu1_i386.deb .
# dpkg -x libglew1.5-dev_1.5.0dfsg1-3ubuntu1_i386.deb .
# tar zxvf Cg-2.1_February2009_x86.tgz
```

Next we need to copy the libraries to the lib32 directory:

```

# sudo cp usr/lib/* /usr/lib32/ 
```

Lets do a little clean up:

```

# cd ..
# rm -r tmp/
# rm ../PCSX2_0.9.6_linux.tar.gz
```

OK now run PCSX2:

```
# ./pcsx2
```

Now you will see everything works as normal.

Hope this helps you guys.

---

### Post by dmizer on 2009-03-16
Moved to the 64bit section of the forums :)

---

### Post by modmadmike on 2009-03-24
yay now I can play guilty gear and Siren2 Japanese ver on my pc.

---

### Post by landeel on 2009-03-25
Previously I was using the window$ version with wine.
It worked, and it's running much faster now.
Thank you!

---

### Post by Stunts on 2009-03-25
Good tutorial.
Just a couple of things tough:
in the ```
 code 
``` sections starting with a # character means "-as root". You should change that character to "$" which means "-as user".
Other than that it seems great.
I once used PCSX2, but to solve the 64 bit problem I compiled from source... It usually gets you a bit of extra performance.
Keep up to good work!

---

### Post by monkeyslayer56 on 2009-05-19
when do were we extract/install the pacakges i get
```
josh@josh-desktop:~/tmp$ dpkg -x libglew1.5_1.5.0dfsg1-3ubuntu1_i386.deb
dpkg-deb: --extract needs a target directory.
Perhaps you should be using dpkg --install ?

```
any idea what i did wrong?


EDIT: never mind i didn;t copy the last(.) at the end

---

### Post by Helekryl on 2009-06-30
Thanks a lot. The guide really helped, at least my pcsx2 launched and recognized bios and plugins.

Nevertheless, any attempt to launch a DVD (Final Fantasy 10) in my case always led to X crash. (I'm using Ubuntu 8.10 x64 and compiz-fusion. I have an Intel Core 2 Quad Q9450 and ATI Radeon 3870x2 with a proprietary ATI driver.)


So, I found out the following:

1. First of all, only disabling compiz and restarting X Server seem to help. When I simply switched to metacity with "metacity --replace" or compiz-fusion-icon applet, it didn't work at all. Disabling visual effects in gnome-appearance-properties and then restarting X also helped.
(Several times I managed to launch the DVD with Normal or Advanced effects somehow, but every time the picture was blinking constantly).

2. After that, the game (its main menu) starts correctly, but pcsx2 freezes on launching 3D when starting a new game. Set Config -> Cpu -> Multi-threaded GS mode on to fix that.

PS sorry for my English :p

---

### Post by Oglon3r on 2009-06-30
whoa i came into this by pure coincidence i shall give it a try, been wanting to try this for the longest time:p
thank you for the guide in advance will bring feedback later

---

### Post by israafiyl on 2009-09-09
hi, when i try to run it i get this error:
```

israafiyl@ubuntu:~/pcsx2$ ./pcsx2
./pcsx2: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```
ty for the tutorial :D

---

### Post by Helekryl on 2009-09-09
This is a library from libgtk2.0-0, and it's strange - X server can't function without it.
Maybe pcsx2 wants a 32 bit library?

Recheck all pcsx2 dependencies listed - after installing them, no message about missing libraries should pop up.

---

### Post by XplOzIOn on 2009-09-28
> **Helekryl said:**
> This is a library from libgtk2.0-0, and it's strange - X server can't function without it.
Maybe pcsx2 wants a 32 bit library?

Recheck all pcsx2 dependencies listed - after installing them, no message about missing libraries should pop up.

I have the same problem, and i have checked all dependencies and everything is installed... Im running a AMD64 system

---

### Post by Helekryl on 2009-10-22
Check the output of the following command:
```
locate libgtk-x11-2.0.so.0
```

The output should be smth like
```
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.1600.1
/usr/lib32/libgtk-x11-2.0.so.0
/usr/lib32/libgtk-x11-2.0.so.0.1600.1

```

---

