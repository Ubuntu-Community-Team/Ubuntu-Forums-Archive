---
title: "ia32-libs &amp; IRAF"
date: 2008-11-04
forum: x86 64-bit Users
---

### Post by super zach on 2008-11-04
Hi all

I just dual-booted my new studio17 dell laptop with vista (came with it) and ubuntu 8.10.  I am really needing to put IRAF onto my new toy and I found a handy 64bit install notes:

[http://geco.phys.columbia.edu/~rubab/iraf/iraf-64-bit_step_by_step_installation](http://geco.phys.columbia.edu/~rubab/iraf/iraf-64-bit_step_by_step_installation)

however, (of course there is a however!) as I was working through this wonderfully provided script I cannot get ubuntu to find  ia32-libs.  I have tried various methods including an installer package:

getlibs-all.deb

which I found on another forum post.

Basically, is there anyway to get ubuntu to find ia32-libs?

Many thanks, zach

---

### Post by TryHarder on 2008-11-04
Try simply 
```
sudo apt-get upgrade
sudo apt-get update
sudo apt-get install ia32-libs
```.

2 first steps is not necessary, but won't harm.
If it still doesn't work so probably you must add some repository to your source.list file. I apologize that i don't know exact address of repository (i'm also newb to Ubuntu).

---

### Post by super zach on 2008-11-04
thanks bud but i tried that already and all I get is a message saying it cant find package ia32-libs :o(

---

### Post by TryHarder on 2008-11-04
doubled... see below

---

### Post by TryHarder on 2008-11-04
Try to open package manager ( system -> Administration -> synaptic package manager) and open there settings -> repositories. mark universe inside (actually mark all of them =) )

---

### Post by TryHarder on 2008-11-04
Try to go to system > administration >synaptic package manager and open there setting>repositories and mark universe and multiverse.

---

### Post by Kevbert on 2008-11-04
The best way to get ia32-libs (32 bit libraries) is to use Getlibs. You can find it via this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=474790").

---

### Post by Kilz on 2008-11-04
> **Kevbert said:**
> The best way to get ia32-libs (32 bit libraries) is to use Getlibs. You can find it via this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=474790").

Getlibs installs 32bit libraries from 32bit deb files. But ia32-libs is a 64bit package that installs a lot of 32bit libraries. Thats why people are suggesting people install it with apt.

My question is that if ia32-libs cant be installed, is the orignal poster sure that they have the 64bit version installed.

---

### Post by Yellow Pasque on 2008-11-04
```
uname -m
```
should return "x86_64".
If it doesn't, you're not using 64-bit Ubuntu.
If it does, then something is wrong with your repos. Post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by super zach on 2008-11-05
Thanks to everyone you have been very helpful!

I ran "uname -m" and the output was "i686".  As its not "x86_64" I am assuming its 32bit rather than 64.  I also checked the ubuntu site where I got the install for 8.10 and I think I downloaded the 32bit version, so why I thought it was 64 is beyond me! :)

I am now going to try and install IFAR using the 32bit notes, wish me luck!

Thanks all! z

---

### Post by super zach on 2008-11-05
Well its been a long morning and afternoon but I have installed IRAF  and it feels like ive just won a marathon.  I used an excellent post at:

[http://ubuntuforums.org/showthread.php?t=912583&highlight=iraf](http://ubuntuforums.org/showthread.php?t=912583&highlight=iraf)

which was very helpful.

Ta for everyone's help!! z

---

