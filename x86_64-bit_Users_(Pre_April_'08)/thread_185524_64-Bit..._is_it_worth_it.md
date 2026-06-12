---
title: "64-Bit... is it worth it?"
date: 2006-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anthem on 2006-05-31
I'm getting ready to install Dapper on my AMD laptop and AMD desktop.  The desktop is running a Sempron64 3400+ with a gig of RAM.  Is it worth running 64-bit?  I don't need a lot of performance; this should give me all the performance I need.  I'm strongly considering installing 32-bit Dapper on both machines so that I can have Flash support, better drivers, and so on.

Thoughts?

---

### Post by khightower on 2006-05-31
That is what I did. When there are more 64 bit apps with full linux support I will setup up a 64bit OS

---

### Post by TrendyDark on 2006-05-31
I have a 64 bit CPU and I can tell you, it's not really worth all the trouble. Though, maybe later down the line it will be a better option.

---

### Post by Kilz on 2006-05-31
[QUOTE=Anthem]I'm getting ready to install Dapper on my AMD laptop and AMD desktop.  The desktop is running a Sempron64 3400+ with a gig of RAM.  Is it worth running 64-bit?  I don't need a lot of performance; this should give me all the performance I need.  I'm strongly considering installing 32-bit Dapper on both machines so that I can have Flash support, better drivers, and so on.

Thoughts?[/QUOTE]

Depends, I have been running Dapper 64 for a bit. One of the nice diffrences between it and Breezy is that you can force install 32 bit applications, copy in a few libs, and they run. If you plan on running hundreds of 32 bit applications maybe it isnt worth it, but if you are going to run 5 or 10 that dont have 64 bit versions, it maybe worth it.
There is no longer a need to set up a chroot if the only 32 bit applications you want are wine, cedega, firefox, and a few media players. I know I wont install a 32 bit version.

---

### Post by panurge77 on 2006-05-31
I agree it's still not worth the trouble. I'm running dapper 64 now but will move to 32 when I get my hands on the final version iso. If you really wanna go 64 bits I must say Suse is easier than Ubuntu, but suse has some other issues that bother me, so I'm staying with Ubuntu ;)

---

### Post by Lonergan on 2006-05-31
I guess it depends on the use.  I've only ever used 64 bit ubuntu and I find that I get enormous functionality out of my system.  Yet, there are times I would like flash, or wma/wmv 9 support.  Codecs are the hangup for me.  Otherwise, pretty well everything I need is running.

---

### Post by Kilz on 2006-05-31
[QUOTE=panurge77]I agree it's still not worth the trouble. I'm running dapper 64 now but will move to 32 when I get my hands on the final version iso. If you really wanna go 64 bits I must say Suse is easier than Ubuntu, but suse has some other issues that bother me, so I'm staying with Ubuntu ;)[/QUOTE]

SuSE 10.1 has more than a few issues, way more. True it may automaticly install the 32 libs for you. But so far I havent found a 32 bit application I cant add to Dapper 64 with sudo dpkg --force-architecture -i <packagename> and some copying some libs into /usr/lib32.

---

### Post by Anthem on 2006-05-31
Interesting, I expected more pushback.

For those using 64-bit systems, what does the 64-bit-ness really give you?  I totally understand for a server install... more than 4GB of RAM can be a big deal.  But other than that...

---

### Post by henriquemaia on 2006-05-31
[quote=Anthem]Interesting, I expected more pushback.

For those using 64-bit systems, what does the 64-bit-ness really give you?  I totally understand for a server install... more than 4GB of RAM can be a big deal.  But other than that...[/quote] 
Responsiveness. Apart from that, I have full support of CPU scaling and Hibernation. The system is by far the best the more stable I have ever tried. Would I get that from the i386 version? Don't know, haven't tried, but this Dapper IS working as I expect it to work, so I don't see the point of using the i386.

---

### Post by Kilz on 2006-05-31
[QUOTE=Anthem]Interesting, I expected more pushback.

For those using 64-bit systems, what does the 64-bit-ness really give you?  I totally understand for a server install... more than 4GB of RAM can be a big deal.  But other than that...[/QUOTE]
I don't know about others, but I'm into 3d modeling, 64 bit POV is a lot faster. I also paid for a 64 bit possessor, why would I want to run a 32 bit OS? I could see if applications were not available, but so far I have been able to add what 32 bit stuff I need.
I think a lot of the "I will just install 32 bit " comes from running older versions where you needed a chroot to run 32 bit app's, it wasn't easy to set up.

---

### Post by flip314 on 2006-05-31
I've tried the k8 x64 kernel and the k7 x86 kernel.  I didn't notice any difference in performance, but there were a number of applications that didn't play well/wouldn't compile under 64-bit.  Given that I wasn't benefiting at all from 64 bits, I decided the 32 bit kernel was a better choice for now.

But, if you're running the i386 kernel, you should upgrade to the k7 kernel.  It should be faster, plus then you can compile all your aps with the k7 optimizations.

At work we're running 64bit scientific linux, but only because the tools specifically need 64 bits (and the servers have more than 4GB memory :-D)

---

### Post by Kilz on 2006-05-31
[QUOTE=flip314]I've tried the k8 x64 kernel and the k7 x86 kernel.  I didn't notice any difference in performance, but there were a number of applications that didn't play well/wouldn't compile under 64-bit.  Given that I wasn't benefiting at all from 64 bits, I decided the 32 bit kernel was a better choice for now.[/QUOTE]
Just a question or two. Was the OS 64 bit Breezy or Dapper? Did you have to compile the applications because there was no 64 bit version? Was there a 32 bit version?

---

### Post by RAOF on 2006-05-31
[QUOTE=Anthem]...
For those using 64-bit systems, what does the 64-bit-ness really give you?  I totally understand for a server install... more than 4GB of RAM can be a big deal.  But other than that...[/QUOTE]
Apart from the lots-a-ram-ness, x86_64 gives you a bit more speed.  Anandtech did some benchmarks at one point, showing improvements from a bit slower (for just one thing), to about 33% faster LAME encoding, to 100% faster for some cryptography (SSL) tasks.

If you don't need the speed (or the "coolness"), you don't need to bother.  Even though it's not that much bother.

---

### Post by beeldings on 2006-05-31
It depends on what you want to use your computer for. If you need Flash and support for restricted formats, go with the 32-bit version. If you like to game or perform system-intensive activities, go with the 64-bit version. From my personal experiences: while multimedia and restricted format support is more developed on Dapper 32, I noticed that Doom 3 ran slower. However, when using Dapper 64, I noticed that Doom 3 was faster, more responsive, but on the flip side multimedia and restricted format support is lacking. For the time being, my suggestion to you would be to stick with Dapper 32 until there are more advances in Flash and multimedia support for Dapper 64. Hopefully 64-bit multimedia and Flash support will have advanced by the time Edgy is released.

---

### Post by Kilz on 2006-05-31
[QUOTE=beeldings]It depends on what you want to use your computer for. If you need Flash and support for restricted formats, go with the 32-bit version. If you like to game or perform system-intensive activities, go with the 64-bit version. From my personal experiences: while multimedia and restricted format support is more developed on Dapper 32, I noticed that Doom 3 ran slower. However, when using Dapper 64, I noticed that Doom 3 was faster, more responsive, but on the flip side multimedia and restricted format support is lacking. For the time being, my suggestion to you would be to stick with Dapper 32 until there are more advances in Flash and multimedia support for Dapper 64. Hopefully 64-bit multimedia and Flash support will have advanced by the time Edgy is released.[/QUOTE]

Would you please tell me what multimedia applications and formats you cant run on 64 bit Dapper? I would like to try and force them in. As for flash, are you refering to flash support in firefox or mozilla?

---

### Post by jdong on 2006-05-31
(I'm slightly changing my position since the last time I've commented on a thread like this)

For the most part, I'd have to say that x86-64 OS'es have little performance benefit to offer over their 32-bit counterparts, unless one of your programs needs access to more than 4GB of RAM [which is not possible under 32-bit]

**However**, thanks both to smarter GCC releases (3.4.x, 4.x.x) and hand-tuned routines for 64-bit, **we are beginning to see 64-bit performance boosts**. Particularly if you do media encoding, compiling, or run intense openssh loads, it's now possible to get a 20% performance increase from switching to 64-bit... but so far in everyday desktop tasks, you will likely not feel a difference. Again, the performance boosts are pretty limited and for the most part there is not a difference.


As far as software compatibility, here's how it breaks down with respect to Dapper:

(1) **Pure 64-bit** (i.e. stock Dapper AMD64): Very straightforward to set up (pop in your install CD). Almost all Ubuntu repository packages come in 64-bit. Some non-repository software may not compile cleanly. 32-bit media codecs and flashplayer will not work. 32-bit kernel modules (drivers) will not work, but all drivers in the repository work fine in 64-bit.

(2) **64-bit with 32-bit programs here and there**: Somewhat straightforward setup, if you are just using a few 32-bit programs. Gets somewhat hairy when you have too many programs. With enough patience/effort, you can get all Ubuntu repository packages to work. Still, non-repository software may not compile cleanly. You can get Flash with a 32-bit Firefox, but 32-bit media codecs are a bit more of a pain. 32-bit only drivers will not work in 64-bit.

(3) **64-bit with 32-bit chroot**: This is basically maintaining a little 32-bit world inside your 64-bit Ubuntu. It takes a deal of initial setup, but once set up it is a breeze to maintain. Basically, "firefox" runs 64-bit firefox while "lin32 firefox" runs a 32-bit copy of firefox. You can use "lin32 apt-get" to install software to the chroot. All repository software works in 32-bit and 64-bit, and you can choose which flavor to run via lin32.  Non-repository sources will compile cleanly under the 32-bit chroot. 32-bit drivers will not work.


So, the most compatible is #3, and if you have the disk space and 30 minutes to dedicate to a HOWTO, I recommend you go for it. That's what I'm doing right now :)

---

### Post by Bokonon on 2006-05-31
If it is your only/primary system, I would stick with 32 bit(k7).  Performance gains are minor shifting to 64 bit if you ask me.  I used my desktop as primary system for a while and definately enjoyed the 32 bit OS vice 64.  I switched to 64 bit now that I have a laptop and can run 32 bit apps on that.

AMD64-X2 with 2G RAM

---

### Post by Anthem on 2006-06-01
Wait, if I'm running on a 32-bit system, is there a k8 kernel available to me?

---

### Post by RAOF on 2006-06-01
[QUOTE=Anthem]Wait, if I'm running on a 32-bit system, is there a k8 kernel available to me?[/QUOTE]
Not from the repositories, as far as I know.  686 or k7 are as far as you'll get.

---

### Post by balleklorin on 2006-06-01
I've been using the AMD64-general version of Kubuntu dapper for some time now, and got no problems related to the 64bit version as far as I can tell.

Why should people run a 32bit OS on a 64bit cpu if they havent got particular needs like a spesific killer app that wont run in the 64 bit edition?

BTW. If people don't use the 64bit release the app makers wont bother making it work...

---

### Post by JoWilly on 2006-06-01
I've been runinng 64bit dapper for a few days. It works very well. The few 32 bit apps needed are easy to install, as others have previously posted.

Install the 32 dapper packages with dpkg -i --fore-architecture.

I have wine, cedega,crossover office, realplayer, adobe reader, picasa, nerolinux, etc... running. Very easy, and works perfectly.

If a 32 app needs some lib, just get the 32 bit dapper deb file, and open it with the archive manager (file-roller), and copy the content of /usr/lib to /usr/lib32.

(nero needs 2 debs : libgtk1.2 and libglib1.2, wine needs 1 deb: libxxf86dga1; thats about all)

There is only one codec I dont have : wmv (audio works), but I have not tried to get it to work as I had no need for it. All other codecs (xvid, aac, mpeg, ogg, mp3, ... mplayer... + encoders like x264, mencoder, ffmpeg, ...) are 64 bit.

For flash, I have installed gnash (there are amd64 debs posted on these forums). It is still in developpment; it does not play all flash movies yet, but plays many.

All in all, 64bit dapper is no trouble at all : for the above, you only need to copy the content of /usr/lib from 3 32 bit dapper deb files...

---

### Post by pato101 on 2006-06-01
[QUOTE=Anthem]Interesting, I expected more pushback.

For those using 64-bit systems, what does the 64-bit-ness really give you?  I totally understand for a server install... more than 4GB of RAM can be a big deal.  But other than that...[/QUOTE]

[LIST=1]
[*]Cool factor.
[*]About 15% of performance improvement respect 32bit at AMD64bit apps.
[*]Handling more than 1GB RAM efficiencly (for specific apps).
[*](Setting up 32bit chroot is not so difficult afterall)
[*]Cool factor 2: I'm already there... you still living at 32bit era?
[/LIST]

---

### Post by Patsoe on 2006-06-01
[QUOTE=Anthem]Interesting, I expected more pushback.

For those using 64-bit systems, what does the 64-bit-ness really give you?  I totally understand for a server install... more than 4GB of RAM can be a big deal.  But other than that...[/QUOTE]

Other than that, the x86-64 extensions offer double the number of registers, that is 16 64bit- instead of 8 32bit-registers. If you're pushing a lot of numbers around, that can help... I still have to do a thorough comparison of my simulation work in 32-bit and 64-bit mode (hope to get to it in two months time :)), but I know a short test with random number generation at double (=64bit) precision was about 30% faster (can't verify this number right now, sorry about that, I'm a bit "handicapped" as I'm away from home for a longer time).

---

### Post by beeldings on 2006-06-01
[QUOTE=Kilz]Would you please tell me what multimedia applications and formats you cant run on 64 bit Dapper? I would like to try and force them in. As for flash, are you refering to flash support in firefox or mozilla?[/QUOTE]

I should have elaborated on this in my original post, but what I meant to discuss was support for restricted formats in Dapper 64, specifically w32codecs. With regards to Flash, I was referencing Flash support in Firefox.

---

### Post by Kilz on 2006-06-01
[QUOTE=beeldings]I should have elaborated on this in my original post, but what I meant to discuss was support for restricted formats in Dapper 64, specifically w32codecs. With regards to Flash, I was referencing Flash support in Firefox.[/QUOTE]


For flash support in firefox, and java, there is a wiki page with instructions on how to install the 32 bit versions on 64 bit [Breezy and Dapper]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava"). 
Im looking into the w32codecs now. I have gotten 32 bit mplayer installed, it needs quite a few libs. But im sure it can be made easier. If I have to I can put up a lib pack on the web space comcast gives me. I dont use it now. Im not sure where the 32 bit codecs go in the file system. But a little research should clue me in.

---

### Post by HankB on 2006-06-01
[QUOTE=jdong]

(3) **64-bit with 32-bit chroot**: This is basically maintaining a little 32-bit world inside your 64-bit Ubuntu.

[...]

So, the most compatible is #3, and if you have the disk space and 30 minutes to dedicate to a HOWTO, I recommend you go for it. That's what I'm doing right now :)[/QUOTE]

This is what I have on my laptop. I found it more awkward than I thought. There are times when I continue to be reminded of the split. It seems to me that a chroot was invented to isolate programs and it takes a lot of work to undo that. For example, if I plug in a USB flash drive, I cannot attach files on it to email because I run firefox in a 32 bit chroot and use gmail for email. I have to copy the file to /tmp which I have bind mounted to make it available. I know there's a way to bind mount the flash drive, but I just haven't bothered. At first I did bother with trying to integrate the chroot into the 64 bit environment, but after a while I just got tired of the seemingly constant tweaks.

One of the other things I've done is to install more 32 bit packages to flesh out the 32 bit environment. At present I'm at: 
```

hbarta@baobab:~$ dpkg -l|wc -l
1276
hbarta@baobab:~$ dchroot -d dpkg -l|wc -l
306

```
So that's nearly a 25% 32 bit install. At the moment, I can't recall why I had to install all of these things, but you do run into dependencies for some things. 

I'll stick with 64 bits because I'll eventualy benefit enough to pay off for the inconvenience. And if no one uses 64 bit stuff, there won't be any reason for anyone to continue to port.

---

### Post by mshores on 2006-06-01
I have only been using Ubuntu for about a week. I tried a 32-bit installation and a 64-bit installation of Dapper Drake. The 64-bit is what I stuck with. I don't mind a little bit of extra set up and really, I kind of like having to figure things out a little more in depth, because it's gotten me actively involved with my computer again instead of it just being another appliance. I'm really interested in figuring out what all I can do with it. It seems to me that if you want something that works without any work, I guess you might try 32-bit but if you are interested in getting a chance to play around with things a little I'd go with 64-bit.

---

### Post by jdong on 2006-06-01
[QUOTE=HankB]For example, if I plug in a USB flash drive, I cannot attach files on it to email because I run firefox in a 32 bit chroot and use gmail for email. I have to copy the file to /tmp which I have bind mounted to make it available. [/quote]

You can just bind-mount /media.... But yes, there are these little things to still resolve after a chroot is set up. Multiarch will be the answer to all these problems, so hopefully Ubuntu will support multiarch soon.

---

### Post by Kilz on 2006-06-01
[QUOTE=jdong]You can just bind-mount /media.... But yes, there are these little things to still resolve after a chroot is set up. Multiarch will be the answer to all these problems, so hopefully Ubuntu will support multiarch soon.[/QUOTE]
It is in a sense, you can install 32 bit applications on a 64 bit Dapper install without a chroot. You couldn't do the same thing with 64 bit Breezy.
What it isn't is automatic support. You have to manually resolve lib dependencies and copy them to /usr/lib32. Personally I find the adding lib's to be much less work in the long run than adding duplicates of programs and resolving ongoing chroot problems.

---

### Post by jdong on 2006-06-01
As I said, chroot is our ultimate band-aid for lack of multiarch support (i.e. apt-get install firefox.i386) :)

---

### Post by Kilz on 2006-06-01
[QUOTE=jdong]As I said, chroot is our ultimate band-aid for lack of multiarch support (i.e. apt-get install firefox.i386) :)[/QUOTE]
It may be looked at as one now. I think mainly because the adding of 32 bit applications to 64 bit Dapper is so new. People are still thinking in terms of what Breezy couldn't do , not what Dapper can do.
I'm not the most brilliant person when it comes to Linux or Ubuntu. I have only been running Linux going on 4 months now, a month on Dapper. I have more or less just tried things and have seen that they work. If I had the background of running Breezy, I'm not sure I would have tried forcing things because it didn't work. I installed a Breezy testing partition to see.
I'm bet someone will come along and write a script that will make it all a lot easier that what we are doing now. I do have an idea about making a lib32 pack to help install whats necessary, but I'm not to sure on the legality of it.

---

### Post by jdong on 2006-06-01
Messing around with installing 32-bit stuff without a 32-bit slottable /bin and a dependency manager is just plain reckless... Mark has suggested Multiarch as a goal for Edgy, so hopefully we see that realized. Until then, a chroot is the best of two worlds.

---

### Post by Weav on 2006-06-01
If I get a computer within the next few months i'm trying to determine if I really should get 64-bit.

Is it really a lot harder to get codecs and applications to work under 64 bit then it is currently with 34-bit? 

I want the fast speed, but not if it's gonna cause lots of confusion and chaos when trying to install applications or other things.

Thanks

---

### Post by Kilz on 2006-06-01
[QUOTE=jdong]Messing around with installing 32-bit stuff without a 32-bit slottable /bin and a dependency manager is just plain reckless... Mark has suggested Multiarch as a goal for Edgy, so hopefully we see that realized. Until then, a chroot is the best of two worlds.[/QUOTE]
Maybe it is, maybe it isn't, I know my system is running fine right now. Just a question, is it just as reckless to run a 32 bit OpenOffice? 
I'm not suggesting running a lot of 32 bit programs, there isn't a need to. For the most part the needed programs could be under 20, probably under 10. There is a lot of good 64 bit software already. 
Are you suggesting that the binaries need a /bin32  separate and for 32 bit executables? If so why? Are you suggesting installing 64 bit and 32 bit versions of the same software on a machine? Why would that be necessary or a good idea?
Its great that Mark has suggested that Edgy be multi arch. But what is the harm that can happen loading 32 bit lib's into a place designed for them?

---

### Post by Kilz on 2006-06-01
[QUOTE=Weav]If I get a computer within the next few months i'm trying to determine if I really should get 64-bit.

Is it really a lot harder to get codecs and applications to work under 64 bit then it is currently with 34-bit? 

I want the fast speed, but not if it's gonna cause lots of confusion and chaos when trying to install applications or other things.

Thanks[/QUOTE]
To be honest, yes it is a lot harder to get some things to run on a 64 bit system if you are using a 64 bit OS. If you want it to "just run" and be able to use auto setup scripts a 32 bit OS is the way to go. 
If on the other hand you want to customise and dont mind messing around you can install 32 bit applications into 64 bit. It may take setting up a chroot, or manualy installing dependant lib's.

---

### Post by jdong on 2006-06-01
> **Kilz]Maybe it is, maybe it isn't, I know my system is running fine right now. Just a question, is it just as reckless to run a 32 bit OpenOffice? 
[/quote]
Well, if the hard-working Ubuntu Openoffice folks did not package a 32-bit Openoffice for you, and you were suggesting trying to do it yourself, I would recommend you to a mental institution  said:**
> 
 I'm not suggesting running a lot of 32 bit programs, there isn't a need to. For the most part the needed programs could be under 20, probably under 10. There is a lot of good 64 bit software already. 
Are you suggesting that the binaries need a /bin32  separate and for 32 bit executables? If so why? Are you suggesting installing 64 bit and 32 bit versions of the same software on a machine? Why would that be necessary or a good idea?

I am suggesting the ability to slot 32-bit and 64-bit programs, side-by-side. Why? Take two popular examples: mplayer and firefox.

mplayer [which is in turn mencoder] benefits greatly from 64-bit optimizations but 32-bit codecs only work with 32-bit mplayer/mencoder. So, it's strongly desirable to be able to use 64-bit mplayer most of the times, but only run 32-bit mplayer when you have things requiring 32-bit codecs.

> Its great that Mark has suggested that Edgy be multi arch. But what is the harm that can happen loading 32 bit lib's into a place designed for them?
Nothing is wrong with it, except right now our package management system has no idea what's going on (apt-get is oblivious to those dependencies, creating the manual process you mention). Having an apt that understands multiple architectures will make it easier to say that AMD64 Ubuntu will include an i386 Openoffice, or allow simultaneous installs of mplayer and firefox, without the need for users (or developers, who have better ways to spend their time and dedicate their talents) to play janitor.

---

### Post by Kilz on 2006-06-01
> **jdong]Well, if the hard-working Ubuntu Openoffice folks did not package a 32-bit Openoffice for you, and you were suggesting trying to do it yourself, I would recommend you to a mental institution  said:**
> 
No Im not recommending a self install of 32 bit OpenOffice. The question was is it reckless to have the 32 bit OpenOffice installed?  Not if its possible for a user to install it. We both know its there.


> I am suggesting the ability to slot 32-bit and 64-bit programs, side-by-side. Why? Take two popular examples: mplayer and firefox.

mplayer [which is in turn mencoder] benefits greatly from 64-bit optimizations but 32-bit codecs only work with 32-bit mplayer/mencoder. So, it's strongly desirable to be able to use 64-bit mplayer most of the times, but only run 32-bit mplayer when you have things requiring 32-bit codecs.

Its possible to install both now. Granted its not possible to install them to the same folder. So far the one multiarch distro's I have ran will not allow you to install both, its one or the other. I haven't thought about installing multiple versions yet, but it doesn't sound like a bad idea. Maybe people installing 32 bit versions should take an extra step and create /bin32, open up the application .deb's like they have done with the lib's and copy the binaries into it.

[quote]Nothing is wrong with it, except right now our package management system has no idea what's going on (apt-get is oblivious to those dependencies, creating the manual process you mention). Having an apt that understands multiple architectures will make it easier to say that AMD64 Ubuntu will include an i386 Openoffice, or allow simultaneous installs of mplayer and firefox, without the need for users (or developers, who have better ways to spend their time and dedicate their talents) to play janitor.
But isn't that what people are already doing with chroot? They have to manually add launchers and installing duplicates of programs and do work arounds because they are in a jail? Granted it resolves some problems, but it creates others. Kind of trading one headache for another. I have never said manually loading 32 bit programs is perfect or easy, its an alternative, and isn't that what Linux is all about, alternatives and options?
When Edgy comes out it may solve all the problems and make it all a moot point. I'm not a coder, but you can bet I will be beta testing. :D But until then you can do it your way, ill keep trying mine. Other people can choose what way they want to go. In the end everyone can be happy. :)

---

### Post by panurge77 on 2006-06-01
I was using an updated version of Dapper amd64 (installed from flight7) and I moved to 32 bits now in final version and it's all strangely faster in 32 bits. So either apt-get could not make it to final version via dist-upgrade or there were something wrong with amd64. Boot is 10 seconds faster now and the system seems to be using less memory...

---

### Post by jdong on 2006-06-01
[QUOTE=Kilz]No Im not recommending a self install of 32 bit OpenOffice. The question was is it reckless to have the 32 bit OpenOffice installed?  Not if its possible for a user to install it. We both know its there.
[/quote]
No, not reckless... that is an acceptable solution for dealing with OOo not being 64-bit compilable. But, it is a labored approach from the developer end (i.e. having to manually package 32-bit binaries every time a new release gets uploaded)


> 
Its possible to install both now. Granted its not possible to install them to the same folder. So far the one multiarch distro's I have ran will not allow you to install both, its one or the other. I haven't thought about installing multiple versions yet, but it doesn't sound like a bad idea. Maybe people installing 32 bit versions should take an extra step and create /bin32, open up the application .deb's like they have done with the lib's and copy the binaries into it.

That's what I'm thinking of. a separate 32-bit bin.

> 
But isn't that what people are already doing with chroot? They have to manually add launchers and installing duplicates of programs and do work arounds because they are in a jail? Granted it resolves some problems, but it creates others. Kind of trading one headache for another. I have never said manually loading 32 bit programs is perfect or easy, its an alternative, and isn't that what Linux is all about, alternatives and options?
When Edgy comes out it may solve all the problems and make it all a moot point. I'm not a coder, but you can bet I will be beta testing. :D But until then you can do it your way, ill keep trying mine. Other people can choose what way they want to go. In the end everyone can be happy. :)

Well, that is exactly what a chroot does for users now. But proper multiarch support will be much more user-friendly and seamlessly integrated, and that's what I'd like to see for improvement.

Chroots are wonderful ,but are not easy to set up for the average beginner.

We both agree that chroots are awesome and are the way to go right now, but I still think we can do better in the future :)

---

### Post by Kilz on 2006-06-01
[QUOTE=jdong]
We both agree that chroots are awesome and are the way to go right now, but I still think we can do better in the future :)[/QUOTE]

I think it best to agree to disagree on the awesomeness of chroots and the best way to run 32 bit apps in Dapper. I will agree that they are best with Breezy  :mrgreen:

---

### Post by asc on 2006-06-02
I've been running Dapper on an AMD 64 for three months. It's extremely fast for the work I'm doing, which is system development, package building and cross-platform web dev. I can run three virtual machines, Debian stable, OpenBSD and Windows XP along with Ubuntu as the host OS. Compiling is fast and proprietary kernel modules, like vmware and nvidia are simple to install.

The one thing that took the longest to configure was a 32 bit firefox and Flash, Java and RealPlayer. None of these proprietary plugins are compiled to the 64 bit firefox. In total it took two hours of configuration.

---

### Post by JoWilly on 2006-06-03
[QUOTE=asc]
The one thing that took the longest to configure was a 32 bit firefox and Flash, Java and RealPlayer. None of these proprietary plugins are compiled to the 64 bit firefox. In total it took two hours of configuration.[/QUOTE]

The blackdown java has a 64bit plugin; it works fine and is in the repo too.

---

### Post by henriquemaia on 2006-06-04
[quote=JoWilly]The blackdown java has a 64bit plugin; it works fine and is in the repo too.[/quote]

From Sun's java site:

**System Requirements**

 J2SE Runtime Environment 5.0 is supported  on Linux platforms running on 64-bit AMD processors.   For supported versions of Linux and desktop managers, along  with disk and RAM requirements, see  [System Configurations]("http://java.sun.com/j2se/1.5.0/system-configurations.html").

64bit is supported.

---

### Post by henriquemaia on 2006-06-04
Double post. Browser problem. My appologies for this.

---

### Post by JoWilly on 2006-06-04
[QUOTE=henriquemaia]From Sun's java site:

**System Requirements**

 J2SE Runtime Environment 5.0 is supported  on Linux platforms running on 64-bit AMD processors.   For supported versions of Linux and desktop managers, along  with disk and RAM requirements, see  [System Configurations]("http://java.sun.com/j2se/1.5.0/system-configurations.html").

64bit is supported.[/QUOTE]

Yes it is (its in the repo too).

But there is no plugin yet with java 5. If you want the web 64 bit plugin you need the blackdow java (version 4, but works as well).

---

### Post by Bghmsh on 2006-06-04
I am doing some high level video editing on a 3200+ 2 GB Ram NVIDIA6800 WDSATA 160Gb and this is the fastest tghing that I have ever seen. I am converting one of my other machines (identical config) to a win 64 x2 core and would be happy to report actual data results

---

### Post by JoWilly on 2006-06-04
[QUOTE=Bghmsh]I am doing some high level video editing on a 3200+ 2 GB Ram NVIDIA6800 WDSATA 160Gb and this is the fastest tghing that I have ever seen. I am converting one of my other machines (identical config) to a win 64 x2 core and would be happy to report actual data results[/QUOTE]

Looking forward to seeing your results.

In my unscientific experience, winx64 was rather slow (general computer usage) (I haven't tried any high level video or such). Vistax64 was much better than winx64.

---

### Post by flip314 on 2006-06-05
[QUOTE=Kilz]Just a question or two. Was the OS 64 bit Breezy or Dapper? Did you have to compile the applications because there was no 64 bit version? Was there a 32 bit version?[/QUOTE]

It was 64bit Dapper vs 32bit Dapper.  Some applications that didn't come in 64-bit flavors I was able to compile from source, others wouldn't compile at all.  Wine, for example, won't compile in 64bit compilers yet, so you need to do some chrooting to get around that.  Since I wasn't getting any benefit from 64bit, I decided to put it off until there's better support.

---

### Post by Kilz on 2006-06-05
[QUOTE=flip314]It was 64bit Dapper vs 32bit Dapper.  Some applications that didn't come in 64-bit flavors I was able to compile from source, others wouldn't compile at all.  Wine, for example, won't compile in 64bit compilers yet, so you need to do some chrooting to get around that.  Since I wasn't getting any benefit from 64bit, I decided to put it off until there's better support.[/QUOTE]

You do know that you no longer need a chroot to [install 32 bit wine]("http://www.ubuntuforums.org/showthread.php?t=185557&highlight=wine+64") and most other 32 bit programs? To get most 32 bit programs installed you can use sudo dpkg --force-architecture -i <packagename> then maunaly copy in any needed lib's to /usr/lib32. Its an option that didnt work with Breezy so some people are unaware of it. Its up to you if you want to wait or use a chroot, but there are options now.

---

### Post by Dillius on 2006-06-05
[QUOTE=jdong]
(3) **64-bit with 32-bit chroot**: This is basically maintaining a little 32-bit world inside your 64-bit Ubuntu. It takes a deal of initial setup, but once set up it is a breeze to maintain. Basically, "firefox" runs 64-bit firefox while "lin32 firefox" runs a 32-bit copy of firefox. You can use "lin32 apt-get" to install software to the chroot. All repository software works in 32-bit and 64-bit, and you can choose which flavor to run via lin32.  Non-repository sources will compile cleanly under the 32-bit chroot. 32-bit drivers will not work.


So, the most compatible is #3, and if you have the disk space and 30 minutes to dedicate to a HOWTO, I recommend you go for it. That's what I'm doing right now :)[/QUOTE]

Is the Hoary version post on setting this up still accurate for Dapper?

---

### Post by jdong on 2006-06-05
Yep, the process hasn't really changed :)

---

### Post by DaveQB on 2006-06-08
I am considering going Kubuntu 64 with my soon hardware upgrade. 

I have done some research and there doesn't seem to be a clear cut best way to install 32-bit apps (Cedega mainly for me)

I have read 


[list]Someone said they just installed them as is an all worked [/list]
[list]some have used the "--force-architecture" method and minor tweaking [/list]
[list]others use a chroot setup [/list]

I like the sounds of the first one, but I think that must be mis-information.  Point 2 and using a simple argument with some manual copying sounds good, but why are people insisting with chroot's if this is so flawless ?

Any conclusions on these different ways ? 

Cheers

---

### Post by Kilz on 2006-06-08
[QUOTE=DaveQB]I am considering going Kubuntu 64 with my soon hardware upgrade. 

I have done some research and there doesn't seem to be a clear cut best way to install 32-bit apps (Cedega mainly for me)

I have read 


[list]Someone said they just installed them as is an all worked [/list]
[list]some have used the "--force-architecture" method and minor tweaking [/list]
[list]others use a chroot setup [/list]

I like the sounds of the first one, but I think that must be mis-information.  Point 2 and using a simple argument with some manual copying sounds good, but why are people insisting with chroot's if this is so flawless ?

Any conclusions on these different ways ? 

Cheers[/QUOTE]

I used --force-architecture" to get cedega and a few other programs installed. I didn't have to do anything or add anything extra for it. It just worked. I think some people are suggesting chroot's for a few reasons.
[INDENT]1. They may want to install and/or think you want to install hundreds of 32 bit programs. - In this case maybe a chroot would be better. But if you are only going to install 10-20 32 bit apps for the few 64 bit versions that don't have the features you want. It isn't really necessary anymore.
2. Its the way its always been done. - Up until the Dapper release using "--force-architecture"  just didn't work. The program wouldn't start no matter what you did. So by recommending a chroot they are recommending a method anyone can use no matter what version they have. People who read the recommendation that are still running Breezy will get the same results.
3. They believe that the program you are installing will not work even if you use "--force-architecture". - A few programs have problems or may give an error in the background. But personally I have not ran into this problem.[/INDENT]
"--force-architecture" is an option now. I'm using it without problems. But its just an option, and in the end that is what using Ubuntu or any version of Linux is about. Having options.

---

### Post by jdong on 2006-06-08
Mainly because force-architecture requires much more manual work -- copying libraries, tracking dependencies, and ultimately keeping track of security updates, etc. Not to mention you cannot install 32-bit and 64-bit software side-by-side for things like mencoder where it'd be beneficial.

---

### Post by DaveQB on 2006-06-08
Well I like this option :D

Is there a list somewhere of commonly used software that hasn't 64-bit versions available ?

So far it seems:

1. Cedega
2. Flash (but always wanted to try Gnash :) )
3. Acroread 
4. Java (or did they just recently release a 64-bit version along with their latest Linux friendly announcement)
5. w32codecs

Anything else ??

Once one knows the software thats troublesome or just doesnt work, then one can make a better decision given their situation

---

### Post by DaveQB on 2006-06-08
[QUOTE=jdong]Not to mention you cannot install 32-bit and 64-bit software side-by-side for things like mencoder where it'd be beneficial.[/QUOTE]

Please explain ?  Your meaning if one installs something like MEncoder in a 32-bit version they would not be able to use it with a codec installed on their system in a 64-bit version???

---

### Post by John Jason Jordan on 2006-06-08
[QUOTE=Kilz]I used --force-architecture" ... A few programs have problems or may give an error in the background. But personally I have not ran into this problem.[/QUOTE]

First, how does one use --force architecture? I assume it is an apt-get install argument, but where does it go in the command? Perhaps a sample line for how you install a program would make it clearer to a command-line dummy like me. Or does Synaptic in Dapper now offer a button for it? (Still using 64-bit Breezy, planning to upgrade soon.)

Second, does anyone know if it will work with Adobe Reader 7.0, RealPlayer, and Flash, and get them working as Firefox plugins as well as standalone apps?

---

### Post by DaveQB on 2006-06-08
[QUOTE=John Jason Jordan]First, how does one use --force architecture? I assume it is an apt-get install argument, but where does it go in the command? Perhaps a sample line for how you install a program would make it clearer to a command-line dummy like me. Or does Synaptic in Dapper now offer a button for it? (Still using 64-bit Breezy, planning to upgrade soon.)

Second, does anyone know if it will work with Adobe Reader 7.0, RealPlayer, and Flash, and get them working as Firefox plugins as well as standalone apps?[/QUOTE]

Its used with dpkg, not apt-get.

This means you will have to find and download the .deb manually and install it locally.  Something like this:

```

dpkg --force-architecture -i some_software.deb

```

---

### Post by jdong on 2006-06-08
[QUOTE=DaveQB]Please explain ?  Your meaning if one installs something like MEncoder in a 32-bit version they would not be able to use it with a codec installed on their system in a 64-bit version???[/QUOTE]

What I'm saying is mencoder's decoding and (more importantly) encoding algorithms receive a significant performance boost when running in 64-bit mode. However, at the same time, only the 32-bit version supports win32codecs. So, with forcing architecture, you have to choose one or another, while with chroot, you can invoke "mencoder", which launches 64-bit mencoder, or "lin32 mencoder", which invokes a 32-bit version of mencoder.

---

### Post by Kilz on 2006-06-08
[QUOTE=DaveQB]Please explain ?  Your meaning if one installs something like MEncoder in a 32-bit version they would not be able to use it with a codec installed on their system in a 64-bit version???[/QUOTE]

Yes and no. 
Yes you wouldn't be able to use a 64 bit codec with a 32 bit application. But that's true if you force or chroot. You need to have 32 bit codecs for 32 bit applications either way.
No what jdong is referring to is installing BOTH the 32 bit and 64 bit application on the same computer. While it would be nice it isn't absolutely necessary. You could also install the 32 bit application and simply rename the executable from application to application32 and still install both. I have mplayer and mplayer32 installed.

---

### Post by Kilz on 2006-06-08
[QUOTE=John Jason Jordan]First, how does one use --force architecture? I assume it is an apt-get install argument, but where does it go in the command? Perhaps a sample line for how you install a program would make it clearer to a command-line dummy like me. Or does Synaptic in Dapper now offer a button for it? (Still using 64-bit Breezy, planning to upgrade soon.)

Second, does anyone know if it will work with Adobe Reader 7.0, RealPlayer, and Flash, and get them working as Firefox plugins as well as standalone apps?[/QUOTE]

I do know that the adode reader 7.0 and firefox w/flash and java can be installed without a chroot because I have them installed. There are a few posts on getting the realplayer installed, but I havent tried it.

---

### Post by tzenes on 2006-06-08
[QUOTE=DaveQB]Well I like this option :D

Is there a list somewhere of commonly used software that hasn't 64-bit versions available ?

So far it seems:

1. Cedega
2. Flash (but always wanted to try Gnash :) )
3. Acroread 
4. Java (or did they just recently release a 64-bit version along with their latest Linux friendly announcement)
5. w32codecs

Anything else ??

Once one knows the software thats troublesome or just doesnt work, then one can make a better decision given their situation[/QUOTE]

there is a thread for this [http://www.ubuntuforums.org/showthread.php?t=191205](http://www.ubuntuforums.org/showthread.php?t=191205)
so far the only one I've gotten working is the w32codecs

There was a thread for wine (its the same thing as cedega but free) [http://www.ubuntuforums.org/showthread.php?t=184050](http://www.ubuntuforums.org/showthread.php?t=184050)

However, I haven't been able to get it to work.

---

### Post by Kilz on 2006-06-08
[QUOTE=tzenes]there is a thread for this [http://www.ubuntuforums.org/showthread.php?t=191205](http://www.ubuntuforums.org/showthread.php?t=191205)
so far the only one I've gotten working is the w32codecs

There was a thread for wine (its the same thing as cedega but free) [http://www.ubuntuforums.org/showthread.php?t=184050](http://www.ubuntuforums.org/showthread.php?t=184050)

However, I haven't been able to get it to work.[/QUOTE]

[I made a howto with instructions for just installing wine here.]("http://www.ubuntuforums.org/showthread.php?p=1114185#post1114185") Its only a few commands.
If you are getting errors, please paste in the termanal session part where you tried to install wine.

---

### Post by maddog39 on 2006-06-08
Yes, but you have to keep in mind that AMD 64-Bit processors are x86_64, meaning they can simultaniously run 32 bit and 64 bit. So if you get the 64 bit version it wont matter. However if you have an intel.... well, thats a different story lol. I just bought a Pentium D and im kinda regretting it. :/

---

### Post by jdong on 2006-06-08
[QUOTE=maddog39]Yes, but you have to keep in mind that AMD 64-Bit processors are x86_64, meaning they can simultaniously run 32 bit and 64 bit. So if you get the 64 bit version it wont matter. However if you have an intel.... well, thats a different story lol. I just bought a Pentium D and im kinda regretting it. :/[/QUOTE]
Whoa, whoa, whoa....

Intel processors supporting EM64T are also x86_64, and are compatible with AMD64 instructions (except the AMD specific ones, such as 3dnow register manipulation). I have no idea what you are referring to, but functionally you will not notice a difference between Intel and AMD 64-bit capable x86 CPU's.

---

### Post by AaronThorpe on 2006-06-09
SO this is on topic.....and I have a great question....

I just made the leap into the blue.....Just dumped microsoft for her cousin linux....(not completely, Im dual booting....but she doesn't know that :) ) So anyway, I just installed the Kubuntu breezy badger 64 bit edition as my first linux system, and boy am I off the a rough start. I'm slowly making my way through the system and learning that I can't just double click anymore. So, I ordered like 10 Kubuntu CD's because I've never ....financially supported microsoft and have every intention of distributing Linux to all my friends so they too may enjoy the vast freedom. 

Anyway...the question.....
With all the trouble im having as a noob to linux in the first place....would it just be easier for me to install dapper drake 32 bit version and save myself the hassle?

---

### Post by Kilz on 2006-06-09
[QUOTE=AaronThorpe]SO this is on topic.....and I have a great question....

I just made the leap into the blue.....Just dumped microsoft for her cousin linux....(not completely, Im dual booting....but she doesn't know that :) ) So anyway, I just installed the Kubuntu breezy badger 64 bit edition as my first linux system, and boy am I off the a rough start. I'm slowly making my way through the system and learning that I can't just double click anymore. So, I ordered like 10 Kubuntu CD's because I've never ....financially supported microsoft and have every intention of distributing Linux to all my friends so they too may enjoy the vast freedom. 

Anyway...the question.....
With all the trouble im having as a noob to linux in the first place....would it just be easier for me to install dapper drake 32 bit version and save myself the hassle?[/QUOTE]
Its quite possible that it would have been easier to start off with 32 bit. But it isn't an impossible task to get 64 bit up and running since you already have it installed. The question you need to ask is answer is what do you want the computer to do? What activities will you be doing with it?
I also think you made the correct decision to keep the duel boot until you learn more. Eventually you may decide to get rid of windows. It took me 3 months, some people never do. Also if you are into games it isn't going to matter if its 32 bit or 64 bit, you may still want to keep the windows partition for that.

---

### Post by AaronThorpe on 2006-06-09
I'll never get rid of windows entirely, I have work programs and what not that I have to use windows for...... but that's all I'd like to use windows for....i Freaking hate windows. 
Anyway, as far as what I'm doing with mycomputer now, just learning linux, I have an FTP server run off of windows, and I know that windows security is .. well ....less than secure. Right now, I just have the dual boot on one laptop. What I'd LIKE to do, is get a system..(an E-machine from Wal-Mart) just to run a server off of with Ubuntu...and yea that's going to be some time before I'm completely acclimated with Linux. As far as my laptop....just ub3r nerd bragging rights. Always been a nerd, always will be, now I can say that I'm an ub3r nerd. Of course, my previous nerd status was using mIRC and a life of IRC and file sharing. However, now that Im finally in college for computer programming...LInux just seemed the next natural step...Of course I have to use windows for work and visual logic...but other than that. All my games I play on Xbox 360. So yea, still not sure if I should make that leap to dapper drake 64 or keep my nerd self to 32....
Here's another question... did windows 64 destroy the 64 bit market?
I mean, I installed the original beta...boy did it boot fast... but that was all it did. Now, it seems that what was once a predicted explosion in the utilization of the 64-bit architecture....turned into more of an episode of seinfeld. Nothing but bad jokes and horrible writing. Anyway...
So which would be better from a noob

---

### Post by DaveQB on 2006-06-10
I'd say go for the 32-bit version to begin with.  But what would I know, haven't played wit hthe 64-bit version myself yet... in the process of upgrading to AMD64 from my Athlon 1700+ FINALLY! :) 

And its geek, NOT nerd, get it right !! :mrgreen:

---

### Post by jdong on 2006-06-10
[QUOTE=AaronThorpe]
Here's another question... did windows 64 destroy the 64 bit market?
I mean, I installed the original beta...boy did it boot fast... but that was all it did. Now, it seems that what was once a predicted explosion in the utilization of the 64-bit architecture....turned into more of an episode of seinfeld. Nothing but bad jokes and horrible writing. Anyway...
So which would be better from a noob[/QUOTE]

Hmm, I wouldn't say so... I would say that Windows XP x64 did squash a lot of the initial enthusiasm surrounding consumer-oriented 64-bit OSes, as did Linux when the x86-64 ports were just coming out (i.e. Gentoo and the other pioneers). It took a while for people to understand how big of a migration this really is.

---

### Post by JoWilly on 2006-06-11
[quote=maddog39]Yes, but you have to keep in mind that AMD 64-Bit processors are x86_64, meaning they can simultaniously run 32 bit and 64 bit. So if you get the 64 bit version it wont matter. However if you have an intel.... well, thats a different story lol. I just bought a Pentium D and im kinda regretting it. :/[/quote] 
Hmmm ? Why so ?

To confirm what jdong said above, I am running dapper 64 on a Pentium D.

Everything works perfectly on dual core, including all 32 bit apps (adobe reader, wine, cedega & windows games, realplayer, flash, crossover office, etc...).

Edit: even nerolinux 32 bit works fine in dapper64

---

### Post by DaveQB on 2006-06-12
What is/was your install method for those 32-bit apps **JoWilly** ??

---

### Post by JoWilly on 2006-06-12
[quote=DaveQB]What is/was your install method for those 32-bit apps **JoWilly** ??[/quote] 
I install all 32bit deb packages with "dpkg -i --force-architecture" (you will find several threads about this in these forums, and there is now also a nice wiki in the ubuntu wikis).

I might also add that the linux picasa also works fine.

There are only 2 details to keep in mind at the moment:

1. nerolinux need 2 32bit libs : for this you open the 32bit debs of gtk1.2 and glib1.2 with the archive manager and copy the .so to /usr/lib32

2. for 32bit plugins in firefox (retail flash,realplayer) you need firefox32 (easiest is to use the one from getfirefox.com)

Apart from the above 2 details, all 32bit apps I have listed install directly with dpkg. I have not found 1 32bit app I could not run.

Edit: don't forget that the ia32 deb packages from the repos (include the 32bit libs) need to be installed.

---

### Post by DaveQB on 2006-06-12
This is very encouraging to use the 64-bit version of Kubuntu.

Thanks.

---

### Post by SVT_Tour on 2006-06-12
Based on this thread I want to switch from Dapper 32 to Dapper 64.  I partitioned my hard drive with an extra 15 gb partition that I want to install it into.  Can I use my same home directory which is in its own partition?  I saw there was a conflict with 32 bit Firefox plug-ins.  Is there anything else I should watch out for?  Or, should I just blow away 32 bit Dapper and start over?
Thanks for the help

---

### Post by JoWilly on 2006-06-12
[quote=SVT_Tour]Based on this thread I want to switch from Dapper 32 to Dapper 64.  I partitioned my hard drive with an extra 15 gb partition that I want to install it into.  Can I use my same home directory which is in its own partition?  I saw there was a conflict with 32 bit Firefox plug-ins.  Is there anything else I should watch out for?  Or, should I just blow away 32 bit Dapper and start over?
Thanks for the help[/quote]

I would say as you already have a working 32bit dapper, its good to install dapper64 on another partition to see if it suits your needs.

Apart from the 32bit web plugins I don't see what else could cause any trouble; in a default install your home directory almost essentially contains config files and no apps. So yes, you should be good to go.

---

### Post by JoWilly on 2006-06-12
... just to add that the native linux Google Earth 4 beta is working perfectly on dapper 64 :D
[URL="http://earth.google.com/download-earth.html"]
http://earth.google.com/download-earth.html[/URL]

---

### Post by dmn_clown on 2006-06-14
[QUOTE=JoWilly]If a 32 app needs some lib, just get the 32 bit dapper deb file, and open it with the archive manager (file-roller), and copy the content of /usr/lib to /usr/lib32.[/QUOTE]

Wouldn't it be easier to to use dpkg?

```
sudo dpkg -x libxyz.i386.deb /usr/lib32
```

---

### Post by jdong on 2006-06-14
I don't think that'd work. That'll put things in /usr/lib32/usr/lib.

---

### Post by JoWilly on 2006-06-14
[quote=dmn_clown]Wouldn't it be easier to to use dpkg?

```
sudo dpkg -x libxyz.i386.deb /usr/lib32
```[/quote] 
Hmm.... I never tried this.

The deb includes its directory tree. Are you sure that dpkg will not extract the deb's dir tree inside /usr/lib32 if you do it this way ?

Edit: jdong beat me to it :)

---

### Post by Mace68 on 2006-08-26
> **dmn_clown said:**
> Wouldn't it be easier to to use dpkg?

```
sudo dpkg -x libxyz.i386.deb /usr/lib32
```

> **jdong said:**
> I don't think that'd work. That'll put things in /usr/lib32/usr/lib.

Would it work if lib was a symlink in /usr/lib32/usr/ pointing to /usr/lib32/ ?

i.e. before using "sudo dpkg -x libxyz.i386.deb /usr/lib32" for the first time do
```
sudo mkdir -p /usr/lib32/usr
sudo ln -s /usr/lib32 /usr/lib32/usr/lib
```
so everything will go into the correct location?

---

### Post by DaveQB on 2006-08-27
I remembering reading through this thread a few weeks ago and thinking when I go 64bit I have to look back through here to work out what I need to manually copy to /usr/lib32.  But doing some googling I found mention of an app/wrapper called Linux32.  Simply use that to call an app do it will be run in "32bit mode".  Wouldn't this solve everyone's problems ? Did it come out after this thread was started or are their some gotchas with linux32 wrapper ?

Also, on a side note. If I compile something in my current 64bit environment it will default to being a 64bit binary and thus will not run on a 32bit only machine ? Or do you need to specifically call something to gcc to compile a 64bit binary ?

Thanks all.

---

### Post by DaveQB on 2006-08-27
Found a nice and simple how-to to get a few 32bit apps only working 

[http://polishlinux.org/linux/ubuntu/kubuntu-606-on-athlon-64/](http://polishlinux.org/linux/ubuntu/kubuntu-606-on-athlon-64/)

Starts about half way down.

---

### Post by jdong on 2006-08-27
> **DaveQB said:**
> I remembering reading through this thread a few weeks ago and thinking when I go 64bit I have to look back through here to work out what I need to manually copy to /usr/lib32.  But doing some googling I found mention of an app/wrapper called Linux32.  Simply use that to call an app do it will be run in "32bit mode".  Wouldn't this solve everyone's problems ? Did it come out after this thread was started or are their some gotchas with linux32 wrapper ?

That's not exactly what the linux32 wrapper does. Linux32 simply sets the current architecture to i386 instead of x86_64. It does not change whether or not a binary is 32-bit or 64-bit, it just tells Linux to "lie" about the architecture. It's used to fool programs into thinking they're running on a 32-bit system when you are in fact running a 64-bit OS. Most of the chroot solutions you see here use linux32 to start a shell, but you still need 32-bit binaries installed to use linux32.
> 
Also, on a side note. If I compile something in my current 64bit environment it will default to being a 64bit binary and thus will not run on a 32bit only machine ? Or do you need to specifically call something to gcc to compile a 64bit binary ?

Thanks all.
Correct, gcc will default to making 64-bit binaries. You use the flag -m32 to generate a 32-bit binary.

---

