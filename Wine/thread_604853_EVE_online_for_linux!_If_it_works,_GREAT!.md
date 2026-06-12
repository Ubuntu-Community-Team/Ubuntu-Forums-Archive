---
title: "EVE online for linux! If it works, GREAT!"
date: 2007-11-06
forum: Wine
---

### Post by Kobin on 2007-11-06
Hi everyone!

Downloading the new Eve online client for linux right now. Hope it works.

Has anyone else tried it yet?
Am I wrong or is this a very important thing for linux?

I hope many will use this opportunity to play a popular game natively on linux! If it is popular enough it might move other gaming companies in the same direction...

---

### Post by michaeel on 2007-11-06
i've tried it and it works good on 7.10.
but i have 17-20% less fps compared to eve online on cedega 6.03, ..maybe just a settings thingy..

---

### Post by rudeboyskunk on 2007-11-06
Yes, this is a VERY good thing for Linux.  One of the biggest games for online gaming, and there is a Linux port.

I've been looking forward to this for so long.  I'm downloading tonight baby.

---

### Post by Rollinco on 2007-11-06
This doesn't seem to be a port but rather a wrapper by Cedega on the windows version.:confused: It doesn't work for me with all dependencies met. I guess I will stick with VO

---

### Post by NiceGuy on 2007-11-06
:(:(:(:(

I just get a silent splash and crash. It was working fine when I used cedega 6.03 so I'll just go back to using that unless anyone has any ideas?

---

### Post by Kobin on 2007-11-06
Im confused:confused:
At cedega.com this is written in the news:

The success of porting EVE Online quickly and efficiently with Cider and Cedega allows CCP to keep a laser-focus on evolving EVE Online, while simultaneously expanding the EVE universe to even more players.

But then in the linked pressrelease:

Later this year, EVE Online will be released for Linux with Cedega directly integrated into the game and on Mac through TransGaming's Cider portability engine.

So is the game actually ported for Mac but run through Cedega's engine on linux? I don't know if it is ported for Mac, but as everything looks like Cedega (options configurations and the fact that it says it is running the program as Windows XP) it must be Cedega.

But still its a fine move I think

---

### Post by NiceGuy on 2007-11-06
My understanding is that 'Cider' is just 'Cedega for Mac'. The Mac version isn't actually ported and runs through a wrapper just like the linux version...

I think...

---

### Post by michaeel on 2007-11-06
> **NiceGuy said:**
> My understanding is that 'Cider' is just 'Cedega for Mac'. The Mac version isn't actually ported and runs through a wrapper just like the linux version...

I think...

thats right, the linux and mac clients are windows binaries, wraped into cedega/cider, there are no native clients for linux or mac. but it works good, and eve is a great game, one of the best i've ever played.

---

### Post by FG123 on 2007-11-06
FFS this isn't a port. The guys who made EVE online do not deserve any credit. They just took the lazy way out, I could have done the same with Wine and achieved better results probably.

---

### Post by chronusdark on 2007-11-06
> **FG123 said:**
> FFS this isn't a port. The guys who made EVE online do not deserve any credit. They just took the lazy way out, I could have done the same with Wine and achieved better results probably.

actually from a business perspective they are taking a big risk just trying this and people like you sure aren't helping to convince companies to try making linux ports. too many people whine when a company tries experimenting with linux, i just tried the client and my ONLY complaint is it runs a little slower with compiz enabled but thats not a big deal to me.

Good job CCP  and heres hoping that world of darkness will get a native port out of all this when it comes out

---

### Post by michaeel on 2007-11-06
if more and more people play such games on linux they will make native clients, you'll see.

---

### Post by Kobin on 2007-11-06
Some of you seem to have EVE online working this way.
My download is finished and it has installed. But when running I get this error:

***@***-desktop:~$ eve
Single-user install...
This is the update checker... 
Running /home/***/.cedega/.updater/cedega_updater.py
/home/***/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Running... /home/***/.cedega/.ui/runGUI
/home/***/.cedega/.ui/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
***@***-desktop:~$ 



Did any of you have cedega installed already before trying this?
Or any other ideas?

---

### Post by NiceGuy on 2007-11-06
> **FG123 said:**
> FFS this isn't a port. The guys who made EVE online do not deserve any credit. They just took the lazy way out, I could have done the same with Wine and achieved better results probably.

I must say I strongly disagree with this and the attitude behind it.

My knowledge in the area is limited but I believe that CCP (the guys who made eve online) are defiantly going about this in the correct way. To port the game over to linux would require a complete re-write of the graphics engine and as the linux playerbase is frankly tiny and would not be worth the effort, lazyness does not come in to it, its just not financially viable. What they are offering is a official and hopefully supported solution for linux and mac users which is a lot more than any other MMORPG I'm aware of.

Not only that but if, as you seem to think,  CCP have just sat back and let transgaming do all the work I would be amazed. I imagine that they've worked closely together to make this possible.

To my mind this is a completely satisfactory solution to a difficult problem. This way they can concentrate on continuing to make eve the great game it is and let a different company who specializes in the area of 'getting games made for windows to work on linux/mac' do that for them. 

Oh and at no additional cost to the subscriber I might add!

---

### Post by Toffeeapple on 2007-11-06
Personally I'm still getting better results with wine, in fact flawless : )

I've been trying the new official linux release thing this afternoon.. but not smoothly, stuttering sound and graphics issues.

---

### Post by NiceGuy on 2007-11-06
lol, well thats better than I'm getting but hopefully things will improve.

/me hopes that this new client will mean that the upgrade to the updated graphics engine will be smoother... although I'll probably set a long skill training just in case...  BS V I think :P

@ Koben - thats exactly what I'm getting. I had Cedega installed when I tried to install it the first time so I removed it and eve (+ the .cedega folder in home) and then re-installed eve... but I still got the same thing :(

---

### Post by chronusdark on 2007-11-06
i have to ask Kobin how different is your setup from the default
my setup is pretty much vanilla and it installed, setup, and ran great

as for graphic engine this Cedega Wrapped version has fixed alot of missing graphics from wine (ie the seperators between menu items and the sliders in character creation) i believe the wine version ran a little faster for me but not that much

something else you have to realize in a couple of months CCP will be upgrading the Eve engine and it will require shader model 3 for the new graphics from what i can tell transgaming has set this as a priority and it may take a while to get shader 3 into wine.  so if you want the new shinies you are going to have to use this wrapper at least for a little while in the near future

---

### Post by Kobin on 2007-11-06
I have a fresh Ubuntu 7.10 install. With installed proprietary driver for my Nvidia Geforce 4 TI 4200 graphics card.

The only extras I have is Gnomebaker and newest Wine.

And I have use the GDebi Package Installer to install eve_000062_all.deb, and I have then chosen to Download from the internet.

If it was something else you ment........?

---

### Post by chronusdark on 2007-11-06
well the errors you are getting look like python is at a wrong version but i dont think you would have installed anything to mess that up

its weird i will think about it a bit more and will post here if i come up with something

---

### Post by Kobin on 2007-11-06
I have Python 2,5 installed

---

### Post by FG123 on 2007-11-06
> **NiceGuy said:**
> I must say I strongly disagree with this and the attitude behind it.

My knowledge in the area is limited but I believe that CCP (the guys who made eve online) are defiantly going about this in the correct way. To port the game over to linux would require a complete re-write of the graphics engine and as the linux playerbase is frankly tiny and would not be worth the effort, lazyness does not come in to it, its just not financially viable. What they are offering is a official and hopefully supported solution for linux and mac users which is a lot more than any other MMORPG I'm aware of.

Not only that but if, as you seem to think,  CCP have just sat back and let transgaming do all the work I would be amazed. I imagine that they've worked closely together to make this possible.

To my mind this is a completely satisfactory solution to a difficult problem. This way they can concentrate on continuing to make eve the great game it is and let a different company who specializes in the area of 'getting games made for windows to work on linux/mac' do that for them. 

Oh and at no additional cost to the subscriber I might add!
This is not the correct way, have to disagree. If they really wanted to have the game available for other platforms in the future, they could have always started with a cross-platform base like OpenGL, but nah, that would have been too smart. Also, the Mac port is exactly that, a native port. They bothered with the Mac even though the numbers probably wouldn't be that much better than Linux anyway.

Don't know why people are so grateful for a wrapper solution. Are we so desperate for commercial games we're prepared to accept anything? We ARE being treated like 3rd-class users here. If we start accepting half-arsed solutions such as this, companies will think it's a viable alternative to a native port. There's a reason I don't use Wine and only play native games. Very disappointed Linux users actually think this is a good thing. I've seen Neverwinter Nights, Doom 3, the Unreal Tournamant series, Quake Wars and etc available for Linux, and now X3 is being ported.

There's no longer any excuse for a lame wrapper.


EDIT: I think I understand your point. The fact they're trying to make some kind of *officially*-recognized Linux solution is worthy of praise. Maybe. Still disappointed.

EDIT 2: Apologies if I seem harsh or zealotry. I'm not trying to be, but I don't like seeing people sell themselves short.

---

### Post by NiceGuy on 2007-11-06
> **FG123 said:**
> This is not the correct way, have to disagree. If they really wanted to have the game available for other platforms in the future, they could have always started with a cross-platform base like OpenGL, but nah, that would have been too smart. 

I don't know why they decided to use the directx base instead of opengl (presumably they had their reasons), but the point is they did. Asking for them to re-write the graphics engine for a tiny minority of users just doesn't make sense. Its also worth mentioning that eve was first released in May 2003 (over 4 years ago) and the 'home user' linux community has grown hugely since then. I don't think anyone could have predicted either the success of eve or linux at that time.

Heck, even ubuntu was only started in what... late 2004? 

> **FG123 said:**
> 
Also, the Mac port is exactly that, a native port. They bothered with the Mac even though the numbers probably wouldn't be that much better than Linux anyway.

Are you sure? Citation?

As the mac client claims to be 'powered by cider' I don't think thats the case.

> **FG123 said:**
> 
Don't know why people are so grateful for a wrapper solution. Are we so desperate for commercial games we're prepared to accept anything? We ARE being treated like 3rd-class users here. If we start accepting half-arsed solutions such as this, companies will think it's a viable alternative to a native port. There's a reason I don't use Wine and only play native games. Very disappointed Linux users actually think this is a good thing. I've seen Neverwinter Nights, Doom 3, the Unreal Tournamant series, Quake Wars and etc available for Linux, and now X3 is being ported. 

There's no longer any excuse for a lame wrapper.

All those games you listed, how often are they updated? Are they ever updated (excluding patches/fixes a few months after release)?

Eve is very different, new content, features and fixes are added continually (ie. every month). Trying to port a game to one or maybe 2 platforms is one thing (still financially questionable though), but maintaining and maintaining support for 3 platforms (assuming you treat linux as one platform which is a stretch in itself) when it when its patched on such a regular basis would be a nightmare!

The reason we are so happy is because a) we love eve and want it to work well on our platform of choice, but more importantly b) its a step in the right direction for gaming in general. It's my hope that as more games become playable on linux and the linux gaming community grows, new games will be released which ARE cross platform compatible.

I understand this may look like a 'stop gap' solution at first glance, but really its not.

---

### Post by NiceGuy on 2007-11-06
> 
EDIT: I think I understand your point. The fact they're trying to make some kind of officially-recognized Linux solution is worthy of praise. Maybe. Still disappointed.

EDIT 2: Apologies if I seem harsh or zealotry. I'm not trying to be, but I don't like seeing people sell themselves short.

I too know where you are coming from, but eve's situation is quite unique and I think this really is the best solution for them.

Also as a company they are quite exceptional in that they actually listen to their users. Most companies make a game to generate as much profit as possible and thats it, ccp actually seem to care about their game and even more so about their community. I couldn't see blizzard doing this... unless they feel the wow player base is being threatened by eve :P

---

### Post by NiceGuy on 2007-11-06
Taken from [http://myeve.eve-online.com/devblog.asp?a=blog&bid=517](http://myeve.eve-online.com/devblog.asp?a=blog&bid=517)

> Q. Is this a native client?
Yes and No. Both Mac and Linux versions use the same underlying portability technology from TransGaming to give direct access to both the native graphics and cpu features of the host platform when running on non-Windows operating systems. In addition, ALL of the game logic is in the Python code which is common across all platforms. So the actual logic is being run exactly the same on Mac and Linux as it would be on Windows. This provides you with a seamless in-game experience regardless of your platform of choice.

and

> Q. Will EVE: Trinity be supported on the Mac and Linux platforms?
A. The Mac and Linux clients will not initially support the upgraded content but will support the Classic client. TransGaming are already working on the new features needed in the underpinning technology (the Shader Model 3 stuff) to be able to support the EVE Premium client and are targeting having support in place early next year but this is still in the early stages. We will keep you informed where this is at and what our expected delivery is for this support.

---

### Post by jergarmar on 2007-11-07
I am a beginner to both EVE and to Ubuntu (just upgraded to 7.10), so I had not yet tried to play EVE through Wine or Cedega. I was pleasantly surprised at how much of a "no-brainer" it was to get it up and running from scratch. I even managed to get the whole thing working with just the graphical interface.

As someone already pointed out, there seems to be a significant FPS hit compared to similar Windows settings, but I had no stuttering or hanging. If anyone has success improving EVE's FPS or the quality in general, I'd love to hear about it. I'm a bit nervous for the future, too, since in a month or two there's going to be a huge graphical engine update for EVE. That will be an interesting test of the viability of this version.

Which reminds me -- this does appear to be just a Cedega "wrapper" around the existing game engine, but it is noteworthy that CCP announced "support" for these Mac and Linux versions. I'm not sure how this "support" manifests itself, but simply announcing it is a good sign. Even if they just want to *appear *to be Linux-friendly, that tells you a lot about the current state of Linux.

Just for info's sake, I have a Geforce 6200 video card, Athlon 64 3400+, 1GB of RAM, and Ubuntu 7.10.

---

### Post by Arcadeoddie on 2007-11-07
Im actually getting the same error.... Python version seems to be incorrect or cedega is not pointing to the correct python version.

Anyone have any idea's? I've tried looking for cedega reference to python but can't find what versions its trying to use. Maybe we can force it to use Python 2.5??

---

### Post by Kobin on 2007-11-09
I have not found a solution the "python" problem yet. So i am running it with wine 0.9.48 and the wined3d.dll.so from 0.9.44 to fix the text issues. but i hope someone will find
 a solution. maybe it is futile but i have mailed transgaming about the problem. i have seen this problem being posted on many forums both german and english. so it seems to be a somewhat common problem.

---

### Post by GregLH on 2007-11-09
Yeah I get the same error also, I just saw this today from swapping back to Ubuntu 7.10 after messing around with PCLinuxOS for a few months ( didn't really care for feisty fawn also it led me to appreciate different distros of Linux too. :) ) I've been getting that python error also and even went as far as to get older versions that said it was compatible with. Just kept getting the slash screen and it would die then did it in the terminal and it would give me a python error. Stinks but what are you gonna do... Other then yell at transgaming till they fix it.

Also on the note of what have been said about wineing/wrapper. I feel that it may be a really odd step but it is a step forward regardless. This provides Linux users the game that they been wanting to play with possible native speeds, however on a downside it does need more requirements to the native windows version. So as far as now goes a wrapper layer will cut it however if Linux does catch on more with gamers, then I personally don't think a wrapper layer will cut it anymore and more game companys will have to consider native Linux versions of the game. However I don't really think this will be happening since I don't think Microsoft will not give up without a fight and try to pay game companys off to use DirectX only.

---

### Post by Norwal on 2007-11-10
I gave up on playing EVE on ubuntu back in January.  But I decided to try it again.  I didn't have any luck at first, put then hit pay dirt.

[http://www.cedega.com/forum/viewtopic.php?p=52070#52070]("http://www.cedega.com/forum/viewtopic.php?p=52070#52070")

Using the fix above I got Eve working on 7.10 with Cedega 6.0.3.

No luck with the "supported" version yet. I will keep plugging away and post any positive results.

---

### Post by Demon012 on 2007-11-11
The wrapper client seems to work well. However my main complaint is that there is currently a bug with it using alsa (if you have alsa set at the sound system in the Eve Online Configuration Panel the login screen does not load). 

If you are getting this problem it is caused by 1 of 2 things:

You have alsa selected as the sound system.

Or

You don't have the correct fonts installed (usally arial.ttf when using wine).

However if you switch the client over to OSS you cannot have any other sounds coming from any other program on your system which is annoying beyond belief. You may be able to run Eve via AOSS (part of the alsa-oss package) however I have not yet tried that. 

Once you get into the game however it seems to run quite smoothly (45fps most of the time on my 8800) and even Eve Voice works for communications.

And regarding the whole debate over Native port vs Wrapper I believe this is a step in the right direction and as previously mentioned in someone else's post porting the Eve graphics from direct x to SDL is a very large costly project. However they may eventually decide to do this when there is a large enough linux user base. 

But in the mean time at least CCP are catering for us via the cedega wrapper which shows that they do indeed care about linux users and I cannot praise them enough for it.

---

### Post by buntunub on 2007-11-13
I just got that arial.ttf in my wine drive and now the game runs just awesome in regular ol wine. No need for Cedega at all. In fact using just plain ol wine, the game seems to run much much better, with better graphics and fps. I can also run it in windowed mode, unlike the cedega port. It does seem to have some stability issues and crashes out very rarely, but its not enough to really get concerned about. Usually only happen when in warp, so even if you do crash out, when you get back in you'll be safe from pvp hit squads for a bit.

BTW, I hope to see ALL you Ubuntu users in deep space soon! Preferably in zero sec area's ready for battle!

---

### Post by buntunub on 2007-11-14
Hey! Why no Eve Online Ubuntu Corp!?.. Perhaps we should all get together and form one?

---

### Post by ELD on 2007-11-14
I get the black screen of death with eve :(

---

### Post by AthlonMDK on 2007-11-16
> **buntunub said:**
> Hey! Why no Eve Online Ubuntu Corp!?.. Perhaps we should all get together and form one?

Good idea... form an alliance against the non-linux users :P

But do you have ideas about what the corp should do and how much time do you intend to spent on the corp?

---

### Post by sloggerkhan on 2007-11-17
It's crashing for me after I finish creating a character and it finishes loading. Going to look through posts/solutions, but is there a possibility it could be an fglrx/ati driver problem?

---

### Post by zmjjmz on 2007-11-17
I constantly get the splash screen - and then nothing happens...

---

### Post by sloggerkhan on 2007-11-17
So the windows client works okay in wine, though some fonts and images show up looking really really crappy and the graphics look kinda low quality, too. But the 'linux' (cedaga) client doesn't seem to work. It crashes after you click the enter ship button.

---

### Post by zmjjmz on 2007-11-17
Neither of them work for me...
I get this trying to run the Cedega one (the .deb installed well though...)
```
Single-user install...
This is the update checker... 
Running /home/zj1992/.cedega/.updater/cedega_updater.py
/home/zj1992/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Running... /home/zj1992/.cedega/.ui/runGUI
/home/zj1992/.cedega/.ui/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser

```
And I just gave up on running it in WINE...

---

### Post by buntunub on 2007-11-17
No clue why it wont run in wine for you guys. I just ran the installer and then moved the ariel.ttf into the wine windows\fonts folder and everything "just worked" after that. I ran into some rare stability issues, but solved it by running the .exe with a nice of -8. I do happen to have an XP dual boot and ran some side by side fps tests on that just to be sure, and found that the client running on the Ubuntu box on wine was 19% faster/better than when running the exact same client/settings on the XP box. The graphics are totally identical as well.

---

### Post by sloggerkhan on 2007-11-17
It does run inder wine for me, some fonts are just so ugly it's unusable.

---

### Post by izizzle on 2007-11-17
What is so great about this game anyways? I looked at some videos and it seems boring.

---

### Post by MonkeyBoy on 2007-11-18
> **izizzle said:**
> What is so great about this game anyways? I looked at some videos and it seems boring.

I played this for a while a year or so ago after becoming bored with WOW.  The main charm of this game is the freedom.  You can attack anyone anywhere unlike in a lot of other MMORPGs.  You can do well just by trading.  Death is a big deal unlike WOW etc.  In other games you tend to be led into what to do next but in EVE you just do what you like.

It does take longer to get used to and it can be easy to get stuck in a rut because the game doesn't suggest what you should do next but this is exactly what MMORPGs should be like.

BTW I am also getting the python error.  The EVE forums have no solutions yet either so I guess we're stuck 'til they sort it out.

---

### Post by Marari on 2007-11-27
> **izizzle said:**
> What is so great about this game anyways? I looked at some videos and it seems boring.

It's just an amazing game! I've been playing EVE for about 3 years now and it never loses it's draw. 

Here are some reasons that users stay with the game as long as they have:
[LIST]
[*]Player vs Player
[*]Player vs Environment
[*]Interact with 30,000 (or more) online players in a TRUE multiplayer static environment
[*]Market warfare (heh)
[*]Industrialization
[*]Economics
[*]Invention
[/LIST]

The list goes on and on.

Essentially, it truly is a game for every player. If you want combat, you can have combat. If you want to mine and create, you can. If you want to research and invent, you can. AFAIK, no other MMO gives you anywhere near the level of freedom and creativity that EVE online gives you.

Spoken with passion. :-)

---

### Post by slavik on 2007-11-27
EVE is different from Doom3 because they are in completely different genres.

I have been using WINE to play EVE since starting (August 31st, 2007). The "EVE Linux client" was nothing to cheer about for me. (unless it was an OpenGL native app).

As for Python logic. This is just as big part of the game as the graphics engine is. Saying that the client is native because a part of it can be run natively is just plain wrong.

---

