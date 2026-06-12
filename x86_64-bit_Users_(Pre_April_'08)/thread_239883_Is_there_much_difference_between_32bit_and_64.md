---
title: "Is there much difference between 32bit and 64?"
date: 2006-08-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by janhenderson on 2006-08-19
I'm running ubuntu amd64 but I'm becoming frustrated that some applications are not available or are a lot more work to get working. For example, I couldn't get squeak to run on ubuntu amd64, and I tried their mailing lists and I figured it just won't happen any time soon. Other things like how there seems to be fewer packages for ubuntu amd64 than the 32bit version, especially so for proprietary software. I even have a friend who just gave up and installed the 32bit on his amd64 because he had problems with wine. What's been your experience?

---

### Post by VirtuAlex on 2006-08-20
> **janhenderson said:**
> What's been your experience?
I'm stubborn enough to use 64. If you feel it takes too much time to get stuff working and you absolutely can't afford to waste your time learning how to do this and that in 64, then you just should run 32. Nobody would ever blame you or call you traitor. There are problems, most of them either fixable or insignificant. The only difference is time you spend learning. I think in 64 you're learning more, so I prefer it.

---

### Post by Kilz on 2006-08-20
> **janhenderson said:**
> I'm running ubuntu amd64 but I'm becoming frustrated that some applications are not available or are a lot more work to get working. For example, I couldn't get squeak to run on ubuntu amd64, and I tried their mailing lists and I figured it just won't happen any time soon. Other things like how there seems to be fewer packages for ubuntu amd64 than the 32bit version, especially so for proprietary software. I even have a friend who just gave up and installed the 32bit on his amd64 because he had problems with wine. What's been your experience?

Wine is installable, check my signature. So is flash and lots of other programs. For Wine its a whopping whole 2 commands to run a install script, then a setup script. I wish I could make it one, but the install needs to be as sudo, and the setup cant be run as sudo.
The diffrence in avalable applications is 2%. Squeak is in the 64bit repositories. [I recommend this page]("http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic") for learning how to install applications with Synaptic. It is in the multiverse, so you are going to have to enable the [extra repositories in Synaptic.]("http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")
This is common stuff you have to know regardless if you run 32 or 64 bit. Synaptic is the main way things are installed.
If you have a problem finding or installing , its best to ask here. Most of the people on the forums will be glad to point you to a page to help. :D

---

### Post by iamhugeinjapan on 2006-08-21
I would like to know if 64 bit boots faster than 32 bit on the same hardware.

Are there any stats on that?

---

### Post by VirtuAlex on 2006-08-21
doubt anyone ever measured it, and doubt there would be any significant difference

---

### Post by janhenderson on 2006-08-21
I just would like to know what advantage I get by running amd64 ubuntu and whether it's significant.

---

### Post by RAOF on 2006-08-21
> **VirtuAlex said:**
> doubt anyone ever measured it, and doubt there would be andy significant difference

Measured by Anandtech, and the difference **is** significant, at least for some things.  Particularly: audio/video encoding/decoding is, on average, 30% faster on the same hardware (x86-64 vs IA32).  Some things (SSL encryption, from memory) were 100% faster under x86-64.

The link to those benchmarks is **somewhere** in my previous posts.  I can't be bothered trawling through to find it at the moment, though :p

Edit: Whoops, the original question was **boots** faster.  No, no idea.  I don't really care about boot time :).  There **is** a reason to use the 64 bit version of Ubuntu, though.  It's faster :).

---

### Post by cocteau on 2006-08-21
I've generally had good experience running 64bit. There has been some problems yes, but using google and these forums has helped me solve most of them.

I'm running wine and firefox with flash and java, thanks to Kilz' guides. Compiling is much faster on 64bit and my feeling is that programs execute faster in general even though I haven't installed a 32bit system to test it against.

The biggest problem I've had (and still has) is poor driver support for my ATI graphics card but that is really more ATIs fault than Ubuntus.

---

### Post by Kilz on 2006-08-21
> **cocteau said:**
> The biggest problem I've had (and still has) is poor driver support for my ATI graphics card but that is really more ATIs fault than Ubuntus.

I agree that ATI has problems since my system has radon x200 graphics. My advice is if you ever get a working driver, dont upgrade it. But looking at the forums, this isnt a 64bit issue. Everyone with ATI has problems.

---

### Post by vanstrien on 2006-08-21
I've run some tests on my box running 32bit and 64bit Ubuntu, although nothing fancy enough to run.  For the most part 64bit is marginally faster, but not anything I would describe perceptibly so.  And as to your original question, I didn't see any faster bootup after moving to 64bit.  

In fact, I'm not so sure some programs aren't running slower.  My 32bit Ubuntu ran like a dream, but since 64bit is a bit of kludge, I think some software isn't installed in its ideal state.

The moral of the story is that if you want a bit of a challenge to squeeze more out of your box, go 64bit.  If you want the pleasure of Ubuntu without the hassles, you really aren't going to lose anything perceptible using 32bit.

---

### Post by Kilz on 2006-08-21
> **vanstrien said:**
> I've run some tests on my box running 32bit and 64bit Ubuntu, although nothing fancy enough to run.  For the most part 64bit is marginally faster, but not anything I would describe perceptibly so.  And as to your original question, I didn't see any faster bootup after moving to 64bit.  

In fact, I'm not so sure some programs aren't running slower.  My 32bit Ubuntu ran like a dream, but since 64bit is a bit of kludge, I think some software isn't installed in its ideal state.

The moral of the story is that if you want a bit of a challenge to squeeze more out of your box, go 64bit.  If you want the pleasure of Ubuntu without the hassles, you really aren't going to lose anything perceptible using 32bit.

AS with anything YMMV. Bootup isnt something that may improve regardeless of the version. 
But like I have said before. If you want a OS that is simple to install, where all you do is pop in a CD and do nothing else. Dont install Linux because _ANY_ version is going to require some setup.
If you want a pop in OS , pop in a Windows restore CD. Of corse there are issues you will have to deal with all the time like spyware, viruses, phone home applications, etc.
To me the setup is nothing to the constant headaches I got with Windows. But some people want Linux to be a safer windows. [Remember Linux is not Windows.]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by cocteau on 2006-08-22
> **vanstrien said:**
> My 32bit Ubuntu ran like a dream.

I've never, not ever, had any operating system that ran like a dream without hassles or additional setup required. Not Ubuntu, Gentoo, Fedora, Windows or OS-X.

But 64bit Ubuntu has so far been the best setup I've had.

---

### Post by janhenderson on 2006-08-22
> **cocteau said:**
> I've never, not ever, had any operating system that ran like a dream without hassles or additional setup required. Not Ubuntu, Gentoo, Fedora, Windows or OS-X.

But 64bit Ubuntu has so far been the best setup I've had.

OK. After perhaps a couple of months of running ubuntu amd64, I'm now running the i386 one. I don't notice any slowdown at all. What I notice though is that getting a desktop set up with the i386 is much more convenient. There seems to be many packages available from the repositories for i386 that aren't for amd64. For example, squeak, scheme48, cmucl, flash, codecs, java 5, and so on. See, I already know how to compile software, it's just a needless hassle, to get the sources, get the development dependencies, and so on. There's a point when you stop learning more in something (eg, installing from source) and it just becomes a needless chore. I'd much rather have something in the repositories.

---

### Post by Kilz on 2006-08-23
> **janhenderson said:**
> OK. After perhaps a couple of months of running ubuntu amd64, I'm now running the i386 one. I don't notice any slowdown at all. What I notice though is that getting a desktop set up with the i386 is much more convenient. **There seems to be many packages available from the repositories for i386 that aren't for amd64. For example, squeak, scheme48, cmucl, flash, codecs, java 5, and so on.** See, I already know how to compile software, it's just a needless hassle, to get the sources, get the development dependencies, and so on. There's a point when you stop learning more in something (eg, installing from source) and it just becomes a needless chore. I'd much rather have something in the repositories.

That's not the truth, 2 of the listed packages are not in the repositories. The rest are, or can be installed with a script of mine and 2 commands in a terminal. So compiling 2 packages is to much of a bother when you already know how. I could see if you didn't know how to compile and install. But you do.
By the way, you have noticed something is missing. You know how to compile. Instead of compiling and maybe, I don't know, making a .deb file so others can have it. You just take, the easy way out. :roll: 
To me this is just plain sad. Ubuntu is community driven. Part of being in any community is giving back something to that community when you can.

---

### Post by AllenGG on 2006-08-23
First, I use my computers to help me make money. (yes, yes, I'm a filthy..etc)
The original question, a valid one , has not been answered.
these quotes **[COLOR=Sienna]from above[/COLOR]**:
[B][COLOR=Teal]"I'm running ubuntu amd64 but I'm becoming frustrated that some applications are not available"
"I would like to know if 64 bit boots faster than 32 bit on the same hardware."
"I just would like to know what advantage I get by running amd64 ubuntu"
"Everyone with ATI has problems."
"After perhaps a couple of months of running ubuntu amd64, I'm now running the i386 one"
*[SIZE=2]end[/SIZE][/COLOR][/B]
64 bit users have been described as 'pioneers'. The only way I could get use of my AMD64 machine was with Ubuntu 5.03
Why buy a 64 bit machine ?
[SIZE=5][COLOR=Sienna] My 32 bit "monster" works well, the 64bit is much faster, more versatile.[/COLOR][/SIZE] 
Only Ubuntu has a solution for Nvidia on 64bit.
For me (extreme impatience), coupling **[COLOR=DarkOrange]Automatix with Synaptic [/COLOR]**has worked effectively, if you haven't tried it, do so:
**[COLOR=DarkRed][AUTOMATIX.]("http://www.getautomatix.com/")[/COLOR]**

---

### Post by Kilz on 2006-08-23
> **AllenGG said:**
> First, I use my computers to help me make money. (yes, yes, I'm a filthy..etc)
The original question, a valid one , has not been answered.
these quotes **[COLOR=Sienna]from above[/COLOR]**:
[B][COLOR=Teal]"I'm running ubuntu amd64 but I'm becoming frustrated that some applications are not available"
"I would like to know if 64 bit boots faster than 32 bit on the same hardware."
"I just would like to know what advantage I get by running amd64 ubuntu"
"Everyone with ATI has problems."
"After perhaps a couple of months of running ubuntu amd64, I'm now running the i386 one"
*[SIZE=2]end[/SIZE][/COLOR][/B]
64 bit users have been described as 'pioneers'. The only way I could get use of my AMD64 machine was with Ubuntu 5.03
Why buy a 64 bit machine ?
[SIZE=5][COLOR=Sienna] My 32 bit "monster" works well, the 64bit is much faster, more versatile.[/COLOR][/SIZE] 
Only Ubuntu has a solution for Nvidia on 64bit.
For me (extreme impatience), coupling **[COLOR=DarkOrange]Automatix with Synaptic [/COLOR]**has worked effectively, if you haven't tried it, do so:
**[COLOR=DarkRed][AUTOMATIX.]("http://www.getautomatix.com/")[/COLOR]**

I think the orignal question of if one or the other version boots faster has been answerd. Basicly the answer is yes. But not a lot of time saving is in the boot time, but in the running applications time.
The concept of everyone with ATI graphics has problems is a truth. I have ATI on 2 computers on my home network. Neither was an easy setup. Upgrading ATI is a disaster. I have yet to have one go right.
The Advantages, Ill add one. I have a cdrom with the 64bit version. I dont with the i386. I found this out when I "upgraded" my ATI drivers this weekend and ennded up having to reinstall. Mistakenly I put the i386 install disk in. I will never make that mistake again. Once it installed and rebooted, the cd wouldnt mount anything.
As for applications, the Orignal poster in post 1 and his last post said squeak wasnt in the repositories. Guess what. It is. [B][COLOR="Blue"]I find a lot of newbies claim applications are missing when in fact they dont have all the repositories enabled.

[/COLOR][/B]

---

### Post by janhenderson on 2006-08-23
I really think it comes down to this. I installed the i386 and then ran automatix, followed by installing the kubuntu-desktop and following the xgl tutorial on the wiki. This gave me a media ready and complete desktop within a handful of hours (of mostly waiting, including downloading the distro, user intervention itself is measurable in perhaps minutes). With the amd64 the story was all different, by the time I changed to i386 yesterday, I had not been able to get some things working, such as xgl though I'd tried all available tutorials, realplayer so I was unable to watch BBC footage, slab menu though i'd tried to compile it, and various other things. It seems you have far more luck of success in getting something working by following a tutorial if you have i386 than amd64 ubuntu, and yes, I did follow the amd64 tutorials where available. 

Anyhow. I'm running now 8 windows, one of them is firefox with 14 tabs, and the responsiveness of the system is instantaneous. Xgl was slow though and seems useless. I'm now settled on kde so the slab menu is of no concern for me anymore. So I may still go back to amd64. 

I'm new to using linux as a primary desktop. Those past two months are my first. I don't feel in a good position of knowledge to give back yet, and my estimation is that learning will take months at least, but I don't want to wait till then to have a functional desktop, especially that the things I'd be hassling with, such as the media stuff, is really of no interest to me in hassling with.

---

### Post by Kilz on 2006-08-23
> **janhenderson said:**
> I really think it comes down to this. I installed the i386 and then ran automatix, followed by installing the kubuntu-desktop and following the xgl tutorial on the wiki. This gave me a media ready and complete desktop within a handful of hours (of mostly waiting, including downloading the distro, user intervention itself is measurable in perhaps minutes). With the amd64 the story was all different, by the time I changed to i386 yesterday, I had not been able to get some things working, such as xgl though I'd tried all available tutorials, realplayer so I was unable to watch BBC footage, slab menu though i'd tried to compile it, and various other things. It seems you have far more luck of success in getting something working by following a tutorial if you have i386 than amd64 ubuntu, and yes, I did follow the amd64 tutorials where available. 

Anyhow. I'm running now 8 windows, one of them is firefox with 14 tabs, and the responsiveness of the system is instantaneous. Xgl was slow though and seems useless. I'm now settled on kde so the slab menu is of no concern for me anymore. So I may still go back to amd64. 

I'm new to using linux as a primary desktop. Those past two months are my first. I don't feel in a good position of knowledge to give back yet, and my estimation is that learning will take months at least, but I don't want to wait till then to have a functional desktop, especially that the things I'd be hassling with, such as the media stuff, is really of no interest to me in hassling with.

I guess what you said about being able to compile things was a lie then? Go head out to i386 land, have fun. Dont contribute anything, just like lots of others. Just keep taking and never give back a thing.

---

### Post by adhuvi on 2006-08-23
> **Kilz said:**
> I guess what you said about being able to compile things was a lie then? Go head out to i386 land, have fun. Dont contribute anything, just like lots of others. Just keep taking and never give back a thing.

I've followed this trat since the start of it  because I recently bought a 64 bit pc and as I previously ran ubuntu on my 32 bit for about 5 months and was very happy I was really eager to install ubuntu 64bit on my new machine. Ican't deny I was dissappointed when I found out about the problems with some apps since I don't have the time to learn all I want. To date I haven't bean able to run flash (and I followed your how to with no succes), nor download de libdvdcodec (synaptic just wont let me) nor manage to enable other repositories (I select them and find them unselected next time I open) and the list goes on. I'd sincerely tought about having a dual boot with a 32bit version and come here only when I have the time to install thing and stuff.

I don't think janhenderson lied when he said he could compile, maybe he used the term incorrectly, that would prove he is new in this and I share the tought about not being able to give back jet. However I'v tried, as you could see in my posts.

Edit: Just installed libdvdcss2 with succes :D , about to test them.

---

### Post by Kilz on 2006-08-23
> **adhuvi said:**
> I've followed this trat since the start of it  because I recently bought a 64 bit pc and as I previously ran ubuntu on my 32 bit for about 5 months and was very happy I was really eager to install ubuntu 64bit on my new machine. Ican't deny I was dissappointed when I found out about the problems with some apps since I don't have the time to learn all I want. To date I haven't bean able to run flash (and I followed your how to with no succes), nor download de libdvdcodec (synaptic just wont let me) nor manage to enable other repositories (I select them and find them unselected next time I open) and the list goes on. I'd sincerely tought about having a dual boot with a 32bit version and come here only when I have the time to install thing and stuff.

I don't think janhenderson lied when he said he could compile, maybe he used the term incorrectly, that would prove he is new in this and I share the tought about not being able to give back jet. However I'v tried, as you could see in my posts.

Edit: Just installed libdvdcss2 with succes :D , about to test them.

Ok you raise a few issues, Ill try to give you some answers to your problems.
1) Dont follow the Howto, download the automatic setup script on the howto's page. 
2) Install libdvdread3 in synaptic and follow the [instructions here]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9")
3)Once you have checked the boxes and clicked ok the repositories are enabled, the next time you open it the boxes will be unchecked, but they are enabled.

I think he knows how to compile things. Once compiled making a deb file is easy as filling out a text file called controll, and using dpkg in the terminal.
Dont get me wrong. I could care less if he uses i386, some other distro, or goes back to windows. what Im sick of is people complaining and not doing anything but complaining. Some people cant do anything, so you cant expect them to give back. But when someone makes the statment that they can compile, but they just are to lazy. I tend to think that kind of person isnt worth helping.

---

### Post by droogy on 2006-08-23
> **vanstrien said:**
> I've run some tests on my box running 32bit and 64bit Ubuntu, although nothing fancy enough to run.  For the most part 64bit is marginally faster, but not anything I would describe perceptibly so.  And as to your original question, I didn't see any faster bootup after moving to 64bit.  

In fact, I'm not so sure some programs aren't running slower.  My 32bit Ubuntu ran like a dream, but since 64bit is a bit of kludge, I think some software isn't installed in its ideal state.

The moral of the story is that if you want a bit of a challenge to squeeze more out of your box, go 64bit.  If you want the pleasure of Ubuntu without the hassles, you really aren't going to lose anything perceptible using 32bit.

Agreed.. 100%.  I've gone 32 from using 64 and havn't noticed a difference other than less hassle.  Once there is more support, I'll consider going back.

To those using 64... let me know when it's ok!

---

### Post by janhenderson on 2006-08-23
> **Kilz said:**
> I guess what you said about being able to compile things was a lie then? Go head out to i386 land, have fun. Dont contribute anything, just like lots of others. Just keep taking and never give back a thing.

Why are you being needlessly confrontational over this? and why would I have "lied"? Look, I know how to compile in the sense that I know to do "configure make checkinstall", and before that try to check the dependencies and if possible ask about them or follow the instructions given, but if there is an error or if i need to pass some parameters then I have no idea what to do. Does this mean I'm "able to compile things"? Yes, in a basic sense, I think so. Does it make an expert at it. No, far from it. 

Has my basic knowledge (3 commands!) of compiling made me successful at compiling everything I'd attempted. Nope. Not at all. It worked if things were straight forward, but there were a few things I'd attempted that I couldn't get compiled; it's really that simple, if things don't behave as expected or as per the instructions then I don't know what to do. 

As for giving back. Give back what? My failures at getting an AMD64 box to work well despite a month or more of tinkering? Give back a 64bit realplayer? I've answered some questions on the forums in what I'd known, such relating to themes and firefox.

---

### Post by Kilz on 2006-08-23
> **droogy said:**
> Agreed.. 100%.  I've gone 32 from using 64 and havn't noticed a difference other than less hassle.  Once there is more support, I'll consider going back.

To those using 64... let me know when it's ok!

Its ok :D

You tried to get 64bit working, looks to me not one of your 12 posts is about installing 64bit. How hard did you try if you didnt ask questions?
The person you quoted as agreeing with has 5 posts, none of them are about getting 64bit running. 3 in the beginers, one in this thread, and one in artwork. Come on at least quote from someone who uses the os. not someone who failed at it.

---

### Post by Kilz on 2006-08-23
> **janhenderson said:**
> Why are you being needlessly confrontational over this? and why would I have "lied"? Look, I know how to compile in the sense that I know to do "configure make checkinstall", and before that try to check the dependencies and if possible ask about them or follow the instructions given, but if there is an error or if i need to pass some parameters then I have no idea what to do. Does this mean I'm "able to compile things"? Yes, in a basic sense, I think so. Does it make an expert at it. No, far from it. 

Has my basic knowledge (3 commands!) of compiling made me successful at compiling everything I'd attempted. Nope. Not at all. It worked if things were straight forward, but there were a few things I'd attempted that I couldn't get compiled; it's really that simple, if things don't behave as expected or as per the instructions then I don't know what to do. 

As for giving back. Give back what? My failures at getting an AMD64 box to work well despite a month or more of tinkering? Give back a 64bit realplayer? I've answered some questions on the forums in what I'd known, such relating to themes and firefox.
:---) Two of the applications you complained about not being in 64bit were development packages. Why would you need them if you couldnt compile?

---

### Post by janhenderson on 2006-08-24
> **Kilz said:**
> :---) Two of the applications you complained about not being in 64bit were development packages. Why would you need them if you couldnt compile?

Which ones? Squeak, scheme48, and cmucl? Those are interpreted languages, they don't require compilation. I'm a newbie at them anyhow. There's a good reason I'm learning those "unpopular" languages; I've been advised they're good teaching languages and good to start with. Squeak is used to teach kids, scheme-lisp is use to teach in college. I've never learned C. 

As for what you said about them not being in the repositories, I assume you checked for them with apt-get from your amd64 like I did, and you're right, if you're using amd64 ubuntu, they're not in the repos, but if you're using i386, well, look... 

[http://packages.ubuntu.com/dapper/devel/cmucl](http://packages.ubuntu.com/dapper/devel/cmucl)
[http://packages.ubuntu.com/dapper/interpreters/scheme48](http://packages.ubuntu.com/dapper/interpreters/scheme48)
[http://packages.ubuntu.com/dapper/interpreters/squeak-vm](http://packages.ubuntu.com/dapper/interpreters/squeak-vm)

There's also a good reason I'm using ubuntu, a newbie distro, and not something more advanced, like perhaps, gentoo or whatever.

---

### Post by Kilz on 2006-08-24
> **janhenderson said:**
> Which ones? Squeak, scheme48, and cmucl? Those are interpreted languages, they don't require compilation. I'm a newbie at them anyhow. There's a good reason I'm learning those "unpopular" languages; I've been advised they're good teaching languages and good to start with. Squeak is used to teach kids, scheme-lisp is use to teach in college. I've never learned C. 

As for what you said about them not being in the repositories, I assume you checked for them with apt-get from your amd64 like I did, and you're right, if you're using amd64 ubuntu, they're not in the repos, but if you're using i386, well, look... 

[http://packages.ubuntu.com/dapper/devel/cmucl](http://packages.ubuntu.com/dapper/devel/cmucl)
[http://packages.ubuntu.com/dapper/interpreters/scheme48](http://packages.ubuntu.com/dapper/interpreters/scheme48)
[http://packages.ubuntu.com/dapper/interpreters/squeak-vm](http://packages.ubuntu.com/dapper/interpreters/squeak-vm)

There's also a good reason I'm using ubuntu, a newbie distro, and not something more advanced, like perhaps, gentoo or whatever.

From the cmucl page you linked to
"This is the basis package for CMUCL. It contains the base image with the **compiler,** PCL (CLOS), and the tty based debugger."

Seems to me code from one of them needs to be compiled.

---

### Post by peterpixel on 2006-08-24
Well, I just joined the forum a couple of minutes ago. I have installed 64bit Ubuntu on my laptop twice already but I never really got into it. I just basically checked it out and removed it after a few weeks. Didn't even fiddle around all that much. I am, however, seriously considering turning Ubuntu into my main OS pretty soon, but like others here I am not sure wether I should go for 32 or 64. I had a look at [getautomatix](http://getautomatix.com/) and it does look like I will be able to get most things that I need quite painlessly for my 64 bit Ubuntu. But, if the perfomance difference is so little I might not bother with it and just settle for 32 bit.

Still very undecided.

---

### Post by dpw2atox on 2006-08-24
Ive noticed that 64bit ubuntu is a lot faster at package management, zipping/unzipping and encoding, other than that its just a little faster overall. 64bit right now does take a little more work to get everything working, for example i have a 32bit firefox, java and flash installed that i use over the packaged 64bit firefox. 

If you want an easy install just go with the 32bit distro, if you wanna tinket, get the 64bit ubuntu.

---

### Post by janhenderson on 2006-08-24
> **Kilz said:**
> From the cmucl page you linked to
"This is the basis package for CMUCL. It contains the base image with the **compiler,** PCL (CLOS), and the tty based debugger."

Seems to me code from one of them needs to be compiled.

Well thanks for pointing this out. I downloaded it as suggested by this page, not run it yet. 

[http://www.cliki.net/SLIME](http://www.cliki.net/SLIME)

Sounds I'll need to use another lisp, perhaps sbcl or clisp.

---

### Post by digi421 on 2006-08-25
I installed xgl and compiz following the guide specifically made for 64-bit here in the forums and it runs just fine. It's extremely fast, really smooth and generally quite sexy :mrgreen: 
I have found that a couple of apps are not available to 64-bit users (though I can't remember which ones).

---

### Post by Kilz on 2006-08-25
> **digi421 said:**
> I installed xgl and compiz following the guide specifically made for 64-bit here in the forums and it runs just fine. It's extremely fast, really smooth and generally quite sexy :mrgreen: 
I have found that a couple of apps are not available to 64-bit users (though I can't remember which ones).

Then they couldnt have been that important. If you find another that you would like to use post it in the sticky or on the forum to see if it isnt avaialable.

---

### Post by cantormath on 2006-08-25
> **janhenderson said:**
> I'm running ubuntu amd64 but I'm becoming frustrated that some applications are not available or are a lot more work to get working. For example, I couldn't get squeak to run on ubuntu amd64, and I tried their mailing lists and I figured it just won't happen any time soon. Other things like how there seems to be fewer packages for ubuntu amd64 than the 32bit version, especially so for proprietary software. I even have a friend who just gave up and installed the 32bit on his amd64 because he had problems with wine. What's been your experience?

yes

---

### Post by Kilz on 2006-08-25
> **cantormath said:**
> yes

You gave up on 64bit because you couldnt get wine installed? Did you post in the 64bit forum area and say you could not get it to work?

---

### Post by coyote._.solitario on 2008-03-25
i think if you got an 64bit machine you should work with the apropiate OS. i'm running an ubuntu7.1 amd 64 on an amd64bit 3000+ without any problems, wine works, flash also, only some programs are restricted in synaptics telling this version is not compatible or suported for an 64bit OS. but nothing really needed to get an well wrking OS.

---

### Post by Alyxandor on 2008-04-30
Maybe I can settle this issue once and for all...  Please note, this IS my first post, because I installed Ubuntu Studio {7.1} amd64 last night...

AND HERE I AM!!  A seven disc centOS install couldn't get me online because I'm using wireless on my dev box, and I don't have fifty feet of CAT 5 and I'm too lazy to unplug and move my equipment to the modem...  Anyway, I've installed Linux a few times, but am essentially mired in newbs-ville, yet the Ubuntu amd64 had me online and editing graphics in less than two hours... And the verdict is?

Inkscape runs about four times faster {personal, non-benchmark}.  An image I was editting at 1024 + 768 pixels in Winblows 32 was making my intel Quad @ 2.4 and 4GB RAM lag like mad...  Even with all other apps closed.  Now?  I've got music running, eclipse jvm hogging 400MB, firefox with my leaky development website on it, and STILL inkscape zooms in and out with sub-second screen refresh.

YOU PEOPLE HAVE SAVED ME MANY, MANY, MANY SECONDS OF WAITING OVER AND OVER AND OVER AGAIN.  THANK YOU!!

{note...  I'm currently upgrading to Hardy in the hopes that it will give me easier access to the 32 media-packages I so sorely desire}  yes?  no?

---

