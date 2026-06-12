---
title: "Seriously - what do I do?!"
date: 2007-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by JC_510 on 2007-05-27
Hi, im getting a laptop soon, almost definately with an AMD Turion 64 Dual core processor. I plan to install Ubuntu and have it run on a dual boot with Windows.

I've seen in so many threads people arguing over what version of Ubuntu people should use. Some say 'just run the 32 bit version, you wont get as much out of your processor, but there will be alot less compatibility issues', and others say to run the 64-bit version.

Baring in mind that im new to Ubuntu, with little programming knowledge, what version of Ubuntu would you recommend I run? And more importantly; **why?**

---

### Post by milton1 on 2007-05-27
That is going to depend heavily on what you use your system for. Some apps will make good use of the 64-bit system, while others will have major compatibility issues. I would recommend making a list of apps you intend to use, then ask about individual functionality of those apps on the different versions. That shouild hopefully tell you all you need to know.

---

### Post by JC_510 on 2007-05-27
Ok, I'll definately be using the laptop for:[LIST]
[*]Firefox
[*]Open Office
[*]Media player applications
[*]The GIMP
[*]Instant Messenger programs[/LIST]and perhaps some other applications that I might 'discover' in Linux (for instance, I would like to experiment with Beryl/Compiz).

EDIT: I also use several plug-ins with Firefox.

Thanks

---

### Post by AllenGG on 2007-05-27
Using Ubuntu 64 bit version for over 2 years, now switched to 7.04, fast, clean, accurate, perfect for the impatient user (me).
Use Firefox, Swiftfox, all plugins, O-O , "Listen",  and have loaded all the 'libdvdcss' essentials for movies etc.   Why buy 64 bit if it's not going to be used ? ;-)

---

### Post by jamesford on 2007-05-27
theres no reason to not use 64 bit anymore, at least i cant find any whatsoever. since feisty codecs have been no problem, nor firerfox plugins and the nspluginwrapper solves the flash problem

---

### Post by jvc26 on 2007-05-27
Have gone back to 64bit after a time of switching ebtween the two, setting up 64bit is one hell of a lot easier than it used to be, doesnt take very long and is fairly simple to get things like flash working (via the install script to put on 32bit firefox and flash) Codecs pretty much dont cause the issues they used to so I'd go for the 64bit version, also by using 64bit you add another user to the community of 64bit users and so make a larger userbase for the developers to develop 64bit plugins for.
Il

---

### Post by aimran on 2007-05-27
64 bit feisty is fine - I'm using it with my compaq v5000 amd64 ati xpress laptop. I had several issues (but solved some of them:

1. Flash player not working for x64

Solution install 32bit firefox and install the 32bit flash player.


2. Streaming wmv files is a problem

Haven't found a solution for this. I still can't stream bloomberg TV - sound is non existent but video is present. The root of this problem is the difference between 64bit and 32 bit extensions.


So there you have it. The 2 main issues that I had with 64 bit as opposed to 32 bit. However I'm still using 64 bit as they're not that much of a problem.

---

### Post by PriceChild on 2007-05-27
I say 32bit.

Unless you are going to run a VERY heavily used openssh server, do extreme video converting or heavily used database systems... you will get very little performance boost from 64bit (apart from placebo)

Using 32bit will also give you the widest choice of packages.

Oh but with 32bit you can only use up to 4Gb of ram

---

### Post by JC_510 on 2007-05-27
Thanks for all of your advice.

But now I'm left even more confused than when  I was before!! 

I've heard many people saying that running 64-bit would give me a huge boost in performance over the 32-bit version, but now you say there is very little? :confused:

If that is the case, then surely there is absolutely no point in running the 64-bit version?!

I'm not running a server or anything like that, just a laptop that will be used quite alot, mainly for internet browsing, Office apps, media players (the thing with wmv files scares me away from 64-bit...) and quite alot of time will be spent on the GIMP (or similar). Any resource-hungry games will be played on the Windows partition that I plan to have, but I assume that whatever type of Ubuntu is on the other partition will make no difference on the Windows side.

Thank you again for all of your comments, I will take them on board before making any final decision :D


P.S. Im planning on getting 2GB of RAM, but that **may** get upgraded to 4GB in a few years.

---

### Post by aimran on 2007-05-27
What they probably mean is that you get a lot of performance boost for certain programs but for others it's barely noticeable. For example I have heard that 3D redering is 30% faster with 64 bit systems. But if you're just browsing the internet the difference is negligible.

OR

They could mean that you could get a hell of a boost but due to the lack of packages you are stuck at square one.

---

### Post by snakedr on 2007-05-27
You could try the 64 bit version. If you don't like it for some reason you can always install the 32 bit version.

If you have enought disk space you could make two different partitions and install 32 bit on one and 64 bit on the other. Then see which one you like. 

I have both the 32 and 64 bit installed in two partitions. For what I do on my computer I can't see a whole lot of difference in speed.

After having a 64 bit processor for 2 years, I'm still waiting for the 64 bit Windows software to arrive. At least there are 64 bit programs for Linux.

---

### Post by PriceChild on 2007-05-28
> **aimran said:**
> For example I have heard that 3D redering is 30% faster with 64 bit systems.Where have you "heard" this? Under what conditions?

---

### Post by Kilz on 2007-05-28
> **PriceChild said:**
> I say 32bit.

Unless you are going to run a VERY heavily used openssh server, do extreme video converting or heavily used database systems... you will get very little performance boost from 64bit (apart from placebo)

Using 32bit will also give you the widest choice of packages.

Oh but with 32bit you can only use up to 4Gb of ram

Do you have benchmarks to back up that statement that you will get little performance?

If you take a look at launchpad, the difference in the number of packages is less than 1%. 


> **PriceChild said:**
> Where have you "heard" this? Under what conditions?

You can search the internet for benchmarks. [Here is just one example.]("http://www.eofw.org/bench/index.php?sortby=2") Sort by CPU/System by clicking it at the top. Take a look at result 115 and 121. In its notes it says the results for 32bit xubuntu were.
What most benchmarks will say, is that if you have 64bit hardware, using 64bit software, and doing number crunching activities like encoding and rendering. That you can have up to a 30% performance increase over running that same hardware with 32bit software. This is because the software is not taking advantage of your hardware to its full potential. You may also not notice the improvement in applications that require low resources.

---

### Post by PriceChild on 2007-05-29
> **Kilz said:**
> What most benchmarks will say, is that if you have 64bit hardware, using 64bit software, and doing number crunching activities like encoding and rendering. That you can have up to a 30% performance increase over running that same hardware with 32bit software. This is because the software is not taking advantage of your hardware to its full potential. You may also not notice the improvement in applications that require low resources.And that is exactly my point.

I know that extreme video encoding constantly or large database usage will use the 64bit potential. But who does that all the time? All the other (normal) activities won't see much of an improvement.

---

### Post by Kilz on 2007-05-29
> **PriceChild said:**
> And that is exactly my point.

I know that extreme video encoding constantly or large database usage will use the 64bit potential. But who does that all the time? All the other (normal) activities won't see much of an improvement.

Not even extreme encoding, but simple video editing, graphics applications, 3d modelers, and more get a performance improvement. There is also a general overall improvement.
So why not use the operating system designed for your hardware, so that when you need the performance it is there? Please dont tell me that you actually believe the FUD about the 64bit version.
Sadly we get users who come into the 64bit section and ask questions of the people who run it, and we have to convince them the FUD they get elsewhere is wrong. Not only that we get well intentioned people coming in here to spread the fud.
Also take into account that there are problems for some people running a 32bit os on 64bit hardware. It isnt a bed of roses for everyone.

---

### Post by PriceChild on 2007-05-30
64bit hardware "should" have complete 32bit compatibility otherwise its broken?

There may be a small increase in performance for programs on 64bit, but not anything big unless they're coded with 64bit in mind.

Give me _proper_ benchmarks and I'll listen to your point of view instead of "general overall improvement" as that just speaks placebo to me.

---

### Post by rjl6591 on 2007-05-30
If you're buying a new laptop, it will have integrated graphics. Make sure it's Intel integrated graphics, as they're the only ones with a proper open-source driver. All the other manufacturers provide binary-only support at best, which is a very inferior and unsatisfactory approach. See [http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS](http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS)

I recommend you go with 64-bit. It works very well and I found Firefox scrolling to be a lot smoother than the 32-bit one. The only problem is with proprietary plugins. e.g. for Flash and Realplayer. However, the nspluginwrapper solution for this works flawlessly. There is no problem with multimedia codecs - everything that is available for 32-bits is also available for 64.

---

### Post by Kilz on 2007-05-30
> **PriceChild said:**
> 64bit hardware "should" have complete 32bit compatibility otherwise its broken?

There may be a small increase in performance for programs on 64bit, but not anything big unless they're coded with 64bit in mind.

Give me _proper_ benchmarks and I'll listen to your point of view instead of "general overall improvement" as that just speaks placebo to me.

No , 64bit hardware should not have compliete backwards compatibility. I never said it should. But that is the opinion of a large segment of the forums. The "just install the 32bit os to avoid problems" mentality is all over the place.

Just as denying it and saying "the 32bit os is not any different than the 64bit one in terms of performance" without some proof is useless. But at least I can point to some benchmarks for some applications.

---

### Post by pentax on 2007-05-30
I'm a Ubuntu newb, so you can safely ignore anything I say;)
I installed Ubuntu 64 10 days ago, and so far have everything working better than I could have hoped; wine, vmware, Firefox 64 with flash (you can find the script here on this forum, it's easy), all my CD/DVD + multimedia stuff works great! I have no regrets at all going with 64.
The biggest problem I had setting Ubuntu was not knowing about the restricted ATI driver, once I got that installed it solved a host of problems - but that would have been the same problem 32bit vs. 64bit.
Why did I go for 64bit? Because I could!

---

### Post by brharri1 on 2007-05-31
I just switched from 32bit to 64bit and I found it much, much easier than I had expected it to be with all the advice floating around that 64bit is too much of a headache, etc, etc. My Nvidia card works fine, beryl works fine, all my programs work fine. The only issue is flash, and the script to install a 32bit swiftweasel with flash worked flawlessly for me. It actually runs faster than swiftfox did for me on 32. I used the medibuntu repositories and all of my codecs work fine. Go 64.

---

