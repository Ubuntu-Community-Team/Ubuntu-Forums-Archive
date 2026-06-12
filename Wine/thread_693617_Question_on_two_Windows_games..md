---
title: "Question on two Windows games."
date: 2008-02-11
forum: Wine
---

### Post by chrispche on 2008-02-11
Does Doom 3 and Quake 4 work in Linux. Do id software have some kind of patch to get them working? Please don't tell me to install Wine, it's a piece of shite.

Although I have a copy of Windows XP running in VMware. Would I be able to play the games in that?

My machine spec is:

Core 2 Duo 2.33, 2gig Ram, nVidia 512mb card. Intel Chipset Motherboard.

OS Ubuntu Linux 7.10 Gnome.

---

### Post by FrozenFox on 2008-02-11
[http://www.liflg.org/?catid=6&gameid=48](http://www.liflg.org/?catid=6&gameid=48)  doom 3 native installer

There's a quake 4 native installer included with wine-doors. 
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)
That particular entry DOESN'T use wine, so I'm not sure why they did it, but it's there.

And no, you can't play 3d games with VMWare because it does not use your "real" video card, it uses a simulated video card, among other reasons. They are working on getting such working, and last I heard some very minor old 3d games worked if you know how to set up that stuff, but certainly nothing new, and especially nothing so heavy as doom or q4.

That said, I seriously disagree. Wine is amazing. Especially when you understand just how difficult what it tries to achieve is and how well it does it, even if its not near perfect. Every release gets better.

---

### Post by dudeofthedead on 2008-02-11
> **FrozenFox said:**
> That said, I seriously disagree. Wine is amazing. Especially when you understand just how difficult what it tries to achieve is and how well it does it, even if its not near perfect. Every release gets better.

How can Wine get any better when it amounts to catching a moving train?  Please share some enlightenment with us.

---

### Post by FrozenFox on 2008-02-11
That's a pretty ridiculous comparison, and the "please enlighten us" was entirely unnecessary.

Windows may be "constantly changing", but wine is doing a pretty decent job of rebuilding the parts of it that are constantly used and hardly changed from release to release -- that is, most of the core of the system. The 'train' moves 10 feet per year. Just look at some of the games it can run to some/decent degrees for chrissake, they aren't really that old -- like call of duty 4, released in very late 2007! It may be eternally playing the catch-up game, but it really doesn't take that long for wine to tag behind in many areas, and it only gets more accurate and compatible with every release.. the negativity i'm getting the impression of is seriously unwarranted.

[http://www.winehq.org/site/myths#catch_up](http://www.winehq.org/site/myths#catch_up)

Please keep an open mind. Not everything is perfect in the land of the free OS, but I think wine does a damn good thankless job towards filling in the gaps even on the newest stuff around despite imperfection.

---

### Post by chrispche on 2008-02-12
> **FrozenFox said:**
> 

Please keep an open mind. Not everything is perfect in the land of the free OS, but I think wine does a damn good thankless job towards filling in the gaps even on the newest stuff around despite imperfection.

The same can be said for non free OS's. Probably with the exception of Mac OSX which is damn near perfect. 
;)

---

### Post by MichaelLerch on 2008-02-12
To be honest, the top three OS's so far are:

1.  Windows (XP / Vista)
2.  Mac OS X
3.  Ubuntu
----------
4.  Fedora Core
5.  Suse
6.  Mandriva
7.  Red Hat
8.  CentOS
9.  Gentoo
10.  TinyLinux


Correct me at any time, but since Ubuntu has gained quite a fair share of attention from Dell owners... that's the only reason it's ranked at 3. 

I think if Microsoft opens the source to DirectX a little more, and Ubuntu was able to integrate it greatly into itself.. it'd surely have a great advantage over Windows.  That'd let gamers such as myself, more to work with in linux. :)

Developers could say, "As long as the OS supports DirectX [x] (where [x] is the version number) the game will work.  Here's the installer script for the most popular distro's and here's a compile script for those who don't have the popular ones."

---

### Post by Ferrat on 2008-02-12
> **dudeofthedead said:**
> How can Wine get any better when it amounts to catching a moving train?  Please share some enlightenment with us.

First of it's not like catching a moving train for the simple reason MS makes 99% of their stuff backward compatible = if you get one thing to work there is a pretty low risk that an MS update will break it totally, that is also one of the reasons linux can't take for ex. the gaming market yet, Linux has no such standards that work on all dists and one thing that works on one version of Ubuntu might break the next due to package updates that the old program can't handle and so on. 
And just the wine project itself is prof of that, they are catching up rapidly and a lot of games using dx9 are now playable that wasn't just a few months ago

---

### Post by FrozenFox on 2008-02-12
> **chrispche said:**
> The same can be said for non free OS's. Probably with the exception of Mac OSX which is damn near perfect. 
;)

I never said there was anything wrong with a mac, aside from the horror stories I've heard about leopard's stability from mac enthusiasts. I want to buy a mac laptop at some point so that I may be knowledgeable 3-fold ;P Or even try out solaris and/or freebsd to make it 4-5-fold :)

I didn't mean to imply windows was terrible either (though I won't lie, I really don't enjoy using it, hehe). It just doesn't change as much as some people like to suggest in terms of wine never catching up, and even the changes that are huge are not too difficult or slow to make up for with wine's setup.

---

### Post by Joeb454 on 2008-02-12
> **MichaelLerch said:**
> 

I think **if Microsoft opens the source to DirectX a little more**, and Ubuntu was able to integrate it greatly into itself.. **it'd surely have a great advantage over Windows**.  That'd let gamers such as myself, more to work with in linux. :)


There's your answer highlighted in bold ;)

MS Won't open the source to DX, because it'd allow Linux an advantage.

---

### Post by dudeofthedead on 2008-02-12
It was meant to be infuriating.  There's nothing wrong with Wine doing a ketchup job, but sometimes I just think that, maybe it's not worth the hassle after all.  I mean, if you really want to play Windows games that bad, then why not keep a Windows partition instead?

> There's your answer highlighted in bold

MS Won't open the source to DX, because it'd allow Linux an advantage.

Wasn't Microsoft very recently forced to give away some of their DX secrets, for (yet again) playing unfair?  It was written that they should from now on facilitate ports to other platforms.  Or something like that.

---

### Post by MichaelLerch on 2008-02-12
> **dudeofthedead said:**
> It was meant to be infuriating.  There's nothing wrong with Wine doing a ketchup job, but sometimes I just think that, maybe it's not worth the hassle after all.  I mean, if you really want to play Windows games that bad, then why not keep a Windows partition instead?



Wasn't Microsoft very recently forced to give away some of their DX secrets, for (yet again) playing unfair?  It was written that they should from now on facilitate ports to other platforms.  Or something like that.

I believe that was in Europe for.. OS reasons.  I can't remember what happened, but it was mostly, "On install, why does it need to be Internet Explorer?  Why not let us pre-install Firefox or something?" and that escalated from there.

Also if Microsoft released DX to the open market, their market share would go for a downward spiral and simply die.  They don't fear Apple, it's the open source community such as Ubuntu that they fear.  They know we will dominate them if we were given then chance.

---

### Post by FrozenFox on 2008-02-12
> **dudeofthedead said:**
> It was meant to be infuriating.  There's nothing wrong with Wine doing a ketchup job, but sometimes I just think that, maybe it's not worth the hassle after all.  I mean, if you really want to play Windows games that bad, then why not keep a Windows partition instead?


Well, my thoughts:

* It's more convenient to stay in linux all the time if possible instead of wasting time rebooting into the other os. Especially if what you want to run performs well enough to be worth the small effort. 

* Wine isn't just for home desktop people. It's much less costly for a company who is easily able to and has the personal ability to install stuff on wine themselves to just run a program working in wine than it is to buy X expensive licenses of windows just to get it working. Particularly large companies. Please don't turn this into a windows vs osx vs  linux cost debate, I'm simply offering a reason that is applicable to some situations, I don't intend to make an overall statement of the times.

* Personally, I (and many others) have tons of seriously stupid problems (like for me, the mouse scroll wheel on 2 different mice that work perfectly in linux randomly deciding to disable themselves, with windows' default drivers or the mouse creators' drivers) in xp (even a fresh install), and rebooting into it just for a game is frustrating, particularly when said bug is active. Hooray run-on sentences!

I had some other stuff to say, but my brain died in the middle of typing this last point.. so I guess this small list is enough for now XD

---

### Post by BlueKoala on 2008-02-13
> **dudeofthedead said:**
> It was meant to be infuriating.  There's nothing wrong with Wine doing a ketchup job, but sometimes I just think that, maybe it's not worth the hassle after all.  I mean, if you really want to play Windows games that bad, then why not keep a Windows partition instead?



I for one don't want to pay or be forced to pay for an OS that I don't want from a company I don't like. I also don't want to deal with anti-viruses anymore unless I get paid for it.

I want to take up programming and contribute to development but I feel like I'm so far behind I don't know where to start. On the other hand, simply having the notion that there's a possibility that I CAN make a difference or a contribution gives me a comforting feeling of control over the software that's being run on my computer; get better sleep. ;)

So far I'm really happy with Wine. I installed steam, installed a font, installed all my games on there and they all run great with the Exception of Civ 4.

---

### Post by Cannaregio on 2008-02-13
> **dudeofthedead said:**
> It was meant to be infuriating.  There's nothing wrong with Wine doing a ketchup job, but sometimes I just think that, maybe it's not worth the hassle after all.  I mean, if you really want to play Windows games that bad, then why not keep a Windows partition instead?


BECAUSE I don't want to keep a windows partition at all. Why should I, if all the games I do want to play do run in wine already (or will run in wine soon anyway)?

They will run in wine anyway: I'm confident because wine is getting better and better, as I have had the opportunity to check myself over the last year. 
I can now run games like hoyle casino, fritz chess and my beloved train simulators, games that were impossible to run only a few months ago. 

If a game is good, it is good for years, not just for weeks. So the fact that you cannot run the games as soon as they come on the market does not matter in the least to me.  They will all run in wine (and, incidentally, be also much more easy to find on the web for free) after a few months anyway. And I'll have the added advantage of knowing from other users' experience if their game engine is really worth playing, or if it was just a frills-oriented crap sale.

---

### Post by dudeofthedead on 2008-02-13
BlueKoala, well great man, but I don't see how one makes a difference when one chooses to buy and run Windows software using Wine.  AFAIK it's only helping Microsoft sell more Windows games, so congratulations.

No matter what, if you run, for example, a game such as HALF-LIFE 2 through Wine, Steam will still recognize your operating system as a Windows one.

Wanna make a REAL difference?  Buy a game like PENUMBRA: OVERTURE at Frictional Games' website, which already has a Linux client (no box though).  Purchasing a Windows box, on the other hand, ain't gonna help PERIOD

---

### Post by FrozenFox on 2008-02-13
> **dudeofthedead said:**
> BlueKoala, well great man, but I don't see how one makes a difference when one chooses to buy and run Windows software using Wine.  AFAIK it's only helping Microsoft sell more Windows games, so congratulations.

No matter what, if you run, for example, a game such as HALF-LIFE 2 through Wine, Steam will still recognize your operating system as a Windows one.

Wanna make a REAL difference?  Buy a game like PENUMBRA: OVERTURE at Frictional Games' website, which already has a Linux client (no box though).  Purchasing a Windows box, on the other hand, ain't gonna help PERIOD

It's true that it's a good idea to support linux games and SOME developers see no point porting when wine works. However, you're on the assumption that MOST developers of software that work in wine won't notice that a lot of people in linux are using it and realize that they have a lot of support there and will port their product. UT games and the Quake games for instance run fine in wine, why would the companies even bother porting them? In the case of id, its because they like doing it, but you'd have to be stone cold dead not to notice all of the new commercial games popping up for linux or with linux support lately, and all of the Loki installers for games that work in wine anyway to run natively on linux.

Besides, where is your reasoning? Having their apps and games people frequently use available to them brings more people to linux, ie creates a larger business market! If it weren't for wine, I think most of the boom in linux users in the last year would have been nonexistent. I certainly wouldn't have come over to the tux side without incentive that my favorite stuff that's not been ported has a chance of working!

In short: nothing will ever have major commercial support without users moving to it, and users will never move to something en masse without support of their favorite things which often there is no alternative or port for.

---

### Post by BlueKoala on 2008-02-13
> **dudeofthedead said:**
> BlueKoala, well great man, but I don't see how one makes a difference when one chooses to buy and run Windows software using Wine.  AFAIK it's only helping Microsoft sell more Windows games, so congratulations.

No matter what, if you run, for example, a game such as HALF-LIFE 2 through Wine, Steam will still recognize your operating system as a Windows one.

Wanna make a REAL difference?  Buy a game like PENUMBRA: OVERTURE at Frictional Games' website, which already has a Linux client (no box though).  Purchasing a Windows box, on the other hand, ain't gonna help PERIOD

ACK! NOOOOOOOO!!!!!
You misunderstood me =(
I run all my games in Linux, I dont use windows at all anymore. 
And I also like to go to EB games and ask the guys if theres a linux binary  for the games Im looking at. I know in advance, I just like to test them when they come up and ask me if I need any help. Like the time I wanted to buy Quake4, it was 20 bucks and I knew and I knew it was ported but I wanted to ask anyway. Maybe it's just purely narcistic, but I enjoyed seeing the games expert have a really puzzled face on a gaming question I was asking him :)

What I meant by making a difference is by going in the code and changing stuff. Which I wish I knew how to do. It's called "code" because ppl like me aren't supposed to understand it. :P

---

### Post by chrispche on 2008-02-17
Ok, I will have Quake 4 the single player version tomorrow. How do I get it working without wine? I assume there is a linux installer of sorts? ID are good in that way aren't they?

---

### Post by FrozenFox on 2008-02-17
> **chrispche said:**
> Ok, I will have Quake 4 the single player version tomorrow. How do I get it working without wine? I assume there is a linux installer of sorts? ID are good in that way aren't they?

Sigh.. The easiest solution (that installs but as i already said -->doesn't use!<-- wine) in all likelihood is in the 2nd post of this thread...

But if you want to do it the long(er) way, maybe "quake 4 linux installer" 's first 3 results in google may help you out..

Come on now..

---

