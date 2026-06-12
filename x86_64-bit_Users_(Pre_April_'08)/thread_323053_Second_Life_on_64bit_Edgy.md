---
title: "Second Life on 64bit Edgy"
date: 2006-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by JackInTheGreen on 2006-12-21
Hey!

My first post on these forums, but they have been a wonderful resource. Lot's of helpful people here, so I thought I would try and see if I get some help with something...actually I have been able to solve all my problems with linux so far, just by using the search function on this forum.

Anyway, I want to run Second Life on my 64 bit Edgy. I get this problem:
> jackinthegreen@Beleriand:~/SecondLife/SecondLife_i686_1_13_1_5$ ./secondlife
bin/do-not-directly-run-secondlife-bin: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory


I have installed all libsdl* packages that are listed in Synaptic Package Manager.

I would be very grateful to anyone who can help me solve this.

Thanks!

---

### Post by janfsd on 2006-12-21
Probably you need to get the 32 bits version of that library, go to packages.ubuntu.com, search for it, and open it with the archive manager and extract it to /usr/lib32 and in the console type sudo ldconfig
That should do it or ask for another library, and just search for it and do the same thing.

---

### Post by xopher on 2006-12-21
```
sudo apt-get install ia32-libs-sdl
```

should do it as far as I know. Post your solution when you get it running though :)

---

### Post by cafuego on 2006-12-30
I've added ia32-libs-sdl as a depend to my package. Any volunteers to see if it actually runs on amd64?

[http://ubuntu.cafuego.net/pool/edgy-cafuego/secondlife/secondlife_1.13.1.6-1cafuego0_amd64.deb](http://ubuntu.cafuego.net/pool/edgy-cafuego/secondlife/secondlife_1.13.1.6-1cafuego0_amd64.deb)

---

### Post by Brent Dax on 2007-01-09
```
bin/do-not-directly-run-secondlife-bin: error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory
```
Now that they've open-sourced it, I tried to compile it on AMD64, but it turns out that the (closed-source) sound library they use isn't packaged for AMD64.  Ugh...

---

### Post by Warbo on 2007-01-09
I got his too, but doing a little searching it turns out that using the 32bit version is fine, although it isn't packaged in amd64 as a "ia32" package. Basically follow the instructions I found from Kilz about getting Wengo working:
 Download this .deb file.
Make sure you have dpkg-dev installed with synaptic.
Extract the .deb with the archive manager, extract the contents of the data.tar.gz archive to your Desktop.
Open a terminal
Run:

sudo cp ~/Desktop/lib/* to /lib32

Now I get past that problem, but onto a "Window creation error" :( Back to Google I go...

---

### Post by Anolis on 2007-03-12
Running Feisty latest updates installed as of 12 March 2007 20:19

> $ uname -r
2.6.20-9-generic

now what do i do.. since unpacking has critically failed
i'm tempted to just reinstall ubuntu seeing as vmware has fsck'd my debian package index miserably

> ~/Desktop/uuid$ sudo dpkg --force-architecture --unpack '/home/a/Desktop/libuuid1_1.38-2ubuntu2_i386.deb' -R /home/a/Desktop/uuid
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg - warning: downgrading libuuid1 from 1.39+1.40-WIP-2006.11.14+dfsg-1ubuntu1 to 1.38-2ubuntu2.
(Reading database ... 
dpkg: serious warning: files list file for package `vmware-player-kernel-modules' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `vmware-player-kernel-modules-2.6.20-9' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-vmware' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `vmware-player' missing, assuming package has no files currently installed.
113900 files and directories currently installed.)
Preparing to replace libuuid1 1.39+1.40-WIP-2006.11.14+dfsg-1ubuntu1 (using .../libuuid1_1.38-2ubuntu2_i386.deb) ...
Unpacking replacement libuuid1 ...
dpkg: error processing /home/a/Desktop/libuuid1_1.38-2ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/bin/uuidgen', which is also in package e2fsprogs
dpkg: error processing -R (--unpack):
 cannot access archive: No such file or directory
dpkg-split: error reading /home/a/Desktop/uuid: Is a directory
dpkg: error processing /home/a/Desktop/uuid (--unpack):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 /home/a/Desktop/libuuid1_1.38-2ubuntu2_i386.deb
 -R
 /home/a/Desktop/uuid
~/Desktop/uuid$


---

