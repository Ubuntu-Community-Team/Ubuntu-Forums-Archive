---
title: "Why the generic kernel?"
date: 2007-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Canada3332 on 2007-02-04
I was running Dapper on my Athlon64 3200+, and then I upgraded to Edgy. However, when I upgraded I lost V4L support. Apart from filing a bug report, no progress has been made, and webcam support continues to be broken. 

This leads me to my other question. Why have all the specialized kernels been replaced by some generic package? I know it was probably a lot of work to maintain all those specialized kernels, but I found them incredibly useful. I feel that the generic kernel is mostly to blame for my webcam problems, and would like to know if there are any repos where I can get a K8 specialized kernel. Thanks.

Athlon64 3200+
Biostar TForce6100-939 (NForce 6100/410)
2GB Corsair TWINX DDR466
NVidia 7900GTX
Ubuntu Edgy 6.10 (x64)

Sorry if this has been asked before. If it has, please redirect me to any previous threads

---

### Post by Kilz on 2007-02-04
> **Canada3332 said:**
> I was running Dapper on my Athlon64 3200+, and then I upgraded to Edgy. However, when I upgraded I lost V4L support. Apart from filing a bug report, no progress has been made, and webcam support continues to be broken. 

This leads me to my other question. Why have all the specialized kernels been replaced by some generic package? **I know it was probably a lot of work to maintain all those specialized kernels**, but I found them incredibly useful. I feel that the generic kernel is mostly to blame for my webcam problems, and would like to know if there are any repos where I can get a K8 specialized kernel. Thanks.

Athlon64 3200+
Biostar TForce6100-939 (NForce 6100/410)
2GB Corsair TWINX DDR466
NVidia 7900GTX
Ubuntu Edgy 6.10 (x64)

Sorry if this has been asked before. If it has, please redirect me to any previous threads

You answered your own question. It is work to maintain the extra kernels. You could try and [compile a kernel yourself]("https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29") but it isnt the easiest thing to do.
Welcome to the world of "The newest thing is broke, why didn't I just keep Dapper"

---

### Post by Canada3332 on 2007-02-04
> **Kilz said:**
> You answered your own question. It is work to maintain the extra kernels. You could try and [compile a kernel yourself]("https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29") but it isnt the easiest thing to do.
Welcome to the world of "The newest thing is broke, why didn't I just keep Dapper"

I've compiled kernels before. The only thing I don't like about compiling kernels is that I have to recompile the NVidia sound/network/video drivers every time I switch between kernels. That is the only thing really holding me back from compiling my own.

And Dapper was nice, but it didn't run Azureus or E17. Then again, Edgy doesn't run Azureus either...

---

### Post by Ocxic on 2007-02-04
the reson for the generic kerenel is to wrap all of the sperate kernels into one, this saves time for the developers and also ends the  "What kernel should i use?" question, I think it's much better and less confuzing for ppl this way, and so far I haven't had any problewms.

and yes Edgy runs azureus, I'm using it right now, make sure ytou have sun java installed, and that you run "sudo update-alernatives --config java" and make sure sun is being used

---

### Post by cmost on 2007-02-04
It's also possible to use Feisty's kernel on Edgy.  See this post for details:

[http://ubuntuforums.org/showthread.php?t=333808](http://ubuntuforums.org/showthread.php?t=333808)

---

### Post by Kilz on 2007-02-04
> **cmost said:**
> It's also possible to use Feisty's kernel on Edgy.  See this post for details:

[http://ubuntuforums.org/showthread.php?t=333808](http://ubuntuforums.org/showthread.php?t=333808)

LOL ya the Feisty **generic** kernel. :)

> **Ocxic said:**
> the reson for the generic kerenel is to wrap all of the sperate kernels into one, this saves time for the developers and also ends the  "What kernel should i use?" question, I think it's much better and less confuzing for ppl this way, and so far I haven't had any problewms.

and yes Edgy runs azureus, I'm using it right now, make sure ytou have sun java installed, and that you run "sudo update-alernatives --config java" and make sure sun is being used

Saving time for the developers, why dont we let them have a vacation? To me this is the weakest part of the argument. The Ubuntu developers are taking a already done distribution (Debian) and add eye candy IMHO. Anything someone asks why something is changed or not ready, its always its to hard on the developers. Maybe they need a vacation, or a hours of meditation.
As for the what kernel should I use, that isnt that hard a question to answer. I think we are dumbing down ubuntu if we take away different kernels for the sake of ending confusion. That you may not have problems isnt the issue, the different kernels were optimized to different processors. What that does is takes away performance.

---

### Post by RAOF on 2007-02-04
> **Kilz said:**
> ...
That you may not have problems isnt the issue, the different kernels were optimized to different processors. What that does is takes away performance.

When they were discussing whether or not to change from processor-specific to -generic kernels (on the ubuntu-devel list), one of the things they were concerned about was performance.  However, the benchmarks of -k8, -k7, -686 etc versus -generic didn't show any real performance difference.

The -generic kernel will **not** be the cause of any problems.  It's exactly the same code.  The only way something could work in a -K8 kernel and not in a -generic kernel is because of a GCC bug.  And even then, it'd be more likely to work in the -generic and not in the -K8.

---

### Post by Kilz on 2007-02-04
> **RAOF said:**
> When they were discussing whether or not to change from processor-specific to -generic kernels (on the ubuntu-devel list), one of the things they were concerned about was performance.  However, the benchmarks of -k8, -k7, -686 etc versus -generic didn't show any real performance difference.

The -generic kernel will **not** be the cause of any problems.  It's exactly the same code.  The only way something could work in a -K8 kernel and not in a -generic kernel is because of a GCC bug.  And even then, it'd be more likely to work in the -generic and not in the -K8.

Where can we find these benchmarks?

---

### Post by RAOF on 2007-02-04
> **Kilz said:**
> Where can we find these benchmarks?

On the ubuntu-devel list, from memory.  [https://lists.ubuntu.com/archives/ubuntu-devel/](https://lists.ubuntu.com/archives/ubuntu-devel/).  Sadly, I can't remember when, but google might show it up.

---

### Post by Kilz on 2007-02-04
> **RAOF said:**
> On the ubuntu-devel list, from memory.  [https://lists.ubuntu.com/archives/ubuntu-devel/](https://lists.ubuntu.com/archives/ubuntu-devel/).  Sadly, I can't remember when, but google might show it up.

So it was the developers benchmarks? Not a 3rd party with no interest in the outcome?

---

### Post by Canada3332 on 2007-02-04
> **Ocxic said:**
> the reson for the generic kerenel is to wrap all of the sperate kernels into one, this saves time for the developers and also ends the  "What kernel should i use?" question, I think it's much better and less confuzing for ppl this way, and so far I haven't had any problewms.

and yes Edgy runs azureus, I'm using it right now, make sure ytou have sun java installed, and that you run "sudo update-alernatives --config java" and make sure sun is being used

No, Azureus didn't work, until I ran my update today. This means that for the month that I've been running Edgy, Azureus hasn't worked. This stuff about "The devs are adding eye candy..." that's total bull. If they have enough time to work on eye candy, they certainly have enough time to work on kernel bugs and broken dependencies. I don't buy that excuse at all. Dapper is **how** old, and Azureus STILL doesn't work. If Feisty isn't really good, I'm going back to Fedora. At least the guys there know how to make an OS that works.

---

### Post by Kilz on 2007-02-04
> **Canada3332 said:**
> No, Azureus didn't work, until I ran my update today. This means that for the month that I've been running Edgy, Azureus hasn't worked. This stuff about "The devs are adding eye candy..." that's total bull. If they have enough time to work on eye candy, they certainly have enough time to work on kernel bugs and broken dependencies. I don't buy that excuse at all. Dapper is **how** old, and Azureus STILL doesn't work. If Feisty isn't really good, I'm going back to Fedora. At least the guys there know how to make an OS that works.

Azureus is a 3rd party application. You cant blame the Ubuntu developers if it doesnt work for you.

---

### Post by cmost on 2007-02-04
"LOL ya the Feisty generic kernel. "

Umm, did I indicate in any way that it wasn't a generic kernel? I am only pointing out that it can be used (it's a more recent kernel than that present in Dapper or Edgy) and might solve the other posters problem.

---

### Post by RAOF on 2007-02-04
> **Kilz said:**
> So it was the developers benchmarks? Not a 3rd party with no interest in the outcome?

I don't think it was a dev who posted it.  The devs asked for benchmarks to justify keeping the proc-specific kernels, and someone provided them.  And they didn't support proc-specific kernels :).

Also, on this very forum there are kernel-interactivity benchmarks for -generic, -386, -686, and -*-smp.  The only difference found was that the -*-smp kernels had *slightly* better interactivity.

---

### Post by russell.h on 2007-02-04
The third result of the first google search I tried seems to have returned what you are looking for:

The actual discussion (and a link to the benchmark results):
[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)

And a direct link to the benchmark results:
[https://lists.ubuntu.com/archives/ubuntu-devel/attachments/20060814/82176505/attachment-0001.eml](https://lists.ubuntu.com/archives/ubuntu-devel/attachments/20060814/82176505/attachment-0001.eml)

The benchmark is open source so you can try it if you really suspect the developers rigged it (yes, I find that hard to believe).

And if you really want an optomized kernel, then instead of demanding that someone make you one, I don't see why you don't just compile one for yourself, since you clearly believe time to be of little value (or is that just the developers time?).

---

### Post by BIGtrouble77 on 2007-02-04
I'm confused, I'm running Dapper and Azureus works.  I have one issue with it tho... The little notice popup by the bottom right side of the gnome panel gets stuck.  I just turned it off and things seem to work fine now.  I installed it through Automatix2.  BTW, I much prefer Ktorrent.

---

### Post by russell.h on 2007-02-04
Apparently the Azureus in the repos is broken (the icon thing mostly, it still "works"). I got a different one from somewhere and it "worked fine" to the extent that Azureus ever works fine - which was why I got rid of it completely. I too much prefer KTorrent.

But yeah, Azureus worked "out of the box" on my computer, except for that issue, which had nothing to do with Ubuntu.

---

### Post by rsambuca on 2007-02-05
> **Kilz said:**
> LOL ya the Feisty **generic** kernel. :)
Saving time for the developers, why dont we let them have a vacation? To me this is the weakest part of the argument. The Ubuntu developers are taking a already done distribution (Debian) and add eye candy IMHO. Anything someone asks why something is changed or not ready, its always its to hard on the developers. Maybe they need a vacation, or a hours of meditation.
As for the what kernel should I use, that isnt that hard a question to answer. I think we are dumbing down ubuntu if we take away different kernels for the sake of ending confusion. That you may not have problems isnt the issue, the different kernels were optimized to different processors. What that does is takes away performance.

Kilz - I'm starting to think that perhaps gentoo or linux from scratch might be better suited to your specific needs.  ubuntu uses the linux kernel, but the developers have done specific things to make the distribution easier to use out of the box for non-hardcore linux users and windows converts.  That is what the developers have decided from day 1.  You can always still compile your own kernel if you wish, but to constantly criticize the developers for doing these things just because they do not agree with your own personal philosophy is illogical.

---

### Post by Kilz on 2007-02-05
> **rsambuca said:**
> Kilz - I'm starting to think that perhaps gentoo or linux from scratch might be better suited to your specific needs.  ubuntu uses the linux kernel, but the developers have done specific things to make the distribution easier to use out of the box for non-hardcore linux users and windows converts.  That is what the developers have decided from day 1.  You can always still compile your own kernel if you wish, but to constantly criticize the developers for doing these things just because they do not agree with your own personal philosophy is illogical.

I would like to try gentoo, but the constant recompiling of everything sounds crazy. Thats why Im using a binary distro. I dont think linux from scratch sounds appealing. Yes I know Ubuntu is targeted at newbies. But shock upon shock I have only been using linux for about a year. When I installed Dapper (which I still run) I had only tried suse for a month
Are you suggesting that the developers are above question, that we should just worship them and never say anything that might upset them?

---

### Post by Kilz on 2007-02-05
> **russell.h said:**
> 
And if you really want an optomized kernel, then instead of demanding that someone make you one, I don't see why you don't just compile one for yourself, since you clearly believe time to be of little value (or is that just the developers time?).

I never demanded a kernel, stop putting words in my mouth.

---

### Post by rsambuca on 2007-02-05
Yeah, sorry Kilz, I never meant to put words in your mouth.  

Regarding the prior statement, I agree that it is always good to question the developers to keep them on their toes, so to speak.  It does seem, however, that you want the benefit of having binaries and doing no compiling, but you want the the binaries specifically written for YOU.  It obviously doesn't work that way.  You will just never have a perfectly optimized rig unless you do some of the compiling yourself.  Just my two cents (Canadian).

---

### Post by Kilz on 2007-02-05
> **rsambuca said:**
> Yeah, sorry Kilz, I never meant to put words in your mouth.  

Regarding the prior statement, I agree that it is always good to question the developers to keep them on their toes, so to speak.  It does seem, however, that you want the benefit of having binaries and doing no compiling, but you want the the binaries specifically written for YOU.  It obviously doesn't work that way.  You will just never have a perfectly optimized rig unless you do some of the compiling yourself.  Just my two cents (Canadian).

No, what I think is that whats available, should keep being available. The K8 kernel I use on Dapper isnt available on Edgy, not that I will ever use Edgy. One of the reasons people use the AMD64 version is for performance. Even a little bit is nice
I think you also have a flaw in the logic that I dont do compiling. A lot of my setup is customized by me. There are things that are not in Ubuntu repositories that I like. Thats one of the major reason Im not upgrading. 
I have also in the past tried to make available things the developers refused to do. Maybe thats why I have no respect for them.

---

### Post by rsambuca on 2007-02-05
> No, what I think is that whats available, should keep being available  I don't agree here.  From a business standpoint, if it is untenable to continue with a specific aspect of their product, then it has to go.  I'm sorry that is an inconvenience to you.
> I have also in the past tried to make available things the developers refused to do.That is one of the greatest things about the linux community, of which you are a welcome part!
> Maybe thats why I have no respect for them.
Well, there are hundreds of other distros available.  I'm sure some of them have developers that you will come to respect.

---

### Post by Canada3332 on 2007-02-05
> **Kilz said:**
> Azureus is a 3rd party application. You cant blame the Ubuntu developers if it doesnt work for you.

I can blame the devs, and I do. See, it was Azureus that was broken, it was the Java package in the repo that wouldn't install. To say that I didn't like Dapper is taking it a bit far. It was a nice OS, and after leaving the compile-everything mentality of Mandriva, it was a welcome change. You might be saying, 'Wait a sec, Mandriva is a binary OS' and you'd be right. But, since my computer comes with Genuine NVidia parts, I had to recompile my kernel and NVidia drivers whenever I changed kernel or driver versions. That gets old fast, **real** fast. It's nice what the devs do, but since I'm on a single core machine, which wasn't the fastest to begin with, every single mili-second faster it is, the more time I save.

---

### Post by BIGtrouble77 on 2007-02-05
I have configured a few Gentoo systems... The major problem (for me) is not the compile time.  It's keeping the damn thing updated.  When you update programs, keeping the config files current is a real pain in the *** because you constantly run the risk of breaking something.  Binary distros don't seem to have that problem. I'm not an Uber Gentoo expert so the updates have been problematic for me.

The Gentoo Gen kernel really kicks ***.   Very easy to recompile.

---

### Post by Lil_Eagle on 2007-02-06
Kliz:  If the kernel issue bothers you, you're welcome to recompile your own, as described [here]("https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29").

However, that site says specifically:> Building and using a custom kernel will make it very difficult to get support for your system. You will not be allowed to file bugs on the custom-built kernel (if you do, they will be Rejected without explanation).

If you have a commercial support contract with Ubuntu/Canonical, this will void such support.

Which may dissuade you from doing so.  

Gentoo on the other hand, ecourages you to build your own, and gives detailed instructions in their guide on how to do it.  One thing to note about Gentoo, is that it does take a long time to install and configure, but once that is done, you have a system built specifically for your machine and to your tastes in software.

If on the other hand, you want a Gentoo base that is already working, then perhaps Sabayon Linux is a good start.  Sabayon comes as a Live-DVD that can install.  The install procedure basically justs copies the DVD to the HD.  It sort of defeats the purpose of Gentoo by doing that, but it gets you a Gentoo system that works in a few minutes instead of a few days.

Another thing to note is that all the compiling that Gentoo does, can be done in the background so you don't have to dedicate your system to it.  You can still use your computer while it's compiling.

My next project is to be installing Gentoo the hard way.  Why?  Because if I can do that, I will learn a great deal about how it works.  The Gentoo documentation is first-rate.

I'm going to be using their alternate install method, chrooting from Kubuntu to install it onto a partition I have reserved.  I'll just skip the last step that installs grub and use my own.

I was tempted to try Linux from Scratch, but I don't want to spend half my time hunting down dependancies.

---

### Post by Jorge on 2007-03-27
> **Canada3332 said:**
> No, Azureus didn't work, until I ran my update today. This means that for the month that I've been running Edgy, Azureus hasn't worked.

Maybe this thread helps, months ago the Azureus issue was discuss and, I think, solved:

[http://ubuntuforums.org/showthread.php?t=219369&page=3](http://ubuntuforums.org/showthread.php?t=219369&page=3)

Hopefully, it will work for you.

---

### Post by CptPicard on 2007-04-12
Actually if you look at how modern processors work, the argument for having a zillion different kernels is getting weaker and weaker every day. Although they externally all (well, the usual PC ones) implement the x86 spec, what they do under the hood is actually something really different, as they optimize the execution of their own micro-instructions that has little to do with the x86 machine code the compiler produces. This is a Good Thing from code portability standpoint.

In particular for your general desktop applications, I would bet quite a lot that the performance difference just isn't there to a degree you'd notice. If you're doing some kind of scientific computing that would require the speed of some special instructions on some weird processor, I could see the point for compiling some specific arch. But for regular use, it's all in the head, and that's one of the reasons why I switched away from Gentoo.

In a few years' time we'll be seeing more and more cores on a CPU, and by then the benefits from fine-tuned machine code will be even more marginal compared to the speed increases that can be gained from multithreading applications. That puts a greater burden on the coder, and that in turn can be relived by coding in higher-level languages, rising the abstraction level ever further away from the iron. I'm still waiting for that Java bytecode CPU... :)

---

### Post by cmost on 2007-04-12
> **Canada3332 said:**
> I've compiled kernels before. The only thing I don't like about compiling kernels is that I have to recompile the NVidia sound/network/video drivers every time I switch between kernels. That is the only thing really holding me back from compiling my own.

And Dapper was nice, but it didn't run Azureus or E17. Then again, Edgy doesn't run Azureus either...

I'm running Azureus in Edgy and it works just fine.  For that matter, I had it running in Dapper as well.  Do you have Java installed properly?  Just curious.

---

