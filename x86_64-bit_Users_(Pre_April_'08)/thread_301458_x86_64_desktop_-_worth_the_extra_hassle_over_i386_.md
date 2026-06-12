---
title: "x86_64 desktop - worth the extra hassle over i386 system?"
date: 2006-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by beastly on 2006-11-17
I recently upgraded my machine to a Core 2 Duo, so when it came to installing the OS I chose the AMD64 version of Ubuntu (which, despite the name, fully supports Intel's EM64T variant of x86_64). Although the install itself has been largely seamless, I have since run into some problems that I didn't expect as I didn't research the issues behind the x86_64 platform. As an example, there is no Acrobat Reader in the 64-bit repositories as a 64-bit build doesn't exist, so it's quite difficult to get working using some kludges with 32-bit libraries. Similarly, installing the Flash player presents the same problem. I thought using Wine with the Windows version of Firefox and Flash plugin may be a solution, but I'm having problems building Wine too :(.

As this is a home desktop system that I want to use with Flash sites like YouTube, and with no requirement for the additional capacity of 64-bit, I am wondering if I'd be better off switching back to the i386 installation. What are the advantages of a 64-bit OS other than the additional memory capacity (that I won't be needing any time soon)? I don't expect a huge performance difference compared to an i686 optimised 32-bit OS.

The other alternative is to have a 32-bit chroot for building, installing and running those programs that are not compatible with 64-bit libs. Has anyone done this successfully, and if so how much work is involved in setting up and maintaining it (installing new stuff etc)? I assume there's no easy way to use the i386 repositories with apt-get in the chroot - is this correct? Finally how seamlessly can such an approach be integrated with the rest of the system?

Any advice appreciated. Thanks.

---

### Post by beastly on 2006-11-17
I should add, I've just been browsing the forum and noticed that some other users have added how-tos on installing a few of my aforementioned apps in 64-bit Edgy, so I'll give those a go when I get a chance.

Still, my main point still stands as there are inevitably going to be programs I come across in future that won't install with 64-bit libs. Do the benefits of a 64-bit OS outweigh the greater support for the mature i386 platform? And does a 32-bit chroot approach provide a good solution to this problem?

Thanks.

---

### Post by artik on 2006-11-17
Yes there are advantages of using 64 bit platform

Benchmarks:
[http://www.geocities.com/artyomtnk/bench-amd-64-32.pdf](http://www.geocities.com/artyomtnk/bench-amd-64-32.pdf)

---

### Post by Kilz on 2006-11-17
> **beastly said:**
> I should add, I've just been browsing the forum and noticed that some other users have added how-tos on installing a few of my aforementioned apps in 64-bit Edgy, so I'll give those a go when I get a chance.

Still, my main point still stands as there are inevitably going to be programs I come across in future that won't install with 64-bit libs. Do the benefits of a 64-bit OS outweigh the greater support for the mature i386 platform? And does a 32-bit chroot approach provide a good solution to this problem?

Thanks.

The number of applications you will need to install 32bit versions of is small. There is a sticky that deals with them. A chroot is an option. But if you only plan on installing a few 32bit applications. Its a lot of work with little gain for the few 32bit applications you need. 
No version of linux can be installed without some setup. Installing a 32bit os on 64bit hardware can have problems of its own.

---

### Post by drphilngood on 2006-11-17
I've used both(but it has been a few months ago for the 64bit) and came to the conclusion that the small increase in performance isn't worth the extra problems.  Although, I did eventually get most everything working, there always seemed to be some app or game that I could not.
I hope you find this helpful.

---

### Post by beastly on 2006-11-17
OK thanks guys I'll stick with the 64-bit version for now, and try working through the how-tos on this forum to get the apps I need working (hopefully without the chroot if possible).

---

### Post by BIGtrouble77 on 2006-11-17
There have been some minor issues for me, but nothing I couldn't work out.  [www.getautomatix.com](www.getautomatix.com) helps resolve the most annoying issues in one shot.

---

### Post by Mongoose on 2006-11-17
I bought a box for using it to it's full abilities, so I use 64bit builds.  It's great for development reasons in my case -- I can build and test 64 and 32 code on one platform.  I use a chroot for more than just 32bit apps, but I run so many VMs it's not a bother to me.  In fact I've just added GNOME lauchers and scripts to things like x-chat to open urls with either 32/64 firefox for example.

Also you can just install lib32 and run acrobat and firefox you install in a place like /opt/bin32 if you wish.  The number of 32bit apps I need are very small I find.  I think I use firefox 32 for youtube urls and totem 32 for the few video formats that need the win32 codecs.  I also run wine for a good bit of stuff, since vmware can't do opengl acceleration.

---

### Post by wdaniels on 2006-11-18
I've been using amd64 for a couple of months now.  Like you, I didn't know about the various issues before I switched.  Whilst I haven't really noticed a huge performance difference, I don't tend to do the kind of stuff where it would show anyway.  I initially had trouble building Wine although I followed one of the HOWTOs and got it working without much trouble.

Eventually I decided to make the small investment in Crossover Office and Cedega which really did make things A LOT simpler to get setup.  I now use Internet Explorer under cxoffice for any IE-only or flash sites that I really want to use, which works 95% of the time, and all of the games I use (Sim City, Anarchy Online) run fine under Cedega, with no 64bit troubles so far.  So now the only extra hassle I have for using amd64 is to launch IE instead of firefox when I need to use a flash website, which is not very often.

It's sometimes harder to find amd64 packages for stuff, though often you can just force the 32bit ones in with --force-architecture and it works fine (e.g. NX).  So for me, I decided that it would be more bother to re-install with 32bit and set everything up again than to work through the issues.  But given this knowledge before the event, I think I would have stuck with 32bit.

---

### Post by Kilz on 2006-11-18
> **wdaniels said:**
> I've been using amd64 for a couple of months now.  Like you, I didn't know about the various issues before I switched.  Whilst I haven't really noticed a huge performance difference, I don't tend to do the kind of stuff where it would show anyway.  I initially had trouble building Wine although I followed one of the HOWTOs and got it working without much trouble.

Eventually I decided to make the small investment in Crossover Office and Cedega which really did make things A LOT simpler to get setup.  I now use Internet Explorer under cxoffice for any IE-only or flash sites that I really want to use, which works 95% of the time, and all of the games I use (Sim City, Anarchy Online) run fine under Cedega, with no 64bit troubles so far.  So now the only extra hassle I have for using amd64 is to launch IE instead of firefox when I need to use a flash website, which is not very often.

It's sometimes harder to find amd64 packages for stuff, though often you can just force the 32bit ones in with --force-architecture and it works fine (e.g. NX).  So for me, I decided that it would be more bother to re-install with 32bit and set everything up again than to work through the issues.  But given this knowledge before the event, I think I would have stuck with 32bit.

You shouldnt even have to do that, Flash 9 beta for linux runs all the flash sites I have been to. Including the ABC page that runs tv shows. All from firefox. Even if you dont want to try the beta, you would probably be more saft running the windows version of firefox and that flash pulgin. Running EI is a security risk, even with wine.

---

