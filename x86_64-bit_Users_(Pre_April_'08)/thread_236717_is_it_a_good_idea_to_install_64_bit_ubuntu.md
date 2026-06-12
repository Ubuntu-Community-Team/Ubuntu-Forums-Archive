---
title: "is it a good idea to install 64 bit ubuntu ?"
date: 2006-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by taner on 2006-08-15
hi all,
i m using ubuntu 32 bit version but i have 64 bit AMD. when i was tried windows 64bit XP it was a big problem with hardware drivers and 32 bit softwares, when i tried to install some 32 bit softwares ther was a errors... and thats why i m ambivalent to install ubuntu 64 bit version ?
would i have problems with 32 bit programs with ubuntu 64 bit version ?
what is the negative parts to use ubuntu 64 bit version ?

thanx.

---

### Post by jamesford on 2006-08-15
the only real problem is the lack of 64 bit flash and codecs. however there is no problem running 32 bit firefox with 32 bit flash and 32 bit mplayer with 32 bit codecs

otherwise 99% of all pacakges are available as 64 bit

---

### Post by kaffelars on 2006-08-15
I'm using the AMD64 version with my Pentium D processor. Haven't tried it with the 32 bit version, but I find the 64 bit very fast.
I used [Automatix]("http://www.getautomatix.org") to install Flash, Mplayer and lots of other stuff (both 32 and 64 bit) and it works great.

Having used it only for a few days, I'd say the bigges disadvantage  is that there is less software compiled for the AMD64 architecture available. I don't find this to annoying though, as 32 bit software  runs fine most of the time. 

(Hint: Manually install 32-bit packages on 64-bit Ubuntu with **sudo dpkg -i --force-architecture <package.deb>**.)

---

### Post by Hg80 on 2006-08-15
> **kaffelars said:**
> 
(Hint: Manually install 32-bit packages on 64-bit Ubuntu with **sudo dpkg -i --force-architecture <package.deb>**.)

Agreed, im Using 64bit and have for months now and its all working fine, but cant find the newest flash player for firefox,
I am running UT2004 and guild wars a dream also

---

### Post by taner on 2006-08-15
Many feel that Adobe has completely abandoned the Linux market, having not released a new version of the player for Linux since the 2004 release of Flash Player 7. Increasingly, websites insist on the use of newer players, which weakens Adobe's claim that their Flash Player is "Linux compatible." Linux users seeking to upgrade to Flash Player 8 are instead redirected to a download page for Flash Player 7 (which they very likely already have installed).

Flash Player 8 is relatively unstable and users having problems are advised to revert to Flash Player 7. Also, Flash Player 8 will not be released for Linux [11] but instead Macromedia is planning to release Flash Player 9 for all the three major operating systems, but not necessarily at the same time [12]. The current (March 2006) Flash Player 7 for Linux has poor sound support (The sound may lag about a second behind the picture). Macromedia has not yet released any of their development software for any UNIX-like operating system except Mac OS X.

Although Linux and Mac have excellent 64 bit support, Macromedia has yet (June 2006) to release a flash player for the x86-64 architecture on any operating system.

[http://en.wikipedia.org/wiki/Macromedia_Flash](http://en.wikipedia.org/wiki/Macromedia_Flash)

---

### Post by RedBoot on 2006-08-15
I had 64 bit Ubuntu installed for a while. It was perceptably faster, but like other have pointed out I couldn't get MacroMedia flash web sites (like google video and pandora.com) to work.  Others here say you can run an older version. I didn't see how to do this (and would like to know how to.)
Also, I use hamachi and its site says it has downloads for x86 versions of Linux. I am assuming this means they wouldn't work under AMD64. Here again, maybe there's a way around these things. 
I now run Ubuntu x86 versions now on desktops with Athlon64s and laptops with Turion64s. It's not as fast, but it's way faster than XP!

---

### Post by John.Michael.Kane on 2006-08-15
RedBoot there's scripts writen by kilz that should almost all of the 32bit issues to be resloved. theres also automatix for 64bit i think. between these two most 64bit users should endup with a fairly decent working system. i know it's not native. however it does hold users over till there is native support.

---

### Post by Kilz on 2006-08-15
> **kaffelars said:**
> I'm using the AMD64 version with my Pentium D processor. Haven't tried it with the 32 bit version, but I find the 64 bit very fast.
I used [Automatix]("http://www.getautomatix.org") to install Flash, Mplayer and lots of other stuff (both 32 and 64 bit) and it works great.

Having used it only for a few days, I'd say the bigges disadvantage  is that there is less software compiled for the AMD64 architecture available. I don't find this to annoying though, as 32 bit software  runs fine most of the time. 

(Hint: Manually install 32-bit packages on 64-bit Ubuntu with **sudo dpkg -i --force-architecture <package.deb>**.)

I have read a few automatrix horror stories for amd64. It may work fine for a lot of people. It just seems those it doesnt work for are the least likly to be able to fix the problems. 
I perfer small setup scripts for a specific thing. The everything and the kitchen sink moves to fast and you may not see the errors.

There really isnt that big a difference in the amout of packages
According to launchpad:
Amd64 has 18609 binary packages
i386  has 19029 binary packages
Its hard to tell exactly if anything is missing because some of the packages for i386 may not be needed for the amd64 platform. 
IMHO the developers need to be more active on getting multiarch working as it would solve all the problems. Instead it was pushed back, and more eye candy was added.

[quote=RedBoot]  I had 64 bit Ubuntu installed for a while. It was perceptably faster, but like other have pointed out I couldn't get MacroMedia flash web sites (like google video and pandora.com) to work. Others here say you can run an older version. I didn't see how to do this (and would like to know how to.)
Also, I use hamachi and its site says it has downloads for x86 versions of Linux. I am assuming this means they wouldn't work under AMD64. Here again, maybe there's a way around these things.
I now run Ubuntu x86 versions now on desktops with Athlon64s and laptops with Turion64s. It's not as fast, but it's way faster than XP![/quote]
The flash FUD strikes again. Anyone that installs the 64bit system needs to check the sticky's in the 64bit section. There are ways to install things to make flash and firefox work without problems.
All 32bit applications will work. It just depends on how much setup needs to be done. I bet forcing in hamachi could be done.

---

### Post by punkybouy on 2006-08-15
I remember this about 10 years ago when Windows went from 16 bit to 32 bit.  The same complaints.  I suspect it will be a few years before we all abandon 32 bit for 64 bit.  Hang in there it will happen.

---

### Post by dpaint4 on 2006-08-16
> **RedBoot said:**
> I had 64 bit Ubuntu installed for a while. It was perceptably faster, but like other have pointed out I couldn't get MacroMedia flash web sites (like google video and pandora.com) to work.  Others here say you can run an older version. I didn't see how to do this (and would like to know how to.)
Also, I use hamachi and its site says it has downloads for x86 versions of Linux. I am assuming this means they wouldn't work under AMD64. Here again, maybe there's a way around these things. 
I now run Ubuntu x86 versions now on desktops with Athlon64s and laptops with Turion64s. It's not as fast, but it's way faster than XP!

SO THIS IS ILLUMINATING!!! I feel like a dolt, but do you mean that I can run X86 Ubuntu on my AMD64? That's not very clear from the way the download page is structured.

I'd love that for the sake of compatibility. I know that AMD64 processors can run 32-bit code and that my Windows machine came with Windows XP Pro (not the 64-bit version) even though the processor is an AMD64. So this is all adding up for me now.

Can someone confirm that I can run Ubuntu X86?

---

### Post by Kilz on 2006-08-16
double post got me again, forums keep timing out lately.

---

### Post by Kilz on 2006-08-16
> **dpaint4 said:**
> SO THIS IS ILLUMINATING!!! I feel like a dolt, but do you mean that I can run X86 Ubuntu on my AMD64? That's not very clear from the way the download page is structured.

I'd love that for the sake of compatibility. I know that AMD64 processors can run 32-bit code and that my Windows machine came with Windows XP Pro (not the 64-bit version) even though the processor is an AMD64. So this is all adding up for me now.

Can someone confirm that I can run Ubuntu X86?

Yes you can run i386 Ubuntu on a amd64 system. But its kind of like buying a corvette, then pulling the spark plugs out from 4 of the cylinders. Will it run? Sure, but will it give you the best performance? No. You may have problems.
As its been pointed out there are few if any reasons any more to install the 32bit version on a 64bit system. Breezy had problems, that some people to this day repeat like they still apply to Dapper when they don't.
What compatibility are you talking about?

---

### Post by RedBoot on 2006-08-16
punkbouy:
> I remember this about 10 years ago when Windows went from 16 bit to 32 bit.

I couldn't agree more. I'm not a pioneer with this kind of thing (mostly because I don't need high performance game/graphics), but we are all eternally grateful for those who are pioneers and deal with all the intitial compatibilty headaches.
Kilz:
> Yes you can run i386 Ubuntu on a amd64 system. But its kind of like buying a corvette, then pulling the spark plugs out from 4 of the cylinders.That's why I drive a Prius at 55mph and let the Corvettes pass me by.:p  It gets me where I want to go.
> You may have problems.
I would disagree with this statement. I think in fact that the problems exist for the pioneers installing the 64 bit operating systems, not for those using the 32bit compatibility mode.

dpaint4:
> Can someone confirm that I can run Ubuntu X86?
I'd guess that over 90% of the systems out there with an Athlon 64 are running XP. And that over 90% of THOSE are running the "regular" XP, not the 64 bit XP. I'd guess the same goes for Ubuntu. 

I wasn't sure what you meant about the instructions on the download page, since I remembered this (ubuntu.com):
> For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure.
But I see what you mean when later they say:
This is pretty clear so far. Yeah, it will run on AMD64.  But later under the AMD section:
> It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.
I think this is a word-smithing problem. I believe they mean to say 'It's only for their 64 bit chips.' not 'It's **necessary **for their 64 bit chips.'

---

### Post by Kilz on 2006-08-16
> **RedBoot said:**
> 
That's why I drive a Prius at 55mph and let the Corvettes pass me by.:p  It gets me where I want to go.


:D  Ok for all the hybrid owners, its like buying a prius, and pulling 2 of the 4 spark plugs out.
My analogy to a Corvette to a 64bit system is a good one imho. 64bit processors are for performance. If you wanted to run a 32bit OS why buy a 64bit system? Why not just buy a 32bit celeron?
There may be a few reasons to run a 32bit OS
1)You need to run a proprietary piece of software for work that cant be made to work in any way on 64bit. This doesn't include flash, java, wine, or anything in the sticky.
2) You are an absolute newbie and don't have the skills to cut/paste or read how to run a setup script. In this case its better to go back to windows because you will fail at 32bit Linux to.
3)Even after trying your best you cant make the hardware use the install cd for the OS. But the 32bit one works. At least make a bug report so it can be fixed.

No matter what Linux distro or version you install there are going to be things you are going to need to setup. If you cant put the time in to learn or setup, just pop in the windows restore disk. I'm beginning to agree with some people that Linux isn't for everyone.

---

### Post by taner on 2006-08-16
before i discovered linux world i bought new pc and it is 64bit system. i paid attention to the performance mostly. and directly i installed to it windows 64 bit system and what was the interesting ? i couldnt do anything ... there were problems with some drivers and i couldn't install some of my favorite programs. i wasted too much time with the stupid problems and there were no solutions. then i installed again windows 32 bit system and again i wasted time to configure it in my style. after that i wanted to try something new. i found ubuntu and i didnt want to install 64bit system ubuntu, to take a risk with 64bit system and to format and install again aplications and waste time...
i use 32bit ubuntu since 3 mounths and i don't want to use again some windows operation systems again i m happy with ubuntu but it is really difficult for me to install again 64bit ubuntu. my 32 bit ubuntu is like my pet i like it with my configurations and it taked too much time for me to configure it with samba, apache, internet sharing, shaping, find and install applications and resolve some other problems... i dont want to do all of these things again if i install 64bit ubuntu. :( i have 64bit system but i didn't know that linux supports powerfull 64 bit system without problems. :-? 

is there a sollution without format and lose my settings to install 64 bit system :p :D

---

### Post by clevershark on 2006-08-16
Incidentally if you want to see the videos hosted on YouTube and Google Video, I wrote an article on my web site describing how to do it:

[http://clevershark.com/?p=1404](http://clevershark.com/?p=1404)

To show the YouTube videos you'll need to have ffplay and ffmpeg installed.

---

### Post by RedBoot on 2006-08-16
CleverShark:
> Incidentally if you want to see the videos hosted on YouTube and Google Video, I wrote an article on my web site describing how to do it:

[http://clevershark.com/?p=1404](http://clevershark.com/?p=1404)

To show the YouTube videos you'll need to have ffplay and ffmpeg installed.

Awsome, simple to follow page, CleverShark. I tagged it on [deli.cio.us]("http://del.icio.us") so I can go there when I next get the nerve up to go 64 bit. I also checked out your main page and found some neat stuff there. Which leads me to a few other questions:

[LIST=1]
[*]You mention that there's a petition page to get Adobe to get of it and upgrade flash to 64bits. Do you know the site since I'd be glad to add my name to the list.
[*]You also mention ATI's driver sucks on a zv6100 laptop and '...that you will not be able to get 3D acceleration working in any way while in Linux...' Is this for 32bit **and **64 bit?
[/LIST]

My other questions aren't relevant to this thread (have to do with your article about wireless on the zv6100) so I'll ask them another time.

---

### Post by Kilz on 2006-08-16
> **taner said:**
> before i discovered linux world i bought new pc and it is 64bit system. i paid attention to the performance mostly. and directly i installed to it windows 64 bit system and what was the interesting ? i couldnt do anything ... there were problems with some drivers and i couldn't install some of my favorite programs. i wasted too much time with the stupid problems and there were no solutions. then i installed again windows 32 bit system and again i wasted time to configure it in my style. after that i wanted to try something new. i found ubuntu and i didnt want to install 64bit system ubuntu, to take a risk with 64bit system and to format and install again aplications and waste time...
i use 32bit ubuntu since 3 mounths and i don't want to use again some windows operation systems again i m happy with ubuntu but it is really difficult for me to install again 64bit ubuntu. my 32 bit ubuntu is like my pet i like it with my configurations and it taked too much time for me to configure it with samba, apache, internet sharing, shaping, find and install applications and resolve some other problems... i dont want to do all of these things again if i install 64bit ubuntu. :( i have 64bit system but i didn't know that linux supports powerfull 64 bit system without problems. :-? 

is there a sollution without format and lose my settings to install 64 bit system :p :D


The solution is simply wait a few months. Edgy will be released  and you will probably want to install it. For the most part it is recommended to clean install an upgraded. Simply use 64bit Edgy.

---

### Post by Kobussie on 2006-08-17
> You are an absolute newbie and don't have the skills to cut/paste or read how to run a setup script. In this case its better to go back to windows because you will fail at 32bit Linux to.

?? So basically you're saying here the every Linux newbie should stick to Windows ?? How to become a not-so-newbie-anymore than?

---

### Post by kaffelars on 2006-08-17
Yes, you can run the x86 version on a 64-bit CPU.

From what I read on the forum, it seems like a lot of people do this because of software compatibility and that the 64-bit version is not that much faster. I haven't done a comparison on my system, though ;)

---

### Post by Kilz on 2006-08-17
> **Kobussie said:**
> ?? So basically you're saying here the every Linux newbie should stick to Windows ?? How to become a not-so-newbie-anymore than?

No, I didn't write that. Since you didn't get what I wrote, Ill expand on it. 
If you don't have cut and paste skills. If you cant type in a command someone gives you to run a setup script. Then there is no way you will be able to successfully install any version of Linux. 
Linux isn't Windows. Even Distro's like Ubuntu that are designed to be newbie friendly require that you have basic skills like knowing how to cut and paste. How to be able to type in a command someone has given you. Linux doesn't guarantee you an OS you may have to do some work.
If you are leaving the 64bit system to avoid these things. Don't even waste the time with the 32bit version. You will still have to do them.
If you want to avoid any setup , even that of simple, basic skills. Go back to Windows.

---

### Post by dpaint4 on 2006-08-17
Thanks guys. Yeah, I'm aware of the performance hit and of not fully benefitting from the CPU. I also understand the agrivation you might feel with someone asking what I asked so thanks also for the kind response.

I'm going to try both versions. From what I've read on the forums, dvd::rip won't run on the 64-bit version and I like to archive my movies and fiddle with video compression. Also something about Wine not running well in 64-but Ubuntu and I like to play Cave Story in Wine. It's my favorite game and finding out that I could still play it in Ubuntu under Wine made me comfortable in switching from Windows a year or so back.

Anyway, I run X86 Ubuntu on my somewhat underpowered laptop and I'm constantly impressed by the speed and stability. So much nicer than Windows on the same machine.

So I bet I wouldn't *mind* X86 Ubuntu on my AMD64, and if I did that, I wouldn't have to do all the strange things to my repositories that I keep reading about to install and run 32-bit applications, or foce them to install in a non-native environment etc.

Man I hate that kind of thing. I always feel like I'm on the verge of destroying my lovely little digital home.

---

### Post by dpaint4 on 2006-08-17
> **Kilz said:**
> If you are leaving the 64bit system to avoid these things. Don't even waste the time with the 32bit version. You will still have to do them.
If you want to avoid any setup , even that of simple, basic skills. Go back to Windows.

Wait wait wait. Whoa. You're sounding kind of angry all of a sudden. Look, I like Ubuntu and don't mind the command line. I'm no coder but I use the command line to move and delete files, or perform batch opperations. I use apt-get from the command line too.

I just wanted to know all my options.

I'll decline the part about 'go back to Windows'. I think I deserve to be here and I respect what you guys do. Learning all the time.

I do benefit from also running a Windows box at home, but I don't think an OS is the same as a football team. I use what I need at the time, and Ubuntu is one of my favorites.

---

### Post by Kilz on 2006-08-17
> **dpaint4 said:**
> Thanks guys. Yeah, I'm aware of the performance hit and of not fully benefitting from the CPU. I also understand the agrivation you might feel with someone asking what I asked so thanks also for the kind response.

I'm going to try both versions. From what I've read on the forums, dvd::rip won't run on the 64-bit version and I like to archive my movies and fiddle with video compression. Also something about Wine not running well in 64-but Ubuntu and I like to play Cave Story in Wine. It's my favorite game and finding out that I could still play it in Ubuntu under Wine made me comfortable in switching from Windows a year or so back.

Anyway, I run X86 Ubuntu on my somewhat underpowered laptop and I'm constantly impressed by the speed and stability. So much nicer than Windows on the same machine.

So I bet I wouldn't *mind* X86 Ubuntu on my AMD64, and if I did that, I wouldn't have to do all the strange things to my repositories that I keep reading about to install and run 32-bit applications, or foce them to install in a non-native environment etc.

Man I hate that kind of thing. I always feel like I'm on the verge of destroying my lovely little digital home.

Wine runs just fine on amd64, look in my signature. 
While the 64bit system may run a 32bit os you may have issues. It may not be smooth sailing with no problems. There have been reports of slow running applications and crashes that stoped happening when the person replaced the os with the 64bit one.

---

### Post by Kilz on 2006-08-17
> **dpaint4 said:**
> Wait wait wait. Whoa. You're sounding kind of angry all of a sudden. Look, I like Ubuntu and don't mind the command line. I'm no coder but I use the command line to move and delete files, or perform batch opperations. I use apt-get from the command line too.

I just wanted to know all my options.

I'll decline the part about 'go back to Windows'. I think I deserve to be here and I respect what you guys do. Learning all the time.

I do benefit from also running a Windows box at home, but I don't think an OS is the same as a football team. I use what I need at the time, and Ubuntu is one of my favorites.

No not angry, just explaining what I wrote to someone who didnt understand it. Some people think that they are going to avoid all problems, if the just do something else. I want them to understand that there may be setup they have to do. I dont want to lie to them and make them think its all easy with no work.
There is no way to avoid it when running Linux. If you want a OS that all you have to do is pop in a CD and do nothing else , install Windows. Of corse you will have to deal with spyware, bloat, viruses, security holes. But you wont have to do setup.

---

### Post by dpaint4 on 2006-08-17
> **Kilz said:**
> Wine runs just fine on amd64, look in my signature. 
While the 64bit system may run a 32bit os you may have issues. It may not be smooth sailing with no problems. There have been reports of slow running applications and crashes that stoped happening when the person replaced the os with the 64bit one.

Cool; yeah. I admit that I have seen the tutorial in your signature. I think that's good. My problem is that when I go through with things like that, I feel I'm adding to my system something that isn't really ready to be added to the system. Basically if I can't apt-get install it and leave it alone, I feel like it's not something that is really yet ready for an *end user* like me.

That goes for tricks to get Flash and Java working as well.

As I use Ubuntu into the future, I will probably become more and more comfortable with things like that. But I hate running things in the command line *IF I DON'T ACTUALLY UNDERSTAND WHAT THEY'RE DOING* or *HOW I MIGHT UNDO IT IF I HAD TO*.

So that's the perspective I come from. 

When I see tutorials like those, I get happy because it usually means a standard implementation is on the way.

As an Example: Compiz+XGL. This was the subject of many a multi-layered tutorial and people filled forums up with confusion and failure. I waited. Yesterday, I apt-get installed them both and booted into a Compiz desktop.

Learning when to jump based is a good skill to have if you're realistic about your skill level. The higher the skill, the earlier you can jump.

---

### Post by Kilz on 2006-08-17
> **dpaint4 said:**
> Cool; yeah. I admit that I have seen the tutorial in your signature. I think that's good. My problem is that when I go through with things like that, I feel I'm adding to my system something that isn't really ready to be added to the system. Basically if I can't apt-get install it and leave it alone, I feel like it's not something that is really yet ready for an *end user* like me.

That goes for tricks to get Flash and Java working as well.

As I use Ubuntu into the future, I will probably become more and more comfortable with things like that. But I hate running things in the command line *IF I DON'T ACTUALLY UNDERSTAND WHAT THEY'RE DOING* or *HOW I MIGHT UNDO IT IF I HAD TO*.

So that's the perspective I come from. 

When I see tutorials like those, I get happy because it usually means a standard implementation is on the way.

Actualy, the wine howto is going to be added to the Ubuntu Wiki. I have been asked permission to use it. So it is going to be somewhat official. In any event it is installing .deb file packages. Packages are removable and replacable.
As for the Firefox howto, yes the howto is old. I left it in place because some people have it installed. In case they need to troubleshoot something if/when an update happenes.
But the scripts install .deb files.The Firefox32 .deb file I created is even avaiable on the page. As they are .deb packages, they are removable, replacable, and upgradeable. In fact thats why the firefox32.deb file is there on the page, upgradeing is as simple as double clicking on it and letting the gdebi deb file installer work.

---

### Post by tomdkat on 2006-08-21
> **Kilz said:**
> The solution is simply wait a few months. Edgy will be released  and you will probably want to install it.When is it due out?  I'm pondering whether to stick with my 64-bit Ubuntu installation or not.  I got a 64-bit machine purely because I got a good deal on the price and it being 64-bit was secondary.  :)

I'm happy with the performance I'm getting but I'm having issues with getting everything I'm interested in running up and running.  I've posted some questions in this forum that have gone unanswered and if Edgy isn't too far out I think I can wait for that and see what it will offer.

For now, I'll see about installing the 32-bit Flash and Java plugins.   :)

Peace...

---

### Post by kaffelars on 2006-08-22
According to [this]("https://wiki.ubuntu.com/EdgyReleaseSchedule") release schedule, Edgy is due on October 26., so it's still a while.

You can always try the prereleases though, if you dare ;)

---

### Post by tomdkat on 2006-08-22
> **kaffelars said:**
> According to [this]("https://wiki.ubuntu.com/EdgyReleaseSchedule") release schedule, Edgy is due on October 26., so it's still a while.Thanks for the link!  I think I can hold out until then.  I'll make my final decision based on Edgy.  :)

> You can always try the prereleases though, if you dare ;)Before my system crash (due to HDD failure), I used to keep my Slackware 8-based system more on the cutting edge than most distros (2.6.17.6 kernel, glibc 2.4, glib 2.10.3 (full release), gcc 4.1.1, and so on) so I might give a prerelease a try depending on how the installation process works.

Peace...

---

### Post by Kilz on 2006-08-22
> **tomdkat said:**
> Thanks for the link!  I think I can hold out until then.  I'll make my final decision based on Edgy.  :) The real improvement for the 64bit version should be in Edgy+1 at the earliest. From what I have read thats when we can expect a multiarch enviromant at the earliest. Once we get that there wont be any work arounds to install 32bit applications. The 32bit and 64bit repositories will install with snaptic.

> **tomdkat said:**
> Before my system crash (due to HDD failure), I used to keep my Slackware 8-based system more on the cutting edge than most distros (2.6.17.6 kernel, glibc 2.4, glib 2.10.3 (full release), gcc 4.1.1, and so on) so I might give a prerelease a try depending on how the installation process works.

Peace...
Personaly I would wait a bit, things are still in process. Think Alpha 1 release for knot1. IMHO I would wait for a beta release before trying to use it every day.

---

### Post by tomdkat on 2006-08-22
> **Kilz said:**
> The real improvement for the 64bit version should be in Edgy+1 at the earliest. From what I have read thats when we can expect a multiarch enviromant at the earliest. Once we get that there wont be any work arounds to install 32bit applications. The 32bit and 64bit repositories will install with snaptic.Sounds good.  Thanks for the add'l info.

> Personaly I would wait a bit, things are still in process. Think Alpha 1 release for knot1. IMHO I would wait for a beta release before trying to use it every day.Gotcha.  This is my first Ubuntu experience and my first "pre-built packages" experience so I'm keeping an open mind.  I just get a little frustrated when packages aren't installed in the manner I'm used to, like glib not including the development files or gcc being installed with front-ends I won't ever use, like Fortran or Ada.

The main thing is I haven't given up on Ubuntu AMD64 yet.  :)

Peace...

---

### Post by Kilz on 2006-08-22
> **tomdkat said:**
> Sounds good.  Thanks for the add'l info.

Gotcha.  This is my first Ubuntu experience and my first "pre-built packages" experience so I'm keeping an open mind.  I just get a little frustrated when packages aren't installed in the manner I'm used to, like glib not including the development files or gcc being installed with front-ends I won't ever use, like Fortran or Ada.

The main thing is I haven't given up on Ubuntu AMD64 yet.  :)

Peace...

Good, I think all 64bit users go through an adjustment where they are not sure if they really lke it. Almost all development files for a package will be in a -dev package. The front ends are because the package has to work for everyone, Im sure the people who use them are happy they are there. 
I wanted to try gentoo, someday maybe I will. But on the 20th page of the install instructions I descided I wasnt ready for it. The moral, no distro is perfect for everyone. Try them all, one will fit.

---

### Post by tomdkat on 2006-08-22
> **Kilz said:**
> Good, I think all 64bit users go through an adjustment where they are not sure if they really lke it.From a pure "user" perspective, I think a native 64-bit Ubuntu distro is great!  The apps I was able to install went in easily and the system is stable, etc.

It's from a development standpoint (at least installing software from source) where I'm having issues.  :)

> Almost all development files for a package will be in a -dev package.Yep, I realize this except for some reason that's **not** the case with [glib-2.10.3](http://www.ubuntuforums.org/showthread.php?t=237549&highlight=glib), for whatever reason.  :(

> The front ends are because the package has to work for everyone, Im sure the people who use them are happy they are there.I can understand that but given how the dev parts are separated from the "main" parts, I would think the GCC frontends would be separately installable items, with the C and C++ frontends being installed by default.  Besides, the GCC sources come in two general flavors, the complete package and with certain frontends broken out (namely Java (GCJ), Ada, Fortran, and even C++).

> I wanted to try gentoo, someday maybe I will. But on the 20th page of the install instructions I descided I wasnt ready for it. The moral, no distro is perfect for everyone. Try them all, one will fit.I actually started with Gentoo and got the system built and booted but I couldn't figure out how to get more than the base system installed.  The instructions take you through getting the base system installed but don't really tell you how to install everything else.  Even if an "emerge" command would be issued to install the rest, the doc wasn't clear on that at all.  So, I bailed on Gentoo and tried Ubuntu. :)

Peace...

---

### Post by RAOF on 2006-08-23
> **tomdkat said:**
> ...

Yep, I realize this except for some reason that's **not** the case with [glib-2.10.3](http://www.ubuntuforums.org/showthread.php?t=237549&highlight=glib), for whatever reason.  :(
...

**I** have libglib2.0-dev 2.10.3-0ubuntu1 installed.  It's from the dapper-updates repository, though, so it's possible that you don't have that repository enabled in your sources.list.

---

### Post by tomdkat on 2006-08-23
My repository list must not be properly updated.  I've sent you a PM.  :)

Peace...

---

### Post by tomdkat on 2006-08-25
Well, it turned out my repository list left out an apparently important repository.   :)

Peace...

---

### Post by geek.de.nz on 2006-08-26
I've installed the 64 bit version, but it runs very slow. I think this is because my chipset is not properly supported.

Specs:
AMD 64 3500+
Asus M2NPV-MX
Chipset:
NVIDIA GeForce 6150
NVIDIA nForce 430 MCP

This is a brand new Motherboard. There is a driver CD with it with Linux drivers, but I cannot get them installed.

I installed the following packages by hand because the NVIDIA installer was complaining (my LAN card doesn't work with the Dapper default drivers, so I had to boot into windoze, download ...):
binutils_2.16.1cvs20060117-1ubuntu2.1_amd64.deb
linux-headers-2.6.15-23-amd64-generic_2.6.15-23.39_amd64.deb

However, the installer was still complaining that it needs the libc development package. I tried to install:
libc6-dev_2.3.6-0ubuntu20_amd64.deb
libc6-dev_2.3.6-0ubuntu20_i386.deb
libc6-amd64_2.3.6-0ubuntu20_i386.deb
libc6_2.3.6-0ubuntu20_amd64.deb
(with #dpkg -i <packagename>), but they wouldn't install. The error was that "the architechture is wrong".


Should I try to install with 
#dpkg -i --force-architecture <package.deb>
?

I don't  want to break my system, although it wouldn't really matter I guess.


Help, I don't know how to go on!

---

### Post by el mariachi on 2007-03-25
the topic is old (kinda) but i just came across the central question of it.

can someone make an update about it? currently I'm running edgy 32bit on a amd64 4000+. i didn't go for 64bit because i was a little afraid of compatibility issues (aside from flash and some other few apps i now know that all my hardware/critical apps work)

someone posted that he/she doesn't like to put new/not completely stable things in his system. i just made the switch from windows and thats exactly how I feel. it seems that every time i do something in the command line it's gonna do something bad lol -offtopic

---

### Post by Kilz on 2007-03-25
> **el mariachi said:**
> the topic is old (kinda) but i just came across the central question of it.

can someone make an update about it? currently I'm running edgy 32bit on a amd64 4000+. i didn't go for 64bit because i was a little afraid of compatibility issues (aside from flash and some other few apps i now know that all my hardware/critical apps work)

someone posted that he/she doesn't like to put new/not completely stable things in his system. i just made the switch from windows and thats exactly how I feel. it seems that every time i do something in the command line it's gonna do something bad lol -offtopic

Stability is not an issue in the 64bit version. It is very stable. As for apps, flash works , its just work (read and follow a howto)to get it installed (32bit firefox/flash or nspluginwrapper).

---

### Post by pixelpainter on 2007-04-03
> my 32 bit ubuntu is like my pet i like it with my configurations and it taked too much time for me to configure it with samba, apache, internet sharing, shaping, find and install applications and resolve some other problems... i dont want to do all of these things again if i install 64bit ubuntu.  i have 64bit system but i didn't know that linux supports powerfull 64 bit system without problems.

I am also a relative newbie w/Linux and very green with Ubuntu, and the only way to learn is by doing.
That said, if you are concerned about messing up an installed os, I have found backing up the partition as an image file is the safest way to go, this way you can do a complete recovery and have things just the way you started.

For me, this works like a charm, and I currently have a triple boot with XP, Vista and Ubuntu.. (I finally found resolution to my own issues.. related to 8800 video card thanks to the great support from people at these forums)

I think it is important to realize it doesn't matter what OS u are using, (or Distro) as long as you are accomplishing the goals you intend to. I never understood why people have to be so forceful (not talking about anyone here :) ) about their opinions in their OS choices, they are all tools to an end result.

Daniel

---

### Post by jmore9 on 2007-05-05
I have installed kubuntu 7.04 64bit and there seems to be some improvement when compiling
the software compared to the 32 bit machine.  Goes a little faster it seems to me.  Also the install went faster by about 16 minutes.  Which I like alot. So all in all if possible everyone should use 64bit and then demand for 64bit software would be all the more pressing

---

### Post by HolyMurderer on 2007-05-06
At this moment, everybody advises 64-bit installation of Kubuntu 7.04?

I've tried it on VMWare (I use only Linux systems for years, I have great experience in it. I prefer KDE and I think that Kubuntu is the best normal Desktop Linux at the moment), and liked it, but I've seen that some software was not the latest, as in 32-bit Kubuntu, (i.e. aMSN).

What's your advice in this ?

Thanks :)

---

### Post by chinakr on 2007-05-06
Can anyone give a performance comparison between the 32-bit Ubuntu and 64-bit Ubuntu on AMD64 or EM64T machine?

Is it worth to transfer to 64-bit platform?

---

### Post by infurnus on 2007-05-16
I would try it i have an AMD 64bit and 7.04 ubuntu installed.  I've not had any stability problems actually I'm using my phone as a modem and posting through firefox. i have successfully gotten wine and my security programs installed and running....and i started my own ftp server from my box :)   I would install the 64 bit and try it out,  other than having to fix the sound card everything else was detected..kismet, wireshark, ettercap, nmap, nessus all still run fine. i havent tried the 32 bit version but my system is extreamly fast with only 1Gb of ram with the amount of programs and tasks i have running ...and if you dont like it reinstall the download for x86 it will cost you a cd.

---

### Post by LuisGMarine on 2007-05-16
Like many have said , just give it a try.  No one in these forums can make the decision for you to try out Ubuntu AMD64, but yourself.  My suggestion is if you have jitters about trying it, partition your hard-drive and free up some space where you can test out Ubuntu AMD64.  This way if something doesn't go the way you play, you always have that Ubuntu 32-bit right there as a fall back.  

For me I took the plunge head first, I completely wiped my hdd and installed just Ubuntu AMD64.  I have to say that it runs better on my current hardware than Ubuntu 32-bit.  I don't know what it is, but everything just works.  One of the most noticible is that back in Ubuntu 32-bit my sound card didn't have software-mixing and 5.1 surround by default.  Here on Ubuntu AMD64, that's not a problem.  Everthing is working straight out of the box.

So in conclusion, free up some space and give Ubuntu AMD64 a twirl.  If you end up not liking it then, just delete and try it again in the future.

Also, a lot of people are going to say that Ubuntu AMD64 is not ready because the lack of packages.  Well, my answer to that is, when more people run AMD64 and make it known to the developers that there is a vast majority of people using 64-bit processors, they start making programs for it.  Simple law of demand.

---

### Post by acutu on 2007-06-03
> **kaffelars said:**
> I'm using the AMD64 version with my Pentium D processor. Haven't tried it with the 32 bit version, but I find the 64 bit very fast.
I used [Automatix]("http://www.getautomatix.org") to install Flash, Mplayer and lots of other stuff (both 32 and 64 bit) and it works great.

Having used it only for a few days, I'd say the bigges disadvantage  is that there is less software compiled for the AMD64 architecture available. I don't find this to annoying though, as 32 bit software  runs fine most of the time. 

(Hint: Manually install 32-bit packages on 64-bit Ubuntu with **sudo dpkg -i --force-architecture <package.deb>**.)

Hi Kaffelars, thanks for this illumination. I had been confused that I had been able to install 4 and 10 year old windows software on Vista on my  triple boot AMD Turion 64x2 and yet whenever I wanted to install a package onto Ubuntu, there was not a 64 architecture version available and the install faultered. So your force suggestion seems like a good idea.

Al C.

---

### Post by Matymoo on 2007-06-04
> **Kilz said:**
>  If you want a OS that all you have to do is pop in a CD and do nothing else , install Windows. 

Actually, it's not that simple in windows!! For many people anyway. Most of my friends/family ask me to install windows for them. They struggle with drivers.  I found that although linux can be more fiddly to start with, it is easier to get the hang of!

---

### Post by Kilz on 2007-06-04
> **acutu said:**
> Hi Kaffelars, thanks for this illumination. I had been confused that I had been able to install 4 and 10 year old windows software on Vista on my  triple boot AMD Turion 64x2 and yet whenever I wanted to install a package onto Ubuntu, there was not a 64 architecture version available and the install faultered. So your force suggestion seems like a good idea.

Al C.

One word of caution, never ever ever ever force install libraries.

> **Matymoo said:**
> Actually, it's not that simple in windows!! For many people anyway. Most of my friends/family ask me to install windows for them. They struggle with drivers.  I found that although linux can be more fiddly to start with, it is easier to get the hang of!

That wasnt a recommendation to use Windows. Just that its easier to install for most people because they have a drive image called a restore disk. The problems with Windows happen whenever you click on start. :D

---

### Post by sirius11 on 2007-06-09
yes you can  and you should

---

### Post by mcook2 on 2007-06-11
I have an Acer T180 with AMD Athlon X64 3800+, 1GB RAM and it came with Vista Premium, 250GB H/D partitioned in half.  I originally bought it so I could get familiar with Vista for work, but the shine soon wore off that.   

Wanting to try Linux again (my main machine is a Mac Mini G4 running OSX 10.4), I resized the D drive in Vista and then went through installing Feisty Server 32-bit dual boot (seamless using Grub when Vista is already installed), then I got Feisty Desktop 32-bit, then went to Desktop AMD64, and found it VERY fast, but bumped into the venerable Flash issue and somehow ended up going back to running Ubuntu kernel 2.6.20-16-generic, which seems to be 32-bit again.

I'm about to see what it takes to get back to 64-bit so I'll let you know how I get on with that.

Meantime I just installed ntfs-3g so I can mount my Vista partitions and read/write to them.  I need the extra space to store virtual machines. This document was very helpful: [http://ubuntuforums.org/showthread.php?t=217009&highlight=mount+ntfs+volume](http://ubuntuforums.org/showthread.php?t=217009&highlight=mount+ntfs+volume).

I found the "No Flash" problem very easy to resolve using  [http://ubuntuforums.org/showthread.php?t=425672&highlight=flash](http://ubuntuforums.org/showthread.php?t=425672&highlight=flash) and [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435).

I guess I'll probably have to do some rework on that if I go back to AMD64. 

Ultimately, for some reason I have this silly notion that I should be able to boot up Ubuntu and run Vista in a virtual machine, regardless of whether any particular program is 32-bit or 64-bit.  I was gratified to see that VirtualBox 1.4 has Vista as an OS option, but I guess that's a whole separate discussion...

---

### Post by ba_shef on 2007-06-11
All,

I have to say that for me, the jury is still out. I instaled the 64 bit version of Ubuntu yesterday on a newly built work PC and have found it something of a mixed experience so far. This being my first experience with actually using a linux-based operting system as a primary (solitary?) OS, I am starting to feel like I threw myself in at the deep end. I have been using unix- or linux- based systems at work because they are massively superior for programming-related tasks, but after many years of practice I had also become rather adept at making Windows do what I wanted it to (although, I have to say that this was with heavy customisation; Windows out-of-the-box is utterly unuseable).

So far, many things in this distribution of Ubuntu have worked perfectly, and have been a real pleasure. While some of it is undoubtedly due to the system I am running, I have to say the speed is blisteringly fast and the whole experience is far more aesthetically pleasing than either the clunky Windows XP interface I am used to, the only-slightly-less-clunky Windows Vista interface or the Versions of the Mac OS I have seen. Furthermore, the endlessly customiseable nature of the system is something whose power grows as its user becomes more adept. 

Unfortunately, one or two other things have required a huge investment of time to make work, and others still elude me altogether. Making my graphics card work was a bit of a pain, and wine still does nothing but dump core no matter which way I try to make it work! I have read one or two blogs and forums on the subject, and I have to say that the principle complaint would be that many of the errors which inevitably occur have little or no real comprehensible explanation, even for someone like myself who is a competent and experienced programmer. I understand that community-developed systems are necessarily a little rough around the edges compared to commercial products. I just feel like a little more help when things do go wrong (and they do seem to rather a lot with this installation of Ubuntu particularly; a friend of mine, who just installed the same distribution in its 32bit incarnation does nothing but laugh at my frustration!) is all that  is required to take this excellent system to the next level, where it is a true alternative to Microsoft-developed OS's for newcomers and has all the stability, flexibility and customisability for which it is admired.

B

---

### Post by crjackson on 2007-06-11
I sure hope you don't give up.  I'm very green with Linux, and I'm setting my things up one step at a time.  I'm no programmer, but I can tweak WinXP and hardware like no body's business.  I've been building computers since the days of CP/M operatings systems and it's always a challenging experience when changing OS's.  My favorite OS of all time was OS/2 Warp - If I could have gotten the software for it that LINUX has (and at the same price), I'd still be running it today.  Man it was fast..

I'm loving U-64 so far, but I'm having to grow with it.  This Forum group has been great in helping me quickly resolve any gorwing pangs/pains.  I haven't tackled the accelerated graphics driver issue yet but it's on my list.  I do boot into windows when I need to do something that my U64 installation isn't ready for yet, but that's becoming less and less.

I've only been playing with U for about a week now.  It took me years to get REALLY proficeint with windows and it's quirks.  We need people like you (experienced programers/IT professionals) to keep Linux alive and growing.  There are things about windows I really like, like excellent hardware support for getting the very last drop of performance from your devices, and things I hate.  I'm becoming more comfortable with U64 each day, and I soon hope Windows will be something I have the Option to use on the rare occasion that I find it needed.  If more people will move to Linux, it will develope into an OS that is for everyone.

Give it a fair chance - a few weeks at least.  Then make your decision.

---

### Post by Kilz on 2007-06-11
> **ba_shef said:**
>  a friend of mine, who just installed the same distribution in its 32bit incarnation does nothing but laugh at my frustration!) is all that  is required to take this excellent system to the next level, where it is a true alternative to Microsoft-developed OS's for newcomers and has all the stability, flexibility and customisability for which it is admired.

B

The question is, does he have the exact same hardware as you? This may have escaped you in frustration, but you do realize [that the]("http://ubuntuforums.org/forumdisplay.php?f=73") ENTIRE [rest of ]("http://ubuntuforums.org/forumdisplay.php?f=131")the [forums is]("http://ubuntuforums.org/forumdisplay.php?f=138") for people having problems with that same 32bit system your friend had no problems with.
The reason some people have no problems is the hardware they are using just happens to be super common. If you have newer hardware, or hardware that isnt as common. Those same problems are going to fact you on the 32bit version.
There is no fool proof install friendly for everyone version of Linux that cant cause problems for some people. It just doesn't exist. 
Anyone who tells you there is 
1. Doesn't know what they are talking about.
2. Is telling you a lie.
3. Is mistaken.
There is no super friendly easy, just pop it in and its ready to go in a few clicks version of Linux. Heck there isnt even a version of Windows like that. If you had to install Windows without ever using it before, with a copy , not supplied from a computer maker ( a restore disk image), but from Microsoft, on a computer you built. You would be just as frustrated.

---

### Post by mcook2 on 2007-06-15
Silly me - of course I am still running 64-bit cos that's what I last installed.

I checked my /boot/config.* files, and all still say: 

CONFIG_X86_64=y
CONFIG_64BIT=y
CONFIG_X86=y

This must be the way to check if you aren't sure, as dmesg doesn't  seem to explicitly say anything like "Hey you, in case you were wondering I am running amd_64-bit, so there".

I guess I  got  confused when VirtualBox failed to boot up my *amd_64* Feisty Live CD, saying s.t. like "you don't have a flat memory architecture - use an i386 CD". I must look into that elsewhere.

I seem to remember that right after I installed my original kernel name used to include *amd_64*, but since then I've upgraded twice and it's long gone.  

Have a nice day,

M.C.

---

### Post by kyrhash on 2007-06-15
I know many people (myself included) think that Automatix is a brute force method it can be useful here.  Use it to download the 32 bit version of swiftfox which runs much faster than firefox.  Then you can easily get into both google and youtube video.

---

### Post by John.Michael.Kane on 2007-06-15
> **kyrhash said:**
> I know many people (myself included) think that Automatix is a brute force method it can be useful here.  Use it to download the 32 bit version of swiftfox which runs much faster than firefox.  Then you can easily get into both google and youtube video.

Thats why theres this [http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java) 

Theres really no need to use the app you listed as a first resort.

---

### Post by bullsmack on 2007-07-08
i keep hearing all this talk about doing "setup". i am new to all this. and to the pc for that matter. but in my limited 2 years of experience i have i have biult my own and now i am one that everyone asks questions to about windows in the game that i run servers in. all i would like to know is what do you mean by "setup"?

if you mean setting up the operating system to run personalized from the begining. then cool. but if you mean everything i will ever install will require me to have programmng skills then i wonder why this operating system would ever be considered by anyone but programmers and wanna bes. i just want all the hacking crashing, viruses, bugs, weird stuff and glitched and slow bottle nexks that come from windows to stop. if i have to do some work im fine with that . my god it seems to me that id just be trading the work i do  now to reinstall windows all the time from the crap ppl llike to lob at my pc because they get banned from my server. and all the weird stuff that happens from windows acting stupid and changing settings out of the blue. if im chaging that work for a little set up work then i dont much see the diffrence. can some one just explain in laymens terms how one would install a game for instance on linux? i mean is it like i have to literally put all the files where they go and name the files and do that sort of thing. or are there set up helps for games and such programs?  i have been reading for days and so far i have not read one thing about how to install ...say... a game? 


i was actually reading the third page of this thread when i posted this.

---

### Post by hendoc on 2007-07-08
I ran 64 bit Edgy, and now run 64 bit Feisty on an AMD64 3200+. Install the OS, then go get Automatics. Then let Automatics install Swiftfox, and lastly let Automatics install the flash plugin and all the codecs you need. My 2.19 Gh processor smokes my 32 bit Celeron D with a 3.2 Gh chip. Theres no comparison in speed to tired old XP.

---

### Post by bullsmack on 2007-07-08
thanks for your helpo

---

### Post by yungwunn911 on 2007-07-22
has the ADOBE flash issue been resolved for 64bit users?

I have an AMD turion 64 system and deciding if i should go ubuntu 64 or 32.

thanks, 

mike

---

### Post by John.Michael.Kane on 2007-07-22
> **yungwunn911 said:**
> has the ADOBE flash issue been resolved for 64bit users?
Resolved in what way?

Most 64bit user install flash using the [Howto Install 32 bit Firefox with Flash ]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java") guide.

> **yungwunn911 said:**
> I have an AMD turion 64 system and deciding if i should go ubuntu 64 or 32.

thanks, 

mike.

As for you deciding should you go ubuntu 64 or 32bit. You may want to read the thread below.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by Deco_21 on 2007-07-23
It works ok in 64-bits , make shure you download the right ubuntu version ok.

---

### Post by yungwunn911 on 2007-07-23
i am downloading the one from the 64bit tutorial. 

file name reads : ubuntu 7.04-amd64

i plan to just boot up off CD and hopefully it will partition with the kernels running off that CD.

would this be ok?

-mike

---

### Post by paulmac on 2007-11-08
AMD 64, Gutsy 7.10, Nvidia video card, all is well.  Automatix is great!  Gutsy 7.10 is the best linux thus far.  

Windows?  whats that?

---

### Post by damvcoool on 2007-11-08
who needs windows and gates when we live in an open world.

wise words that someone said (i don't know who)

now 64bit is worth it, you just have to add a couple of repositories to make it better but it is defenetly worth it.

Flash and Java are now supported not by default but it's not as hard as before, it's now a few clicks away.

---

### Post by Orval on 2007-11-09
And what repos are that?

---

### Post by Kilz on 2007-11-09
Why was a 4 month old post revived?

---

### Post by jim_meech on 2007-11-09
There is absolutely no problem with running 32bit x86 ununtu on 64bit AMD hardware.
I run 32 bit on my AMD athelon 4200 x2 because I can not get some windows apps to work corectly under wine in the 64bit ubuntu.
You will not notice too  much performance loss on evryday applications.

Regards
jim

---

### Post by damvcoool on 2007-11-09
This is the Script I use to add all my Repositories.
just copy it into a text file name it sources.sh, give execute permision. and double click on it run in terminal, and that's it. remember to refresh synaptic you will have a few new things.

[/code]
#!/bin/sh
# Seveas&#8217; packages

wget [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg)
sudo apt-key add 1135D466.gpg
rm -fr 1135D466.gpg

sudo echo deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas all >> seveas.list
sudo echo deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas all >> seveas.list
sudo cp seveas.list /etc/apt/sources.list.d/seveas.list
rm seveas.list 1135D466.gpg

# Bleeding edge wine packages
wget [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
sudo apt-key add 387EE263.gpg
rm 387EE263.gpg
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

# Penguin Liberation Front

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - 
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

# Skype packages

#echo deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free >> /etc/apt/sources.list.d/skype.list
#sudo cp skype.list /etc/apt/sources.list.d/skype.list
#rm skype.list

# Debuntu Ubuntu edgy packages

# GPG Key: [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)

wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)
sudo apt-key add GPG-Key-chantra.txt
rm GPG-Key-chantra.txt
echo deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse >> debuntu.list
echo deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse >> debuntu.list
sudo cp debuntu.list /etc/apt/sources.list.d/debuntu.list
rm debuntu.list


# Geole Repositories
wget [http://ubuntu.geole.info/dists/feisty/Release.gpg](http://ubuntu.geole.info/dists/feisty/Release.gpg)
sudo apt-key add Release.gpg
rm Release.gpg
echo deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) gutsy universe multiverse >> geolebuntu.list
echo deb-src [http://ubuntu.geole.info/](http://ubuntu.geole.info/) gutsy universe multiverse >> geolebuntu.list
echo deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) gutsy-backports main restricted universe multiverse >> geolebuntu.list
echo deb-src [http://ubuntu.geole.info/](http://ubuntu.geole.info/) gutsy-backports main restricted universe multiverse >> geolebuntu.list
sudo cp geolebuntu.list /etc/apt/sources.list.d/geolebuntu.list
rm geolebuntu.list



# iced-tea updates
wget [http://apt.mediatomb.cc/key.asc](http://apt.mediatomb.cc/key.asc) -O- -q | sudo apt-key add -
echo deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/ >> people_ubuntu.list
echo deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/ >> people_ubuntu.list
sudo cp people_ubuntu.list /etc/apt/sources.list.d/people_ubuntu.list
rm people_ubuntu.list


# Mediatomb
echo deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty main >> mediatomb.list
echo deb-src [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty main >> mediatomb.list
sudo cp mediatomb.list /etc/apt/sources.list.d/mediatomb.list
rm mediatomb.list


# Automatix Reporitory

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)
gpg --import automatix2.key
gpg --export --armor E23C5FC3 | sudo apt-key add -
rm automatix2.key
echo deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main >> automatix.list
sudo cp automatix.list /etc/apt/sources.list.d/automatix.list
rm automatix.list


## Avant Window Navigator and Exaile
wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
echo deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy all >> syz.list
echo deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy all >> syz.list
sudo cp syz.list /etc/apt/sources.list.d/syz.list
rm syz.list
[/code]

---

### Post by rsambuca on 2007-11-09
I hope you don't plan on a smooth upgrade to Hardy Heron!!!

---

### Post by bapoumba on 2007-11-10
This thread is now outdated. No need o revive it, closing.
Feel free to use the report button if you need it reopened.

---

