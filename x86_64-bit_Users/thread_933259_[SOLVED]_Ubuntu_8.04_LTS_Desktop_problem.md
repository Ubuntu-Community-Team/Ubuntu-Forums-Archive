---
title: "[SOLVED] Ubuntu 8.04 LTS Desktop problem"
date: 2008-09-29
forum: x86 64-bit Users
---

### Post by demonchu on 2008-09-29
Hello fellas. I am sorry if I am writing this topic in the wrong place, but I am still newbie. I have one big problem with my Ubuntu - it is sucking all of my RAM. I have 2 GB of RAM and when I start the computer, the memory is used only 30%, after a few minutes 1 GB has passed, and after half an hour I have only at about 200-300 mb of free RAM. I am using Ubuntu 8.04 LTS Desktop i386 on AMD Athlon 64 4200+ am2 socket. I have 2 more GB swap partition but I didn`t really believed I will have to use it. Something is sucking my memory, but I cannot find out what is wrong. I searched in the "process dispatcher" and nothing was using more than 30 MB of ram. Some people say that compiz is cousing this problem, but it is not. I checked. Here I will show you some info:

[http://www.uploading.com/files/AMZIVL9P/test.txt.html](http://www.uploading.com/files/AMZIVL9P/test.txt.html)

and the picture I attached

Sorry if I posted this in wrong section, but I need some help.

---

### Post by raul_ on 2008-09-29
Most of that memory is cached. Basically, your used RAM is about 300 mb (the +/- buffers line).

The cached memory is used to optimize performace: speed up the use of programs, etc etc.

Linux's memory management is top notch ;)

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management")

> The reason Linux uses so much memory for disk cache is because the RAM is wasted if it isn't used. Keeping the cache means that if something needs the same data again, there's a good chance it will still be in the cache in memory. Fetching the information from there is around 1,000 times quicker than getting it from the hard disk. If it's not found in the cache, the hard disk needs to be read anyway, but in that case nothing has been lost in time.



---

### Post by demonchu on 2008-09-29
Oh, this is good. You helped me a lot. I thought there was something wrong. So this means that I`ve opened many programs and files and the memory is being used for them, and if I try to find something later it will be much easier and faster? Thanks a lot.

---

