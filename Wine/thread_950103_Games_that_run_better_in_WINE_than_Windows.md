---
title: "Games that run better in WINE than Windows"
date: 2008-10-16
forum: Wine
---

### Post by dagoss on 2008-10-16
Has anyone encountered a game that runs better using WINE than it does running natively in a Windows environment?

---

### Post by TekNullOG on 2008-10-17
I would be curious to know this too... I've heard people mention things like this before though...

---

### Post by Griffin Bain on 2008-10-17
i think you could make the argument that sim city 4 deluxe edition works better in wine than in actual windows.

---

### Post by Wickd on 2008-10-17
Well actually I do play a lot of call of Duty 2 and personally I find the game quaility drastically better on Wine than on Windows

---

### Post by Ameneon on 2008-10-17
Playing Football Manager 2007 and 2008, I have to say both play at least as well or better in WINE than in Windows. IMHO.

---

### Post by rakris on 2008-10-17
Most curious newbies would have this problem. 

When they use wine for the first time :):)

Actually Windows is always better than wine provided its not infected :P

---

### Post by Colro on 2008-10-17
> **rakris said:**
> Actually Windows is always better than wine provided its not infected :P

Exactly. As long as the user sitting in front of the computer isn't stupid enough to get his machine compromised in some way, all windows game will run better on...windows. I've heard people say X and Y game run better on WINE, tested them, and denied their claim. The only games that seem to run equally well as they do in windows are older ones such as Half-life 1 (and mods) and Warcraft 3. Even the popular World of Warcraft in OpenGL mode **does** have performance losses, although with top end hardware it's unlikely you'll notice the difference.

Not trying to insult WINE, the project is great and helps a lot of people, but these claims are fruitless. Even Counter-Strike: Source runs noticeably slower on my machine with the lowest possible settings and Direct X level set to 7 on WINE, whereas it runs flawlessly on the highest possible settings in Vista; and that's considered a well-supported "platinum list" game.

---

### Post by Ameneon on 2008-10-17
Not quite true, rakris. It all depends on the game. Remember that you will have a quantity of system processes that may steal more resources in Windows than they do in ubuntu, in such cases (or indeed infection or other system corruption) a game may well run better in wine than in windows.

---

### Post by ajackson on 2008-10-17
I think it's down more to linux/wine having lower overheads than windows in terms of resources (mainly memory), so there is more memory available to the game so it performs a bit better.

How much better is another matter and you then have the overheads of wine having to translate calls into something more linux friendly which eats back on the performance bonus.

So it's swings and roundabouts and highly subjective :)

---

### Post by rakris on 2008-10-17
> **Ameneon said:**
> Not quite true, rakris. It all depends on the game. Remember that you will have a quantity of system processes that may steal more resources in Windows than they do in ubuntu, in such cases (or indeed infection or other system corruption) a game may well run better in wine than in windows.


You are comparing infected windows and rock solid uninfected Ubuntu. 
try comparing both with good envirnoments :) Windows is better than wine. Even in windows u can tweak to get minimun processes or increase your memory.

---

### Post by Espryon on 2008-10-17
> **dagoss said:**
> Has anyone encountered a game that runs better using WINE than it does running natively in a Windows environment?

Actually yes

World of Warcraft , Call of Duty 4, Call of Duty 2 , Unreal 3, Counterstrike, Team Fortress 2 , and Project 64 keep in mind with registry and game performance tweaks there on the app list on [www.winehq.com](www.winehq.com) i used mostly all of them

---

### Post by Ferrat on 2008-10-17
This debate has been up a few times and the fact is that some people get better performance from running some games under WINE instead of on Windows and there are different reasons really. 

First of if you compair with VISTA you should take in to account that VISTAs "cool" graphic desktop effects just like the eye candy on Ubuntu affects the performance, VISTA gives ~20% less FPS on most game when compared to XP, while last tests I saw of WINE vs XP gave a ~10% loss (in general). 

Also on Linux some hardware works better than others, ATi graphic cards have way better drivers for Windows while nVIDIAs is more at the same level i.e. using ATi most like you'll get a bigger loss. 

Then as some of you have the stated facts about resources, connected to the first example with VISTA but other than that Linux users seldom have the same amount of crap running etc, like nowadays many drivers and hardware comes with their own programs that auto start etc on Windows (not taking to account viruses and other malicious software) and all those little programs tend to clog the system + anti virus, software firewalls etc. 

You also got the "false" performance boost, WINE doesn't process everything just as Windows does since some things are just not implemented etc. Might be something more or less useless and probably is if the game is running fine but Windows still use it and while WINE just ignore it that's why many games work best when you add the WINEDEBUG = -all before launching (WINE just disregardds everything that it can't understand). 
A good example of a similar situation is the old GeForce MX series, hated by some loved by others. I for one loved them, for the simple reason that they worked just in that manner, the MX didn't have shaders and back in the days shaders wasn't a requirement but an extra and IMO they didn't make enough change to really be needed, so when a game used a shader a GeForce 4 card with better "real" performance actually gave less FPS since it had to calculate all the shaders while my old MX card just ignored them. :D
It's a boost but at the cost of losing something else.

Then you got the small, small percentage of actual performance boosts, where the WINE guys have out done them selfs producing a more efficient code for the same problem getting a faster yet equal result to Windows. 
(this is very uncommon) 

So over all, yes you can get better performance running a game under Linux/WINE (or cedega) than you can under Windows but it's often a "false" boost, not that you should care, you still get the same game:P 
But it's a complex question since it it depends on how you see performance, as I said last tests I've seen has shown a ~10% loss over all on the actual functions between WINE and XP which IMO isn't bad at all for something that was designed for a different system compared to the system it was build for.

---

### Post by skirkpatrick on 2008-10-17
All I know is that I played Call of Duty (the original) in a competitive gaming clan and had my Windows tweaked to hell and back to boost the FPS.  I still had problems in the first two minutes of connecting to a server with Punkbuster causing lags.

I ran CoD on Wine/Linux with NO tweaking of Wine and got about 20% higher FPS and no Punkbuster problems.

---

### Post by Colro on 2008-10-17
^-- ??

Last time I checked, punk buster doesn't work **at all** in wine -- it doesn't even launch. You must be playing on non-PB servers now, which generally will, yes, have significantly less lag. If you're talking about single player, then I'm going to have to say your windows installation was probably bogged down by something - spyware or otherwise.

---

### Post by xmagixx on 2008-10-17
> **Espryon said:**
> Actually yes

World of Warcraft , Call of Duty 4, Call of Duty 2 , Unreal 3, Counterstrike, Team Fortress 2 , and Project 64 keep in mind with registry and game performance tweaks there on the app list on [www.winehq.com](www.winehq.com) i used mostly all of them

punk buster still dont work. and it's only the marginal of people that can get half of those games to work under wine.
it's true though that the wine registry can be tweaked for good perfermence. neverthe less vista still runs the games smoother overall imo


i wanner play CoD4 !! stupid wine

---

### Post by Ameneon on 2008-10-17
> **rakris said:**
> You are comparing infected windows and rock solid uninfected Ubuntu. 
try comparing both with good envirnoments :) Windows is better than wine. Even in windows u can tweak to get minimun processes or increase your memory.

TBH I did not read "tweaked" from the subject post but by all means if you put that implication in there then chances are Windows will come better off in nearly all cases, anything else would be not only surprising, but sensational. Native support is gonna win in 99% of the cases. The fact of the matter though is that the majority of gamers, power users like the ones who transit to Linux or otherwise, do not have a tweaked system for performance.

And I'm not so sure that barebones Linux w/GUI will not be slimmer and easier on the system than barebones Windows as well, at that.

Not that I am a linux fanboy, I work on MS support (for some weeks more at least) and I generally find (in particular XP) Windows very stable and efficient for most needs, however I don't use it on my personal systems any longer, although unless Valve should suddenly provide Linux support for their games (and lets face it, HL2 in Wine is a second hand solution even if it's playable) I will likely spend some time there again once Episode 3 is released.

But that's my 2c

---

### Post by BigBananaMan on 2008-10-17
> **Griffin Bain said:**
> i think you could make the argument that sim city 4 deluxe edition works better in wine than in actual windows.

Sim city 4 runs poorly on my system.  As fast as a slide show, hangs when I load a city, and all of the buttons are blank so I have to guess what they say before clicking them.  It's completely unplayable until I can fix those problems.

---

### Post by YokoZar on 2008-10-17
This question will have as many different answers as "how can I make my game run faster?"

Maybe there are driver differences.  Maybe there's a Wine bug.  Maybe other programs are hogging resources.  Maybe Linux is faster at something than its Windows equivalent.  Maybe it's all in your head.

---

### Post by Butthead on 2008-10-18
Maybe the computer you run Wine + plus the game on now is much faster than the older Windows one you used to run it on? :confused:

---

### Post by Greyed on 2008-10-18
> **Espryon said:**
> Actually yes

World of Warcraft , Call of Duty 4, Call of Duty 2 , Unreal 3, Counterstrike, Team Fortress 2 , and Project 64 keep in mind with registry and game performance tweaks there on the app list on [www.winehq.com]("http://www.winehq.com") i used mostly all of them

You're kidding, right?

WoW in WinXP, 20-30FPS in Netherstorm.  Wine, 12-15FPS.
TF2 in WinXP, 22-32FPS on most maps w/DX9 and most settings set to high.  Wine, 8-12FPS in DX8.1 with all settings set to low.

I only wish they ran better because I'd be able to dump WinXP.

Want to know what's really going on?  [http://en.wikipedia.org/wiki/Placebo](http://en.wikipedia.org/wiki/Placebo)

---

### Post by Blitzkr1eg on 2008-10-19
Interesting thread, but I guess technically a clean Windows install + appropriate drivers will be better than Wine. The thing is that with Windows numerous things can go wrong, thus when you do the side by side comparison with Wine, what might happen is that since Windows has some issue, it's resulting in inferior performance when compared to Wine which is probably running a more stable system as your Linux OS might be in better shape.

In order to completely prove this claim I'd say someone would have to setup two clean OS installs, one with Linux + wine and one with something like XP with the appropriate drivers. And then test out the game performance to see if it's really accurate to say that Wine will "really" result in better performance.

---

### Post by Tim0miT on 2008-10-20
> **Wickd said:**
> Well actually I do play a lot of call of Duty 2 and personally I find the game quaility drastically better on Wine than on Windows
i also heard that COD 2 worked better in wine :D

---

### Post by del_diablo on 2008-10-21
Heroes 3 works better under Wine than in Vista/XP, has yet to experience a crash or unstability *whistles*.

---

### Post by skirkpatrick on 2008-10-21
> **Colro said:**
> ^-- ??

Last time I checked, punk buster doesn't work **at all** in wine -- it doesn't even launch. You must be playing on non-PB servers now, which generally will, yes, have significantly less lag. If you're talking about single player, then I'm going to have to say your windows installation was probably bogged down by something - spyware or otherwise.

I didn't say anything about running on non-PB servers or in single player mode.  Back when I played CoD (the original), all competitive servers had PB running and CoD ran fine under Wine.  I was never invalidated on a PB server and the server would collect valid PB screenshots from me.

I also never had problems running True Combat: Elite under Wine on PB servers.

---

### Post by dagoss on 2008-10-22
Just to throw this out there too, what about older games?  For example, I remember the last time I tried to play Wizardry Gold with XP it ran very poorly.  Perhaps I'll have to dig the CD out and see how WINE handles it on my system.

---

### Post by skirkpatrick on 2008-10-22
Depending on how far back you go.  The whole reason I installed Ubuntu on my wife's computer is because Dungeon Keeper and Dungeon Keeper 2 wouldn't run on XP and Bullfrog went out of business before they could patch it.

---

### Post by smmalis on 2008-10-22
Rise of Nations worked right out of the install on Wine, won't even start in Vista.

---

### Post by rocky5051 on 2008-10-22
I don't have top of the line hardware on my system (GeForce 4000MX, AMD Athlon T-Bird 1.4ghz...built out of new and old parts xD), but having an older system has occassionaly exposed some performance gain in certain games.

Unreal Tournament GOTY (using high-res textures) and Call of Duty 1 both perform a little better on Wine for me than they had on Windows XP. Actually, UT performs considerably faster than on Windows with it's OpenGL renderer and even sounds better on ALSA than it did on Windows. Even running Compiz-Fusion doesn't take from the performance gain.

Although, it's probably just due to functions Wine doesn't implement yet, some of which may be inefficiant or not really necessary in some cases. Call it a "fake" performance gain if you will, but I have definately experienced better performance under Wine with CoD 1 and UT than I had under Windows.

---

### Post by northrup on 2008-10-23
Perhaps I should begin testing older games on my PC.  On one of my computers I have a clean Win 2000 install and a clean UbuntuStudio 8.04 install with Wine.  I've already tested a couple of games on both platforms, with many errors in Wine where there were few if any in Windows.  However, one game did run much better on Wine than it did on Windows: Command and Conquer: Red Alert.  Yeah, one of the more ancient games.  Runs fine in Wine, has lots of issues in Win 2000.
 
Some other games I've tested:
 
Sid Meier's Alpha Centauri
Works fine in Windows, crashed after first in-game animation in Wine
 
Microsoft Flight Simulator 98
Works decent in Windows (some lag), crashes after a little while in Wine
 
I'll soon test Homeworld and see how it performs; it would be the first highly 3d game to run on that computer.

---

### Post by Espryon on 2008-10-23
> **Greyed said:**
> You're kidding, right?

WoW in WinXP, 20-30FPS in Netherstorm.  Wine, 12-15FPS.
TF2 in WinXP, 22-32FPS on most maps w/DX9 and most settings set to high.  Wine, 8-12FPS in DX8.1 with all settings set to low.

I only wish they ran better because I'd be able to dump WinXP.

Want to know what's really going on?  [http://en.wikipedia.org/wiki/Placebo](http://en.wikipedia.org/wiki/Placebo)

they do on mine i get close to 200-350 fps and 30-70ping

---

### Post by Mistrblank on 2008-10-23
> **Greyed said:**
> You're kidding, right?

WoW in WinXP, 20-30FPS in Netherstorm.  Wine, 12-15FPS.
TF2 in WinXP, 22-32FPS on most maps w/DX9 and most settings set to high.  Wine, 8-12FPS in DX8.1 with all settings set to low.

I only wish they ran better because I'd be able to dump WinXP.

Want to know what's really going on?  [http://en.wikipedia.org/wiki/Placebo](http://en.wikipedia.org/wiki/Placebo)

Meh.  WoW on the same system, vanilla WinXP install to SP3 and up to date drivers I now get the same frame rates consistently testing with the in game timetest as I do with Wine.  Wine itself took a considerable amount of time to configure however and there is a noticeable loss not having D3D enabled (won't even run with D3D on my setup) so it wasn't without cost.  But OpenGL winxp to wine is the same.  In many respects I get better performance because under Wine, multi window support is better for me (I do lose frames going to windowed mode in WinXP for some reason).  

I have also noticed a significant halving of my latency from 250ms to 115-130ms ping times going to Linux.  It's a shame though that on the same network, the Mac laptop I have drops latency to 80ms, but overall can't support the graphics of the game using onboard video.

I really do think it varies based on hardware and user dedication to getting things running.  Realistically Wine will not be encumbered by Windows services and it is a lot easier to find information on tweaking Linux services and running processes.  This dedication is one of the reasons that I'm moving back to consoles whenever I can for games (like Fallout 3), as cool as it is to have the customization in games, sometimes it becomes a liability when I'm concerned about every little graphical twitch that I think could be averted.

---

### Post by DoktorSeven on 2008-10-23
I have a very low spec system (about the minimum WoW can use), and it **does** run better in Wine than Windows.  I believe main reason is that Windows takes up more resources than Linux (I run fluxbox and very few things in the background -- installed a minimal CLI Ubuntu system.  Windows is also tweaked the best I can get it -- all unnecessary services stopped, running bblean instead of Explorer, etc) -- base (without WoW running) memory usage in particular is at least 3x higher in Windows than in my Linux system.

FPS is consistently higher in Linux than in Windows.  Play is smoother.  Large populated areas grind to an actual slideshow in Windows, not so in Linux.

Both use the same configuration for WoW (running from the same place on my Windows drive).  

I've seen the same with other games like HL2 and Portal.  Some might argue (as someone above did) that Wine is giving some sort of "false" performance boost, but when you're playing the exact same game, exact same graphics, and getting a better experience out of Wine, semantics doesn't matter.  The game plays better under Wine, period.

---

### Post by vegetable92 on 2009-08-13
no games work on linux its too complicated to do.you will need a linux expert to do it.

---

### Post by Duskao on 2009-08-16
Vegetable92, Give POL (playonlinux) a try. It uses wine, but with a bunch of games it does a lot of the tweaks to get the games running. I myself am still fairly new to Ubuntu/Linux and I have had most of the games I have tried to get running in one way or another and I even have an Ati video card, so thats with the driver problems. 

I'm not saying everything works perfectly, great, modestly or even at all in some cases, but if you don't like windows it is at least worth a try. Here is a bit of a list I have had working with wine to some degree and a rating of how well they ran 1-10... none of which have worked better on linux then windows though.

Half-Life 2 (7)
Team Fortress 2 (4)
Mass Effect (2)
Day of Defeat (6)
Plants vs Zombies (5)
Guild Wars (9)
Lord of the Rings Online (8 )
Fallout 3 (4)
Chronicles of Riddick (10) (ran about equivlant to windows)
Indiana Jones and the Emperors Tomb (6) (missing faces???? but the performance was fine)
 
I have tried a lot of different games and I'm at about 50-50 to being able to get games to work. I have always used the newest wine release with POL.

I am certainly no linux expert. I can hardly use the command line in the terminal.

---

### Post by yanom on 2009-10-07
StarCraft totaly runs better in Wine. Under native windows the graphics are reversed (like a photo negative) but it looks fine under Wine.

---

### Post by MetroidJunkie2008 on 2009-10-07
Ironically, the 2D games seem to give me more problems on Wine than the 3D ones. With games like Spore and Sims 3, no problems. Same speed as Windows. Ultra 3D Pinball Creep Nights? (Not actually 3D, uses 2D sprites) lags for no reason. Maybe it's the drivers.

---

### Post by bigseb on 2010-04-09
> **smmalis said:**
> Rise of Nations worked right out of the install on Wine, won't even start in Vista.
For real?! That's great, I love that game and the the one after, Rise Of Legends. Haven't played 'em in a while so I will try this out tonight still!!

You rock! :guitar:

---

### Post by LoloftheRings on 2010-04-15
Absolutely!
Warcraft 3 on Windows 800x600 all high settings: 60fps
Warcraft 3 on Linux 1440x900 all high settings with anti aliasing though nvidia control panel: 150 fps

If that ain't a clear difference Oo

Testing system: 
Intel i5 661 clocked at 3.75 Ghz
Asus gts250 1gb
Kingston DDR3 4GB

Windows 7 Home Premium 64 bits
Arch Linux 64 bits

Had 80 fps on Ubuntu (still better than 60). Don't know why, maybe drivers. I did give Arch a bit more love when installing.

---

### Post by cyrex on 2010-04-16
The following games i have tested on both Windows XP, Windows 7 and Ubuntu 9.10 with wine. This games run faster or better (more fps) on wine than on windows:


1. WoW - Runs better on wine than on windows. I actually have (using the same PC) a 20% to 35% better performance. This has been tested also by other friends who wanted wow on their PC and i showed them Ubuntu. The Wine i used is not modified or anything, is the standard one that comes using the link in winehq.org

2. Half-Life 2 - I mean WTF. I thought this game was going to lag or something on wine. It ran better than windows. I was really impressed (and still am)

3. Quake 3 - Another WTF. Am talking here about the Quake 3 Arena for windows, not the one for linux. It has much more FPS than on windows.

4. Need 4 Speed Underground - Ran about 15% better on wine.

That is all.

---

### Post by darklegion on 2010-05-06
> **LoloftheRings said:**
> Absolutely!
Warcraft 3 on Windows 800x600 all high settings: 60fps
Warcraft 3 on Linux 1440x900 all high settings with anti aliasing though nvidia control panel: 150 fps

If that ain't a clear difference Oo

Testing system: 
Intel i5 661 clocked at 3.75 Ghz
Asus gts250 1gb
Kingston DDR3 4GB

Windows 7 Home Premium 64 bits
Arch Linux 64 bits

Had 80 fps on Ubuntu (still better than 60). Don't know why, maybe drivers. I did give Arch a bit more love when installing.

You probably have V-Sync enabled on the windows box, which will lock FPS at the monitor's refresh rate (which is probably 60hz)

I think as far as the video side is concerned, most games are not going to run better under wine. There is a hefty hit from the conversion from direct3d to opengl, and it's going to take a lot of optimisation for that performance hit to go away.

Also, as a side note for people looking to increase performance with wine: CPU is more important than the GPU, provided that you are using a decent NVIDIA card. Because wine is bottlenecking the GPU using a faster CPU can help reduce this bottleneck. I'm getting quite a large performance increase from overclocking my e5200 from 2.5ghz to 3.6ghz. Upgrading my video card produced virtually no improvements, except for games that were already running at high framerates. 

I imagine that people with i5/i7 CPUs will be getting quite good performance with wine, although I have not tested this myself.

---

### Post by cogadh on 2010-05-07
I've been going through some of my GOG-purchased games lately and found that two in particular run infinitely better in Wine than in Windows: MDK2 and Septerra Core. While both games do run well enough in Windows, because of their age, they sometimes have issues that require some "under the hood" tweaking to make them work better. With Wine, both games simply work right out of the (digital) box.

> **darklegion said:**
> 
I think as far as the video side is concerned, most games are not going to run better under wine. There is a hefty hit from the conversion from direct3d to opengl, and it's going to take a lot of optimisation for that performance hit to go away.

That only really applies to Direct3D-based games. Any game that is already OpenGL is not going to have that performance hit. That's why games based on things like the Unreal Engine can and will run just as well, if not better, in Wine as they do in Windows.

---

### Post by darklegion on 2010-05-08
[QUOTE=cogadh] That only really applies to Direct3D-based games. Any game that is already OpenGL is not going to have that performance hit. That's why games based on things like the Unreal Engine can and will run just as well, if not better, in Wine as they do in Windows.[/QUOTE]

Yes, this is true. There aren't many games that support OpenGL, though. And many of them support Linux natively, anyway. The exception being World of Warcraft, which is a big exception but not really a game I'm interested in playing.

---

### Post by hikaricore on 2010-05-08
> **darklegion said:**
> Yes, this is true. There aren't many games that support OpenGL, though. And many of them support Linux natively, anyway. The exception being World of Warcraft, which is a big exception but not really a game I'm interested in playing.

Bull****, there are tons of games that use/have support for OpenGL that aren't native titles.
You should really do a little more research on a subject if you intend to make these kinds of claims.

---

### Post by cogadh on 2010-05-08
> **darklegion said:**
> Yes, this is true. There aren't many games that support OpenGL, though. And many of them support Linux natively, anyway. The exception being World of Warcraft, which is a big exception but not really a game I'm interested in playing.
Just using my one example of the Unreal engine, we are talking well over 100 different games that all support OpenGL:
[http://en.wikipedia.org/wiki/List_of_Unreal_Engine_games](http://en.wikipedia.org/wiki/List_of_Unreal_Engine_games)

Start adding to that all the games based on the Quake and idTech engines then all of the "lesser" game engines and you are talking thousands of titles that all support OpenGL or have the option to use OpenGL.

---

### Post by Legendary_Bibo on 2010-05-20
Well I'm going to contribute my two cents by testing out some games I bought through steam when I had Vista. By the way will they just work? Anyways here's what I'm testing.

What I'm running on:
HP DV700 Laptop with
ATI HD RADEON 3200 256mb
AMD TURION 64-bit Dual-Core
4gb of RAM
Ubuntu 10.04 LTS
and the latest version of Wine.

[B]Braid - Runs beautifully without any issues for me. The only thing is that Braid and the Gnome panels don't like each other. You'll be stuck playing with both your panels and your screen will go to a low resolution (at least for me) which doesn't revert even after quitting Braid.
Team Fortress 2
Gary's Mod
Killing Floor - Runs, and seems to run smoothly on the menu except for mouse issues. I can start a game, and it loads faster than on Vista, at first it was jumpy then played normally until enemies spawned which made my laptop crash.
Audiosurf - Runs and loads, but you can't get beyond the screen that has all their new reports and other crap.
Psychonauts
Portal - Turns out it's free until May 24th...and it works great besides a few graphical glitches. It ran at 60fps for me on the standard settings. It only slowed down whenever a portal opened up.

[/B]And the only other two game I must have bought while drunk because I think I got them both for five dollars, but they kind of suck.

[B]Ben There, Dan That!
Time Gentlemen, Please!
[/B]

---

### Post by nlstone123 on 2010-05-20
About the only game I play anymore is World of Warcraft and overall I would have to say it runs a good deal better when playing it in WINE. As for the frames per second it is generally 10-20 better then Windows. The biggest difference though is my latency which is always much lower in Ubuntu then in Windows. Always been stumped by that one.

I had Windows XP that I replaced with Windows 7 64bit but it was always the same deal. In Windows my latency was at the best of times around 150 and as high as 250-300 at times. This is with a clean install, not running anything like torrents etc in the background either. Now on Ubuntu 10 64bit running WoW in WINE I normally get around 50-80ms latency.

As a side note I've also tried Half-Lfie 2, Dark Messiah Might and Magic and a hand full of other games I bought on Steam and they all worked fine. Really the only reason I still have Windows are a few games that only run in Direct X 10 like Just Cause 2.

---

### Post by darklegion on 2010-05-22
> **cogadh said:**
> Just using my one example of the Unreal engine, we are talking well over 100 different games that all support OpenGL:
[http://en.wikipedia.org/wiki/List_of_Unreal_Engine_games](http://en.wikipedia.org/wiki/List_of_Unreal_Engine_games)

Start adding to that all the games based on the Quake and idTech engines then all of the "lesser" game engines and you are talking thousands of titles that all support OpenGL or have the option to use OpenGL.

I'm pretty sure that Unreal Engine 3 doesn't support Opengl, at least on windows. As for older games that support Opengl. Most of them are so old that using the Direct3D mode will still result in 100+fps. Could be useful on systems with very weak cpus/gpus, though. Also in the cases where direct3d mode causes glitches.

---

### Post by darklegion on 2010-05-22
> **Legendary_Bibo said:**
> 
**Braid - Runs beautifully without any issues for me. The only thing is that Braid and the Gnome panels don't like each other. You'll be stuck playing with both your panels and your screen will go to a low resolution (at least for me) which doesn't revert even after quitting Braid.**


Try using Wine's virtual desktop mode to work around the resolution issues.

---

