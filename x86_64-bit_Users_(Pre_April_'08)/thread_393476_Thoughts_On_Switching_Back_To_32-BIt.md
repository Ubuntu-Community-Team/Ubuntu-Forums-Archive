---
title: "Thoughts On Switching Back To 32-BIt"
date: 2007-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by jlacroix on 2007-03-25
Hello everyone, I've been using Ubuntu x64 for a while now because I've been having quite a bit of problems with it. I'm hoping to get everything resolved though so I can keep my 64-bit version, I heard that if I go back to 32-bit it would be slower, but I don't know for sure.

I have an AMD Sempron with 64-bit. When I was using 32-bit on my old PC before I upgraded, I had zero problems, however I am having difficulties with the following things.

First, Flash support. I'm using Feisty now, but when I was using Edgy, I installed a 32-bit Swiftfox that allowed me to have full Flash support everywhere. The unfortunate side effect was that the Swiftfox browser would lock up after each flash movie I watched, or any movie for that matter would outright kill it. Another thing was that I couldn't have an instance of Firefox running at the same time as Swiftfox, as if I had Firefox running and I tried to start Swiftfox, it would start another instance of Firefox instead. I'd rather not use Swiftfox altogether. I want my flash/youtube.

I can't watch any embedded movie in a website, even if it does not use Flash. An instance of a movie player appears in the websites movie frame, but the movie never loads (regardless of format) and if I can't download it, I can't watch it. I installed all the GStreamer things but it didn't fix it.

Even though I dislike Linspire (Ubuntu has newer software) I love the Linspire theme. When I was using 32-bit, I found a deb of the Linspire theme for Ubuntu that works great. I can't get it working with 64-bit. Even with force-architecture, it won't work. I think its inexcusable to make a theme depend on the architecture but thats just me.

Anyway I don't really want to go back to 32-bit I was just hoping for work arounds. I also play MAME and it runs fast, and I'd be afraid it wouldn't run fast if I downgraded to 32-bit. Ironically WMV files worked right out of a fresh install for some reason.

What do you guys think?

---

### Post by Kilz on 2007-03-25
> **jlacroix said:**
> Hello everyone, I've been using Ubuntu x64 for a while now because I've been having quite a bit of problems with it. I'm hoping to get everything resolved though so I can keep my 64-bit version, I heard that if I go back to 32-bit it would be slower, but I don't know for sure.

I have an AMD Sempron with 64-bit. When I was using 32-bit on my old PC before I upgraded, I had zero problems, however I am having difficulties with the following things.

First, Flash support. I'm using Feisty now, but when I was using Edgy, I installed a 32-bit Swiftfox that allowed me to have full Flash support everywhere. The unfortunate side effect was that the Swiftfox browser would lock up after each flash movie I watched, or any movie for that matter would outright kill it. Another thing was that I couldn't have an instance of Firefox running at the same time as Swiftfox, as if I had Firefox running and I tried to start Swiftfox, it would start another instance of Firefox instead. I'd rather not use Swiftfox altogether. I want my flash/youtube.

I can't watch any embedded movie in a website, even if it does not use Flash. An instance of a movie player appears in the websites movie frame, but the movie never loads (regardless of format) and if I can't download it, I can't watch it. I installed all the GStreamer things but it didn't fix it.

Even though I dislike Linspire (Ubuntu has newer software) I love the Linspire theme. When I was using 32-bit, I found a deb of the Linspire theme for Ubuntu that works great. I can't get it working with 64-bit. Even with force-architecture, it won't work. I think its inexcusable to make a theme depend on the architecture but thats just me.

Anyway I don't really want to go back to 32-bit I was just hoping for work arounds. I also play MAME and it runs fast, and I'd be afraid it wouldn't run fast if I downgraded to 32-bit. Ironically WMV files worked right out of a fresh install for some reason.

What do you guys think?

While you can install 32bit firefox and flash, link in my signature. You have made the choice to use an operating system that is currently in Beta testing (Feisty). Everything should work, but I cant guarantee that it will remain so as the developers are still working on this operating system. 
If you do chose one script of mine to install I recommend the Edgy one as there is no Feisty script (yet).
My scripts use the mplayer plugin for other formats, it seems to do good.

Second I will address moving to 32bit. You can, hopefully it will work. You see you now have 64bit hardware, and in theory it should work. But in reality the 32bit operating system doesn't always work correctly with 64bit hardware. It isn't the easy, no hassle way out some people make it to be. If you do have a problem, you will be in no mans land. The 32bit forums will not know about the hardware, and the 64bit section doesn't know about the software.

---

### Post by jlacroix on 2007-03-25
Thanks for the reply. I can't attribute my problems to using a development version, because I had the same problems with stable as well.

I used your script and it did install a 32-bit firefox, the only issue being that the 32-bit firefox cannot access the internet while the native firefox can. Probably just an issue with Feisty, or it could be a missing library. Any ideas?

I like what you have done with those packages, that script was pretty cool. I hope you do one for Feisty when it comes out.

---

### Post by Kilz on 2007-03-25
> **jlacroix said:**
> Thanks for the reply. I can't attribute my problems to using a development version, because I had the same problems with stable as well.

I used your script and it did install a 32-bit firefox, the only issue being that the 32-bit firefox cannot access the internet while the native firefox can. Probably just an issue with Feisty, or it could be a missing library. Any ideas?

I like what you have done with those packages, that script was pretty cool. I hope you do one for Feisty when it comes out.

I think you may want to go back and read the rest of the post.

---

### Post by dfreer on 2007-03-26
The problem with firefox not accessing the internet may be due to IPv6 being enabled. I'm sure their is a better how-to somewhere on the forums, but here's the short way to disable it.

Type about:config in the firefox browser. Scroll down to network.dns.disableIPv6. Right-click on it and Click "Toggle". This should highlight it in bold and change the value from "False" to "True"

See if that fixes the firefox problem.

---

### Post by fakie_flip on 2007-03-26
I haven't had any problems running the 32 bit Ubuntu on 64 bit hardware. The reason I did it was because the 64 bit version of Ubuntu would not boot and hung on errors :(

---

### Post by Kilz on 2007-03-26
> **fakie_flip said:**
> I haven't had any problems running the 32 bit Ubuntu on 64 bit hardware. The reason I did it was because the 64 bit version of Ubuntu would not boot and hung on errors :(

Its possible to have problems. Not that everyone will have problems. Did you try the alternate install cd?

---

### Post by jlacroix on 2007-03-26
> **Kilz said:**
> I think you may want to go back and read the rest of the post.
Or if you could be so kind as to save me the trouble and explain what you mean.

---

### Post by jlacroix on 2007-03-26
> **dfreer said:**
> The problem with firefox not accessing the internet may be due to IPv6 being enabled. I'm sure their is a better how-to somewhere on the forums, but here's the short way to disable it.

Type about:config in the firefox browser. Scroll down to network.dns.disableIPv6. Right-click on it and Click "Toggle". This should highlight it in bold and change the value from "False" to "True"

See if that fixes the firefox problem.

Thanks! That definitely worked. Now, the only problem I'm having with the 32-bit browser is watching videos on cnn.com, it goes into an infinite loop with loading the URL and the Movie.

---

### Post by Kilz on 2007-03-26
> **jlacroix said:**
> Or if you could be so kind as to save me the trouble and explain what you mean.
If you had looked at the entire howto you would have seen


**[SIZE="4"][COLOR="Sienna"]Feisty[/COLOR][/SIZE]**
The script installs onto herd4 but the browser and other 32bit applications cant access the internet. This is because of ipv6 support. It is possible to disable ipv6 and everything will work (to me it seems faster to).

But someone gave you the easy way out, it was much easier to be pointed at the answer, rather than look for the large bold brown Feisty instructions.


> **jlacroix said:**
> Thanks! That definitely worked.

Yep you solved it for Firefox. You dont happen to run any other 32bit applications that need to access the internet, do you?

---

### Post by jlacroix on 2007-03-27
No, I don't run any other 32-bit apps. By the way, is there a way I can convert a 32- bit KDE theme to 64-bit?

---

### Post by Kilz on 2007-03-27
> **jlacroix said:**
> No, I don't run any other 32-bit apps. By the way, is there a way I can convert a 32- bit KDE theme to 64-bit?

I dont know, I have never ran kde so I dont know whats involved in the theme. Im kind of surprised that a theme is dependent on the architecture.

---

### Post by jlacroix on 2007-03-28
Well, the theme is a *.deb file. Even though I prefer KDE, I have to say that Gnome has the absolute best theming system. With KDE you either compile by source or install a deb. The deb I have is 32-bit. I can probably track down the source code file if someone can help me make a new deb. Its my favorite theme so thats why I care so much about it.

---

### Post by jlacroix on 2007-03-29
Another problem I'm having is that when I play a video in firefox32, it crashes the browser completely every 1 out of 3 times.

---

### Post by Thene on 2007-03-30
Hi jlacroix,

I have gone through the same thing. I bought a new HD last year with the intention of running Windows, but changed my mine and went to Ubuntu instead. I didn't even think of what that meant considering I'd just got a system that was a Pentium D (Intel 64).

I had a few problems installing Dapper, but then got it to work, had some problems with Edgy and the whole time I was tossing up in my mind whether or not to get another 32bit system.

In the last week I upgraded to Feisty (& found my Leadtek card worked even better than previous which was one of my main problems) and a couple of hours ago I installed Beryl - flawlessly - (that's right I was geared up for a fight with my system, just in case).

Anyhow I guess a bit long-winded but what I'm trying to say is - Don't give up, it can only improve. (Not to mention with the help of some of the really helpful people here.) :D

---

### Post by Seq on 2007-03-30
Does anybody have a list of issues that are experienced when running a 32-bit OS on a x86-64 platform? I thought the design of the platform was to transparently work with 32-bit operating systems and software.

I've been running 32-bit Edgy and Feisty on a x86-64 machine (Core 2 duo), and most consumers are running 32-bit operating systems as well (Windows XP and Vista both have 64-bit versions, but try finding them on computers in Future Shop or Best Buy).

I was under the impression that if you don't really need the extra address space (large amounts of RAM), there was no real advantage to running 64-bit right now (other than being 1337), and you're just exposing yourself to compatibility issues (flash being the example used here)

Update: I should say Large file support as well as large amounts of ram above. From what I understand, Video editing and the like would benefit from the larger address space, even discounting the RAM benefits.

---

### Post by Kilz on 2007-03-30
> **Seq said:**
> Does anybody have a list of issues that are experienced when running a 32-bit OS on a x86-64 platform? I thought the design of the platform was to transparently work with 32-bit operating systems and software.

I've been running 32-bit Edgy and Feisty on a x86-64 machine (Core 2 duo), and most consumers are running 32-bit operating systems as well (Windows XP and Vista both have 64-bit versions, but try finding them on computers in Future Shop or Best Buy).

I was under the impression that if you don't really need the extra address space (large amounts of RAM), there was no real advantage to running 64-bit right now (other than being 1337), and you're just exposing yourself to compatibility issues (flash being the example used here)

I started a post to get that list, [URL="http://www.ubuntuforums.org/showthread.php?p=2377325#post2377325"]but its only just started.
[/URL]
You really cant compare what is happening in the windows area to linux. Windows has real driver issues (lack of 64bit drivers)that dont exist in linux. 
There are performance benefits to running the 64bit version. There is the overall slight improvement, and the 30% increase in number crunching applications like 3d and encoding. Secondly the perceived compatibility problems for the most part are FUD. You mention the only real compatibility issue (flash) , and there are ways of working around it.
So the question should be, "Should I give up the ability to get some performance increase because I have to spend an extra half hour(maybe less) getting flash to work?"

---

### Post by Rui Pais on 2007-03-30
> **jlacroix said:**
> Well, the theme is a *.deb file. Even though I prefer KDE, I have to say that Gnome has the absolute best theming system. With KDE you either compile by source or install a deb. The deb I have is 32-bit. I can probably track down the source code file if someone can help me make a new deb. Its my favorite theme so thats why I care so much about it.

Hi,
since a theme it's just pics and scripts, should be plenty safe force installation, no mater what arch is indicated on install script of the deb.

Just use:
```
sudo dpkg --force-architecture -i <package_name.deb>
```

Another way would be decompress the deb and check inside data.tar.gz for the theme folders and manually copy it for your kde themes folder.

---

### Post by jlacroix on 2007-03-30
I did the force architecture for the theme deb, and it did install but the theme is not listed in the themes list for you to select. No matter what you do the theme will not install in an un-native platform. I don't know why.

---

### Post by Rui Pais on 2007-03-31
it looks that kde themes require some compilation of some kind... 

have you try to build the package? 
Make sure that you have deb-srcs on yor sources.list and do it with: 
```
sudo apt-get -b source <package_name>
```

or try with apt-build (some times one works over the other...)

Here 2 links about how-to use them, if you don't know such how-to-do it that way:
[apt-get from source]("http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html").
[apt-build how-to]("http://julien.danjou.info/article-apt-build.html").

Good luck.

---

### Post by HankB on 2007-03-31
> **Kilz said:**
> 
Secondly the perceived compatibility problems for the most part are FUD. 
Spread by those if us who get tired of the additional fiddling required to get everything working in a mixed 32/64 bit environment.

Maybe it's because I've been using 64 bit Ubuntu for a couple of years now. Perhaps if I did a fresh install, things would go better. I run some stuff in a 32 bit chroot and it seems like I have to have a *lot* of stuff installed to get that to work.

But right off the bat, I get a little reminder on the task bar when there are updates to install. With the chroot, I have to manually "apt-get update;apt-get upgrade" to get updates. 

I have to add extra stuff to get mounts to be accessible in the chroot. Remember the original intent of a chroot jail was to *isolate* programs there from the rest of the system, so it's not the best starting point to set up something that integrates seamlessly. The seams are there on purpose.

Now I expect you to reply that there are fixes for all of these little things. And I want you to know that I truly appreciate your help with providing the fixes. I really do. But the fact that the fixes are required to do the same things that don't require fixes in a pure 32 bit environment make my point.

I do run 64 bit Ubuntu on my Turion based laptop, but I gave in and installed 32 bit on the desktop that my wife uses. 64 bit was just too fiddly for her as she's not a geek. She just wanted things to work.

In my experience 32 bit runs w/out any difficulty on an AMD 64. I did test some encoding using lame and it did run slower, but most other things will be just fine.

And I still keep 64 bit on my laptop, hoping that some day it will be on an equal footing with the 32 bit systems.

-hank

---

### Post by Kilz on 2007-03-31
> **HankB said:**
> Spread by those if us who get tired of the additional fiddling required to get everything working in a mixed 32/64 bit environment.

Maybe it's because I've been using 64 bit Ubuntu for a couple of years now. Perhaps if I did a fresh install, things would go better. I run some stuff in a 32 bit chroot and it seems like I have to have a *lot* of stuff installed to get that to work.

But right off the bat, I get a little reminder on the task bar when there are updates to install. With the chroot, I have to manually "apt-get update;apt-get upgrade" to get updates. 

I have to add extra stuff to get mounts to be accessible in the chroot. Remember the original intent of a chroot jail was to *isolate* programs there from the rest of the system, so it's not the best starting point to set up something that integrates seamlessly. The seams are there on purpose.

Now I expect you to reply that there are fixes for all of these little things. And I want you to know that I truly appreciate your help with providing the fixes. I really do. But the fact that the fixes are required to do the same things that don't require fixes in a pure 32 bit environment make my point.

I do run 64 bit Ubuntu on my Turion based laptop, but I gave in and installed 32 bit on the desktop that my wife uses. 64 bit was just too fiddly for her as she's not a geek. She just wanted things to work.

In my experience 32 bit runs w/out any difficulty on an AMD 64. I did test some encoding using lame and it did run slower, but most other things will be just fine.

And I still keep 64 bit on my laptop, hoping that some day it will be on an equal footing with the 32 bit systems.

-hank

Maybe the problems are because you are using a chroot, something that isnt required as of Dapper.

---

### Post by emofine on 2007-04-12
> **Kilz said:**
> I started a post to get that list, [URL="http://www.ubuntuforums.org/showthread.php?p=2377325#post2377325"]but its only just started.
[/URL]
You really cant compare what is happening in the windows area to linux. Windows has real driver issues (lack of 64bit drivers)that dont exist in linux. 
There are performance benefits to running the 64bit version. There is the overall slight improvement, and the 30% increase in number crunching applications like 3d and encoding. Secondly the perceived compatibility problems for the most part are FUD. You mention the only real compatibility issue (flash) , and there are ways of working around it.
So the question should be, "Should I give up the ability to get some performance increase because I have to spend an extra half hour(maybe less) getting flash to work?"

Actually, I have a major problem with the 64-bit version, although admittedly very few people will have this issue: there is no Contivity (Nortel networks) 64-bit Linux VPN client support that will work on Ubuntu, which means I have to use the hated Windows to work remotely; a huge pain because I do that quite often. I have searched far and wide, and for long, and all I could find is that Novell has a 64-bit Contivity plugin, but I would have to buy and install Suse Linux (SLED) to use that and I am happy with Ubuntu and don't feel like buying Suse. The company that provides the VPN software, Apani Networks, is not interested in making a 64-bit version for Linux. Weird, because they make a 64-bit version for Solaris. The software is not Open Source, so I cannot even get the source code to hack, which I would do if I could get hold of it.

So *some* people have big issues, which took way more than a half hour and is still not solved.  I am considering reverting to 32-bit just so I can work via the VPN. That's how much of a hassle it is. But I don't know if I am ready to mess with my setup, which is complex and works great except for the VPN issue. :(

---

### Post by dfreer on 2007-04-12
> there is no Contivity (Nortel networks) 64-bit Linux VPN client support that will work on Ubuntu

I do not use this software, btw. But have you tried using the 32-bit linux client in 64-bit Ubuntu yet? If so have you posted a thread of any issues you encoutered? Someone may be able to help you get the 32-bit client running, since 64-bit ubuntu runs 32-bit code...

---

### Post by emofine on 2007-04-18
> **dfreer said:**
> I do not use this software, btw. But have you tried using the 32-bit linux client in 64-bit Ubuntu yet? If so have you posted a thread of any issues you encoutered? Someone may be able to help you get the 32-bit client running, since 64-bit ubuntu runs 32-bit code...

64-bit Ubuntu does indeed run 32 bit code, but this is different. The Apani client links with the kernel and creates  two loadable modules. It is provided only with gcc 32-bit compiled libraries and a couple of wrapper C files for kernel integration. I have built this and got it working on a 32-bit CentOS 3 VM, but, AFAIK, you cannot use it with a 64-bit kernel. 

This is what happened when I tried:

ld: Relocatable linking with relocations from format elf32-i386 (/home/xxxx/apani/cvc_linux-rh-gcc3-3.5/src/k2.6/../libmishim-2.6.a(linux_int_26.o)) to format elf64-x86-64 (/home/xxxx/apani/cvc_linux-rh-gcc3-3.5/src/k2.6/mishim.o) is not supported

Note that the libmishim.a file is supplied pre-compiled for Linux by Apani. No source code is provided for that, otherwise I would be ok.

Thanks anyway.

---

### Post by ssavelan on 2007-04-18
I tried 64-bit for a while; but could not hang with the extra inconvenience.  I hope that other users persist so that the OS will grow up and n00bs like me will be able to benefit.

sos

---

### Post by renderedbrian on 2007-04-19
I have been a 64bit user for the past year or so.
However I have now went to a 32bit install.

Life is much simpler now I went to 32bit!

(Also since blender 2.43 is not 64bit compatible, and will be a few months before the developers make it 64bit compatible since I run 32bit ubuntu I can run blender 2.43 without any problems now!)

[Blender!]("http://www.blender.org/")

---

### Post by Kilz on 2007-04-19
> **renderedbrian said:**
> I have been a 64bit user for the past year or so.
However I have now went to a 32bit install.

Life is much simpler now I went to 32bit!

(Also since blender 2.43 is not 64bit compatible, and will be a few months before the developers make it 64bit compatible since I run 32bit ubuntu I can run blender 2.43 without any problems now!)

[Blender!]("http://www.blender.org/")

While I dont use blender that much, it seems to work just fine with the 2.43 version in the 64bit repo's.

---

### Post by 9a3eedi on 2007-04-19
I doubt anybody would get any problems when running a 32bit OS on 64bit hardware. I run XP 32bit on Pentium D, which is 64bit. No problems (but eventually I DID get viruses :P )

in any way, each has its own advantage. You can choose whatever you want. You can always format a couple of years later, and install the other.

Might I also mention that a couple of packages avaliable for 32bit ubuntu aren't there for 64bit? namely wine.. which is strange considering how popular the thing is. But there's an easy howto guide to compiling wine, which worked flawlessly for me. 

I'm running 64bit edgey. Yes, it does have its fair share of incompatibilities.. but I can live without these programs, and I believe over time as more and more people migrate to 64bit the compatibility will just increase.. and eventually 64bit will be more compatible with programs compared to 32bit. We're under this transition phase at the moment :)

---

### Post by Kilz on 2007-04-20
> **9a3eedi said:**
> I doubt anybody would get any problems when running a 32bit OS on 64bit hardware. I run XP 32bit on Pentium D, which is 64bit. No problems (but eventually I DID get viruses :P )

in any way, each has its own advantage. You can choose whatever you want. You can always format a couple of years later, and install the other.

Might I also mention that a couple of packages avaliable for 32bit ubuntu aren't there for 64bit? namely wine.. which is strange considering how popular the thing is. But there's an easy howto guide to compiling wine, which worked flawlessly for me. 

I'm running 64bit edgey. Yes, it does have its fair share of incompatibilities.. but I can live without these programs, and I believe over time as more and more people migrate to 64bit the compatibility will just increase.. and eventually 64bit will be more compatible with programs compared to 32bit. We're under this transition phase at the moment :)

[There are problems with running the 32bit os for some people.]("http://ubuntuforums.org/showthread.php?t=395164")  There is a 64bit wine package. Do a search of the 64bit section for wine.

---

### Post by renderedbrian on 2007-04-20
> **Kilz said:**
> While I dont use blender that much, it seems to work just fine with the 2.43 version in the 64bit repo's.

Apparantly files saved on the 64bit build of blender won't open up in 32bit blender...

I realise I probably won't be getting the best performance out of my Athlon 64 3000+ running 32bit ubuntu, but I seem to prefer the simplicity of a 32bit install.

:popcorn:

---

### Post by Kilz on 2007-04-20
> **renderedbrian said:**
> Apparantly files saved on the 64bit build of blender won't open up in 32bit blender...

I realise I probably won't be getting the best performance out of my Athlon 64 3000+ running 32bit ubuntu, but I seem to prefer the simplicity of a 32bit install.

:popcorn:

Each and every time I read a comment like that, that 32bit install is easier. I think about the little bit of one time setup vs the hours and hours of rendering time saved. So what if the files from a 64bit blender dont work in 32bit blender? If you have the 64bit version, why would you want to transfer files from the 64bit machine to run them on a slower 32bit machine?
I dont use blender much, but I do work with 3d models. The 30% improvement in rendering speed can shave off 2 or 3 hours on a model.
Even if I added all the little applications that make up the less than 1% of applications with a slight setup need (most people have less than 5 applications). It still wouldnt be be more. It also isnt like you dont have any setup or problems in 32bit. The rest of the forum proves that.

---

