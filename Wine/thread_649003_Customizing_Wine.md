---
title: "Customizing Wine"
date: 2007-12-24
forum: Wine
---

### Post by Ertai87 on 2007-12-24
OK, so I'm trying to customize Wine to work like Windows on Linux.  Here's what I want:

I have a widescreen monitor on my computer.  In Windows, when I played fullscreen games (the one I'm playing is Warcraft 3), it would put the game window in the center of my screen and have 2 black bars down the sides so that my mouse couldn't exit that screen.  Also, I could minimize the window by using ALT-TAB.

So far, I've found that I can either have fullscreen, stretched to the sides of the screen and destroying the aspect ratio, or windowed mode which doesn't lock my cursor and also can't be used in maximum resolution due to the top bar, or I can have fullscreen maintain aspect ratio mode which puts my game window at the top-left corner of my screen instead of in the middle.

In all cases, I am unable to minimize the game window by using ALT-TAB, and when I play the fullscreened version, other running applications have processes that cut through my game window which is kind of distracting.  In the windowed case, every time I click with my mouse, the screen flashes.

Is it possible to do what I want?  And if so, does anyone know how?

---

### Post by Mellowdrone on 2007-12-24
> windowed mode which doesn't lock my cursor

I don't intend to be the be-all in terms of answering your post. I'm somewhat experienced with Wine for a few applications, but none in terms of gaming.

Winecfg has an option called 'Allow DirectX apps to stop the mouse from leaving their window' or something to such an effect under the Graphics tab I believe. Have you given this a shot for windowed applications?

---

### Post by Ertai87 on 2007-12-24
OK, that seems to work for locking the cursor in windowed mode.  Anyone else have solutions for any of the other problems?

---

### Post by FRuMMaGe on 2008-03-09
I would very much like to maintain the aspect ratio.

Any help would be appreciated.

---

