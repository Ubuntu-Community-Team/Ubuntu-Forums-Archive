---
title: "32 bits applications performance"
date: 2007-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by c_pradelli on 2007-01-17
Hello,
I need to install a server (HP xeon 64bits) and I need to decide which version of ubuntu to install.
The problem is that some of my critical applications are 32 bits.
The performance of this applications will be better or worst on the 64 bits version?

---

### Post by phossal on 2007-01-17
I say stick with 32Bit. There is almost no downside. If you go with 64Bit, there is almost no advantage.

---

### Post by enopepsoo on 2007-01-17
I think there is an advantage!  The advantage is being super cool for using a 64 bit OS. :cool:

---

### Post by kuja on 2007-01-18
The 32-bit specific programs won't differ in performance **at all** on the 64-bit version.

---

### Post by phossal on 2007-01-18
> **kuja said:**
> The 32-bit specific programs won't differ in performance **at all** on the 64-bit version.

I think I know what you mean, but it isn't exactly true. I specifically use the 32-Bit JDK6 and 32-Bit eclipse on my AMD64. The performance *is* significantly different. It's quite *better* than the 64-Bit performance. This is true for a lot or programs.

---

### Post by c_pradelli on 2007-01-18
I don't understand, do you mean that 32-Bit JDK6 and 32-Bit eclipse are faster than 64-Bit JDK6 and 64-Bit eclipse on 64-Bit OS, or that 32-Bit JDK6 and 32-Bit eclipse are faster on 32-Bit OS than on 64-Bit OS?

---

### Post by phossal on 2007-01-18
I mean that the combination of the 32BIt packages is faster on all platforms than the comparatively slow combination of the 64Bit packages. I would not use the 64Bit packages on ANY platform. 

I would say that the cooperation of the 32Bit packages on my Ubuntu machine is *as fast* as a Windows install.

---

### Post by BIGtrouble77 on 2007-01-19
Phossal,
You're going to have to back up those statements with some proof.  I run a java based web application.  I talked to the developer of the web framework I use and he said he did some benchmarking and the 64bit build is a HUGE improvement.  So he strongly suggested going with a 64bit distro.

Now for c_pradelli I think I'd suggest going the 32bit root if he has mission critical apps that only have 32bit builds.  You can get around a 30% performance improvement for some 64bit optimized apps, but he won't see any of that with his 32bit apps.  So it's not really worth the added aggrevation.  

Plus, Intel's 64bit implementation is inferior to AMD's so you may not see the same improvement.  You only start to see Intel break away with their Core2 processors.

---

### Post by phossal on 2007-01-19
I suggest gaining some practical experience before demanding proof *of me*. Advice with the caveat that it came from third party isn't exactly a boolean truth. When I say the performance of the 32Bit packages rivals Windows, I mean it in the sense that when I open eclipse, I don't want to slit my own wrists while waiting for it to load/open a window/save a change, etc. If you don't instantly notice it, fantastic. If I can see the performance difference in *minutes* on my watch, it's obvious enough to skip the benchmarking programs, right? 

I've downloaded the different combinations for different architectures and installed them more than 100 times. If you're having a better experience, fantastic. I would *not* use the 64Bit packages, and I've even switched back to 32Bit *Ubuntu* on my AMD64.

Now, at the end of asking me to provide you with some proof, you double back and suggest the 32Bit packages if he has "mission critical" apps? Perhaps you should stick to dishing out advice that is relevant to your experience, and not on what some *developer* told you. The odds are good that you simply misunderstood him, and, more likely, that you misunderstood me.

I would advise a third party who sees the posts from each of us to download the 32 AND 64 bit packages (for the JDK and eclipse respectively), and to install them in every possible combination. It doesn't take that long. In an hour, you'll be an expert. Or they can trust a dopey answer they heard from *a guy who heard from a guy who is a developer*.


And, for those of you who care, I install the packages this way: [Install JDK6, Tomcat6, and eclipse]("http://ubuntuforums.org/showthread.php?t=332674")


*Many of the mods run 64Bit platforms with 32Bit Ubuntu. It isn't an accident. 32Bit Ubuntu clearly *isn't* BIGtrouble.

---

### Post by c_pradelli on 2007-01-19
The real situation is:

I need to run a server to share files, serve Firebird databases and run an Application Server done in Kylix by me (the most important application).
I can get Firebird 64 bits, no problem here. But I can't build my application in 64-bits because kylix is only 32-bits.

My question is, what is the best OS version to use here?

If I use a 64-bits OS, I think I will get better performace with Firebird, but what about my Kylix application?, it will run slower than in a 32-bit OS or it will run at the same speed.

Thanks everybody for the help.

---

### Post by phossal on 2007-01-19
> **c_pradelli said:**
> My question is, what is the best OS version to use here?

Ask the mods. Many of them have 64Bit platforms and run 32Bit Ubuntu. There are still many dependencies, and many "better built" 32Bit packages. Back to my original blurb: there is no real disadvantage to running 32Bit Ubuntu, and no *advantage* to running 64. Good luck.

---

### Post by BIGtrouble77 on 2007-01-26
Argh, I should have kept up on this thread.

Phossal, chill dude.  I am a developer myself, but I'm not a java developer.  I use eclipse everyday for a java based web framework (xslt scripting) and for Ruby on Rails.  I have about 7 years of practical experience.  I also build custom enterprise level servers for mission critical web applications.  Is that sufficient?  BTW, My eclipse setup screams.  

Perhaps you haven't configured your system well?  The reason I consulted with this developer is because he has a wide variety of Java apps installed at Meryll Lynch in a finely tuned environment.  He's spent many hours benchmarking 64bit java vs. 32bit java. 
In the case of a server, a Java program on a 64-bit JVM will probably perform better over a long period of time, but startup will be a little longer.  My startup times are not bad at all, eclipse is swift and my apps compile and load quickly.  Because c_pradelli wanted a server setup, 64bit java may be appropriate but a 32 bit distro may also be better simply because of the kylix app he's using.  In other words, he shouldn't avoid using a 64bit distro because he wants to use java.

I highly recommend not installing eclipse or java (blackdown or sun) from the repos.  I find it brutally slow.  Maybe that's where you're having issues.  I've got a custom setup for both eclipse and java which has resulted in a much faster environment- even faster than my old win setup.

---

### Post by phossal on 2007-01-26
> **BIGtrouble77 said:**
> Argh, I should have kept up on this thread.

Phossal, chill dude.  I am a developer myself, but I'm not a java developer.  I use eclipse everyday for a java based web framework (xslt scripting) and for Ruby on Rails.  I have about 7 years of practical experience.  I also build custom enterprise level servers for mission critical web applications.  Is that sufficient?  BTW, My eclipse setup screams.  

Perhaps you haven't configured your system well?  The reason I consulted with this developer is because he has a wide variety of Java apps installed at Meryll Lynch in a finely tuned environment.  He's spent many hours benchmarking 64bit java vs. 32bit java. 
In the case of a server, a Java program on a 64-bit JVM will probably perform better over a long period of time, but startup will be a little longer.  My startup times are not bad at all, eclipse is swift and my apps compile and load quickly.  Because c_pradelli wanted a server setup, 64bit java may be appropriate but a 32 bit distro may also be better simply because of the kylix app he's using.  In other words, he shouldn't avoid using a 64bit distro because he wants to use java.

I highly recommend not installing eclipse or java (blackdown or sun) from the repos.  I find it brutally slow.  Maybe that's where you're having issues.  I've got a custom setup for both eclipse and java which has resulted in a much faster environment- even faster than my old win setup.


Bizarre. Posts like this make me believe any future conversation is *worthless*. It's like you haven't read any of the previous posts from *anyone, including yourself.* There isn't any *debate* between us, and you don't have to justify anything. Just give your advice to the OP and leave me out of it. ;)

No offense dude, but the question the OP asked was a simple one: which version of *Ubuntu?* Answer: 32Bit.

---

### Post by Enverex on 2007-01-26
I'm on 64bit hardware and using 32bit Ubuntu. I just got tired of issues that would pop up due to something not wotking with 64bit or not working properly. The only times you'll ever see any improvements really are when doing things like encoding/decoding and encryption/decryption and that's only if those apps have been optimised for 64bit (else it'd end up being slower). Quite simply 64bit on the desktop is a waste of time at the moment unless you intend to use more than 4GB of RAM.

---

### Post by phossal on 2007-01-26
> **Enverex said:**
> I'm on 64bit hardware and using 32bit Ubuntu. I just got tired of issues that would pop up due to something not wotking with 64bit or not working properly. The only times you'll ever see any improvements really are when doing things like encoding/decoding and encryption/decryption and that's only if those apps have been optimised for 64bit (else it'd end up being slower). Quite simply 64bit on the desktop is a waste of time at the moment unless you intend to use more than 4GB of RAM.

It's a common belief in the forums for those of us with 64Bit arch's. We could all be wrong. But I'd rather be wrong than without *wireless,* if you get me. ;)

---

### Post by BIGtrouble77 on 2007-01-26
phossal, this dialogue has been thoroughly useless.

---

### Post by BIGtrouble77 on 2007-01-26
> **Enverex said:**
> The only times you'll ever see any improvements really are when doing things like encoding/decoding and encryption/decryption and that's only if those apps have been optimised for 64bit 
That's not entirely true.  Read this thread:
[http://www.ubuntuforums.org/showthread.php?t=318743&highlight=64bit+benchmarks](http://www.ubuntuforums.org/showthread.php?t=318743&highlight=64bit+benchmarks)

---

### Post by Enverex on 2007-01-27
That test is inherantly flawed. The 64bit distro is optimised for many things that the "i386" one isn't due to the baseline that the 64bit processors come in with (they can assume support for many things such as mmx, mmxext, sse, see2, etc) as well as being able to optimise up to the equivelent of i886 level as opposed to i386 which the x86 distro is optimised (or rather not optimised) for.

So in summary, despite the tester not optimising the machine, it already was which means although 64bit Ubuntu would be faster for the reasons explained, it's not directly because of it being 64bit (the amount of which is due to it being 64bit is still unknown).

---

### Post by BIGtrouble77 on 2007-01-27
Enverex, I don't really understand what you said.  I think you're saying that the i386 kernel does not support any modern processor extensions, which I think is incorrect ( don't have a 32bit machine nearby to check for sure).  I think that generic kernel pretty much supports everything now- infact, I think some of those architecture specific ones have been depreciated now, like the K8 and SMP kernels.  I Remember back a few years ago it was much more limited (mainly ram limitations), but since dapper I think it's very usable on all platforms.  I also think you'll see very minor performance differences between the different 32bit kernels.  

Someone please correct me if i'm wrong.

---

### Post by Enverex on 2007-01-28
No, I mean all the compiled applications as well as the kernel will have higher level processor optimisations, not just the kernel alone.

---

### Post by kuja on 2007-01-28
> **BIGtrouble77 said:**
> Enverex, I don't really understand what you said.  I think you're saying that the i386 kernel does not support any modern processor extensions, which I think is incorrect ( don't have a 32bit machine nearby to check for sure).  I think that generic kernel pretty much supports everything now- infact, I think some of those architecture specific ones have been depreciated now, like the K8 and SMP kernels.  I Remember back a few years ago it was much more limited (mainly ram limitations), but since dapper I think it's very usable on all platforms.  I also think you'll see very minor performance differences between the different 32bit kernels.  

Someone please correct me if i'm wrong.

I don't think the -386 kernel supports all the modern optimizations. The generic (a -686 kernel) does though.

---

