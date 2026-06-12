---
title: "Ubunut 32 vs 64 bits - benchmarks"
date: 2006-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by artik on 2006-12-14
I case you still not sure what is better 32 or 64

There is an article that I have prepared that compares 32 vs 64 bit performance of wide range of software.

[http://art-blog.no-ip.info/files/amd64vsi386.pdf](http://art-blog.no-ip.info/files/amd64vsi386.pdf)
or
[http://art-blog.no-ip.info/files/amd64vsi386.odt](http://art-blog.no-ip.info/files/amd64vsi386.odt)

---

### Post by Sqwishy on 2006-12-14
wow that's pretty tight! :-D nice find

---

### Post by kleeman on 2006-12-14
Interesting read thanks for doing all that it is pretty useful. Any idea why the relative performance of 32bit and 64bit for apache  equalized as the number of concurrent requests increased?

The octave results are very interesting for me as a scientist.

---

### Post by tszanon on 2006-12-14
Wow...I was about to give up 64bit, but I think I should reconsider...
Thanks a lot! =D>

Hope this document is read by those who think that converting 32bit applications to 64bit isn't worth the effort!!![-o<

---

### Post by kleeman on 2006-12-14
Artik, could you provide some more specific information on the kernels you used? The generic ones from edgy? I assume that the i386 results reflect some optimization by the i386 generic kernel?

---

### Post by artik on 2006-12-15
> **kleeman said:**
> Artik, could you provide some more specific information on the kernels you used? The generic ones from edgy? I assume that the i386 results reflect some optimization by the i386 generic kernel?

Yes I had used default Ubuntu kernels and standard software packages.

However I think that kernel does not have huge effect in most of cases like multimedia, math, gaiming or CSS rendering because all of them much more CPU related then kernel. If it would effect then it should mostly effect applications like Apache that do lots of networking and IO and not programs like octave.

---

### Post by artik on 2006-12-15
> **kleeman said:**
> Any idea why the relative performance of 32bit and 64bit for apache  equalized as the number of concurrent requests increased?
Yes, I think it is some kind of top IO bound that could be done on the network (however I'm not sure). This looks like some kind of saturation level that can be reached is such case. However 64 bit apache gets much faster to its top performance level - or more effective even for low number of concurent requests. However this is only assumption.

> **kleeman said:**
> The octave results are very interesting for me as a scientist.
I assume same difference may be achived using 64 and 32 bit versions of matlab. But I do not have them so I used octave.

---

### Post by predaeus on 2006-12-15
good work, thank you!

---

### Post by jvc26 on 2006-12-15
wow thats really interesting stuff! Good work. :)

---

### Post by artik on 2006-12-18
Update:
Measurements of Blender were done.
Different details on measurements were added.

The documents are updated.

---

### Post by kmccoy on 2006-12-18
I read that they actually said the 64bit version used more memory and was slower than the 32 bit edition. (a different article)Hmmmmm now who do I believe?

This is from another forum....

"Well, I have three Linux versions running alongside on the same hardware, and one shared /home across them all... The 64-bit versions of Linux (my primary desktop is FC5 x86_64) does tend to eat twice the RAM of 32-bit. And, again, that makes sense. The size of the bits of data that go through the processor are twice as big. All the programs for FC5 x86_64 are usually 64-bit, which means that all of them process in 64-bit sizes of ints and floats and any other data type. This also means twice the RAM as the data flows from the CPU to memory and back. To put it simple:

Any 32-bit distro running the same on the desktop: GNOME session, Firefox, Thunderbird, Gkrellm three gDesklets and a couple dock apps (CPU speed monitor, network monitor) uses roughly 200-220Mb RAM. The same desktop running in 64-bit ranges from 350-410 Mb RAM. On fresh "boot" or login, my session is roughly 80Mb in the 32-bit systems, where as in 64-bit it starts at 256Mb pretty much all the time (some times it is 249).

This behavior has been pretty much the same with any other x86_64 distribution I have tried, but again, due to size of data types, this actually makes sense to me. The same goes for Windows XP 64-bit Edition, it uses twice the RAM as the 32-bit version on fresh boot."

---

### Post by kleeman on 2006-12-18
Nothing inconsistent here. Both are correct. 64bit apps use twice as much memory and some of them (particularly those which are cpu dominated rather than io dominated) are faster than the 32 bit equivalents.

---

### Post by superspak on 2006-12-19
wow, i had no idea, ill definately give ubuntu 64 bit a download now

---

### Post by RAOF on 2006-12-19
> **kleeman said:**
> ... 64bit apps use twice as much memory and some of them (particularly those which are cpu dominated rather than io dominated) are faster than the 32 bit equivalents.

Not totally correct.  
<tech-jargon>
Linux (IIRC) uses an LP64 setup - that means chars, shorts, and ints have the same storage as on 32bit systems (8, 16, and 32 bits respectively).  Only *long*s and pointers are bigger, each being 64bits.

As far as I'm aware, this doesn't change the size of floats or doubles at all, either.  They're still 32 & 64bits respectively.
</tech-jargon>

So, 64bit programs **will** take up more memory, but nowhere near twice as much.
[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit) for reference.

Edit:  Having read that, I am amazed that lame is not substantially faster under AMD64.  I recall a benchmark where lame was ~33% faster under AMD64 than i386.  I may test this myself :).

---

### Post by Gumpy on 2006-12-19
are these benchmarks comparing an i386 kernel to a k8 kernel? ](*,)

---

### Post by artik on 2006-12-19
> **kleeman said:**
> Nothing inconsistent here. Both are correct. 64bit apps use twice as much memory and some of them (particularly those which are cpu dominated rather than io dominated) are faster than the 32 bit equivalents.

Not exactly... Yes 64 bit app use more memory...
Clean load of live CD 139MB on 32 bit and 170 at 64.
Blender had used 410 MB in 64 bit mode and 300MB in 32 bit. But it is not "twice". More but not twice.

BTW good point to verify.

---

### Post by artik on 2006-12-19
> **Gumpy said:**
> are these benchmarks comparing an i386 kernel to a k8 kernel? ](*,)

Not exactly default Ubuntu 32bit kernel on livecd is i686 smp (uname -r). The architecture called i386 but default optimization of higher processors.

---

### Post by kleeman on 2006-12-19
> **artik said:**
> Not exactly... Yes 64 bit app use more memory...
Clean load of live CD 139MB on 32 bit and 170 at 64.
Blender had used 410 MB in 64 bit mode and 300MB in 32 bit. But it is not "twice". More but not twice.

BTW good point to verify.
Yeah theoretically twice as much. Fair enough. I compared firefox last night and it actually uses THREE times as much memory on 64bit compared with 32 bit for some reason. I did a standard identical open browser on two systems and got 16M on 32 bit and 45M on my 64 bit system.

---

### Post by RAOF on 2006-12-19
> **kleeman said:**
> Yeah theoretically twice as much. Fair enough. I compared firefox last night and it actually uses THREE times as much memory on 64bit compared with 32 bit for some reason. I did a standard identical open browser on two systems and got 16M on 32 bit and 45M on my 64 bit system.

I'll just chime in again with: Theoretically, **nowhere near twice as much**.  Most data types don't change size.

Those Firefox numbers will have to be explained by some other mechanism (such as: how were you measuring them?).  There's no way the same code built for x86-64 would use 3 times as much memory to do the same thing.  Which, of course, must mean that it's doing **different** things :p

---

### Post by tkjacobsen on 2006-12-19
First of all, one should not make speed tests from a live cd... The better speed of the 64-bit processor could reflect faster decompression from the livecd image... Second one should not use alpha versions of software and/or use different operating systems in same test - not the same kernel.. Is dapper 64 better than dapper 32 or is edgy 64 better than edgy 32???

Also the gain percentages are calculated wrong. If you have a gain greater than 100% you will  use negative time running the task... Time differences should be devided by the time on the i386 kernel not the x64 kernel...

But anyway nice with some benchmarks..

---

### Post by kleeman on 2006-12-19
> **RAOF said:**
> I'll just chime in again with: Theoretically, **nowhere near twice as much**.  Most data types don't change size.

Those Firefox numbers will have to be explained by some other mechanism (such as: how were you measuring them?).  There's no way the same code built for x86-64 would use 3 times as much memory to do the same thing.  Which, of course, must mean that it's doing **different** things :p
I used the gnome system monitor and the browsers were identical (i.e. same extensions and version). In addition they were viewing the identical web page. I agree with your theoretical argument but your explanation of differing measuring devices and/or browser doing different things is not true. I am as surprised as you.

---

### Post by artik on 2006-12-19
> **tkjacobsen said:**
> First of all, one should not make speed tests from a live cd... The better speed of the 64-bit processor could reflect faster decompression from the livecd image...
Not correct. The program were installed to unionfs systems and not come as part of livecd, more then that they are cached and loaded to memory. So the fact the program run from LiveCD may influence only the start time or access time to programs that come with the CD but not  the runtime of programs that are installed to unionfs.
More then that usage of LiveCD promise exact testing conditions - same software runs in same situations. 

> **tkjacobsen said:**
> Second one should not use alpha versions of software  The software is not alpha - Lame, oggenc and all other porgrams come in their stable versions.

> **tkjacobsen said:**
> different operating systems in same test - not the same kernel.. Is dapper 64 better than dapper 32 or is edgy 64 better than edgy 32???

Two version of system are used because of very simple reason - first tests were done much earlier. So I decided not to rerun them in order to get same results. More then that I do not compare Dapper 32 to Dapper 64. I compare the software run times.


> **tkjacobsen said:**
> 
Also the gain percentages are calculated wrong. If you have a gain greater than 100% you will  use negative time running the task... Time differences should be devided by the time on the i386 kernel not the x64 kernel...
First of all gain was calculated as following
100%*((32bit run time/64 bit run time)-1)
100%*((64bit FPS/32 bit FPS) - 1)

So in case of better performace on 64bit SW you get positive run time. if 32 bit software faster you get negative run time. Gain means 64bit architecture performace gain. I do not see any problems with these calculations. Correct me if I wrong.

> **tkjacobsen said:**
> But anyway nice with some benchmarks..
Thanks.

[LIST]
[*]These benchmarks are not "scientifically absolutly correct" or "performed in ideal lab conditions". However they are *good enough* for getting understanding of potential gains that 64bit architecture gives.
[*]These benchmarks do not compare operating systems but software that runs on them. I do not think there will be difference in runtime If I will run AviDemux on BSD/Solaris or Linux when it is compiled with same flags. I can assume that there might be a difference in such programs like Apache that do lot of multiprocessing and IO but not for programs like octave or oggenc. So the importance of kernel versions is not so high
[*]In comparison with most of benchmarks that are seen over the net that compare "FPU" speed, speed of gz or standart CPU benchmars, that are usualy used to measure performace of *same software* on *different CPUs*, I had tested *different sotware* on *same CPU*. So the standard tests that are used in HW tests not allways applicable.
[*]I didn't tested specific operations (like FPU speed) but I had taken typical tasks that  computers are used - multimedia, math, graphics, servers etc and compared the entry system speed - How much faster you can peform these taks if you use 64 bit system instead of 32bit.
[/LIST]

---

### Post by Popoi on 2006-12-20
Nice test! I just hope people pay more attention to x64 with plugins for Java, Flash and Windows Media Files Types ;)

---

