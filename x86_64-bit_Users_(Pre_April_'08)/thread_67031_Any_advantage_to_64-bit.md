---
title: "Any advantage to 64-bit?"
date: 2005-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaz514 on 2005-09-19
Hey, I have an AMD64 CPU, I was wondering if there was any advantage to using the AMD64 version of Ubuntu over the i386 version. 64-bit seems to cause problems with installing stuff, shared libs, Flash, etc., but does it actually perform better than 32-bit or anything? (No, I don't have >2GB RAM) Or should I just use 32-bit for maximum support and compatibility? I'm kinda confused...

---

### Post by greenfrog on 2005-09-19
The only Linux 64 bit that I have found that is ready for prime time is SuSE 9.3,
but I don't find enough difference to use it full time.

---

### Post by tonym on 2005-09-19
The more that people use AMD64 and raise patches/suggestions/bugs the faster it will become as well supported as i386.

---

### Post by DancingSun on 2005-09-19
You can do a search on the web.  I did it once and found some performance studies on 64-bit applications.  The rough conclusions at the time of the studies (just when AMD64 retailed) were that in your day to day applications, you can get around 10% increase in performance, but also a performance penalty on some applications as well.  The applications that benefit the most from 64-bit are floating point intensive programs, like scientific applications, games .... etc., these applications can get around 40% performance increases.

---

### Post by mlomker on 2005-09-19
> should I just use 32-bit for maximum support and compatibility? I'm kinda confused...

Probably.  I just like to be different.  If you want life to be easier then stick to 32-bit.

---

### Post by gaz514 on 2005-09-19
[QUOTE=mlomker]Probably.  I just like to be different.  If you want life to be easier then stick to 32-bit.[/QUOTE]
 Alright, I've just decided to go with 32-bit for now, as you said, to make life easier.

---

### Post by acariquara on 2005-09-19
[QUOTE=gaz514]Alright, I've just decided to go with 32-bit for now, as you said, to make life easier.[/QUOTE]

Suit yourself. It's about choice anyway - just realize that when you are ready to go back to 64-bit, you already have what it takes.

Personally, I was an Ubuntu fan before joining the 64 bit army. Actually, I bought this processor/mobo combo just for experimenting with Ubuntu64. So far, so good...

---

### Post by wmcbrine on 2005-09-19
[QUOTE=gaz514]does it actually perform better than 32-bit or anything?[/quote]IMHO, yes, quite a bit.

> *(No, I don't have >2GB RAM)*Files over two or four gigs can also be easier to work with on a 64-bit system -- think mmap(). Even something as simple as "cmp" breaks on my old 32-bit Mandrake system when I try it on large files.

> *Or should I just use 32-bit for maximum support and compatibility?*I found the problems minimal, and nearly all were solved via chroot. The only thing I've found that absolutely won't run in this environment is DOSEmu.

---

### Post by gaz514 on 2005-09-23
What is this 'chroot' I keep hearing about? I'm relatively new to Linux so I don't know what it means, but I've heard about it being used to solve problems with 64-bit- Official Community & Forums

---

### Post by mlomker on 2005-09-23
[QUOTE=gaz514]What is this 'chroot' I keep hearing about? I'm relatively new to Linux so I don't know what it means, but I've heard about it being used to solve problems with 64-bit- Official Community & Forums[/QUOTE]

If you search you will find some how-to's.  Basically it is a way of installing a mini 32-bit copy of the operating system into your 64-bit system.  

That's actually how Windows works--there are 16-bit and DOS subsystems that allow older applications to work.  The difference is that you don't have to know or set anything up in Windows.

---

### Post by DeathOnJuice on 2005-09-24
[QUOTE=mlomker]If you search you will find some how-to's.  Basically it is a way of installing a mini 32-bit copy of the operating system into your 64-bit system.  

That's actually how Windows works--there are 16-bit and DOS subsystems that allow older applications to work.  The difference is that you don't have to know or set anything up in Windows.[/QUOTE]
 mlomker, could you please link me to one of these guides?

---

### Post by DancingSun on 2005-09-24
Just do a forums search on "chroot 32 bit howto".  We'd rather give you the fishing stick than the fish.

---

### Post by mlomker on 2005-09-24
Here's the fish:  [Wiki page.](https://wiki.ubuntu.com/DebootstrapChroot)

---

### Post by rasinesh on 2005-09-30
Hello to everyone 
i am a newbie and have been using 32 bit ubuntu(5.04 Hoary) for some time, i am using an AMD64 so thought of trying the 64 bit ubuntu and installed it. But the gdm doesnt start up in the 64 bit one, its starts(and crashes) thirce and gives an error log which which says that, "No Screens Found" :confused: but nothing of sort happens in the 32 bit one 
can anyone give me any solutions :( 
this is the first time i am posting to some forum so donno whether its the right section i am in or not 
have a nice day everyone

---

### Post by mlomker on 2005-09-30
Double-check your video card driver and try a different one (perhaps 'vesa').

**dpkg-reconfigure xserver-xorg** at the prompt.

---

### Post by rasinesh on 2005-10-01
Thnx for the reply
i have tried using the dpkg command and could not solve the problem :( ( of course a newbie :( :( ). i am thinking of replacing the "xorg.conf" file of the 64 bit os with that of the 32 bit one which works perfectly alright. 
the question now is Will it work ??
:confused: 
Thnq for ur attention again

---

