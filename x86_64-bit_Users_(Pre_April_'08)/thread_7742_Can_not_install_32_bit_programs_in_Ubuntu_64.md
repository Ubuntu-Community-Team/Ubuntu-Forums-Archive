---
title: "Can not install 32 bit programs in Ubuntu 64?"
date: 2004-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by jkarpago on 2004-12-10
Hi:
I have installed Ubuntu64 today but I find some problems that did not like me.
The problems are with some programs I could not use and with the sources.list IU use before.

I try to install xawdecode ( xdtv ) through apt but I fails in all the lines that I added to sources.list, and this lines are correct because I try in a 32 bit Ubuntu and they worked.

I could not install avidemux , or flash.

So, I wonder, am I useless user or simply those programs not work and I must install ubuntu 32 to use them?

---

### Post by dbcoder on 2004-12-10
You need to have an installation of ubuntu 32 to run 32 bit applications

---

### Post by Gibbz on 2004-12-11
so would that mean the only decent game playable on 64bit linux would be ut2k4? i havent seen many 64bit games or apps, is it not possible like with winxp64bit to run 32bit apps if you had some of the right p[akages installed?

---

### Post by dbcoder on 2004-12-11
Suse 9.2 64-bit has 32 bit emulation!

---

### Post by BoyOfDestiny on 2004-12-11
[QUOTE=dbcoder]You need to have an installation of ubuntu 32 to run 32 bit applications[/QUOTE]
 Open Office is 32-bit, doesn't compile under 64-bit (AFAIK)...so it means 32-bit apps can be run since ubuntu amd64 has it. Anyone care to shed some light on the tricks needed to install and run these apps. Might be handy if ia32 emulation lib can do the job, vs chrooting for a few apps?

---

### Post by Ribs on 2004-12-20
[QUOTE=BoyOfDestiny]Open Office is 32-bit, doesn't compile under 64-bit (AFAIK)...so it means 32-bit apps can be run since ubuntu amd64 has it. Anyone care to shed some light on the tricks needed to install and run these apps. Might be handy if ia32 emulation lib can do the job, vs chrooting for a few apps?[/QUOTE]

in the case of OpenOffice, a library is supplied by the Ubuntu team to emulate the 32-bit calls it makes. It's called ia32-libs-openoffice.org. Check synaptic for it and you should see it's installed.

Gentoo supplies users with really good ia32 libraries which make using a chroot pretty much redundant. It's a crying shame Ubuntu doesn't do the same thing really, it would be things a lot more simple. They supply one ia32 library other than the openoffice one, but that's not good enough for my needs, sadly.

I am wondering if it's possible to create ia32 packages myself and use those...  :-k 

-Ribs.

---

### Post by soloha on 2007-02-28
I've been just downloading the 32bit libs I need (using command ldd on 32 binaries to find out which) from packages.ubuntu.com, using the archive manager to extract the libs and sticking them in /usr/lib32 and this has worked for me.

---

### Post by asdf25 on 2007-02-28
If you hadn't noticed, this thread is over two years old, and things have changed a lot since then.

---

### Post by starcannon on 2007-03-02
Things haven't changed enough, I'm getting the old cedega error on an install of Ubuntu 64 that I downloaded and installed just today.

---

