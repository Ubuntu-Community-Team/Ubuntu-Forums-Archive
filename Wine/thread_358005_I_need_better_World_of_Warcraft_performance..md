---
title: "I need better World of Warcraft performance."
date: 2007-02-10
forum: Wine
---

### Post by Amadeo on 2007-02-10
Hey guys.  I'm running Ubunty Edgy with the newest Nvidia drivers.  I've enabled Fast Writes and SBA, and even got NvAGP working instead of AGPGART - all in attempts to improve performance in World of Warcraft.  The problem is, nothing works.  I hear a lot of people say that WoW runs just as well for them in Linux as in Windows.  This isn't the case for me.  I get 15 fps standing outside in Telaar in Linux, and 40 in Windows.  I use the same Config.wtf file for both operating systems, except for the special entries that are Linux-specific (OpenGL, Sound).

I have done the wine registry setting for OpenGL, but I don't believe that is needed anymore, as I saw no framerate change.  Indoors, my framerate is fine, I'm pushing 50-60 fps.  As soon as I walk outdoors where there is more to render, my framerate drops right to 15-ish fps.

There must be more ways to improve performance.  I don't mind if I lose image quality, but I need to at least double my Linux performance if the game is to be playable at all.  I'd appreciate any and all help.

Thanks guys!

---

### Post by Sammi on 2007-02-10
What are your system specs? CPU, graphics card, RAM?

Are you sure you did the registry tweak right? You do know that the entries are case sensitive, right? Please give us a screenshot of your regedit window, while you're looking at the tweak, so we can confirm.

---

### Post by Sammi on 2007-02-10
You can also help us to help you by posting the output of these commands:
```
glxinfo | grep vendor[LEFT][LEFT][LEFT]glxinfo | grep 'OpenGL version'
lspci | grep -i nvidia[/LEFT]
[/LEFT]
[/LEFT]

``` 
 And let this command run for a while, say 30 seconds, then post the output:[LEFT]```
glxgears -printfps
```[/LEFT]

---

### Post by Amadeo on 2007-02-10
Hi Sammi,

I have a Pentium 4 - 2.26GHz with 1GB RAM and an Nvidia 6600GT.  Here are the results of those commands:

```
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

OpenGL version string: 2.1.0 NVIDIA 97.46

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)
```


For the glxgears:

```

32771 frames in 5.0 seconds = 6554.053 FPS
32768 frames in 5.0 seconds = 6553.542 FPS
32775 frames in 5.0 seconds = 6554.978 FPS
32792 frames in 5.0 seconds = 6558.328 FPS
32760 frames in 5.0 seconds = 6551.846 FPS
32784 frames in 5.0 seconds = 6556.688 FPS
32750 frames in 5.0 seconds = 6549.517 FPS

```

Screenshot:
[http://i13.tinypic.com/2m2xiya.png](http://i13.tinypic.com/2m2xiya.png)

Thanks!!

---

### Post by Sammi on 2007-02-10
Sadly everything seems to be in order, so I have no idea what to suggest :confused:

I have a very similar setup to yours, with the same drivers, and I get between 20-30 fps during regular gameplay, and much higher rates indoors.

---

### Post by Amadeo on 2007-02-10
When you are getting framerates like that, are you speaking of areas in the expansion or in the old world? I imagine I'd get around 30 fps in some old world areas, but The Burning Crusade is much more demanding, and unfortunately, I can't afford to lose such significant framerate.

I'm curious if it's an issue existing outside of wine, or if there might be any other tweaks I could do to improve performance.

---

### Post by Sammi on 2007-02-11
I don't play much anymore, so I've not been in outland.

One more tip is to try to change the shader settings in WoW. They're found under video settings, and there are a lot of different thing to chose. Try every combination of video settings you can think of.

---

### Post by ilmorris on 2007-02-13
> **Amadeo said:**
> When you are getting framerates like that, are you speaking of areas in the expansion or in the old world? I imagine I'd get around 30 fps in some old world areas, but The Burning Crusade is much more demanding, and unfortunately, I can't afford to lose such significant framerate.

I'm curious if it's an issue existing outside of wine, or if there might be any other tweaks I could do to improve performance.

Blizzard has commented a couple of times stating the Outland is more demanding on the whole for a computer.  Not sure if it was intentional, or if they miscalculated somehow.  But people that I have spoken within my guild commented also that they on average are seeing anywhere from 10-20 fps lower while in outland, even on Windows systems.

---

### Post by Toxicity999 on 2007-02-15
Draenor (Outland) is more demanding because of having so many doodads as Blizz calls them, and overall higher model quality from what I've seen. Plus 90% of your server will be there. Heh. Not to mention waaaaay bigger zones.

---

### Post by justin whitaker on 2007-02-16
> **Amadeo said:**
> Hey guys.  I'm running Ubunty Edgy with the newest Nvidia drivers.  I've enabled Fast Writes and SBA, and even got NvAGP working instead of AGPGART - all in attempts to improve performance in World of Warcraft.  The problem is, nothing works.  I hear a lot of people say that WoW runs just as well for them in Linux as in Windows.  This isn't the case for me.  I get 15 fps standing outside in Telaar in Linux, and 40 in Windows.  I use the same Config.wtf file for both operating systems, except for the special entries that are Linux-specific (OpenGL, Sound).

I have done the wine registry setting for OpenGL, but I don't believe that is needed anymore, as I saw no framerate change.  Indoors, my framerate is fine, I'm pushing 50-60 fps.  As soon as I walk outdoors where there is more to render, my framerate drops right to 15-ish fps.

There must be more ways to improve performance.  I don't mind if I lose image quality, but I need to at least double my Linux performance if the game is to be playable at all.  I'd appreciate any and all help.

Thanks guys!

I'm having the same issue. Apparently the guys over at Codeweavers have BC running at acceptable frame rates in all areas...I purchased a copy and will let you know how it goes.

---

### Post by Toxicity999 on 2007-02-16
Cossover's staff does a ton, if not most of the contribution to wine so if you really want something to run better, you should buy crossover, and file bugs or vote there, whatever they do. They're paid to hack away at wine, they might be more willing to dive right in. One problem is, they probalby all play on similar machines in an office, or at home (good ones) so, you should ask about submitting testing data, and what kind of environment they would want you to run it in, etc.

---

### Post by justin whitaker on 2007-02-16
> **Toxicity999 said:**
> Cossover's staff does a ton, if not most of the contribution to wine so if you really want something to run better, you should buy crossover, and file bugs or vote there, whatever they do. They're paid to hack away at wine, they might be more willing to dive right in. One problem is, they probalby all play on similar machines in an office, or at home (good ones) so, you should ask about submitting testing data, and what kind of environment they would want you to run it in, etc.

The other nice thing about them is the truth in advertising clause. :)

---

### Post by kano on 2007-02-16
I am running the same graphics card (Geforce 6600GT), and WoW plays beautiful in everywhere, including outdoor Outlands. I followed the WoW/Wine guide on the wiki, and that's it. This is without a dedicated X server, and I usually have a couple firefox windows, terminal, text editor open in the background.

The only really difference I see is that I'm using an AMD machine (Barton 2500+), but same amount of ram, etc... So maybe it has something to do with the in-game video settings?

---

### Post by justin whitaker on 2007-02-17
Ok, following up, I installed WoW and TBC via Crossover...and everything works perfectly. It feels like 30fps outdoors, a little more indoors. No scratchy sound, no real issues other than some of the HTML in the news and updates screens do not load. 

Very impressive.

Goodbye Cedega!

---

### Post by mitchbones on 2007-02-17
Try turning down your distance, that doubled my FPS. That would explain the indoors/outdoors issue.

---

### Post by Praill on 2007-09-18
I've had the exact same problem since patch 2.0. As soon as 2.0 came out WoW started freezing and the "fix" was to change your wine settings to emulate NT4.0. This worked, but with the poor FR outside. Now, after various wine releases, you can use any windows version you want, but the FR problem remains (about 8fps for me anywhere outside whereas its 30+ in windows).

I'll try this codeweavers solution and post the results. I really hope it works so I can finally (and hopefully for the last time) neglect my windows partition.

---

### Post by psychok9 on 2008-05-04
> **justin whitaker said:**
> Ok, following up, I installed WoW and TBC via Crossover...and everything works perfectly. It feels like 30fps outdoors, a little more indoors. No scratchy sound, no real issues other than some of the HTML in the news and updates screens do not load. 

Very impressive.

Goodbye Cedega!

I've tried Crossover and I had the same performance :(

---

### Post by Perfect Storm on 2008-05-04
[img]http://www.imageviper.com/displayimage/116046/0/necromancing.jpg[/img]

---

