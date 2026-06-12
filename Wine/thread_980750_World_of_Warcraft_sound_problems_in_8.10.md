---
title: "World of Warcraft sound problems in 8.10"
date: 2008-11-13
forum: Wine
---

### Post by drytear on 2008-11-13
Hi, i just upgraded from 8.04 to 8.10 and now my sound in WoW with wine is choppy. Any idea how to fix it? Used to be fine before the upgrade.

---

### Post by davebgimp on 2008-11-13
Same problem here.

I tried increasing the sound buffer size in wtf.config, but the stutter stays.

---

### Post by cozmoz on 2008-11-14
I have the same problem, it's very annoying. I hope there's an easy way to fix it.

---

### Post by binbash on 2008-11-14
disable pulse audio

---

### Post by drytear on 2008-11-14
i have everything set on alsa, even wine is set to use alsa for WoW. can pulse audio still be the problem ?

---

### Post by stimpak on 2008-11-14
its pulseaudio that creates all that shuttering.

open terminal and type 

```
killall pulseaudio
``` 

that should take care it

---

### Post by cozmoz on 2008-11-14
that did it for me :)

---

### Post by drytear on 2008-11-14
i did another thing, switched everything to pulse audio, configured wow in wine to use OSS and ran it with padsp wine <WoW path here> , and it works. One thing i didn't test it's if i can have multiple sound while playing WoW.

---

### Post by OMJD on 2008-11-14
I'm also having this issue. 

> **stimpak said:**
> its pulseaudio that creates all that shuttering.

open terminal and type 

```
killall pulseaudio
``` 

that should take care it

Will I need to do this every time I restart the computer?

EDIT: Appears that I need to do it every time. Is there a way of automating this?

Cheers.

---

### Post by stimpak on 2008-11-15
the other way around is ...to emulate an emulation heh..

open the terminal and :

```
padsp winecfg
```

then go at audio and choose **OSS**

then add the padsp prefix at your wow launcher

eg it should read

```
env WINEPREFIX="/home/nikos/.wine" **padsp** wine "C:\Program Files\World of Warcraft\Launcher.exe"
```

---

### Post by munmon on 2008-11-16
> **drytear said:**
> i did another thing, switched everything to pulse audio, configured wow in wine to use OSS and ran it with padsp wine <WoW path here> , and it works. One thing i didn't test it's if i can have multiple sound while playing WoW.


Yep. It does play other sound as well while running WoW in the Background

---

### Post by Mikethk on 2008-11-19
I did it in a easier way :)

WOW works on OSS. So go to Wine configuration and put audio to only OSS.

If you "sudo killall pulseaudio" you kill all programs using pulseaudio, which is boring :)

So instead you want to configure where ALSA has to work instead of pulseaudio on your Ubuntu computer. 
Go to system - preferences - pulseaudio preferences and disable all the ****. 

Now go to system - preferences - sound and put it on Analog (ALSA) on 3 of them. Cause you want your "music and movie" to be using pulseaudio. 
(---- I thogth that i could offcourse use OSS instead of ALSA here, but then the sound was bad in WOW-----)

When i did these changes exalty like this, it all worked for me. 

What i concluded was, that I need pulseaudio, ALSA and OSS to make all the stuff work. :lolflag:

---

### Post by k1ngb0b0 on 2008-11-20
> **stimpak said:**
> the other way around is ...to emulate an emulation heh..

open the terminal and :

```
padsp winecfg
```

then go at audio and choose **OSS**

then add the padsp prefix at your wow launcher

eg it should read

```
env WINEPREFIX="/home/nikos/.wine" **padsp** wine "C:\Program Files\World of Warcraft\Launcher.exe"
```


This worked great for me, the choppiness is gone!

Edit: Fixed my other problem too :)

---

### Post by Emanuele_Z on 2008-12-01
Acutally I had to **remove** pulseaudio, because, as Stefan Dosigner pointed out ( [http://www.mail-archive.com/wine-devel@winehq.org/msg42322.html](http://www.mail-archive.com/wine-devel@winehq.org/msg42322.html) ), it is not able to provide direct hardware access, hence a huge FPS drop when the process (pulseaudio) is running.

For example I was running all MAX (but no AA and normal shadows) in Grizzly Hills and my FPS were:
with PA process running: 18
without PA process running: 28
As you can easily notice the game **isn't playable with 18 FPS but is with 28 FPS**.

After that I tested it another time and everything was confirmed again.
So I just uninstalled PA.

Now the FPS is even slightly better than 8.04.

my hardware is:
nVidia 8600 GT Mobile 512
Intel Core Duo T7700
2GB RAM
my screen resolution is:
3600x1280 (got 2 screens)
my WoW window resolution is:
1920x1280 (full HD)
the graphics are maxed out but no AA and no fancy shadows.

---

### Post by Evilarcher2000 on 2008-12-02
> **stimpak said:**
> its pulseaudio that creates all that shuttering.

open terminal and type 

```
killall pulseaudio
``` 

that should take care it

That solved the audio problem indeed :)
Unfortunately, it left me with one problem: The game is _still choppy!_
The audio sounds great now, and I'm thankful for that, but the login screen is moving frame by frame.. Does anyone possibly have a solution for that?

---

