---
title: "Hauppauge PVR 350 works or not in Breezy 5.10 64Bit?"
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by SleepyHollow on 2005-10-31
Hi folks,

I just want to know if the hauppauge PVR 350 could work in this environment or not. I tried to find some how-to's but nothing there, especially for using 64Bit-Breezy. 

The big question: How to install ivtv in order to make the card work? Where to get the driver? Building from scratch or using a binary package? I would prefer the last.

I tried to install mythtv via apt-get (read PVR 350 is supported this way) but only some errors occurs with "dependencies". 

It would be great if the PVR 350 could have been convinced to work. My Wlan WMP54G of linksys ist working good with WPA2 out of the box. Also the driver of nvidia for my 6600GT. I'm impressed.

---

### Post by queenorych on 2005-10-31
great board.  Get the ivtv driver from the ivtv people (google ivtv) and compile it yourself.  You will need the kernel-source and kernel-headers.  Read there doc.  Shouldn't be too hard.  I think after a make install you will need to move the /lib/modules directory created by ivtv to the appropriate modules difrectory for your kernel.  There should be pleanty of docs and help from the ivtv people.

Good luck

---

### Post by FluffyElmo on 2005-11-01
I have a PVR150 working with AMD64 Breezy and have no problems. I followed the instructions from the how-to link below and everything went smoothly. 

[http://www.abarbaccia.com/content/view/19/31/]("http://www.abarbaccia.com/content/view/19/31/")

One tip that isn't in the how-to, after installing the driver you should be able to get video and audio using the command: mplayer /dev/video0

---

### Post by SleepyHollow on 2005-11-01
[QUOTE=FluffyElmo]I have a PVR150 working with AMD64 Breezy and have no problems. I followed the instructions from the how-to link below and everything went smoothly. 

[http://www.abarbaccia.com/content/view/19/31/]("http://www.abarbaccia.com/content/view/19/31/")

One tip that isn't in the how-to, after installing the driver you should be able to get video and audio using the command: mplayer /dev/video0[/QUOTE]


Thanks for the link. I give it a trial.

---

### Post by SleepyHollow on 2005-11-02
Hi there,

alright, I tried this howto, but this error occurs:

When making "make oldconfig":

<terminal-output>
root@bruchtal:/usr/src/linux# make oldconfig
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Fehler 127
make: *** [scripts_basic] Fehler 2
</terminal-output>

(By the way: I changed the "gcc-3.4" to "gcc" only, it compiles all, but the resulting modules have the wrong magic kernel version. This is not really what i want. This is the result of hacking a makefile. I'll never do it again.)

What was the reason for this error with the gcc-3.4? I'm using Breezy Badger 5.10 AMD64-generic without any further modification.

<gcc-version>
root@bruchtal:/usr/src/linux# gcc --version
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
</gcc-version>

---

### Post by FluffyElmo on 2005-11-02
Breezy has gcc-4.0 installed by default, however the kernel and modules are built with gcc-3.4. Install gcc-3.4 and try setting the CC environment variable to gcc-3.4 before building and it should work.
```

sudo apt-get install gcc-3.4
export CC=gcc-3.4
make
...etc
```

You will likely have to do a *make clean* before building as well. Sorry, I changed my default gcc to 3.4 when I installed the Nvidia driver so forgot that itr might be a problem.

---

### Post by FluffyElmo on 2005-11-02
One more thought, in case the export CC=gcc-3.4 doesn't work, you can change the */usr/bin/gcc* symlink to point to *gcc-3.4* or edit the make file to use *gcc-3.4*.

---

### Post by SleepyHollow on 2005-11-02
Thanks fluffyelmo,

now it works. The first advice was sufficient. "mplayer /dev/video0" shows Video and Audio. :D

Any suggestions which TV-applications are useful? Mythtv is not installable with apt-get, errors with dependencies.

---

