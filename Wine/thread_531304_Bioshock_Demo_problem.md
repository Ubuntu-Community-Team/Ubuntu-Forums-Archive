---
title: "Bioshock Demo problem"
date: 2007-08-21
forum: Wine
---

### Post by Nehvrook on 2007-08-21
Hey all, I just downloaded the Bioshock PC demo and got it working on my Windows Hard drive. Now I've moved it over to Linux and I've used wine to install it.

When I first tried to run it I got an error message in the console saying a few .dll files were missing. I found them in System32 and that got me past that problem but now I get an error when I run the game which tells me to go here 
[http://www.securom.com/message.asp?m=module&c=8008](http://www.securom.com/message.asp?m=module&c=8008)

Apparently it thinks there is some debugging software going on in the background?

I tried using WINEDEBUG=-all but it still said the same thing.

So my first question is, Is it just thinking wine is something it's not

And my second question is, why the hell would running debug software prevent me from running the game?!

---

### Post by Golyadkin on 2007-08-21
Well, the problem is in the SecuRom copy protection as the link already shows. That software checks whether you have the official DVD, but also check if you don't have software that can be used to crack the game. Examples of this are virtual cd/dvd drives (like Daemontools or Alcohol  in Windows) and disassemblers, or debugging tools. However, this is a bit paranoid behaviour of these SecuRom protected games.

---

### Post by Nehvrook on 2007-08-21
I see, but this is a free demo? I guess I need something similar to a cracked .exe, but who would make that for a demo lol

---

### Post by cogadh on 2007-08-21
I'm shocked that you got past the install. Wine usually has huge problems with brand new games, especially a "Games for Windows" game. Good for you for trying though.

---

### Post by Golyadkin on 2007-08-21
I am waiting for someone to try the final version of Bioshock for the PC with Cedega. If it works, I am gonna buy a Cedega subscription.

---

### Post by Nehvrook on 2007-08-21
hehe thanks. The installation went very smoothly actually. I assumed since Bioshock is running the Unreal 3 engin it will be OpenGL (I'm pretty sure since there will be a linux version of Unreal Tournament 3) so I thought I stood a fair chance of it working under wine.
Pity about this damn securom problem.

I'll buy the game soon and someone will definatly create a cracked .exe for that. I'll give it a go and post my results on if it runs any good in Wine

---

### Post by l_bratch on 2007-08-21
Unfortunately the game is infact D3D (9 and 10 actually).

UE3 has support for both.

The problem with Securom is a known problem with other games too, see this bug:

[http://bugs.winehq.org/show_bug.cgi?id=7065](http://bugs.winehq.org/show_bug.cgi?id=7065)

---

### Post by chiefwhosm on 2007-08-21
Have to admit I was surprised when securom popped up when I thought I was onto a winner with it. Makes me wonder if the bioshock team used the soon to be released full exe file (possibly slightly edited) for the demo version since I cant see any other reason why they'd have securom in the demo.

Installation was extremely fast and it was nice to see that wine got the setup to skip the installation of directx, I was worried (having had it do it automatically on my XP, which was stupid when I was already up to date :D) that it would destroy wines native dll files :)

---

### Post by GFree678 on 2007-08-21
The installer works well because it's an established installer (InstallShield), and nothing custom or "Vista-only" or anything crap like that. The reason the demo has securom is because apparently the logic being used is that the demo exe, if left unprotected, could be used to create a crack for the full version of the game.

Hence, by securom protecting the game, they'll ensure the cracked version of the full PC game has to be released in **two** days instead of **one**. :)

Still impressed you're trying it in Wine anyway. I wouldn't have bothered, given the requirements.

---

### Post by m3metix on 2007-08-21
I had a similar securom problem with the Tomb Raider: Legend demo so I used a cracked exe and it worked perfectly. I think that you should definitely try the Bioshock demo with a cracked exe when one is available.

---

### Post by GFree678 on 2007-08-21
> **m3metix said:**
> I had a similar securom problem with the Tomb Raider: Legend demo so I used a cracked exe and it worked perfectly. I think that you should definitely try the Bioshock demo with a cracked exe when one is available.

The Legend doesn't doesn't use securom, does it? I never had any issues with it.

I DID have an issue with the TR Anniversary demo, but the way to fix that was simple - run winecfg and set the platform to "Windows Vista". Seems Vista was the only setting it would run at. Maybe Bioshock will work if you try that?

---

### Post by chiefwhosm on 2007-08-21
Nice tip, and it worked  :) Next error encountered:

Failed to create the GameExplorer 

The steam demo is identical to the normal downloadable one (was hoping it would have had securom removed and some steam thing put in its place) so for anyone interested they both have the same problems.
> 
Still impressed you're trying it in Wine anyway. I wouldn't have bothered, given the requirements.

I wanted to see if the performance was any better under wine, because my specs are higher than the minimum, yet even at really low res the framerate is 22fps, and every few steps dropping to 0fps in windows.

---

### Post by m3metix on 2007-08-22
It seems like GameExplorer is a Vista thing, did you have your windows version set to Vista in winecfg? If so then I would try it with windows version set to Win XP. If you didn't then nevermind :)

---

### Post by cogadh on 2007-08-22
#-o
Um, no, nevermind, I can't do it...

---

### Post by redsmoke on 2007-08-22
setting it to win2k3 seems to get past the game explorer issue but it still crashes out. I'll spare you the output but it appears to be something with the kernel32

---

### Post by Polygon on 2007-08-22
you could try playing the game through Steam..... steam works perfectly in linux, but i highly doubt the game would run though...

---

### Post by Corvus.E on 2007-08-22
No go with the Steam version either.

---

### Post by redsmoke on 2007-08-22
tried with cedega 6.0.2 after installing a few DLL files I got it to install and almost start but still comes short of starting though it does seem promising as the debug output shows it loading through the direct3d stuff as though its going to start then abruptly crashes with no reason in debug output. I have one more idea on how to get it to work that i will try tonight if that is a no go then ....I will just wait and see.

---

### Post by pelicanghost on 2007-08-24
how did he install it under Wine?
How do you use Wine?

---

### Post by cogadh on 2007-08-24
Click on the "Stuff I've learned about Wine" link in my signature.

---

### Post by deadmoo on 2007-08-24
If you are trying to get this working, then you may be interested in this bug on wine's bugzilla: [http://bugs.winehq.org/show_bug.cgi?id=7065]("http://bugs.winehq.org/show_bug.cgi?id=7065")

---

### Post by bash on 2007-08-25
Apperently we aren't the only ones with problems getting Bioshok to work. Our dear friends in the Windows community seem to be plagued by the same problem.

It looks like the beloved SecuRom copy protection installs some kind of rootkit to "protect" the game. 

Just a couple of links:

[http://forums.2kgames.com/forums/showthread.php?t=6628](http://forums.2kgames.com/forums/showthread.php?t=6628)

[http://forums.2kgames.com/forums/showthread.php?t=7775](http://forums.2kgames.com/forums/showthread.php?t=7775)

[http://forums.2kgames.com/forums/showthread.php?t=7646](http://forums.2kgames.com/forums/showthread.php?t=7646)

[http://digg.com/gaming_news/BioShock_SecuROM_customer_support_at_its_finest_pic](http://digg.com/gaming_news/BioShock_SecuROM_customer_support_at_its_finest_pic)


Or just their Support forum in general. Its one big mess ...

[http://forums.2kgames.com/forums/forumdisplay.php?f=42&order=desc](http://forums.2kgames.com/forums/forumdisplay.php?f=42&order=desc)

---

### Post by Mongoose on 2007-08-25
It's not a rootkit, however it is a horribly designed peice of software in terms of the consumer.  The 'rookit' comes from it using a registry key that's supposedly unremoveable.  This triggers some antivirus software to declare it's a rootkit.  It isn't  actually a rootkit, and it's a false alarm.  It does however run a system service too.  I think the idea was to let Windows users play the game as non-Admin level users in Windows with the system service.  That's ok, since that actually aids user security.

Now the real issue is that you have an internet doggle and two valid install 'keys' controlled over the network.  If the (un)install cycle doesn't work or you have to reinstall Windows you start losing these keys pretty fast -- and you only have two.  So when the network / the 'key' server / (un)install process fail you are SCREWED.  Every one of these events has happened so far.  I'm passing the game due to these issues.  The only way I would even consider buying it is when this hits the bargin bin.

Update:
The number of keys for the retail version are increased from 2 to "3 to 5" according to 2k software.  Yeah, I'm not sure why it's "3 to 5" and not a single quantity either.  That inspires confidence.  ^^

---

### Post by cogadh on 2007-08-25
Ken Levine said in an interview that he considers the copy protection they used to be a mistake and they will be patching that two install limit to increase it. They have also decided to remove the internet activation feature, due to the server problems they had on launch day:
[http://www.joystiq.com/2007/08/24/levine-confirms-no-ps3-bioshock-and-does-mea-culpa-on-pc-issues/](http://www.joystiq.com/2007/08/24/levine-confirms-no-ps3-bioshock-and-does-mea-culpa-on-pc-issues/)

---

### Post by deadmoo on 2007-08-25
> **cogadh said:**
> Click on the "Stuff I've learned about Wine" link in my signature.

Thanks for compiling this information.  I wouldn't have been able to get as close to getting the demo to work as I did without it.

---

### Post by cogadh on 2007-08-25
No problem, I'm glad it helped. :) 

I'm always updating it with new info, so if you discover any new general pointers (non game specific) on Wine usage, let me know so I can add them to the document.

---

### Post by aldenhg on 2007-08-26
So does anyone know of a way to emulate the SecuRom software? If I'm not mistaken DeamonTools can do something like that, so it should be (theoretically) possible.

---

### Post by Nehvrook on 2007-08-26
So I've bought Bioshock. But I can't install it. It finishes installing fine but then it tries to patch. And we're back to the securom message. I have a cracked .exe but that's no good because as soon as it fails to patch it removes the whole game it just installed XD

Any idea's?

---

### Post by deathchimp on 2007-08-26
Have you tried disconnecting your internet?

---

### Post by cogadh on 2007-08-26
> **aldenhg said:**
> So does anyone know of a way to emulate the SecuRom software? If I'm not mistaken DeamonTools can do something like that, so it should be (theoretically) possible.
All Daemon Tools does is create a virtual CD drive that tricks Securom into thinking that you have the actual disk in the drive. Then the Securom protection can run normally. Wine doesn't have that kind of virtual CD functionality and even if it did, you still have the problem of Securom not actually being able to run in Wine. It is one of the things on the Wine "to do" list, and we already do have some support for older Securom protection schemes, so I would expect some of these newer protection schemes to work eventually.

---

### Post by aldenhg on 2007-08-26
Thanks for the clairfication. My lack of pirating colors must be showing through.

---

### Post by cogadh on 2007-08-26
> **aldenhg said:**
> My lack of pirating colors must be showing through.
Hey, in my book, that's a good thing. :)

---

### Post by rofthorax on 2008-12-27
> **Mongoose said:**
> 
Now the real issue is that you have an internet doggle and two valid install 'keys' controlled over the network.  If the (un)install cycle doesn't work or you have to reinstall Windows you start losing these keys pretty fast -- and you only have two.  So when the network / the 'key' server / (un)install process fail you are SCREWED.  Every one of these events has happened so far.  I'm passing the game due to these issues.  The only way I would even consider buying it is when this hits the bargin bin.


I bought Bioshock at 5 dollars.. I don't buy second rate developers crap at retail unless I think I can get it to work in Wine. Just the fact that it doesn't work in wine, should be a standard for proving it's close-coupling with Windows and it's likely future obsoletion due to changes in the API that come with every new release of Windows.. What I'm saying is Wine has staying pwoer, games that don't run on wine don't have staying power.. You'd think that the biz-heads in these game companies would get that.. It may not be 10% of the market now, but in two years the Linux crowd could be 100% of the market and might pay out about 50% of what the game did for its lifetime.. I think Valve is aware of this, and ID as well, but the biz-heads in EA and elsewhere are clueless.. 

I think its partly a problem with the consumers too.. People will always pirate regardless of platform, why put bogus copy protection on games? It's not for piracy, it's to keep the consumers from ever really owning their games.. Nobody owns Vista, they own a license to use Vista.. It's just the way things are going, and the only thing these game companies will listen to, amidst this recession in the American industry, is money.. What's funny is that Ubuntu userbase is growing, and people like Amazon are taking notice, but the game developers are living in caves, looking toward and industry dominated by EA.. And you'd think they would go for the undominated market, Clue... Linux and MacOSX.. Clue.. Wine?
And if it works for those platforms it works for Windows as well.. 

I say develop for Wine first, then add in the special stuff for Windows.. Or, use Wine to cross-compile windows programs and do detail work on the resulting binary toward making it a native application. Better yet, open source the parts of the program that the game developers don't want to develop, so as to make the transition easier on the next release. 

I mean, which is cheaper, a PC with Linux on it and the ability to play games, or a PC with Vista installed and the long-term expense of having to repurchase Windows, when the consumers could be spending their money on graphics cards and games.. You'd think the game developers would have a clue.

---

