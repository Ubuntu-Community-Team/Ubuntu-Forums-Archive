---
title: "Some missing software on Ubuntu AMD64"
date: 2004-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmatrix on 2004-10-18
I have came across a few pieces of software that I would like to see in universe/multiverse for AMD64.

cdrdao (I used that Sarge package)
ooqstart-gnome (Sarge package)
tvtime (No Sarge or Ubuntu package)

Not sure about these ones:
libdvdcss2 (Does this work on AMD64?)
mplayer/mencoder packages would be nice as well for AMD64. Currently using a ia32 chroot with these packages.

---

### Post by Vermyndax on 2004-10-21
Could you go into a little more detail about how you got tvtime to work?  I assume you got it working through the chroot and had to add sources to synaptic...

(Yep... can you say... newb?)

---

### Post by goatboy on 2004-10-21
mplayer/mencoder is in multiverse (mplayer-amd64), and you can get libdvdcss2 by running /usr/share/doc/libdvdread3/examples/install-css.sh.

---

### Post by Vermyndax on 2004-10-21
That's nice but... I really need a tv viewer to work ;)

---

### Post by defcon-1 on 2004-10-21
*That's nice but... I really need a tv viewer to work*
Same here.

---

### Post by K6-III on 2004-10-21
Thanks for the instructions for libdvdcss.  They worked great!

---

### Post by dmatrix on 2004-10-22
well I just found out that most things are in multiverse in amd64, they just are not built yet. 

Add this line to your /etc/apt/sources.list
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse

Then make sure you have a compiler installed:
sudo apt-get install gcc g++

Then you can start building things:
sudo apt-get update
sudo apt-get source --compile tvtime

It will probably error out with needing some build dependencies. apt-get all the dependencies and try to compile it again. Eventually you will end up with a nice amd64 binary deb file that you can install with dpkg.

By doing this I got tvtime, ooqstart-gnome, acidrip and mplayer/mencoder with libdvdread support. 

Still testing building things. Still cannot get cdrdao to compile on amd64 it complains about X86_64 stuff?

---

### Post by K6-III on 2004-10-22
I also have issues with compiling CDRDAO.

---

### Post by jdong on 2004-10-24
adding in complaint about lack of WINE... ;)

---

### Post by xpt on 2005-01-23
[QUOTE=dmatrix]I have came across a few pieces of software that I would like to see in universe/multiverse for AMD64.

cdrdao (I used that Sarge package)
[/QUOTE]

Can anyone give me a direct link where I can dl this package please? 

I've been to [http://debian-amd64.alioth.debian.org/](http://debian-amd64.alioth.debian.org/), but I couldn't find it. More over, I found an amd64.txt, in which stats that the cdrdao failed on something...

please help. 

PS. I saw in another thread that it could be compiled. But I'm also having problem compiling it.

thanks

---

### Post by xpt on 2005-01-23
Also, I can't seem to find the rar package. 

What's your solution? 

thx

---

