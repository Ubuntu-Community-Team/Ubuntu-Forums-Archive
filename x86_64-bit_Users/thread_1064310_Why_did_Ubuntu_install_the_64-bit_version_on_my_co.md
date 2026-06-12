---
title: "Why did Ubuntu install the 64-bit version on my computer?"
date: 2009-02-08
forum: x86 64-bit Users
---

### Post by racie on 2009-02-08
I installed Ubuntu 8.10 through Wubi and found out that a lot of the things I was trying to do didn't work because I have the 64-bit version of Ubuntu.  Now, my question is... why did Wubi install the 64-bit version onto my computer?  I have a relatively new Vista laptop and right now I'm dual booting it with Ubuntu.  Kind of a silly question, but I'm full of questions right now.  =P

---

### Post by movieman on 2009-02-08
> **racie said:**
> Now, my question is... why did Wubi install the 64-bit version onto my computer?

Because it has a 64-bit CPU?

What doesn't work on your system? All my Linux boxes are 64-bit and now that Adobe have released a 64-bit Flash there's nothing I do that doesn't work on them.

---

### Post by cjazz on 2009-02-08
This is from the Wubi site faq:


Why is the AMD64 version of Ubuntu getting downloaded and installed?

You probably have a 64 bit machine, the 64AMD installation is appropriate for all 64 bit architectures whether AMD or Intel.


Can I force Wubi to download and install a 32 bit version of Ubuntu?

Yes, either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument.

---

### Post by jocko on 2009-02-09
> **racie said:**
> ...a lot of the things I was trying to do didn't work because I have the 64-bit version of Ubuntu.
What doesn't work? Is it worth crippling your cpu by installing a 32 bit os?
64 bit ubuntu has no problem running 32 bit applications, you just need to make sure you have 32 bit versions of the libraries the application depends on.
Have you installed the package ia32-libs? It will take care of some basic 32 bit libs.
[This]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") may also be helpful if you need more.

---

### Post by jespdj on 2009-02-09
> **racie said:**
> ... and found out that a lot of the things I was trying to do didn't work because I have the 64-bit version of Ubuntu.
Really? How do you *know* that "a lot of the things" you were trying don't work because you are using 64-bit Ubuntu?

64-bit Ubuntu works just as well as 32-bit Ubuntu. Note that a lot of people often blame problems on the fact that they're running 64-bit Ubuntu, while they really have no idea what the real cause of their problems is.

Tell us exactly what problems you've encountered and we'll help you to solve them. It's most likely that running the 64-bit version is not the cause of your problems, even though you think so.

---

### Post by bford16 on 2009-02-09
> **jespdj said:**
> Really? How do you *know* that "a lot of the things" you were trying don't work because you are using 64-bit Ubuntu?...It's most likely that running the 64-bit version is not the cause of your problems, even though you think so.
Hear, hear!! I use 32-bit ubuntu 8.10 (xubuntu) on one machine and 64-bit on another.  The only difference in usability is Flash, which tends to act up on the 64-bit machine.  (I haven't installed the 64-bit Flash, which was still in Alpha, last time I checkec.)

---

### Post by jespdj on 2009-02-09
Flash works fine on my 64-bit Ubuntu 8.04 machine. If you install the package **flashplugin-nonfree**, you'll get 32-bit Flash with a wrapper (nspluginwrapper) to make it work inside 64-bit Firefox. There's also a beta version of 64-bit Flash available.

I've never had any problems with Flash on my 64-bit Ubuntu machine.

---

### Post by racie on 2009-02-09
Okay, okay, I don't need flaming, I'm just a newbie.  >.<

Aren't 64-bit machines older machines than 32-bit ones, or does it not work that way?  I have no knowledge of any of this.  =P

---

### Post by kjb34 on 2009-02-09
64 bit machines are more recent than 32 bit machines

---

### Post by howefield on 2009-02-09
> **racie said:**
> Okay, okay, I don't need flaming, I'm just a newbie.  >.<

Don't worry about it :):)

There are a few subjects in the forum that bring out the "best" in people, you know, things like Linux vs Windows, KDE vs Gnome, 32 bit vs 64 bit ect,ect.....

---

### Post by shane4stef on 2009-02-09
Try looking for kilz...he has script for Flash and Java. Just a few clicks and everything should work fine. If you have problems with these he will guide you in the right direction.:guitar:

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by racie on 2009-02-09
> **kjb34]64 bit machines are more recent than 32 bit machines[/QUOTE]
Oh, I had it backwards.  lol

[QUOTE=howefield said:**
> Don't worry about it :):)

There are a few subjects in the forum that bring out the "best" in people, you know, things like Linux vs Windows, KDE vs Gnome, 32 bit vs 64 bit ect,ect.....

Haha yeah.

Oh, and thanks for the link, shane4stef.

---

### Post by steveneddy on 2009-02-10
I run 64 bit and the Flash 10 64 bit version for Linux runs great on my machine.

You're using Wubi?

Dude, just partition and install. It's what all the cool kids are doing.

---

### Post by racie on 2009-02-10
me am to dum two yoose partitioning stuffz =P

---

### Post by PGHammer on 2009-02-17
> **movieman said:**
> Because it has a 64-bit CPU?

What doesn't work on your system? All my Linux boxes are 64-bit and now that Adobe have released a 64-bit Flash there's nothing I do that doesn't work on them.

True!

I have both the 64-bit Java and 64-bit Flash installed on the Intrepid 64-bit side of "Mighty Mouse V2.0" (dual-boot of Vista Ultimate 64-bit and 8.10 64-bit).  Now if they could create 64-bit version of Java and Flash plug-ins for Windows, I'd finally be a Happier Camper.

(All of my hardware is supported in 64-bit Windows and Linux today.   For the most part, performance is as good or better in 64-bit compared to 32-bit.  (What performance loss there has been is confined to less than five applications, and the loss even in those five is minimal; the five applications in question are all 32-bit and have no 64-bit equivalents for now.) Having less than 4 GB of RAM (I have a grand total of 1 GB in my system due to a DIMM socket issue with the motherboard itself, so it's not software) has been a non-issue.  The fact that it largely isn't an issue makes me wonder why I continue to hear the "don't upgrade/crossgrade to 64-bit [insert OS here] unless you have 4 GB or more of RAM" mantra at all.  All the research I've done (most of it has been hands-on, as opposed to relying on the word of others) has thoroughly flown in the face of that accepted argument.  The question (as long as your computer's CPU supports 64-bit, as well as the rest of the hardware) should no longer be "why 64-bit" but "Why NOT 64-bit?", and especially if you have 4 GB or less.)

---

### Post by jocko on 2009-02-18
> **PGHammer said:**
> Having less than 4 GB of RAM (I have a grand total of 1 GB in my system due to a DIMM socket issue with the motherboard itself, so it's not software) has been a non-issue.  The fact that it largely isn't an issue makes me wonder why I continue to hear the "don't upgrade/crossgrade to 64-bit [insert OS here] unless you have 4 GB or more of RAM" mantra at all.

Some people seem to think "64 bit *can handle* more ram" means "64 bit *must have* more ram", or even that it means that the ability to handle more ram is the *only* benefit with 64 bit.
A 64 bit os will use a *little* bit more ram than a 32 bit os (as 64 bit instructions are larger than 32 bit), but the only situation where that would make a 32 bit os perform better than a 64 bit os is when the amount of ram is so low that ram space is the bottleneck for the entire system (which mean 64 bit would run out of ram and start swapping a little bit sooner than 32 bit). As long as you have enough ram space for whatever you are doing with your computer, 64 bit will perform better than 32 bit.

---

### Post by crjackson on 2009-02-18
> **racie said:**
> me am to dum two yoose partitioning stuffz =P

**_I agree completely!_**

;) - Sorry, couldn't resist! Just kidding...

---

### Post by stchman on 2009-02-20
Flash 10 64bit alpha runs very well on 64 bit Ubuntu.

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

As for Java, I used the Icedtea plugin.  Works fairly well.

---

### Post by dcstar on 2009-02-21
> **jespdj said:**
> Really? How do you *know* that "a lot of the things" you were trying don't work because you are using 64-bit Ubuntu?
.......

And we are still waiting for an answer to that ridiculous statement.

---

