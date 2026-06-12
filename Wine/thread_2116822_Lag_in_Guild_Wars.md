---
title: "Lag in Guild Wars"
date: 2013-02-16
forum: Wine
---

### Post by DeeJayndZ on 2013-02-16
Well im new to ubuntu as of like 48 hours ago, im running a 2.6ghz P4 processero on a GA-8SG800 Motherboard with a Nvidia Geforce 6600gt AGP8x also with a 1.5gb of ram.

As i installed ubuntu, i realised that it was very laggy, i love the layout, and enjoy ubuntu. But however im finding it hard to be able to run Guild Wars without a serrious lag problem, I have tested that it dosent lag with windows xp pro sp3. <snip>

I was just wondering is there a way to get all the driver's are uptodate kinda like the windoes ones? and if i have to install all the mobo drivers that normally come on a disc (which i dont have and will just get drivers from gigabyte's website) 

And also, if i could have some friendly advice or mods, or programs people are willing to recomend, or help as im really intrested in Linux my main OS, as i only used for about 24hours and only rebooted my HDD to play my game. Lol. In the process of putting ubuntu back on tonight and leaving it that way for now hope someone can help.

---

### Post by n4pgw on 2013-02-16
Mine runs well on 3GB RAM, but I understand that installing Gnome-fallback will make it much faster.  Also Xubuntu doesn't have the overhead of Unity as the 12.xx versions have.

---

### Post by lisati on 2013-02-16
Thread closed for staff review: [s]we don't support pirated copies of software here[/s].

---

### Post by lisati on 2013-02-16
Thread reopened.

---

### Post by sandyd on 2013-02-16
Thread reopened after it failed to reopen ;)

---

### Post by varunendra on 2013-02-17
..and* moved to **Wine**,* which I'm sure the OP is using to run the game.


@ DeeJayndZ,
A few things you should know -
> **DeeJayndZ said:**
> 
As i installed ubuntu, i realised that it was very laggy, i love the layout, and enjoy ubuntu. But however im finding it hard to be able to run Guild Wars without a serrious lag problem, I have tested that it dosent lag with windows xp pro sp3.
First things first - your motherboard and related CPU/RAM combination is too old to run Ubuntu with Unity 3d smoothly. Read point 2 below to know why.

Some other issues -

Any game or software that runs on XP (or any windows version) **can not run** on Linux _directly_.

So if you are running the same installer on Linux to install the game, you are actually installing it over a '**Compatibility Layer**' *(like 'wine' software in Ubuntu)*, which provides the same environment as windows to the installer - thus making it 'believe' that it is running on windows.

Obviously, this process of 'emulating' windows environment needs a lot of extra work in the background and even then is not guaranteed to always work.

As such, if there is even a slight lag in the Linux OS (ubuntu in your case), it is definitely going to badly affect the performance of the game / software which you are running over such a 'Compatibility Layer' since it needs almost twice the work needed to run the game / software.

One of the very few solutions to this problems is what *n4pgw* suggested above. That is, use a lightweight desktop environment to make sure it is light on system and leaves enough processing power for the additional work.

> I was just wondering is there a way to get all the driver's are uptodate kinda like the windoes ones? and if i have to install all the mobo drivers that normally come on a disc (which i dont have and will just get drivers from gigabyte's website)
I can see two immediate problems -

1) Aa far as I know, gigabyte does not provide drivers for Linux; at least not for that motherboard. Besides, I don't think even the best drivers can make any difference for reasons given in the next point,

2) If your motherboard is [this one]("http://www.motherboard.cz/mb/gigabyte/GA-8SG800.htm"), it is too old to run Ubuntu with Unity 3D and a game over 'wine' simultaneously. LGA 448 type processors are really outdated now and you can't expect so much from them, even with 1.5 GB RAM which would be DDR1 333MHz at most. A possible solution may be using '[Lubuntu]("http://lubuntu.net/")' instead of default Ubuntu. It will be much lighter on system, hopefully, leaving enough resources for the game.


> im really intrested in Linux my main OS, as i only used for about 24hours and only rebooted my HDD to play my game. Lol.
There are many hardcore linux users on these forums who are stuck with windows only because their favourite games can't run on Linux, or not as good as they can compromise with. So, dual booting with XP can also be a solution, if nothing else works. ;)

That being said, please pay special attention to what lisati suggested you in PM, and be extra cautious with your choice of software sources.

---

### Post by DeeJayndZ on 2013-02-17
Thanks so much for the support so lubuntu you say, well yeah i didnt really know wjere to start when it came to linux, as im trying to upskill. Unfortanetly i jave a level 5 in computing im only 22 and got it ahen i was 17 trying to look for a job as of late bust most want people with experience in linux and server situations, hmm i currently have a dual partition for win xp and ubuntu 12.10 guess im back to the drawing board again. Lol. Been there like 5 timea in last 3 days but guess ill try agian. Need tl re install xp as justgets past the check and then nothing, but ubuntu loads fine, jst a little slow. 
 
Thanks for all your advice guys keep adding if feeling the need i take all criticisim with regards

---

