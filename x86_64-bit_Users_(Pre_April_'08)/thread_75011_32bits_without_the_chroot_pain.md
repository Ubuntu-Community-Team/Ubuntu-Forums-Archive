---
title: "32bits without the chroot pain?"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bloot on 2005-10-13
Well, that's what I am wondering, if there's any way out to run 32bit apps without doing the painful chroot trick.

I've noticed a lib32 directory and don't know much about what can be done with it.

Hope it can be as easy as it is with gentoo for example!.

Greetings. :smile:

---

### Post by emrys on 2005-10-13
It would be wonderfull.

Someone?

---

### Post by Dr. Nick on 2005-10-13
Search "linux32" in synaptic and read up on it, I have tried with limited success as some 32bit apps need 32bit libraries, But it might work for a simple app not needing many libraries.

---

### Post by Kuolio on 2005-10-13
With most of the programs out there, there is some ways to get them working in 64bit w/o chroot, but it seems that with every program you have to "hack" someparts of your configs or something..

i.e. you can get w32codecs working by just installing them from mplayer hq (read the READ ME and search for these forums), some1 made a nice mplayer32 binary with wmv9 codecs included etc.

So, lots of things that are 32bit you can have working when using 64bit system, you just need to hack some and do research.

---

### Post by Bloot on 2005-10-13
So I guess it's not as simple as installing any 32bit package and the os itself put it in the right place, I supposed that lib32 had something to do with it. We'll have to wait 'till it's implemented in the way in gentoo and others is as I said before.

Thanks!.

---

### Post by rplantz on 2005-10-13
[QUOTE=Bloot]So I guess it's not as simple as installing any 32bit package and the os itself put it in the right place, I supposed that lib32 had something to do with it. [/QUOTE]

I started my Ubuntu adventure on an amd64 running hoary.

I had already written a textbook on assembly language programming under Linux. The amd64  instruction set is somewhat different, so I had to figure out how to assemble, link, and run my programs in 32-bit mode.

I had to install ia32-libs.

I had to change my makefiles so that assembly is done with the --32 option, and C/C++ complilation and library linking are done with the -m32 option. (Some of my programs mix C, C++, and assembly.)

This creates 32-bit code, including library routines, and sets everything up to run in 32-bit mode. All my programs work just fine.

Here I am at the limit of my knowledge about this. I don't know why a program that was compiled in a 32-bit system (hence, in 32-bit mode) will not run on my amd64. I have some ideas, but I need to learn more about this before I say something stupid.

I guess the point here is that I think it's pretty easy to create 32-bit programs that will run on a 64-bit system, but I may be missing something important.

Bob

---

### Post by RAOF on 2005-10-13
I think the trick is that **all** of the program needs to be 32bit - including all the dynamically linked libraries, everything **they** link to, etc.  Untill the lib32 directory contains a 32bit version of everything, there'll be problems running 32bit programs.

That's not to say it's in any way impossible.  In fact, it should be possible to make 32bit packages for breezy64 - I'd like to see some in the repositories (particularly firefox, for flash :) )

---

### Post by rplantz on 2005-10-13
[QUOTE=RAOF]I think the trick is that **all** of the program needs to be 32bit - including all the dynamically linked libraries, everything **they** link to, etc.  Untill the lib32 directory contains a 32bit version of everything, there'll be problems running 32bit programs.

That's not to say it's in any way impossible.  In fact, it should be possible to make 32bit packages for breezy64 - I'd like to see some in the repositories (particularly firefox, for flash :) )[/QUOTE]

I'm pretty sure you're right. I compiled a "hello" C program both in 32-bit and 64-bit versions. When I do a readelf on the executable files, the 32-bit version has a statement
```

 [Requesting program interpreter: /lib/ld-linux.so.2]

```
which resolves through several links to /lib32/ld-2.3.5.so, and the 64-bit version has the statement
```

[Requesting program interpreter: /lib64/ld-linux-x86-64.so.2]

```
which resolves to /lib64/ld-2.3.5.so.

The .so means these are shared libraries.

And now I've hit the limit of my knowledge in this area, but I'll probably keep trying to figure it out 'cause I think it's fun. One of the many perks of being retired! :-)

Bob

---

### Post by DancingSun on 2005-10-13
I believe the problem with running 32-bit programs on the 64-bit Ubuntu is mostly related to dependencies as well.  On programs that require little or no external library dependency, 32-bit programs compiled on a 32-bit system run with little to no modification.  For example, games.  Many games are pretty well self-contained.  That is, they require very few externally linked libraries.  America's Army and Enemy Territory both are only available in 32-bit binaries, but they ran without a hitch on my 64-bit system (5.04).

I guess that would suggest, a statically linked 32-bit program should have little problem running under a 64-bit OS in an AMD64 compatible processor.

---

