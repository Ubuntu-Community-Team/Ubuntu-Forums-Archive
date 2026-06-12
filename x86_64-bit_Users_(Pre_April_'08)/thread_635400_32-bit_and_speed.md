---
title: "32-bit and speed"
date: 2007-12-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ob1 on 2007-12-08
I made a partition for XP(32-bit) for the sole purpose of games and I find it to be a little faster than Ubuntu 7.10(64-bit). According to the manual that my motherboard came with, 32-bit OS are just as compatible as 64-bit(and it is 64-bit architecture) so has anyone tried both Gusty Gibson 32-bit and 64-bit on a X86 64-bit platform and noticed any differences in responsiveness?

---

### Post by dewey on 2007-12-08
The speed difference isn't always visually apparent.  64-bit shines during number crunching sequences, like converting media types or ripping cds.  You may not notice blazing speeds, but it should be running more efficiently.  If it's running slower, I'd recommend looking into things such as your video drivers, because it should at least be equal in speed to the same release 32bit.

I've run both 32-bit feisty and 64bit feisty, as well as 64bit gutsy, and I find no reason to use 32bit. The "incompatibility" of 64bit with programs is greatly exaggerated, I haven't had a problem getting any programs to work.

---

### Post by Ob1 on 2007-12-08
> **dewey said:**
> The speed difference isn't always visually apparent.  64-bit shines during number crunching sequences, like converting media types or ripping cds.  You may not notice blazing speeds, but it should be running more efficiently.  If it's running slower, I'd recommend looking into things such as your video drivers, because it should at least be equal in speed to the same release 32bit.

I've run both 32-bit feisty and 64bit feisty, as well as 64bit gutsy, and I find no reason to use 32bit. The "incompatibility" of 64bit with programs is greatly exaggerated, I haven't had a problem getting any programs to work.

I have the right official drivers and all and there aren't any problems, I've just read and heard that 32-bit versions of whatever OS can be quicker in some tasks.

---

### Post by Kilz on 2007-12-08
> **Ob1 said:**
> I have the right official drivers and all and there aren't any problems, I've just read and heard that 32-bit versions of whatever OS can be quicker in some tasks.

I dont think thats possible. Please provide a link to this information you say you have read.
As far as compatibility, yes a 32bit operating system will run on 64bit hardware. But a 32bit os will not make full use of the hardware. It runs in 32bit mode. You may as well buy 32bit hardware (if you can anymore) if your planing on running a 32bit os.

---

### Post by dptxp on 2007-12-09
> **Ob1 said:**
> I have the right official drivers and all and there aren't any problems, I've just read and heard that 32-bit versions of whatever OS can be quicker in some tasks.

Yes, you can have programs badly altered to 64 bit running slower. And yes, there are such programs if I correctly recall some evaluation reports on processors. But these are exceptions. And for short time.

---

### Post by fineas on 2007-12-09
> **Ob1 said:**
> I have the right official drivers and all and there aren't any problems, I've just read and heard that 32-bit versions of whatever OS can be quicker in some tasks.

Here, there is a comparison between 32bit and 64bit [http://art-blog.no-ip.info/files/amd64vsi386.pdf](http://art-blog.no-ip.info/files/amd64vsi386.pdf). Clearly, for games, 64bit performs better than the 32bit.

---

### Post by mma8x on 2007-12-09
> **Kilz said:**
> I dont think thats possible. Please provide a link to this information you say you have read.
As far as compatibility, yes a 32bit operating system will run on 64bit hardware. But a 32bit os will not make full use of the hardware. It runs in 32bit mode. You may as well buy 32bit hardware (if you can anymore) if your planing on running a 32bit os.

[http://www.phoronix.com/scan.php?page=article&item=616&num=1](http://www.phoronix.com/scan.php?page=article&item=616&num=1)
[http://www.linux.com/articles/114024](http://www.linux.com/articles/114024)
[http://www.linuxhardware.org/article.pl?sid=05/02/24/1747228](http://www.linuxhardware.org/article.pl?sid=05/02/24/1747228)
[http://64-bit-computers.com/linux-ubuntu-610-64-bit-vs-32-bit-benchmark-test.html](http://64-bit-computers.com/linux-ubuntu-610-64-bit-vs-32-bit-benchmark-test.html)
[http://www.worlds-fastest.com/wfz998.html](http://www.worlds-fastest.com/wfz998.html)

most of the time it seems that the 64 bit gain is minimal, if any.  for many common apps 32 bit actually seems faster.

---

### Post by dptxp on 2007-12-09
> **mma8x said:**
> [http://www.phoronix.com/scan.php?page=article&item=616&num=1](http://www.phoronix.com/scan.php?page=article&item=616&num=1)
[http://www.linux.com/articles/114024](http://www.linux.com/articles/114024)
[http://www.linuxhardware.org/article.pl?sid=05/02/24/1747228](http://www.linuxhardware.org/article.pl?sid=05/02/24/1747228)
[http://64-bit-computers.com/linux-ubuntu-610-64-bit-vs-32-bit-benchmark-test.html](http://64-bit-computers.com/linux-ubuntu-610-64-bit-vs-32-bit-benchmark-test.html)
[http://www.worlds-fastest.com/wfz998.html](http://www.worlds-fastest.com/wfz998.html)

most of the time it seems that the 64 bit gain is minimal, if any.  for many common apps 32 bit actually seems faster.

As I have already said, not all programs are optimized for 64 bit, they have just been ported with
minimal work just to ensure functionality. So there will be programs running faster in 32 bit versions.

This is from the article from Linux.com
[COLOR="DarkOrange"]Please note that this article was posted on 15th June 2005. Obviously a lot has changed since then in favor of 64 bit[/COLOR]

 [COLOR="Blue"]Conclusions

While everyday "Internet and email" desktop performance of a 64-bit operating system may not be much different from that of a 32-bit platform, CPU- and memory-intensive applications see significantly enhanced performance. 3D gaming performance could suffer from not-yet-perfect Nvidia drivers (there were two newer "unstable" versions of the Nvidia driver in Portage at the time of this writing) and 64-bit game binaries that are still experimental. 64-bit gaming is, after all, a new thing to PC game developers.

64-bit operating systems may not be practical for simple desktop use at this point, partially because of some of the hassles in setting them up, and partially because they offer little performance increase for most desktop applications. But the advantage of running a Web or email server is obvious when you look at the OpenSSL and MySQL results, assuming you use those technologies.

Sometimes the purpose of a benchmarking project is to show which squeaky wheels need the grease. This benchmarking project has shown that there's still a long way to go for AMD64-specific optimizations in the GNU/Linux world.
[/COLOR]

[COLOR="Red"]The first link is for a post dated 29th Dec. 2006, the 3rd one 24th Feb. 2005, 4th is 8th Nov 2006, 5th has no date. The posts are pretty old, so
please show some recent one[/COLOR]

---

### Post by mma8x on 2007-12-09
well, i don't think anybody is arguing that 64 bit doesn't have the potential to be faster.  at this point though, the gains in most circumstances are minimal, if any.  i'm tired of googling; maybe you could post some recent articles showing 64 bit gains? at least one of those comparisons was using feisty, so fairly relevant here.

---

### Post by Thelasko on 2007-12-09
I find 64-bit much faster, but I think that just has to do with my machine.

---

### Post by dptxp on 2007-12-10
> **mma8x said:**
> well, i don't think anybody is arguing that 64 bit doesn't have the potential to be faster.  at this point though, the gains in most circumstances are minimal, if any.  i'm tired of googling; maybe you could post some recent articles showing 64 bit gains? at least one of those comparisons was using feisty, so fairly relevant here.

Best way is to install both and see for yourself which one works out better for you. Speed differences shall vary from program to program. So, check the programs you are going to use.

---

