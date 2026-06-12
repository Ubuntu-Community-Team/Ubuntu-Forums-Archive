---
title: "Full screen Performance drop"
date: 2012-09-07
forum: Wine
---

### Post by HonorableGoat on 2012-09-07
First off, sorry if this has been asked before.  My search-foo is a little weak it seems.

Whenever I bring a game to Full screen mode from Window mode I have a rather noticeable drop in performance.  An example of this is when I've been playing Rage in POL it runs as smooth as silk (or Teflon, however you want to look at it) but as soon as I bring it to full screen mode the performance drops quite a bit, which is a bit of a pain. :(

I don't have a problem playing games in window mode, but it would be nice if I could have them running in Full screen mode.  it only seems to have come about since I started using Unity3d, which I would really like to stay with if I can.

The system I'm running is well above the requirements for the game so I'm at a bit of a loss.  I've included some information below if that helps :D

Ubuntu 12.04
Nvidia 304.43 drivers from the PPA repository (the default ones weren't playing to nice with dual monitors)
Intel i5 and a Geforce GTX 560

Any help would be greatly appreciated :)

---

### Post by vexorian on 2012-09-08
I would recommend against using non-2D unity while playing full screen games anyway. To me, it makes performance worse and it also seems to cause issues with keyboard detection. It is normal to have worse performance because non-2D unity uses your GPU.

You can just switch to unity 2D *while playing games*. When you want to use desktop apps, move to unity 3D.

Actually, what I do is far more extreme, I have a [terminal sesion](http://ubuntuforums.org/showpost.php?p=12153855&postcount=8), so my WINE games have full access to resources as the only app in the background is a gnome terminal.

---

### Post by HonorableGoat on 2012-09-09
Ah, that's a shame that Unity 3D does that.  I'm a fan of how it looks.  I'm assuming I'll need to log out and select Unity 2D from the login prompt to get it to load that?

(Sorry, I'm a bit of a newbie, I haven't been using Linux all that long)

Edit:
I've just tried using Unity 2D and the performance gain is crazy.  Aren't they looking at removing Unity 2D in the next release, this would make me sad...

Edit2: 
I've just made Unity2d the default session in the lightdm.conf.  It's not like the 2D version is ugly, and damn the performance loss is silly with the 3D implementation.

---

### Post by vexorian on 2012-09-09
You can turn on metacity compositing in unity-2d (or run it with mutter). This will make unity-2d use transparencies and windows and menus will have cool shadows.

It appears to me that the fault of unity's performance is 100% on compiz. When you replace with metacity or mutter and use unity-2d it gets fixed.

Edit: I am trying out two scripts to switch between Unity-2d and 'real' unity. My computer is fast so the performance drop of unity is not a big issue *most* of the time. Only when running powerful games and unity-2d although fast, has some weakneses (The global window buttons only work if you use Ambience or Radiance themes, else they fallback to some ugly little thingies. Also the menu bar "blinks" instead of fading when you put your mouse over, it is hard to notice at first (compiz unity's fade lasts little time) but after plenty of use, it becomes obvious that compiz unity's menu bar is a lot easier on the eyes.

The advantage of these scripts is that I won't have to close every single app before doing the switch. 

These are the scripts.

- From compiz unity to unity-2d:
```

#!/bin/sh
metacity --replace &
unity-2d-panel &
unity-2d-shell &

```
-From unity-2d to compiz unity:
```

#!/bin/sh
pkill unity-2d
compiz --replace &

```

---

### Post by HonorableGoat on 2012-09-11
Whoops.  Sorry I forgot to check this thread and it appears I don't have notifications setup.

Thanks for the script :)

A little concerned that the Unity3D interface causes this much of a problem.  It's a shame they're going to be removing it in a later version given the performance degradation on Wine and other apps in full screen mode (Unless I've read wrong?).  

Edit:
Oh well, maybe they'll fix performance problems and all will be well :D

---

