---
title: "[SOLVED] What's up with 64bit?"
date: 2008-10-26
forum: x86 64-bit Users
---

### Post by Andrew79 on 2008-10-26
Just a curious question. I am looking at getting a new computer, and want to know what is the differance between 32 and 64? I am learning most of my computer skills here on Ubuntu, and don't know maybe some of the basics. Also, is the a difference for Ubuntu on 32 vs. 64?

---

### Post by cariboo on 2008-10-27
The programs in 32 bit and 64bit are the same, the real difference is the amount of memory  each version can access the 32bit version can only access 3,2Gb. A 64bit system can assign up to 2^64byte --> 16 Exabyte.
 
I have run 64bit since Dapper and haven't run into any insurmountable problems. The support for java and flash has gotten better especially  in Intrepid, which will be out Next week. I found that on my computer 64bit runs a bit faster than it did with a 32bit insatallation.

Jim

---

### Post by Agent ME on 2008-10-27
64 bit is a little faster in case I remember right, noticeably on some tasks such as compiling, and utilizes the processor better. It's also needed to be able to use more than 4gb of ram.

But some (mainly proprietary) programs don't support 64-bit properly; flash and java are common problems for 64bit users, but I think flash support is pretty good now out-of-the-box due to a wrapper script of some sort. I think the most common problem with 64 bit is driver support - some odd devices may not be supported on 64 bit operating systems. Though on Linux, 32 bit isn't much better with driver support :P

I'd say try 64 bit, and see if you don't run into any bumps.

(I run 64 bit - my only problem is that occasionally I have to kill firefox and restart it due to something about flash messing up in order to get flash to work again. Certainly not a show-stopper for me, especially since firefox remembers what pages I had open.)

---

### Post by Sef on 2008-10-27
> But some (mainly proprietary) programs don't support 64-bit properly; flash and java are common problems for 64bit users....

As for Java, there is OpenJDK, and Java does have a 64-bit version now.  However, there is still no plugin yet.  For more info, read '[Java on 64-bit Systems]("http://ubuntuforums.org/showthread.php?t=774956")'.

---

### Post by BGFG on 2008-10-27
Check out the sticky at the top of the page by John.Michael.Kane it'll clear some 
things up for you.
I suggest you go 64. It's faster and support is steadily getting better.

---

### Post by felker2 on 2008-10-27
> **cariboo907 said:**
> The programs in 32 bit and 64bit are the same, the real difference is the amount of memory  each version can access the 32bit version can only access 3,2Gb. A 64bit system can assign up to 2^64byte --> 16 Exabyte.


I would say: programs in 32 bit and 64 bit are *not* the same; a program is compiled for 32 bit *or* 64 bit. You can check the bit-ness of a program with the "file" command. For example, apache2 on my 64-bit Ubuntu is 64-bit:

```
sander@ubuntu804:~$ file /usr/sbin/apache2
/usr/sbin/apache2: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
sander@ubuntu804:~$
```

And yes, with the correct 32-bit libraries you can run a 32-bit apps on a 64-bit OS. 

I've been running 64-bit since June 2007, and I've not experienced any serious problems.

---

### Post by Yellow Pasque on 2008-10-27
One other consideration that I'm not sure is addressed in the sticky is 64-bit wireless drivers. If your wireless card doesn't have a working native Linux driver, you may have to use a Windows driver with ndiswrapper. Using ndiswrapper with 64-bit Linux/Ubuntu requires drivers written for Windows XP-64. Not all wireless chipsets have this type of driver available.

---

### Post by cariboo on 2008-10-27
I really didn't mean that 32bit and 64bit programs were the same, it was just a general comment that the two versions  worked the same way. In other words when you're running a program you can't tell if it is 32bit or 64bit.

Jim

---

