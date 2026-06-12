---
title: "New Linux user: Should I switch to 32bit?"
date: 2006-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by pbaehr on 2006-01-19
I'm new to Linux. I'm coming from Windows. I would consider myself above average, but not expert when it comes to computers.

I recently installed the 64 bit version of Breezy. I've managed to get things set up pretty decent. I love the whole apt-get concept, but I run into trouble when I can't find a 64 bit package for something I want to install. My understanding is that the only solution at that point is to compile from source, something which I've yet to have luck completing.

To further the problem, I have an ATI Radeon video card and can't seem to enable 3d acceleration. Apparently that's a pretty common problem but I don't know enough about the inner workings of Linux yet to even know where to start. (I could do it in a flash in Windows).

Long story short (I tend to ramble), would I have a much easier time getting a handle on things in the 32 bit version? Is it better supported or am I going to run into the same problems? Should I start with 32 bit and switch back to 64 bit once I've got my feet wet?

---

### Post by brk3 on 2006-01-19
Hmm. I would stick to the 64-bit, compiling most packages isnt too hard once you have the main developement libraries installed. If you would like to post the details of one you've tried to compile and failed, I could tell you what the problem is.
The main steps are:

- Install checkinstall(this is a package that allows you to create .debs of source files so they're easier to keep track of and uninstall later).

- type ./configure

- type make

- type sudo checkinstall

and follow the instructions!

As for your ati problem, I have the same myself. Its annoying but im not even  sure if its a possibility, ATI just dont give good linux support.(i count myself lucky to have 2d acceleration!!) There may be some ways but they're complicated and certainly not for linux newbies. I would recommend taking a dump in an envelope and sending it ATI.

---

### Post by pbaehr on 2006-01-19
Thanks for the input. I'm leaning toward keeping it simply because it feels wrong to not take full advantage of my hardware.

Compiling from source is something I'm sure I can get working. From the errors I was getting it looks like I'm just missing some necessary piece of software. (I get an error when trying to run ./config...something about autoheaders) If I continue to have trouble with that I'll post about it another time since I'm at work now.

My biggest grievance is the ATI drivers because I'm looking to ultimately trash Windows and ditch the dual boot setup I've got now but I can't do that until I can get my periodic UT2004 fix without it. I'll seriously consider your suggestion regarding sending a "message" to ATI.

---

### Post by happyponcho42 on 2006-01-20
Google and the use of quotation marks in your search queries are your best friends when you run into problems compiling from source :)

I actually gave up on 64bit Breezy but I should be back soon, once I get some new hardware.

---

### Post by morphodone on 2006-01-20
I respectfully disagree...

I would start over with 32 bit for now...
I don't think you'll see much performance increase with 64 bit anyhow.

Question - were you using 64 bit windows?

Since ATI has such poor driver support for linux anyhow, adding 64 bit to the
equation just makes it worse...

Once you get 3d acceleration going, running UT2004 should not be a problem.

---

### Post by pbaehr on 2006-01-23
No, I wasn't using 64 bit Windows. After fussing with Ubuntu over the weekend I'm still torn between taking advantage of my 64 bit architecture and getting the ATI set up so I can ditch Windows all together. I really like the linux OS. It brings me back to the good ol' days when the OS wasn't so tightly locked down.

Being new to looking for Linux hardware support from vendors, I'm not sure whether to expect a fix for the problem in the near future but based on what people are saying about ATI I'm guessing it will be a long wait.

---

### Post by KRiSX on 2006-01-23
to go from 32bit to 64bit or vice versa... u have to format and reinstall... so make your decision now...

i'm also torn between the 2.. i have never run ubuntu 64bit... but i did run suse 10 x64 just recently... and it can be a real pain in the backside getting things to work... i've currently taken linux off my main system to play around with windows x64.. i am typing this on my linux box, which runs ubuntu 5.10 32bit (its only a P3 667... so i have no choice).. and its great

i think at the moment... staying with 32bit isn't all that bad... i agree its a shame to waste 64bit hardware with 32bit software... but when the software isn't all that great right now... it makes sence to stick with what works!

---

### Post by pbaehr on 2006-01-23
Well, just to update you my original question is officially a moot point since I'm writing this from a fresh install of the 32 bit version of Ubuntu.

If I was a more seasoned Linux user I'd have stuck it out and struggled but since I'm just starting out the last thing I need is support problems plaguing me. Sometimes I don't know if it's a problem with what I'm doing or someone else's problem and for now I need to be sure that it's my problem so I can learn how to fix it.

I'll probably upgrade to 64 bit either when I become more adept or when it becomes less broken.

Thanks for the input.

---

### Post by RAOF on 2006-01-23
[QUOTE=galgoz]When you make your own packages how do you uninstall?  With Synaptic you just right click and chose remove?  Will packages you install yourself that you compiled show up there too?[/QUOTE]
When the final step is "sudo checkinstall", then yes, to uninstall you can just select it in synaptic & check "remove".

This is because the checkinstall program runs "make install" (you'll see that as the final step of most install-from-source guides), sees what it would do, and then makes a debian package which will do just what "make install" would do, and then installs it.  This means that the package manager (synaptic/apt) knows about the package & all the files it creates, and so it can remove it.

---

### Post by galgoz on 2006-01-23
I am just getting ready to install ubuntu on a 64bit capable machine.  After reading this I think it might be a good idea to stay with a 32 bit installation.  My only question is this...  After you install a 32 bit install can you easy upgrade to 64bit or does it require format and reinstall.

---

### Post by galgoz on 2006-01-23
[QUOTE=brk3]Hmm. I would stick to the 64-bit, compiling most packages isnt too hard once you have the main developement libraries installed. [/QUOTE]

When you make your own packages how do you uninstall?  With Synaptic you just right click and chose remove?  Will packages you install yourself that you compiled show up there too?

---

### Post by al108 on 2006-01-24
I have this problem too. I want to use 64bit for Cinelerra but I know I will miss all the other stuff wich is not available for 64bit yet. I already have two Windows installations on my HDD (one for games other things and one for video editing). I would hate to have two Ubuntu installs on the top of that. I think I'll be going to 32 bit

Alex

---

### Post by Lord Illidan on 2006-01-24
64 bit is still an emerging technology, so you can expect these things to happen. Use 32 bit, and then switch to 64 bit when it has stabilised enough.. If you put your /home on a seperate partition, then reinstalling shouldn't be so hard, as your data will be safe..

About the graphics cards, with Linux NVIDIA rules!!

---

### Post by m.musashi on 2006-01-24
Okay, lots of great ideas here, but for the new(er) Ubuntu user with a fancy new AMD 64 CPU is there a clear preference? I just want a PC that works to the best of its ability and I'd like to try and move away from Windows. If the 64 bit is going to be work to use, can you do a dual boot with a 32 bit for daily use and a 64 bit for playing around? Or is that just asking for even more troubles?

So, if you want a fully functional OS that doesn't require continual "fixing" is there any concensus - 32, 64, Breezy, Dapper, or something else altogether?

Thanks.

---

### Post by al108 on 2006-01-25
Unless you are doning some heavy computing you probably won't notice the difference 32 vs 64bit. For general office use any recent Ubuntu (and probably any major Linux distros) don't require "fixing" and works out of the box. For games and multimedia expect to do some reading and typing. 

Dual boot 32/64bit shouldn't be a problem, but I didn't get to try yet because my HDD is crowded already. It looks after reading some more that you can make almost everything work in 64bit but it may require some skill and knowledge. Yesterday I've reinstalled 32 bit Ubuntu since I don't have the skill and time to mess around.

Alex

---

### Post by JackDog on 2006-01-26
[QUOTE=KRiSX]to go from 32bit to 64bit or vice versa... u have to format and reinstall... so make your decision now...
[/QUOTE]

No you dont. Use LVM and create two root partitions, one for 32b and one for 64b. Have a third partition for your home directories. That way you can install both archs on the same system, and switch between them. Using "linux32 chroot" you should also be able to run just about any 32b application you have installed in your 32b install. 

The downside is you will have two installs to maintain, but with Ubuntu its easy anyway. I do this at work since I develop and test 64b/32b applications and it works very well. I have 5 different distros installed on the same system and frequently add/remove them. Its a very viable setup.

---

### Post by TheForumTroll on 2006-01-26
If you dont mind having to do some work to get stuff working and live without a few apps then i'd say go for 64 bit. (Why buy a 64 bit CPU and use a 32 bit OS?) 

I was in the same place as you a few weeks back and i did go for 64 bit. The only downside (well, depends who you ask really) is that i no longer use Ubuntu. I'm now a very happy Gentoo user :D

Their package system is a bit like apt, but instead it downloads the source and compiles it *automatically* on you machine.

So to say it short: I would go for 32 bit ubuntu if I wanted something easy that "just works" or 64 bit Gentoo for more speed and control over what i install.

Installing Gentoo takes some time, but i've learned a LOT from it. Ubuntu is great but i didn't really learn anything from installing/using it. Now i have a bigger chance to fix something myself if it breaks cause i understand Linux a whole lot better than i did before :)

Also if you really need something that just dosen't work in 64 bit you can run it in different ways. Chroot is one way, dual boot is another.

---

### Post by slavik on 2006-01-26
the Gentoo system is similar to the ports system on freebsd I heard ...

---

### Post by Tichondrius on 2006-01-26
ROFL, no it's not true that you can get anything to work in 64-bit. Well I guess if you include writing stuff yourself from scratch, then yes you can get anything to work, and good luck on doing that. But for all practical purposes, many things are just missing in the 64-bit world and most of the time the alternatives are quite a hassle. For example, you might need to download the source and compile and install yourself (not using apt). So there you go creating huge system maintenance issues (not to mention the compilation hazards) because your installed packages are no longer tracked by apt. Sometimes you can download the 32-bit version and run it in emulation. In fact this is quite common and you'll be surprised to know that it runs a little slower than if you ran the same 32-bit app on a 32-bit system. So that cancels out the miniscule perofrmance advantage you get from running 64-bit apps because your 32-bit apps are actially slower than before. Not to mention that it's also a huge hassle sometime to run 32-bit apps in emulation because you need to get 32-bit libraries those apps depend on, so now you have multiple library paths that need to be used by different apps. Sometimes even that doesn't work and then you need to set up a complete chroot 32-bit envrinment to run your 32-bit app in, but then of course you more than double your system maintenance issues, plus make the system much less convenient to use.

To be more specific, lets go thru some of the missings apps and packages. Do you view web pages that use the flash plugin ? say goodbye to them in 64-bit. Do you want to listen to wma audio files ? not on 64-bit. DVDs ? no. Drivers ? many don't exist in 64-bit. How about playing games ? cedega doesn't work in 64-bit, and same goes for wine. Software from third party software repositories ? usually they don't keep 64-bit versions.

And the above is only for things you simply can't get at all. The stuff you can get to work usually involves a lot of hassles like I explained above. 

And all this for what ? the difference in most apps and desktop environment is so small (1-2%) you will not be able to notice it. Only a few apps really take advantage of 64-bit to get a big improvement, and most of these apps are related to media processing. So unless you specifically know you are going to be havily using an application which runs significantly faster on 64-bit, and you are ready to deal with all the limitations and hassles for other parts of your system, then and and only then should you install a 64-bit linux.

Otherwise just wait until support for 64-bit matures.  


btw, all the above is based on personal experience as I installed and used 64-bit ubuntu a while ago, as well as 64-bit windows xp. Both were just a big waste of time with little or no gain.

---

### Post by midwinter on 2006-01-26
Yeah, you just have to decide if you'll mind missing a few things if you go the 64 bit route.   Personally i'm perfectly happy with my 64 bit install, I can't stand flash (it's awful), and i'm not exactly desperate to get wma or the latest wmv working either.  DVD's work fine for me, I don't think you'll have any problems there. 

Anyway, i'm looking at Gentoo 64 right now too..

---

### Post by RAOF on 2006-01-26
It really isn't as restrictive as Tichondrius reports.  Some things which are awkward in 32bit become more awkward (wine springs to mind, ATI drivers as well).  It is more difficult to get flash to work (but it is possible).  And there **is** little gain.

If you don't mind reinstalling, the 32bit version will be a bit easier to get some things working.

---

### Post by TheForumTroll on 2006-01-28
[QUOTE=Tichondrius]
To be more specific, lets go thru some of the missings apps and packages. Do you view web pages that use the flash plugin ? say goodbye to them in 64-bit. Do you want to listen to wma audio files ? not on 64-bit. DVDs ? no. Drivers ? many don't exist in 64-bit. How about playing games ? cedega doesn't work in 64-bit, and same goes for wine. Software from third party software repositories ? usually they don't keep 64-bit versions.
[/QUOTE]

**Thats just plain wrong. **Don't give advice about something you clearly don't know much about. I can play DVD's, play games like Guild Wars in Cedega, see Flash in webpages and all my rather new hardware works without no need for downloading drivers (except the nvidia driver, had to download that one and it worked in first try). All i had to do was install Linux and thats it. It worked. \\:D/ 

[QUOTE=Tichondrius]
btw, all the above is based on personal experience as I installed and used 64-bit ubuntu a while ago, as well as 64-bit windows xp. Both were just a big waste of time with little or no gain.
[/QUOTE]
I agree: 64 bit Windows is a waste of time, but 64 bit Linux is not. (Maybe 64 bit ubuntu are, but then its a ubuntu problem _not_ a 64 bit linux problem)
I have to ask, why did you buy a 64 bit CPU when your not going to use it?
It's like buying a 7.1 surround soundcard and only buy 2 speakers :rolleyes:

---

### Post by RAOF on 2006-01-29
[QUOTE=TheForumTroll]...
I have to ask, why did you buy a 64 bit CPU when your not going to use it?
It's like buying a 7.1 surround soundcard and only buy 2 speakers :rolleyes:[/QUOTE]
I'd guess because the athlon64s are also the best 32bit processors ;)

---

### Post by Tichondrius on 2006-01-29
[QUOTE=RAOF]I'd guess because the athlon64s are also the best 32bit processors ;)[/QUOTE]


Exactly, most benchmarks conducted in reviews comparing CPUs are done using 32-bit software, and Athlon 64 is the best value CPU you can get, especially for gaming, doubly so because of it's overclocking abilities. The 64-bit feature is nice and promises a small performance improvement (mostly due to all the internal registers being 64-bit) comapred to 32-bit, but the real gain will be when you need to use use more than 4GB of memory, which is currently not the case yet (at least not for most people).  And don't forget that when running 320bit software on a 64-bit OS, you get a small performance hit due to system call translation layer. So until most apps are availalbe in 64-bit, it's not worth getting it for the miniscule perofrmance gain.

And check your facts again, go to any third party repository like universe and compare the list of available package for amd64 and i386 - there are a lot less packages ready for amd64. Sure you might be able to compile yourself if the source is available but most people don't want to do that and it's not guaranteed to work.

You are lucky nvidia actually publishes their drivers in 64-bit version at the same time as the 32-bit. But ati doesn't even have a 64-bit version of their drivers. And so is the case for many hardware manufacturers, as well as many commercial apps. My 64-bit Ubuntu install was too much trouble with all the problems with codecs, plugins, chroot environments, multiple lib paths etc. I really don't miss it just so I can say I've fallen for the 64-bit marketing gimmick.

---

### Post by RAOF on 2006-01-29
[QUOTE=Tichondrius]...So until most apps are availalbe in 64-bit, it's not worth getting it for the miniscule perofrmance gain.
[/quote](Almost) All the apps in the Ubuntu repositories are 64bit.  There are exactly 2 32bit programs on my Ubuntu - OpenOffice & wine.  You can also get a 32bit mplayer from the repositories.

[QUOTE=Tichondrius]
...But ati doesn't even have a 64-bit version of their drivers. And so is the case for many hardware manufacturers, as well as many commercial apps...[/QUOTE]
When did you last use Ubuntu64?  There are 64bit (proprietry) ATI drivers in the main repository!  It is true that 3rd party repositories often don't have a amd64 section, but I've never really wanted anything from them.  

Universe is only sort of 3rd party, and it still contains all the 64bit packages I want.  The only thing I don't have is (native) Flash, & I don't really miss it, either ;)

---

### Post by Tichondrius on 2006-01-29
Can you play WMA ? Real player ? quicktime ? didnt think so, but hey that's fine, who really needs them anyway ?

---

### Post by RAOF on 2006-01-29
[QUOTE=Tichondrius]Can you play WMA ? Real player ? quicktime ? didnt think so, but hey that's fine, who really needs them anyway ?[/QUOTE]
Probably can't play WMA.  Never tried :).  You can't play DRM'd WMA on **anything** but windows, and that's the only reason I'd have a WMA file.  Ditto for Real Player, but I think you can install it. (Where "it" is the 32bit version)

Quicktime movies/audio play just fine.  You don't get iTunes, of course, but there are plenty of (IMO) nicer/better native players out there.

How easy 64bit Ubuntu is depends on what you want to do with it.  Staying with free(ish) codecs, and open source stuff, I've had barely any problems.

---

### Post by midwinter on 2006-01-29
Huh?  Of course there are 64 bit ATI drivers, and quicktime/dvd's work perfectly.   

Try not to give incorrect information.  And if you do, perhaps acknowledge it. ;)

Edited for politeness.

---

### Post by Tichondrius on 2006-01-29
You can't even get the new firefox 1.5 for 64 bits, so you need to get the 32-bit  version and run it using 32-bit libraries and plugins. It becomes a huge mess because of having to keep multiple library paths for the different components. And like I said before, there is a hit on performance when using 32-bit apps because of the 32/64 translation, which causes these apps to perform slower even though the system calls done by the kernel on thier behalf run in 64-bit. This is just one example how installing an app not available yet in 64-bit causes such a headache:

[https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

The bottom line is that issues like this come up all the time with 64-bit ubuntu, so what you have to ask yourself is what are you really getting for all this hassle ? I mean, I would understand dealing with this hassle for 20% performance gain, but for an insiginificant 2% performance gain,  it's hardly worth it.  Some people do it for the novelty, but that wears off pretty fast and all that's left is a mess.

---

### Post by RAOF on 2006-01-30
Got any benchmarks for 2% performace gain?  The numbers I've heard are more like 10% for most stuff, and more for some applications.  On the other hand, I can't give you references to those benchmarks either ;).  *Do* you have any benchmarks?  They'd be interesting reading.

Firefox 1.5 **is** available in 64bits - in Dapper.  Breezy (32 or 64 bit) won't be seeing any 1.5 packages in the repository, or even in backports - it's just too embedded in all sorts of stuff.

And those instructions aren't **that** much more difficult than getting Firefox 1.5 on 32bit Breezy.  I'm not saying that Breezy64 is as easy (to do the complicated stuff) as Breezy32, but it really is not that much more difficult.  And if you stay in the official (main, universe, multiverse) repositories, it's no more difficult at all.

---

### Post by Tichondrius on 2006-01-30
Yes, what I'm saying is based on benchmarks and results from reputable sources, and not just on what "i've heard" somewhere.

[http://www.anandtech.com/linux/showdoc.aspx?i=2213&p=1](http://www.anandtech.com/linux/showdoc.aspx?i=2213&p=1)

Here's an exceprt from the summary:

"We were extremely pleased to see the 64-bit applications generally perform better than their 32-bit counterparts. Unfortunately, there were still several cases where 64-bit binaries performed slower; John the Ripper being one of those examples. Some software, like MEncoder 1.0pre5 proved difficult to install on SuSE 9.1 x86_64 as well. We didn't even touch on the hundreds of software ports that do not have working 64-bit binaries yet, including Wine. **Sometimes the advantage of speed does not outweigh the advantage of software compatibility**. "

---

### Post by RAOF on 2006-01-30
Interesting.  Thanks for the link.

Actually looking at those benchmarks show that some things are dramatically faster - the database tests are about 1/3 faster, pov-ray at more than 1/3 faster, the chess & synthetic benchmarks don't show much difference, lame is 2/3 faster, gzip is ~10% faster, and the encryption is mixed, ranging from more than twice as fast for SSL-RSA to slightly slower for MD5.

So, all in all, that seems to be more than ~2% faster ;).  It still may be too much effort for you, and I wouldn't recommend it to a newcomer who *hadn't already installed it*, but the speed increases are much more pronounced than I thought.

---

