---
title: "64 bit move"
date: 2006-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by joao82 on 2006-11-01
Hi!
I've been trying Ubuntu and other distros of Linux on my computer for quite some time. But now I bought a laptop with a 64 bit processor (AMD Turion 64) and I'm not certain which kind of Linux should I install. It came with Windows XP, 32 bit obviously, and I don't know if I can have a 64 bit Linux running in the same hard drive. No idea if I even should be messing with 64 bit OS in the first place.
What are the main differences? I see some people in the forums having problems installing programs on 64 bit processors. Do you advise moving to 64 bit Linux? Can I run a 32 bit Ubuntu over a 64 bit processor? Which are the best 64 bit distros?

So many questions and so little patience from me. Any advice would be welcome.
Thanks
Joao

---

### Post by raqball on 2006-11-01
You can run, and it's in my opinion best, to run the 32 bit version of Ubuntu. You will get various opinions here so why not download botheversions of the live cd and give them a whirl :)

EDIT: My son's pc is a 64 and he is running the 32 bit problem free :)

---

### Post by Virak on 2006-11-01
> **joao82 said:**
> What are the main differences?
x86-64 processors support way more than 4 GB of ram. Additionally, they have more registers, which can give big speed improvements in some cases.
> Do you advise moving to 64 bit Linux?
If you use any binary-only programs without x86-64 support, then no. Running those will probably be possible, but it's a pain compared to native 64-bit programs.
> Can I run a 32 bit Ubuntu over a 64 bit processor?
Yes.
> Which are the best 64 bit distros?
I've only ever used 64-bit on Ubuntu, so I can't really answer this.

---

### Post by pbaehr on 2006-11-01
For what it's worth, I have an AMD64 processor and opt to run the x86 version of Ubuntu because it is better supported. Certain things, like installing my video drivers, are much trickier in the 64 bit version.

There is definitely less hardware support for the 64 bit version. I'm not saying it can't be made to work, but for a beginner-intermediate user like myself, I find the 32 bit version much simpler.

I have tried both and never noticed a performance drop on the x86 version and I couldn't get 3d acceleration working on my video card in the 64 bit version, whereas in the x86 version it was a very simple matter.

It all depends on how Linux savvy you are and how much time you are willing to spend troubleshooting.

---

### Post by Cynical on 2006-11-01
Overall 64-bit support isnt very good these days. (for windows as well) I would say that Gentoo has the best 64-bit support currently.

I would recommend running a 32-bit version of Ubuntu though, until you get a handle on what using a 64-bit distro is about.

---

### Post by joao82 on 2006-11-01
ok, in that case I better stick to the 32 bit version. thanks for your answers.

---

### Post by Kilz on 2006-11-01
Sadly you got answers from people who dont run the 64bit version. For the most part there is verry little that will not run on the 64bit version. What little is left can be installed with setup scripts, howto's or simple64 with little effort.

---

### Post by joao82 on 2006-11-01
> **Kilz said:**
> Sadly you got answers from people who dont run the 64bit version. For the most part there is verry little that will not run on the 64bit version. What little is left can be installed with setup scripts, howto's or simple64 with little effort.

that's a very impressive howto on your signature. the simple64 application looks promising. thank you, it showed a whole new way.

---

### Post by BIGtrouble77 on 2006-11-01
I don't understand these responses at all.  64bit is VERY well supported in Ubuntu.  I'm still using my original Dapper64 day one install and it's been fantastic.  Granted, you'll need to install some 32bit software, but automatix and the howto forum here take care of just about anything you'll come accross.  

64bit OS's are not going away.  Within the next year or two people will be forced to use a 64bit distro simply because they'll want to use 4gb of memory.

---

### Post by Case_f on 2006-11-01
Well, I've tried 64bit Ubuntu few times before along the way (been with Ubuntu since the beginning) and always went back to 32bit because I needed 32bit chroot for most of the programs I usually use, so I didn't think the 64bit was worth it for me. But with the release of Edgy final I've finally made the switch for 64bit as I've found out that the overall support has improved (and yeah, I'm more comfortable in Linux than I was before). Setting up the programs I use was (in no small part thanks to Ubuntu forums members) much easier than I remembered from Dapper or earlier 64bit releases and now I have everything I've had in 32bit working perfectly in 64bit, even 32bit apps like Wine and such, and without chroot, too. And it's great using apps that are running my CPU the way it was meant to and are optimized specifically for it. So, absolutely no regrets here, there really seems to be way too much FUD over 64bit when there's no need for it (at least not anymore).

---

### Post by Cynical on 2006-11-03
Interesting responses. I actually did run 64-bit edgy for a little while (please dont assume I would talk about something that I've never experienced) and for the average user there is absolutely no reason for doing so. The only tangible benefits are during compiling, compression, and 3d modeling. I dont understand how you can say support for 64-bit is good when adobe wont even release a flash plugin for us.

[quote=Case_f]And it's great using apps that are running my CPU the way it was meant to and are optimized specifically for it[/quote]

Well X86-64 was designed with 32-bit backwards compatibility in mind. Technically, 32-bit applications are optimized specifically for it.

[quote=BIGtrouble77]Within the next year or two people will be forced to use a 64bit distro simply because they'll want to use 4gb of memory.[/quote]

32-bit distributions can handle using 4GB of memory just fine.


And apparently I'm the one spreading misinformation.

---

### Post by Case_f on 2006-11-03
> **Cynical said:**
> I dont understand how you can say support for 64-bit is good when adobe wont even release a flash plugin for us.

As for me, that doesn't concern me that much, as Opera is still 32bit and will be for some time. I'd much rather have 32bit Flash 9 working flawlessly with it than 64bit Flash. Although it would be nice if the people with other browsers that have 64bit versions had a choice, sure.



> Well X86-64 was designed with 32-bit backwards compatibility in mind. Technically, 32-bit applications are optimized specifically for it.

That may be so, but still there's facts like that on my machine generic Ubuntu 32bit Mplayer uses about 15% more resources than generic Ubuntu 64bit Mplayer (with the same video, of course). When I custom compile the 32bit one, it falls to about 10% more. When I custom compile the 64bit one, its resource consumption stays the same (as the 64bit generic). I understand that it isn't the case with every program, but still, why settle with generic 32bit built system when I can run optimized 64bit one that almost compares to custom compiled (and even has noticeably better performance than 32bit in some cases, see that Mplayer) and still have everything I need working perfectly? There's really no point for not running 64bit for me.

---

### Post by fabertawe on 2006-11-03
> **Case_f said:**
> [snip] When I custom compile the 64bit one, its resource consumption stays the same (as the 64bit generic). I understand that it isn't the case with every program, but still, why settle with generic 32bit built system when I can run optimized 64bit one that almost compares to custom compiled (and even has noticeably better performance than 32bit in some cases, see that Mplayer) and still have everything I need working perfectly? There's really no point for not running 64bit for me.

Hi Case_f,

Can these 64bit optimizations be applied at the './configure' stage? If so, would you mind sharing them please?

Cheers ... Paul

---

### Post by Case_f on 2006-11-03
I don't know of any actual optimizations for 64bit (other than specifying your architecture, SSE support and such to compiler and/or ./configure process, if you know, what you're doing - see documentation of GCC and Mplayer). But that was, in fact, precisely my point - you don't need those in 64bit, because even generic packages from repositories are much better optimized for your specific 64bit CPU than they are in 32bit system - CPU 'capabilities' differ much less in 64bit 'world' than they do in 32bit, where your basic generic package still needs to run fine on quite old CPUs that don't support much of the current technologies - which can make quite a difference, as in my Mplayer example.

---

### Post by tomdkat on 2006-11-03
> **Cynical said:**
> I dont understand how you can say support for 64-bit is good when adobe wont even release a flash plugin for us.
64-bit support from **Ubuntu** is different from 64-bit support from third party vendors.  

Peace...

---

### Post by BIGtrouble77 on 2006-11-03
> **Cynical said:**
> 32-bit distributions can handle using 4GB of memory just fine.


And apparently I'm the one spreading misinformation.

Cynical, you're an ***.  I meant to say "over" 4gb of memory, but that's quite trivial in this discussion.  And if you didn't realise, this is only as of the 2.6 kernel.  Process in 2.4 kernel could only access, at most, 2gb of memory.  I also think there are some software limitations in 32bit distros like JVM which only use 2gb memory.  Have fun being your miserable self.

---

### Post by Cynical on 2006-11-03
[quote=tomdkat]64-bit support from Ubuntu is different from 64-bit support from third party vendors. [/quote]

Which is exactly why I put it this way.

[quote=me]Overall 64-bit support isnt very good these days. (for windows as well)[/quote]


[quote=BIGtrouble77]Have fun being your miserable self.[/quote]

I appreciate your maturity.

---

### Post by Fully216 on 2006-11-03
I personally feel that 64-bit computing has come a long way.  There is no denying that it will eventually become the future of computing, although many argue if the future is now.

I have tried Suse, Fedora, and Ubuntu 64-bit.  Personally, I have had the easiest time with Ubuntu and just simply like it better (the community, overall feel, geared for my level of linux knowledge, and many other reasons).

My analogy for the overall development of other 64-bit distros compared to ubuntu would be the same stability gained going from windows 95 to 98 (16 to 32 bit computing).  What I mean is that I had never realized before that a computer is not supposed to freeze every day until I changed to 32-bit computing with windows 98.  In the same way, I have had many other issues with other OSes that are just not present in ubuntu, which feels more stable.

I now enjoy my 64-bit computing environment with all the benefits that come along with it.  I feel that many others could too; there is no need to fear 64 bit computing.  About the only limit I have found is that flash is not supported, so I use 32 bit flash.  I think it would be a big deal only if I couldn't get flash to work, which was not that difficult.

Bottom line, my vote is that 64-bit rocks, especially with Edgy!! :cool:

---

### Post by mojoman on 2006-11-04
I've used both the Breezy and Dapper as 32-bit and now I'm using dapper 64-bit. There are quite a few programs that aren't available as 64-bit but there are ways to get around this. In my experience, the 64-bit version is not less stable than the 32-bit version and I haven't so far had any problems with my 64-bit dapper.

---

### Post by joao82 on 2006-11-04
hmmmm I've forgot to ask... Imagine that I have a full installation of Ubuntu-64 on my system. Can I install/run a 32 bit program on it? or maybe compile it.
I'm feeling really dumb.

---

### Post by mojoman on 2006-11-05
> **joao82 said:**
> hmmmm I've forgot to ask... Imagine that I have a full installation of Ubuntu-64 on my system. Can I install/run a 32 bit program on it? or maybe compile it.
I'm feeling really dumb.

yes, you can, and no, it's not a dumb question. It does take some twisting and tweaking but there are some good manuals for this and some automated scripts as well. Take a look at this thread, it'll help and it's a good starting point.

[http://www.ubuntuforums.org/showthread.php?t=191205](http://www.ubuntuforums.org/showthread.php?t=191205)

Best regards
/Mojoman

---

### Post by joao82 on 2006-11-05
ok, so I can't install those programs directly. thanks.

---

### Post by BIGtrouble77 on 2006-11-08
> **joao82 said:**
> ok, so I can't install those programs directly. thanks.

There are many 32bit apps that can be installed directly on a 64bit system, you just need the proper libraries installed.  For instance, I have opera, firefox, google earth, cedega, JAlbum, mysqlcc and mplayer working in my 64bit install, all being 32bit apps.  None of them required any special effort except installing some special libraries from the repos.

Automatix ([www.getautomatix.com](www.getautomatix.com)) is an easy way to get some of the more common 32bit apps and firefox plugins installed in 64 bit dapper/edgy.

---

