---
title: "nVidia drivers, where can I find better?"
date: 2006-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jjandrj6679 on 2006-11-08
Hi there,
I am running nVidia on my system, (specs below). I was wondering how I can update them so that they include Pixel Shader 3.0, Vertical shaders & a simular program to DirectX 9c.
I only dicovered that It didn't have them when I used Wine to install 3DMark05. I used this program all the time in Xp, its seemed to install ok using Wine but it will not run any thing although it will start up. 

Any help would be appreciated
Yours
Josh

---

### Post by pony-tail on 2006-11-08
At least the nVidia drivers work - I use Radeons - I would like to download a driver that works ! - but back to the issue at hand , you could use the latest drivers from nVidia's website there should be a change log stating what they support and what they don't but they are to my knowledge the newest that you can get !

---

### Post by fabertawe on 2006-11-08
> **jjandrj6679 said:**
> Hi there,
I am running nVidia on my system, (specs below). I was wondering how I can update them so that they include Pixel Shader 3.0, Vertical shaders & a simular program to DirectX 9c.
I only dicovered that It didn't have them when I used Wine to install 3DMark05. I used this program all the time in Xp, its seemed to install ok using Wine but it will not run any thing although it will start up. 

Any help would be appreciated
Yours
Josh

Hi Josh,

At least it looks like you've got Wine working now.

I think you are expecting way too much from Wine. I have no idea how 3DMark05 would work under VMWare but it may be worth trying. From what I understand, running things like Source games (Steam) can work with Wine but at very low framerates. It sounds to me like you should keep the XP partition (maybe slimmed down) just for gaming. I know ID port their games to Linux and Quake4 runs just as fast as under Windows for me.

Paul

---

### Post by jjandrj6679 on 2006-11-08
To be totally honest I didn't get anything from Wine, just a huge headache, Nothing works at all. I wasn't sure what to expect from Wine, but I'll play with it some more.

As to nVidia I used their latest driver, but I am unable to configure it as I can't find any referance for it on my system? Well anything I could use.

If I cant get Shader 3.0 & DirectX or equivalent then I can't run my games (F.E.A.R & GTA SA) and were back to square one, ie keep Xp on dual boot.
Any help anyone?

Josh

---

### Post by kuja on 2006-11-08
The (propietary) Nvidia Linux drivers don't include directX support. I don't think there's a way for you to get it either. They certainly still shell out their fair share of performance though. Mmmmmm Quake 4 set to Ultra :mrgreen:

---

### Post by fabertawe on 2006-11-08
> **kuja said:**
> The (propietary) Nvidia Linux drivers don't include directX support. I don't think there's a way for you to get it either. They certainly still shell out their fair share of performance though. Mmmmmm Quake 4 set to Ultra :mrgreen:

An 18 second boot and Q4 on ultra... I'm beginning to think you're some kind of god ;) 

Paul

---

### Post by jjandrj6679 on 2006-11-08
I am not entirly sure that I did install the most up to date software.
I seem to have both of these downloaded drivers saved to a file.
```
NVIDIA-Linux-ia64-1.0-5336-pkg1.run
NVIDIA-Linux-x86_64-1.0-7184-pkg2.run
NVIDIA-Linux-x86_64-1.0-8776-pkg2.run
``` 

A) How do I check which one was installed?
B) How do I install the newer driver if not already installed?
C) Would I need to uninstall the currant version I have installed?
I'm still struggling with learning the command line controls so any help would go miles for me. I tryed a couple of commands but it still didn't work, just lack of knowledge thats all, I'll get there in the end.

To be totaly honest, I can't ever remember having such an anoying Opp sys, that took so much of my time and brain space, but with windoze it was just point & click, nothing to learn. So in the end I came to the conclusion that I'll stick with U64 and learn something for the first time in 40 years. That is as long as you lot are prepared to answer many stupid questions of mine.

So a cool response to the stupid "Q" above would be appreciated.

Yours
Josh

---

### Post by kuja on 2006-11-08
The easiest way to install the nvidia drivers is to do like this in a terminal:
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

---

### Post by jjandrj6679 on 2006-11-09
I did as you said and it installed
nvidia-glx 1.0.8776+2.6.15.12-1
The 8776 is the most up to date as far as I can see.

I suppose that I have to install a game thru wine if I want to carry on playing it, and that assumes it will work.

Are there any replacements for Directx 9c that you know of? 

Josh

---

### Post by kleeman on 2006-11-09
The latest stable driver is actually 9629 which has quite a few enhancements over 8776. You have to install it manually however (there is a good howto by tselliot somewhere on the forums).

---

### Post by jjandrj6679 on 2006-11-10
Hi There

Thanks for that info, I have managed to download, this driver " NVIDIA-Linux-x86_64-1.0-9629-pkg2.run " but I haven't a clue how to get it installed?? Any help. What are we supposed to do with .run files as everything I do doesn't work, but then I'm new to Linux and still trying to figure out what goes where in the command line...???..

Josh

---

### Post by kleeman on 2006-11-10
Check this out:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

You need to use method 2 I think. This means that every time there is a kernel update you need to repeat the procedure. I believe tseliot has put up some repos with this driver but I don't know if x86_64 (64bit OS) is supported yet.

---

### Post by cafg10 on 2006-11-10
Actually the 9629 drivers can be easilly be installed by following the guide avaible at [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy) if you stop before the beryl installing part, but if you want beryl as well you may continue with all the guide.

Aside from that, DirectX is a microsoft thing, so i think you will never see any other OS supporting DirectX, but wine comes with a partial compatibility layer, that supports some parts of the DirectX implementations.

So you cant most likelly run any windows specific game without **a lot** of effort, maybe you can think playing Warcraft or the Native Neverwinter Nights or even Quake 4 (own the first two myself)

---

### Post by jjandrj6679 on 2006-11-10
Hi there
Thanks for that, I'm new to linux hence all the windoze Q's.
Couple of Q's about both of the links that you two provided.

1) I am on Drapper Drake, it says for Edgy only? Can I still use it?
2) The latest driver is 9629 but this guide is for 8774 OR 7184
3) What is Beryl?

Am I being over causious and I should just follow the instuction?
Should I updat to Edgy? as I'm going to re-boot my pc very soon?
This has been a test bed to see if I could get away from "MS", so I've messed this Opp Sys up a bit with the little/no knowledge I have, hence re-boot.
Sorry for the stupid Q's

LFTHFUS
Josh

---

### Post by cafg10 on 2006-11-10
Actually you can't because it uses a diferent kernel version than dapper, som you  may stay as well with the 8774 driver, which works very nice on dapper.

3DS Mark, i recommend you to start using Blender, it is a little hard to learn but can import/export on many formats (including 3ds one and maya).

So migrating from windows is not always as easy as it seems,  specially for 64bit users.

---

### Post by jjandrj6679 on 2006-11-10
Hi
So I wasn't going mad then?? lol

Ok do you know how to enable coolbits in the nvidia driver, or is that only on the 9629?

As for DirectX, I guess Linux is a very differant system to Windoze. So what takes the place of DirectX then? something has to, dosn't it??

I thought Blender was a C.A.D prog, not benchmarking software like 3DMark05?

---

### Post by kuja on 2006-11-10
Blender is 3d Animation software (commercial applications would be things like C4D and 3DSM) 

Direct-X is a proprietary Windows multimedia api for things like 3d graphics, sound, and probably other things that I don't even care about. 

The closest equivalent in terms of graphics anyhow is OpenGL.

---

### Post by jjandrj6679 on 2006-11-11
Im getting the hang of this now, so if I want to play game, which I do, Ill have a better chance of getting them working if I go for OpenGL.

Do you think though its worh changing to Edgy and what would be the benefits.

I did find nVidias Overclocking prog in the Debain menu so I can have a bash at that.
Thanks for that guys, I'm still learning but I'm getting there slowly.
Greatfully Yours
Josh

---

### Post by kuja on 2006-11-11
I found it worthwhile to upgrade to edgy. Some of the things that were giving me trouble were fixed in edgy. Not much of a difference between dapper and edgy (that you'll notice) though, for the most part, just updated software.

---

### Post by jjandrj6679 on 2006-11-14
Thanks for that info you guys.
I'm downloading both 64 & 32 bit Edgy.
Should I stick with 64 or should I go 32? Is it easier for a begginer, like me? but then again the deep end is usually the place to start.
I take it, that Edgy is just an updated Drapper Drake? If I'm right why isn't there Service Pack (Windoze Thingy) like SP1 & 2 for Drapper? Is it easy to update, or would I have to re-boot with a the Edgy?

Josh

---

### Post by kuja on 2006-11-14
No, Edgy is just another release. Ubuntu does a release every six months. Every fourth release is a Long Term Support release. 6.06 (2006, June) was a long term support release. Some programs may see updates in the dapper-updates or dapper-backports repository, but for the most part things are going to stay the same.

---

### Post by jjandrj6679 on 2006-11-15
I think I understand, so Edgy is an updated version and there will be two more "releases" and then another "long term support release"? Gotcha, I think. so I gotta ask this, if Edgy is just another "release", what is the differance between that and a "long term support release"? As you can see I still have a "Windoze mentality" where you get updates galore then a new opp sys like Vista is to Xp.
Sorry to be a pain, just trying to get my head into Linux & away from Windoze.
Any hows I have dowloaded Edgy64 and will be instaling it tonite. Will it be a full istall with format & partition, or does it update what is needed?
Yours
Josh

---

### Post by kuja on 2006-11-15
That depends which cd you downloaded. If you downloaded the desktop cd then you indeed have to do a full reinstall with format & partition. The alternate cd however gives you the option of just doing an upgrade, with which there are a couple ways of doing it.

Oh, and the difference between a release and a long term support release is for how long it will recieve security updates. Normal releases are supported for 18 months. LTS releases are supported for 3 years on the desktop and 5 years on the server.

---

### Post by jjandrj6679 on 2006-11-15
I gotta ask.
Whats the differance between a "normal" release & a "LTS"?
I can assume that an LTS is a reworked edition that had all the previous updates/patches/fixes on one disk.
So are Drapper & Edgy normal or LTS? full or just updates?
Sorry to be so anoying.

I downloaded the desktop cd version, I do not mine rebooting though. 
Should I install Xp & U64 on the same or seperate drive? I don't think it realy matters... Does it?? 
Josh

---

### Post by kuja on 2006-11-15
It won't matter whether you install them on the same drive or not. Just be sure to install windows first if you plan to have it installed. Installing it second can cause issues. (ie: your grub being removed from the MBR)

The LTS releases are supposed to be more polished and stable, as a result of the work from the previous releases. It's a somewhat strange seeming development cycle.  Three releases working up to one LTS release that gets supported for longer. I guess LTS releases are appealing to businesses who consider it time consuming/costly/troublesome/whatever to upgrade, and would rather have one release that has security support for years than to upgrade every six months.

The present & past Ubuntu releases:
4.10 (aka Warty Warthog)
5.04 (aka Hoary Hedgehog)
5.10 (aka Breezy Badger)
6.06 (aka Dapper Drake) **First LTS release
6.10 (aka Edgy Eft)

---

### Post by jjandrj6679 on 2006-11-16
That all makes perfect sence, now, thanks for that.
Ill give it a bash tomorrow/today/when ever I awake.
Being a newbee still I hope that I can remember all my settings & How to's.
I must admit its easier to set up Xp than it is Linux, but I'll put that down to inexperiance. Take for example nlite, it extracts what you dont want from the install disk adds all the updates & Sp's, installs drivers and progs automaticly and sets up your pc just the way you like it. All from the install disk, I don't suppose that there is a version for Linux?

Josh

---

### Post by kuja on 2006-11-16
There won't be any service packs AFAIK. There are ongoing security updates though, from the security.ubuntu.com repository. Also, there is only one type of update in Linux that actually requires a reboot, and that is the kernel itself.

---

### Post by jjandrj6679 on 2006-11-18
Hi there
I rebooted with Edgy64, had a few problems with the install and still have.
Wasnt as easy to install as Drapper. I think the nvidia driver is 8776. Should I update it for the latest?
JJ

---

