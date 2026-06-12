---
title: "Wine consume too much CPU?"
date: 2011-08-21
forum: Wine
---

### Post by tingxyu1996 on 2011-08-21
Hello there!

Yesterday I successfully run a few games in Wine. The old classic games such as Starcraft and Counter Strike 1.6 works 100% fine! But when I was playing Counter Strike Source, it is so laggy even I set all graphical settings to 'low'.

Is it means the CPU is very busy? Wine consume too much CPU? I run it in Windows, all settings to 'high' = no problem; but in Ubuntu Wine = can't play.

Here's my CPU log:
Intel(R)Core 2 Duo E7400
1920 x 1080 resolution.
Nvidia GeForce 9500GT GDDR3

Anyone gives me an answer? :D

---

### Post by disabledaccount on 2011-08-21
Yes, wine consumes more CPU time for running games, because it emulates DirectX API components and 3D translatios are especially heavy task.
Therefore it's always better to check AppDB and forums for solutions/optimizations - like running game with opengl renderer or forcing lower dxlevel.

But in Your case I think it may be some problem with gfx drivers. What linux distro You are using, what wine version?

---

### Post by cwwilson721 on 2011-08-21
> **tomazzi said:**
> ...
But in Your case I think it may be some problem with gfx drivers. [COLOR="Red"]What linux distro You are using[/COLOR], what wine version?
Gotta love people who don't read.

Two things:
[LIST=1]
[*]This is the UBUNTU forums, so...
[*]And their Ubuntu version is right there.to the left, under their name.
[/LIST]

Now, back to the OP's issue...

Have you installed the proprietary drivers? (nvidia-current)
Which wine version? (Run 'winecfg, and look in the 'About' tab)

Now, you do have to remember that wine does not run D3D games as fast as Windows (with some exceptions). And since your card/chip is rather anemic to begin with (a 9500GT has a rather 'narrow' memory bandwidth), you will more than likely run into issues like these.

I would venture the major bottleneck is video, then CPU.

A way to check CPU utilization is to use Conky, or something like it, that has a CPU% meter on it. (I use it in WoW all the time, to check CPU %, and memory % too)

---

### Post by disabledaccount on 2011-08-21
> **cwwilson721 said:**
> Gotta love people who don't read.

Two things:
[LIST=1]
[*]This is the UBUNTU forums, so...
[*]And their Ubuntu version is right there.to the left, under their name.
[/LIST]
1. ...so it means nothing, actually
2. ...but it also means nothing - at least it's not obvious, unless You belive in everything that peples have in their signatures.

> **cwwilson721 said:**
> And since your card/chip is rather anemic to begin with (a 9500GT has a rather 'narrow' memory bandwidth), you will more than likely run into issues like these.

I would venture the major bottleneck is video, then CPU.Wait, what? Have You ever seen CSS? It is playable even on Intel gfx, so please... 9500GT can run Crysis with medium details/resolution, so it's definitvely NOT "narrow" memory bandwidth. But I agree (as suggested before) that it can be issue with gfx drivers.

---

### Post by cwwilson721 on 2011-08-21
I stick with 'anemic'.
> ...
 650/1625/800-900 MHz for the GPU, shader cores and 256/512 MB of memory tied to a bus-width of 128-bits
... That's rather narrow to me. Not as bad as say a 9400gs (64-bit memory bus), but definitely low-end.

So, as I said, bottleneck #1 is GPU, next is CPU

---

### Post by tingxyu1996 on 2011-08-22
> **tomazzi said:**
> What linux distro You are using, what wine version?
Ubuntu 11.04 and Wine 1.3.26 latest beta version(someone recommended me to update into this version.) And, how to force lower DirectX version?

> **cwwilson721 said:**
> Have you installed the proprietary drivers? (nvidia-current)

Yes, I installed it and it runs perfectly.

> **cwwilson721 said:**
>  (a 9500GT has a rather 'narrow' memory bandwidth), you will more than likely run into issues like these.

Nah... 9500GT with DDR3 is much better than DDR2, run Crysis 2 with 1280 x 720 medium settings = no problem and Black Ops 1440 x 900 'Very High' settings(with AA 4x) no problem.

Okay, let's come back to the main question:
So now, I explain it.
In Counter Strike Source, I set the graphical settings into all 'High', and then start a game.
In a map without any bots, it is perfectly smooth. But, with 15 bots, it'll became laggy.
Especially in de_dust or some place which it got water, it'll become very lag.
And then, the sound will become... uh... like... not continious.. hard to explain about sound problem.

Even if I set the graphic setting high or low, de_dust and some place which got water still laggy. So, maybe it is not graphic driver problem.

So, maybe it is CPU problem, right?

---

### Post by tingxyu1996 on 2011-08-22
Ok, so... Anyway to reduce the CPU consumption? Or what Windows Emulator program is better?

---

### Post by disabledaccount on 2011-08-22
> **tingxyu1996 said:**
> In Counter Strike Source, I set the graphical settings into all 'High', and then start a game.
In a map without any bots, it is perfectly smooth. But, with 15 bots, it'll became laggy.
Especially in de_dust or some place which it got water, it'll become very lag.
And then, the sound will become... uh... like... not continious.. hard to explain about sound problem.
As I said before: appDB is really good place to start:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)
(HOW TO section)

Additionally, starting from 1.3.24 WINE is less "stable" because of some serious changes in architecture, so You may want to try previous versions.

> **tingxyu1996 said:**
> Or what Windows Emulator program is better?
Everything is based on WINE and Wine Is Not Emulator :)

---

