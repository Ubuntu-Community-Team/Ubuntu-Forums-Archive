---
title: "Left 4 Dead, windows or linux? HELP"
date: 2008-11-23
forum: Wine
---

### Post by billybag on 2008-11-23
So my friend has been nagging me to get this left 4 dead game. I realize it uses the steam engine and so i would like to install it on an OS and stick with it.

I can be *safe* and install it on windows vista, an OS it was *designed* for. To do this, i have to reinstall windows vista because i keep getting some memory crash error with explorer.exe whenever i finally connect to wifi. And then of course, after taking the time out to install vista i will then have to get my grub menu back and yadda yadda yadda. hastle.

OR i can take a little risk and install it on ubuntu linux. I am still on 8.04 until the next linux mint comes out. I want to know if anyone has heard of anyone that has had luck with left 4 dead on linux. I dont want to install it, have it not work right, then have trouble installing it on windows due to duplicated product codes.

---

### Post by eragon100 on 2008-11-23
According to the wine appdb, it basically runs fine (gold rating), however, it has extremely bad performance, making it unplayable on all but the fastest hardware (and I mean really, really fast.)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=33902](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=33902)

I would recommend you run it under windows :(

---

### Post by Dizzle7677 on 2008-11-23
Try it on both and decide for *yourself*. You can run "Vista/XP(tm)" in *KVM* ,'VirtualBox', %20%/etc>.

---

### Post by billybag on 2008-11-23
I was going to do that, but i cant tap into my NVIDIA card through a virtuamachine. I also dont know if i will run into the multiple install problem. Thw whole "you have already instaleld this... blah blah blah"

---

### Post by eks on 2008-11-25
> **billybag said:**
> I also dont know if i will run into the multiple install problem. Thw whole "you have already instaleld this... blah blah blah"

Steam shouldn't have this problem. They do have copy protection, some even securerom if the game demands it, but mostly of THEIR games (Valve games) are quite easy to manage and install. The nice thing is that it stays "in the cloud", so you can install it anywhere you want. I bought TF2 and L4D and installed on both work and home machine. On work, me and colleagues even downloaded just once and copied over to the other people that paid for it on the service. You just copy to the same folder and Steam checks the files.

But I have yet to try Steam on Linux though.

---

### Post by Crafty Kisses on 2008-11-25
> **eragon100 said:**
> According to the wine appdb, it basically runs fine (gold rating), however, it has extremely bad performance, making it unplayable on all but the fastest hardware (and I mean really, really fast.)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=33902](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=33902)

I would recommend you run it under windows :(

So basically it doesn't run...

---

### Post by karth on 2008-11-26
this isn't quite true, as I completed the demo on a P4 2.8GHz w/ 3GB ram and a 7600 GS 512MB AGP

it was running @ approx. 10-12 fps even during a steady zombie charge.

It does run, it doesn't have such bad performance as stated above.

---

### Post by Dark9204 on 2008-11-26
In my opinion, everything below 30FPS are unacceptable.
And to play a game at 10FPS, how can you even consider that gaming?

Anyway, to improve performance in most games you should run it with the -dxlevel 81 and WINEDEBUG="-all"
Example: WINEDEBUG="-all" wine C:/Program\ Files/Steam/Steam.exe -applaunch 240 -dxlevel 81

The WINEDEBUG="-all" tag means that wine wont debug your program and report errors into the terminal.

However, since people says that it "Runs extremely slow, even with all details on low. Huge mouse lag", you shouldn't bother to try to play this in wine.

---

### Post by Dark Aspect on 2008-12-09
Its slow,very very slow and largely unplayable. However if you do decide to play left4dead here are some ways to get it "some what" playable.

First, fire up the registry editor

```
wine regedit
```

[HKEY_CURRENT_USER\Software\Wine\Direct3D] 

OffscreenRenderingMode = fbo
UseGLSL = enabled
VertexShaderMode = hardware
PixelShaderMode = enabled
DirectDrawRenderer = opengl
RenderTargetLockMode = auto

Second, load the game with this

```
aoss env WINEDEBUG=-all wine-pthread C:/Program\ Files/Steam/Steam.exe
```

"-dxlevel 81" won't work because this game only supports Direct X 9 models and not Direct X 8. Once in game turn multicore rendering off and set shader level to low. This helps get about 40 FPS in game play but still only about 15-20 FPS in heavy combat. If you want to play this game full speed than I suggest windows sadly.

---

### Post by jacksaff on 2008-12-10
If you buy it through steam it doesn't matter which platform you use. You can install it on as many computers & operating systems as you like. You just can't be logged onto steam from two places at once.

---

### Post by rryan on 2008-12-11
> **Dark Aspect said:**
> Its slow,very very slow and largely unplayable.

I don't know what's different about me, but it works fine for me. I'm not even using the registry tweaks you mention. I just installed it and played it with no customization. 

Make sure to turn desktop effects off, since then Left 4 Dead will be fighting with Compiz for control of your video card.

I don't have awesome hardware, but my machine is modern:
Core 2 Quad 2.4ghz and a GeForce 8600 (very cheap graphics card, much less powerful than an 8800). 

As I said, it worked perfectly for me. Sofar I've only played single-player though. 

I haven't tried turning the settings all the way up yet, but I was playing on what I'd call 'medium' settings. I switched to bilinear filtering instead of anisotropic, because anisotropic is expensive on my graphics card.

---

### Post by hyperhopper on 2008-12-26
> **rryan said:**
> 
Make sure to turn desktop effects off, since then Left 4 Dead will be fighting with Compiz for control of your video card.

[B]I don't have awesome hardware, but my machine is modern:
Core 2 Quad 2.4ghz and a GeForce 8600 (very cheap graphics card, much less powerful than an 8800)[/B].

im gonna try to do the same thing, but i only have

P4 2.66 GHZ
512 RAM
geforce 5200!!!!

*gulp*

---

### Post by billybag on 2008-12-26
good luck. It worked great except for the actual game. It was way to laggy. 
Your setup is only a bit better than mine. Good luck anyway.

---

### Post by nbotticelli on 2009-02-04
How do you think this would fare under WINE on a laptop with a dual-core 1.66GHz cpu with 2GB ram plus an Nvidia Go 7600 with 256MB?

Would this be at all decently playable you think?

I currently have it on here running under XP and the settings have to be set down somewhat but it still looks fairly decent.

How much of a performance hit should I expect?

---

### Post by Bios Element on 2009-02-05
> **nbotticelli said:**
> How do you think this would fare under WINE on a laptop with a dual-core 1.66GHz cpu with 2GB ram plus an Nvidia Go 7600 with 256MB?

Would this be at all decently playable you think?

I currently have it on here running under XP and the settings have to be set down somewhat but it still looks fairly decent.

How much of a performance hit should I expect?

Eh, It'd be pretty horrid. That's a worse setup then mine And I hardly find it playable.

---

### Post by taylorfaux on 2009-02-05
meh if you have poor hardware, and can handle playing the game in a small window, I think it runs pretty playable.  I have an old Toshiba Qosmio I bought in 2004, and it runs good enough in a window.  Portal and Team Fortress run perfect, but this game is a little heavy on my slow hardware, but windowed it's not really an issue.

---

### Post by lordmoosh on 2009-02-15
Left 4 dead runs terribly slow on my system:

Ubuntu 8.10 64Bit
Wine 1.14
AMD Athlon x2 3.0 GHz
Nvidia Geforce 7900GS
4 Gigabytes of Ram


I don't see any graphics artifacts or any glitches though.

Forgot to mention this is with the lowest settings at 800x600...

---

### Post by TVMA on 2009-02-19
It runs okay for me.. 38 fps right now..

I'm running

Ubuntu 8.10 64 bit
AMD quad core 2.4 phenom
8 gigs or RAM
ATI HD4850 video card

so I guess it should run at least decent..

---

### Post by kimbecause on 2009-02-20
Mine started out fairly slow but added the tweaks at the start of the thread and now runs about 40 frames ...

I don't have any sound though. I took "aoss env" so am launching like this:

WINEDEBUG=-all wine-pthread C:/Program\ Files/Steam/Steam.exe -applaunch 500 -novid

anyone else have this problem? or is that just a wine thing ?

---

### Post by karth on 2009-02-20
If you really plan on using OSS through the alsa compatibility layer, your line should read as follows:

> WINEDEBUG=-all **aoss** wine-pthread C:/Program\ Files/Steam/Steam.exe -applaunch 500 -novid

But I recommend you set ALSA as the sound output in winecfg and leave out the aoss wrapper, since the recent bugs appear to have been resolved in the latest builds.

I'm surprised you didn't put the C:\... part into quotes though, I just learned something ;)

Anyway, I have changed my rig since my last post on this topic, I am now getting a fairly good framerate with slightly better settings than defaults.
But I still have an annoying glitch: when I end a scenario, and spawn into the next one in the campaign, on some specific scenarios, I get total black screen. Quitting then rejoining solves the matter, but it's very annoying...

---

### Post by BoneSmash on 2009-02-20
Wine 1.1.16 should offer a massive speed boost to all Source games, that is if I understand one of the latest patches submitted to Wine related to the sRGB texture bug correctly.

[http://www.winehq.org/pipermail/wine-patches/2009-February/069448.html](http://www.winehq.org/pipermail/wine-patches/2009-February/069448.html)

---

### Post by betrunkenaffe on 2009-02-21
I installed L4D on my Pangolin Laptop and it plays fairly well, I get 25 FPS which drops to 18 FPS during large mobs of zombies. I was testing it out and didn't really notice any problems graphically (I couldn't tell difference between it and a Windows one running). I ran into some sound issues is about it, but that's a problem with Pulseaudio and steam. That was with Wine 1.1.15

---

### Post by xycris on 2009-02-24
Hi,

Is it possible to play L4D in Linux on LAN? Me and my friends wanna try it out but can't seem to figure things out on how to connect with one another. #-o

We are all running Kubuntu 8.10 with a capable hardwares specs to play at 29 fps at 1024x768 resolution.

Thanks for the help in advance.

---

### Post by betrunkenaffe on 2009-02-24
> **xycris said:**
> Hi,

Is it possible to play L4D in Linux on LAN? Me and my friends wanna try it out but can't seem to figure things out on how to connect with one another. #-o

We are all running Kubuntu 8.10 with a capable hardwares specs to play at 29 fps at 1024x768 resolution.

Thanks for the help in advance.

Also played with my buddy over the internet, worked fine. Even had voice (although still glitchy sound), no fiddling was required..

---

### Post by u235sentinel on 2009-02-25
> **eragon100 said:**
> According to the wine appdb, it basically runs fine (gold rating), however, it has extremely bad performance, making it unplayable on all but the fastest hardware (and I mean really, really fast.)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=33902](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=33902)

I would recommend you run it under windows :(

That's the ONLY reason I haven't purchased it yet.  I would buy it if it ran well under WINE.  Gold rating yes but if it lags then I don't bother.

I have a bunch of other Source games which run just fine and I do have beefy hardware running Ubuntu 8.04 and WINE 1.0.1.  Other games including Oblivion, Morrowind, Starcraft, etc...  In other words I have a lot of Windows games running great.  

I always check the winehq.com appdb before making a purchase.  In several cases I purchase 3 or 4 copies.  One for each computer (mine, my wife's, my kids computers and so on).

Here's wishing for the native Left 4 dead to come out soon.  I've love to get it.

---

### Post by wolfyking2 on 2009-02-25
> **Dark9204 said:**
> In my opinion, everything below 30FPS are unacceptable.
And to play a game at 10FPS, how can you even consider that gaming?

Anyway, to improve performance in most games you should run it with the -dxlevel 81 and WINEDEBUG="-all"
Example: WINEDEBUG="-all" wine C:/Program\ Files/Steam/Steam.exe -applaunch 240 -dxlevel 81

The WINEDEBUG="-all" tag means that wine wont debug your program and report errors into the terminal.

However, since people says that it "Runs extremely slow, even with all details on low. Huge mouse lag", you shouldn't bother to try to play this in wine.Over 30FPS?  Geez, most of the FPS games I run only get like 9 FPS and I can play just fine :)

---

### Post by betrunkenaffe on 2009-02-25
Why are you still running 1.0.1 instead of upgrading to 1.1.15 of wine?

On the 30fps thing, most WoW players are used to less than 30, in some places, you are lucky to get 10

---

### Post by karth on 2009-02-26
1.0.1 is the version included in the standard ubuntu repositories, if he hasn't added the dedicated wine repo, he's to go with 1.0.1 .

Well that slowness issue is merely from two pages before, things have changed since then... but of course, YMMV

---

### Post by MCMXCIII on 2009-06-05
Googling will tell you how to install the steam server to run natively in Linux... Then there's no need for WINE (which I've never used...) After installing Counter Strike: Source from the Steam servers it runs fine as if it was native in Linux.

Hope that helps.

---

### Post by Oden42 on 2009-08-23
Sorry I know this Thread must be dead but what the hey. I have ubuntu 9.04 and have the must up to date wine and when trying to run L4D it tells me that I do not have pixel compression on or something like that every time it does say that it locks the computer up and I have to restart it. When I had XP it ran ok not great but ok I have a Acer aspire 4730z its a good little computer but not really made to play games but she manages though. So can any one help me if there is hope I may have to get another computer to play this game. I really do not want to go to windows and I don't have the money to buy a Apple and I really don't want on ether. So please help someone:confused::(

---

