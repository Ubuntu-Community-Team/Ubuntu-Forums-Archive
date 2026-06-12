---
title: "gcc and 64bit"
date: 2008-08-01
forum: x86 64-bit Users
---

### Post by scamio on 2008-08-01
Hi guys!
I am buying a quite powerfull computer for scientific calculation which will have 8 Gig of Memory. For this reason I will have to install a 64 bit OS. 
What's the best 64 bit OS? I found Ubuntu 32bit great. Is it the same for the 64 bit version.
But the most important question I would like to ask you is the following. I am a programmer (let's say between a beginner and a medium level) and I use Geany to write software in C and gcc to compile. My question is: "is geany still going to work under a 64 bit OS? And, above all, what about gcc? If I compile a program with gcc under a 64 bit OS do I have to compile it again in order to make it work under a 32 bit OS.
Please forgive me if the question is silly, but I really never worked with 64bit OS.
Thanks in advance for your help

---

### Post by howlingmadhowie on 2008-08-01
1  geany will work.
2  gcc will compile for whatever target you tell it to.
2a i don't know what targets are available on the default gcc in ubuntu.
3  if you compile a program with a target of x86-64, it won't run on a standard x86

---

### Post by forger on 2008-08-01
If it's for scientific calculations, you're probably good to go with any operating system :)

You can run 32-bit software on 64-bit Ubuntu
```
sudo apt-get install util-linux ia32-libs ia32-libs-gtk
```

[http://packages.ubuntu.com/search?searchon=names&keywords=ia32](http://packages.ubuntu.com/search?searchon=names&keywords=ia32)
you can even install 32-bit deb packages on 64-bit ubuntu:
[http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/](http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/)

---

### Post by stchman on 2008-08-01
> **scamio said:**
> Hi guys!
I am buying a quite powerfull computer for scientific calculation which will have 8 Gig of Memory. For this reason I will have to install a 64 bit OS. 
What's the best 64 bit OS? I found Ubuntu 32bit great. Is it the same for the 64 bit version.
But the most important question I would like to ask you is the following. I am a programmer (let's say between a beginner and a medium level) and I use Geany to write software in C and gcc to compile. My question is: "is geany still going to work under a 64 bit OS? And, above all, what about gcc? If I compile a program with gcc under a 64 bit OS do I have to compile it again in order to make it work under a 32 bit OS.
Please forgive me if the question is silly, but I really never worked with 64bit OS.
Thanks in advance for your help

Yes, nearly everything that worked under 32 bit Ubuntu works under 64 bit.  I use Netbeans (in the repositories) and it works fine under 64 bit.

The only thing I have found that gives me a little bit of trouble under 64 bit is bluetooth.  I have tried 2 different adapters (new one is an IOGear GBU221P) and I still cannot sync my phone.  On 32 bit it worked very well.

Geany, Netbeans, and Eclipse all work under 64 bit.

To develop in Java you will need to install Icedtea(open Java).

You can also use Bluefish and Gedit for editing.

I don't know if there is an option to compile in 32 or 64 bit using gcc.  I imagine there is as you might want the executable file to run on 32 and 64 bit.

---

