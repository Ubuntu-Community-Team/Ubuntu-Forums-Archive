---
title: "Starcraft + Wine= Cannot get mouse to stay on game"
date: 2008-09-14
forum: Wine
---

### Post by bexamous on 2008-09-14
Argh I've been trying to play Starcraft and I'm SOOOO close.... almost better than Windows.... except I cannot get the mouse to stick to the game which makes it insanely hard to move around the map.

winecfg setting "Allow DirectX apps to stop the mouse leaving their window" does nothing.

I've tried everything I can think of, there must be some way to fix this.

Ideas?

---

### Post by syntaxers on 2009-06-27
I'm having the same problem. Any assistance would be great!

I am running Wine using a virtual desktop in windowed mode with the 'Allow DirectX apps to stop the mouse leaving the window' option checked.

---

### Post by jhoeijao on 2009-06-27
> **syntaxers said:**
> I'm having the same problem. Any assistance would be great!

I am running Wine using a virtual desktop in windowed mode with the 'Allow DirectX apps to stop the mouse leaving the window' option checked.

Try the latest wine version 1.1.24. I'm using starcraft portable version with no problem with it.

---

### Post by donkyhotay on 2009-06-27
You could try playing starcraft fullscreen, mouse can't leave the game then! (c:

---

### Post by Sugi on 2009-06-27
I couldn't understand playing StarCraft without Full screen mode for any reason specially on my 1920x1080.  Maybe your setup isn't as big as mine, but wouldn't full screen be better for playing Starcraft anyways?  And the last I heard, **winecfg setting "Allow DirectX apps to stop the mouse leaving their window" does nothing.** That feature has been broken for ages.

Try either 1.1.24 with windows mode or try full screen and get back to us.

Sugi

---

### Post by del_diablo on 2009-06-27
> **donkyhotay said:**
> You could try playing starcraft fullscreen, mouse can't leave the game then! (c:

It would, where there not for the chances of when you shutdown that it will scale down to starcrafts size(600x400 is it?) and there is nothing to do with it.
If somebody knows a way to forcefully stretch it could work, scaling it fullscreen without it being fullscreen that is.

---

### Post by delerious010 on 2009-07-03
Fullscreen aint working for me either.

I'll have a 640x480 fullscreen window taking up my entire 1650x1080 screen .... however scrolling to the edges will reveal the rest of my super-zoomed in desktop.

For the previous poster .. ctrl+alt++ or - to change resolutions to those previously defined in xorg.conf. If it's auto-detecting you're screens resolution, it'll only have the 1 mode to return to.

---

### Post by elitenoobboy on 2009-07-06
There are a couple of hacks out there that can increase SC's resolution.
[http://www.youtube.com/watch?v=bmJPAFCE0F0](http://www.youtube.com/watch?v=bmJPAFCE0F0)
I have tried them, and could only get one of them to work, once. After I restarted SC, it would just crash with wine.

Instead of manually changing the entire desktops resolution, you could also try compiz's enhanced desktop zoom plugin. After telling it not to center the screen on the mouse, the scroll would stay inside the window better. Compiz doesn't have input redirection, so making the window bigger isn't possible with it at this time.

---

