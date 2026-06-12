---
title: "Gaming with Cedega on 64-bit"
date: 2005-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jet2k5 on 2005-08-15
Sorry if this might seem as a double thread to some of you, but I need a newone with almost no replies.  So tomorrow is the night.  As of right now I have the money to buy the new computer, I've been struck with bad luck and I missed the bank, so now I have to wait until tomorrow.

So here is my question for those people that might game on Ubuntu 64-bit.  I'm looking for a distro that is easy, I seriously don't want something hard, I don't have the time to be fixing things here and there, just to get me playing a game.  I know that you can install Cedega on 64-bit, does anyone here have a link to that wiki?  I can't seem to find it.

So what would you guys rate gaming on Ubuntu 64-bit?  From 1 being the easiest to 10 being ther hardest thing that you have ever done.  The first game that I'm going to be getting is Americas Army.  Since it's free and it kicks ass.  I will download that as soon as I get Ubuntu on my computer.  I was going to install Windows XP , but it's really not worth it.  I know I can somehow game on Ubuntu.  

My question is really how easy is it to play games on Cedega and a 64-bit distro?  Like is there any kind of special set ups that I should know about?  My other question if not, should I just install 32-bit Ubuntu until Ubuntu 64-bit improves?  I really wouldn't like to do this, but I don't want to have to deal with a heap of trouble just to get some basic things working.   Just not worth it for me.  Like I said I have less time with school, so I don't have the time to mess around.  Please help me make the right choice before Friday ( today is monday and the parts should get here on Friday ( hopefully ) )

Thanks, and I hope to work with some of you guys on this.

---

### Post by DancingSun on 2005-08-15
Unfortunately, objectively speaking, I think if you want pain free gaming, keep the XP installation.  I understand Cedega works for many games, but even then there are quirks for some games.  For example, in the Gaming forum, there is a thread about some right click bug with World of Warcraft on Cedega.

In my opinion, an emulation/compatibility layer like Cedega is not the way to go in the long run.  The best way to create an equally enjoyable gaming experience on both Linux and Windows is to have the developers develop games that are cross-platform.  This isn't as hard as it sounds because most games don't use a lot of platform specific libraries (the only major platform depedency in use for Windows games is DirectX).  But the key is to design the game with cross-platform in mind.  Reduce platform dependencies and when the time comes to porting the game, it will be much easier.

Reading a couple of the threads in the Gaming forum tells me that while you can run many games in Cedega, the experience is frequently subpar when compared to running on Windows.  Plus, the audio experience seem to be better under Windows, due to having the manufacturer's support for proper sound drivers.

For games that have native Linux ports, it's really easy to install and start playing.  True Combat: Elite was a piece of cake to install, as the Loki installer is setup so that it will search for the directory where you installed ET.  So it's basically: make the installer executable, and click install.  Although, I did need to do something to make the sound work (this has to do with Linux's sound system, as it seems like older Id games like quake2 and ET only work with OSS and not the newer ALSA, so this problem will also be present if you use the 32-bit Ubuntu.  Newer games like the Doom3 demo, however, did not have this problem).

I think for most games, 32-bit or 64-bit Ubuntu doesn't really matter that much, as most Linux ports rely fairly little on external libraries (at least that's true for most Id and Epic games).  Not sure about Cedega though, since I haven't tried it.  BTW, here's the wiki for Cedega on AMD64:
[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

I'm dual booting Ubuntu64 and Window XP, and so far I like it.  Everything that works in Ubuntu, I'll use it in Ubuntu.  If I don't have time to make it work in Ubuntu, or if it's just flat out not available for Linux, I'll just boot back into XP.

I have half of my HDD dedicated to WinXP, although I'm starting to think that I should shrink that :).  Even though 95% of the time I'm on Ubuntu64 right now, WinXP still comes in handy from time to time.  Especially if you have gagdets, since portable MP3 players, digital cameras, new printers, and scanners have much better support on Windows.

Also, you should keep in mind that the official backports project has started to port software packages to AMD64, so I think the usability gap between the 32-bit and 64-bit Ubuntu is going to decrease significantly as the months pass by.  Although 32-bit Ubuntu still holds the advantage of able to use Flash and win32codecs "more easily".

Edit: Almost forgot my rating for Ubuntu64 on games.  Well, I've only played Neverwinter Nights, Doom3 demo, AA, ET, and TC:E, they all worked painlessly.  Yes, in some cases, I had to do something to make the game work correctly (again, mostly sound problems), but they're not rocket science.  **So my rating on gaming with native Linux ports is an 8!**  In fact, it surprised me how easy it is it install these games without debs.  The game installers that were used are very easy and effective.

---

### Post by DancingSun on 2005-08-15
I also want to point out what I see as the main difference between Linux and Windows, from a user's point of view.

While many things don't work with Linux out of the box, in many cases there is a way to get it to work properly, as Linux is very open and allows the user to access many configuration files and change different system modules.  So given enough knowledge of the system, Linux can probably work more "properly" than Windows.  Plus, with Linux, you are not forced to shell out money to buy the next version of Windows to have your bug "fixed".

Windows on the other hand, has many things working out of the box.  But due to its closed nature, if something doesn't work correctly, most of the time there are no proper solutions.  Instead, there are a lot of work-arounds.  Even if the source of the problem is some simple setting, chances are these setting are not neatly tucked into a configuration file for you to edit.  Not to mention, you can't swap the OS's system components for another one if the one you are using is causing trouble.

So while you might say you don't have time to fiddle around with things in Ubuntu now.  I'm sure you'll get addicted to fiddling around with the internals of Ubuntu once you start to get aquainted with the system.  I'm a living example of this addiction :)

BTW, if you own a multi-button mouse (I own a Logitech MX510), I think I know the "proper" way to get all the buttons working.  I even got the "switch application" button to work in games on Ubuntu, which I was not able to get it to work in Windows!  I probably should make a how-to on this, but I'm too lazy :P.  The optical scan resolution, however, is another story as I don't know of a way to verify if I have the 800dpi thing working or not.

---

### Post by Jet2k5 on 2005-08-15
Thanks a lot for the reply.  This has really helped me.  The thing is that my copy of windows isn't .. let just say " Proper " windows.  I'm not going to go into that.  But if you are smart you will know what I mean.  The only thing that I'm really going to use windows for is BF2.  Right now I only own StarCraft, which I can play on Linux with Cedega no problem.  I don't have a problem trying to go Ubuntu all the way.  I will have to use Ubuntu and see what is up.  So now that my question is answered here is the other one.

Have you played a game like AA and seen where it works better?  Like in Windows ( which sounds like the more logical choice ) or in Linux?  Or just flat out the same?  I personally would think that they both are the same.  Since they are on opengl.

Once again thank you for your help.  Just FYI I will be ordering my parts tomorrow night.  It's much faster than I thought.  Which is awesome!  So I'm firstly going to install Ubuntu 64-bit.  Use that for a couple of times, as far as getting everything working with firefox and stuff and trying out Linux naitive games like AA.   Then if I'm not happy just go onto Windows.

---

### Post by DancingSun on 2005-08-15
Some school offer discounted Windows, you might want to look into that.

A word of warning, if you might add Windows later on, you will need to plan it out early, as Windows like to be in the beginning of the HDD.  Which means, if you think you will install Windows later on, you'll need to leave some blank free space at the beginning of your hard drive when you partition the HDD for Ubuntu.  Or else, you will be getting into some nasty headaches trying to get Windows installed.

Also a little tip when making partitions for Ubuntu.  Mount "/home" on a separate partition.  This is what I did.  The intention is that if I ever want to switch to 32-bit Ubuntu or want to do a clean install of Breezy when it comes out, all my games, which I explicitly instructed the installers to install under /home/username/games, will be left alone and only the "/" partition will be overwritten.  Although I must admit I don't know how the details of that work, nonetheless, this tip was pointed out by several install guides that I read.


Edit:
The last time I played AA on Windows was when I before I built my new computer, so I was still on a plain old ATI Radeon (yep, the original one), so it's not really comparable.  However, I did play TC:E on both Windows XP and Ubuntu 64 on the new computer.  I did not do any benchmarking but I think the performance for both Window and Ubuntu on a GeForce 6600GT are both good enough that I don't notice any big difference.  However, I did notice that the fonts in the in-game menus in TC:E is much smoother looking.  Maybe the Linux drivers had some form of anti-aliasing (I know it's not full-screen because I still get jaggies on the 3D polygons) turned on by default.  But then again, even in GNOME the fonts look better than in Windows, IMHO.  BTW, I can snipe sooooo much better now that I can extend the in-game corona to "extreme", no more fog blocking my scoped aim!

---

### Post by Jet2k5 on 2005-08-15
I think i can specify to isntall Linux on the back of the hdd.  This way the front is open for Windows.  My school is cheap and so is my state ( Florida )  they don't provide such things.  Anyhow I'm off to sleep.  I will TRY to aim at the Linux desktop, but chances are I'll have to install windows.  I'll decide tomorrow.  Windows might be up there.

---

### Post by DancingSun on 2005-08-15
Jet2k5, I edited my previous post to include some game comparison.

---

### Post by Jet2k5 on 2005-08-15
sounds like an awesome plan dude.  I can't wait.  Maybe we can play like AA together if you want ;)

---

### Post by DancingSun on 2005-08-15
[QUOTE=Jet2k5]sounds like an awesome plan dude.  I can't wait.  Maybe we can play like AA together if you want ;)[/QUOTE]
Sure thing!  I think the next step is to get Teamspeak packaged for AMD64...hopefully Tamir or someone can help us do that.  I really miss those CS days when I can communicate with teammates via the voice comm.  Makes co-operation much easier.

Have you played True Combat: Elite yet?  I think you'll like it.  It's very similar to AA, but you get to play the bad guys, and they have a different set of weapons where the performance are slightly different from the CTs.  The game is much more fast-paced, but I think that's mainly due to the map designs, as they are smaller, and less open-air.  AA is good, but I get bored after a while since there isn't a lot of maps to play...OH!  That just reminded me!  AA on Linux is an **OLDER VERSION**!  Which means you don't get to play with the people that have the newest version of AA!!!  I think that was the main reason why I got bored, because there are so few servers and players playing the older version.

---

### Post by Jet2k5 on 2005-08-16
Yeah I saw that the other day when I was about to download it.  I hear that CS just got support for the voice-communication stuff in Cedega.  I think it's the CounterStrike Source of something of that sort.  Anyhow this is going to be good.  I can't wait to build this computer.

---

### Post by Jet2k5 on 2005-08-16
What is this i hear that Cedega or the " games " have to be run in the chroot mode?  I thought you just force the arch on Cedega and just go about installing the games.  I went and visited the transgaming forums and alot of the Ubuntu users mention that they run the games from a chroot environment.  What is up with that?!?!?

---

### Post by DancingSun on 2005-08-16
Dunno, maybe they didn't see that wiki?  Don't worry, when you get your computer built, you can try it out and see what works :D

Edit:
Oops! I'm sorry, did I just make your wait more painful?:-\"

---

### Post by Jet2k5 on 2005-08-16
[QUOTE=DancingSun]Dunno, maybe they didn't see that wiki?  Don't worry, when you get your computer built, you can try it out and see what works :D

Edit:
Oops! I'm sorry, did I just make your wait for painful?:-\"[/QUOTE]


haha I already got hurt.  I have to wait ti'll tomorrow to order again.  I HOPE this is the last time.  Seriously :)

---

### Post by DancingSun on 2005-08-17
[QUOTE=Jet2k5]haha I already got hurt.  I have to wait ti'll tomorrow to order again.  I HOPE this is the last time.  Seriously :)[/QUOTE]
 #-o 





 ](*,)

---

### Post by Jet2k5 on 2005-08-17
It Is Done!  I Have Order The Last Parts To My Computer!  They Should Be Here In 3 Days!!!!!!!!!!

---

### Post by DancingSun on 2005-08-17
Gah! **Three** days!!! Oh! The agony! =P~

So you'll either get it this Sat. or next week!

---

### Post by Jet2k5 on 2005-08-17
Yeah I know.  But I might have to find a new screen.  The one I have right now can only do up to 1024x768 @ 60Hz.  KDE gives me the option to go up to 87Hz but it just spazes out and crashes.  So I'm going to go look around Staples, Office Max and other retail shops to see if I can find something cheaper.

---

### Post by DancingSun on 2005-08-17
What's the monitor's model?  Is this a new monitor?

---

### Post by DancingSun on 2005-08-22
So, have you finished building your computer yet, Jet2k?

---

### Post by Tamir on 2005-08-23
Sorry for being stupid, but doesn't AA have a linux version? it doesn't matter if it is for 32 bit, I know my sister was playing it without chroot on her gentoo 64.

Can I enjoy with you on game too :)?

---

### Post by DancingSun on 2005-08-23
[QUOTE=Tamir]Sorry for being stupid, but doesn't AA have a linux version? it doesn't matter if it is for 32 bit, I know my sister was playing it without chroot on her gentoo 64.

Can I enjoy with you on game too :)?[/QUOTE]
Yes AA has linux version, but it is one version behind the windows release :(.  Still, I think we were talking about the linux verison and it's performance versus the windows counterpart.

But yes, join the AMD64 gaming crowd Tamir!

---

