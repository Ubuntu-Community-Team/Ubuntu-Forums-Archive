---
title: "Packet Tracer 32bit on 64bit platform. (PROBLEM)"
date: 2008-08-06
forum: x86 64-bit Users
---

### Post by qbox on 2008-08-06
Hi
I want to do some Packet Tracer Activities for a cisco lessons and I downloaded from cisco web page a installation for packet tracer program.
The file I downloaded is .bin and is for 32 bit platform.
First I make chmod +x packetTrace.bin and I try to start with ./packetTrace.bin command. 
The console return me this

```
dpkg: error processing PacketTracer-5.0.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 PacketTracer-5.0.i386.deb
```

I think how to compile 32 bit application under ubuntu 8.04 64bit.
Is it possible to compile 32 bit application if I install some libraries?:confused::confused:
Can some one give mi a little help?
Thank you.

---

### Post by qbox on 2008-08-06
I need help quickly... please anyone...
Any help about upper problem or please tell me how to take out only PacketTracer-5.0.i386.deb from the .bin file?
If i take out this file I will try to install with command 
dpkg -i --force-all ./PacketTracer-5.0.i386.deb
I think that will work.

---

### Post by qbox on 2008-08-06
I cant believe. 30 reads and no one to have some clue around this?
:lolflag:
Please any help. I need to install or extract .bin file. File is for 32-bit arhitecture I need to make it work on 64.

---

### Post by pana.corbului on 2008-08-07
If I'm not mistaking on cisco netacad sources are also available to download. You can compile from sources I guess.

---

### Post by qbox on 2008-08-07
What? Im BLIND?
I didnt see the last .tar.gz file in the download section...
THANK YOU
:guitar::popcorn:

---

### Post by qjuanp on 2008-08-08
First you must download Packet Tracer v5,0 in the package for generic Linux from CISCO, PacketTracer5_generic.tar.gz

then

$ tar xfzv PacketTracer5_generic.tar.gz

$ cd PacketTracer5

$ sudo ./install

that it's all

_____________
qjuanp
[http://qjuanp.wordpress.com](http://qjuanp.wordpress.com)
[http://colossus.utp.edu.co](http://colossus.utp.edu.co)

---

### Post by Narf on 2008-11-13
... or you could run the self-extracting binary and wait until the EULA is displayed. Then open up a terminal window and look for the .deb under /tmp/selfextract.<somerandomstringhere>/.
And there you go - you can now try to install it with --force-architecture. However, compiling from source is better if you want to avoid eventual errors.

---

### Post by dedyisn on 2009-01-12
> **Narf said:**
> ... or you could run the self-extracting binary and wait until the EULA is displayed. Then open up a terminal window and look for the .deb under /tmp/selfextract.<somerandomstringhere>/.
And there you go - you can now try to install it with --force-architecture. However, compiling from source is better if you want to avoid eventual errors.
thanks for your help
I have this problem too and now its solved because of your suggest

---

### Post by dwar80 on 2009-01-30
> **dedyisn said:**
> thanks for your help
I have this problem too and now its solved because of your suggest

Ditto. Thanks.

---

### Post by sartipi.m on 2009-05-13
type these:

[B]sudo apt-get install ia32-libs-gtk
./packettracer.bin[/B]

---

### Post by hovrashko on 2009-09-06
$ tar xfzv PacketTracer5_generic.tar.gz

$ cd PacketTracer5

$ sudo ./install

that it's all

did work for me on ubuntu 9.04 x64, but I had to change packetTracer52 =)

thanks a lot

---

