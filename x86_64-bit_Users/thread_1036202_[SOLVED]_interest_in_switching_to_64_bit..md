---
title: "[SOLVED] interest in switching to 64 bit."
date: 2009-01-10
forum: x86 64-bit Users
---

### Post by banana jama on 2009-01-10
i been using the 32 bit version of ubunutu but have always wanted to switch to 64 bit but never did because i heard there was problems. i want to know from 64 bit users if:
          1) there is a noticable difference in boot time,speed and performance between 32 and 64.
          2) any problems with 64 bit os such as with nvidia or any other drivers.
          3) also my  laptop uses a artheros ar5007eg wifi does anyone out there also uses this wifi modelue and if so does the 64 bit version work with it (if you had to do something to get it to work please write what you did)
          4) can software that was made for a 32 bit work on a 64 bit.

thanks in advance,
                   newbie

o yeah im using a laptop with a 2.0 ghz amd turion 64x2, 2 gb of memory and 250 gig hard drive.

---

### Post by VastOne on 2009-01-10
> **banana jama said:**
> i been using the 32 bit version of ubunutu but have always wanted to switch to 64 bit but never did because i heard there was problems. i want to know from 64 bit users if:
          1) there is a noticable difference in boot time,speed and performance between 32 and 64.
          2) any problems with 64 bit os such as with nvidia or any other drivers.
          3) also my  laptop uses a artheros ar5007eg wifi does anyone out there also uses this wifi modelue and if so does the 64 bit version work with it (if you had to do something to get it to work please write what you did)
          4) can software that was made for a 32 bit work on a 64 bit.

thanks in advance,
                   newbie

o yeah im using a laptop with a 2.0 ghz amd turion 64x2, 2 gb of memory and 250 gig hard drive.

Have only ever used 64 bit with Heron and now Intrepid...

Never ever had a single issue and have yet to find anything I cannot run.

Flash was an issue and you had to use several other things, but now there is an Alfa 64 bit libflashso from adobe that works flawlessly.  Once you install to 64bit, just search this forum for 64 bit flash and you will find the link and instructions for install.

Edit The 64 bit Alpha Flash is now a sticky at the top of this very forum....

Good luck... It is my opinion that the 64 bit "issues" are old and/or FUD related...

VastOne

---

### Post by sleepyjon on 2009-01-10
I've been running 64 bit since Gutsy. The only problem I've ever had has been with flash, and with the 64bit alpha I haven't had a single problem since.

32 bit software will work in 64 bit.

---

### Post by 73ckn797 on 2009-01-10
> **banana jama said:**
> i been using the 32 bit version of ubunutu but have always wanted to switch to 64 bit but never did because i heard there was problems. i want to know from 64 bit users if:
          1) there is a noticable difference in boot time,speed and performance between 32 and 64.
          2) any problems with 64 bit os such as with nvidia or any other drivers.
          3) also my  laptop uses a artheros ar5007eg wifi does anyone out there also uses this wifi modelue and if so does the 64 bit version work with it (if you had to do something to get it to work please write what you did)
          4) can software that was made for a 32 bit work on a 64 bit.

thanks in advance,
                   newbie

o yeah im using a laptop with a 2.0 ghz amd turion 64x2, 2 gb of memory and 250 gig hard drive.

See specs in signature. 

I am currently running 8.10 32 & 64 bit on the desktop on 2 separate 160Gib drives. Cannot run on laptop, not 64bit.

Switching back and forth for the typical stuff I use my computer for, I find that the 32bit seems a little more quicker opening programs and generally in all other aspects. I have not timed it but it is noticeable.

I assume that the differences are due to how memory is used from what I have read prior to my trying it out. The 32bit sees 3.3Gib of 4Gib and the 64bit sees 3.9Gib. I have not decided whether I will use 64 regularly but do like the performance. I was holding out until Flash was available and now that it is I can do what I need for work.

For me, having a 64bit mobo, I want to utilize the full performance available. That may only be a mental thing and I have plenty of mental things to deal with...:guitar:

---

### Post by jespdj on 2009-01-10
> **banana jama said:**
> 1) there is a noticable difference in boot time,speed and performance between 32 and 64.
Don't expect to see a difference in boot time and there's no noticeable performance difference for most applications. For some applications that are processor-intensive (encoding or decoding audio or video, for example) there can be a significant speed boost (even 50% or more faster than 32-bit).
> 2) any problems with 64 bit os such as with nvidia or any other drivers.
Not anymore than the 32-bit version; there's a 64-bit version of the nVidia drivers.
> 3) also my  laptop uses a artheros ar5007eg wifi does anyone out there also uses this wifi modelue and if so does the 64 bit version work with it (if you had to do something to get it to work please write what you did)
I have no experience with that WiFi but if it works on 32-bit then there's no reason to think that it will be a problem on 64-bit.

> 4) can software that was made for a 32 bit work on a 64 bit.
Yes, 32-bit software also runs on 64-bit Ubuntu. But almost all software is available as 64-bit software. There might be a few proprietary programs that are 32-bit only (Skype and Google Earth for example), but you can install them on 64-bit, and you might need to install the necessary 32-bit libraries. (Skype and Google Earth can be installed from the [Medibuntu](http://www.medibuntu.org) repository, no need to do difficult things).

Read the sticky topics at the top of this forum, for example:
[Advantages and Disadvantages of 64bit. (Plus install Guides)](http://ubuntuforums.org/showthread.php?t=765428)
> **VastOne said:**
> Flash was an issue and you had to use several other things, but now there is an Alfa 64 bit libflashso from adobe that works flawlessly.  Once you install to 64bit, just search this forum for 64 bit flash and you will find the link and instructions for install.
Flash has never been an issue really; since Ubuntu 7.10 (Gutsy Gibbon) it was just as easy to install on 64-bit as it was on 32-bit, because Ubuntu would automatically install nspluginwrapper to make 32-bit Flash work on 64-bit Firefox.
```
sudo apt-get install flashplugin-nonfree
```
> **73ckn797 said:**
> I was holding out until Flash was available ...
That wasn't necessary, because it has been working on 64-bit for a long time.

---

### Post by banana jama on 2009-01-10
thanks this thread was very informative and i am going to partion my hard drive and place a 64 bit version of ubuntu with the hopes that it will replace my 32 bit.

---

### Post by nss0000 on 2009-01-10
BJ:

Even for a casual lusr x64HH is just about bullet-proof ... stuff just works even FLASH,  JAVA plugin and WINE.  

Entirely different territory than ... RedHat_6.

---

### Post by tuxxy on 2009-01-10
Switch to 64-bit you know you want too :P

---

### Post by Arup on 2009-01-10
On x64 Ubuntu since its inception, absolutely no issues and by Intrepidx64, everything thats on x32 is there on its repos as well. Point is why waste the x64 bandwidth of your CPU with x32 when there is a viable option. Everything works, you can install 4+GB of ram without any issues, its rock solid and faster than x32 when it comes to CPU intensive tasks like encoding etc.

---

### Post by 73ckn797 on 2009-01-11
> **jespdj said:**
> That wasn't necessary, because it has been working on 64-bit for a long time.


My error. Flash was working. I was having Java issues. Java would not work for the *Aurigma Image Uploader* that I needed for work purposes. Other than that Java worked. The latest Java solved the issue for me and I am running 64bit daily.

---

