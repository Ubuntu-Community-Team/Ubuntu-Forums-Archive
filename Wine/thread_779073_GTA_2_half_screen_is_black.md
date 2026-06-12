---
title: "GTA 2 half screen is black"
date: 2008-05-02
forum: Wine
---

### Post by JayeD on 2008-05-02
I'm new to using wine and thought that since GTA and GTA2 are free from Rockstar I'd try them. The game installed fine but whenever I start it I get a small window with the top half fine but the bottom half completely black. The game responds fine, but is obviously unplayable. Any ideas what I can do? I'm not sure what details you need so here's what I can think of...

wine 0.9.59
**Audio**
ALSA Driver
Full hardware acceleration
44100 Sample Rate
16 bits/sample
No Driver Emulation

**Graphics**
Allow the window manager to control windows
Emulate a virtual Desktop 1024 x 768
Vertex Shader Support - tried both options
Allow Pixel Shader - tried both options
Screen Res 96dpi

---

### Post by Pdennis on 2008-05-06
Same problem here.  If I disable my proprietary graphics driver, I can get as far as the menu, but the game is too slow to play.

---

### Post by krazyd on 2008-05-07
try the latest wine (0.9.61) available from the [winehq website]("http://winehq.org"). I was playing this yesterday (off my windows partition) and it worked okay.

---

### Post by JayeD on 2008-05-07
> **krazyd said:**
> try the latest wine (0.9.61) available from the [winehq website]("http://winehq.org"). I was playing this yesterday (off my windows partition) and it worked okay.

Hi, thanks I did try this but it didn't work either.
I also tried Guild Wars and that failed straight after downloading the stuff. I'm guessing it may be an issue with me having an ATI card on my laptop. WINE itself works to my knowledge since I have tried a few apps like notepad++ and they work.

---

### Post by krazyd on 2008-05-07
This might be the case - I have an nVidia card.

Unfortunately the current ATI driver support for linux is totally crap. I've given up on linux for my notebook for that reason. :P

---

### Post by JayeD on 2008-05-08
I don't really have any problems with the ATI driver other than this tbh. It runs all 3d stuff fine in Linux and is quick. Games with WINE are the first time I've had a problem and since I really play games on my 360 and Wii it's not much of a problem, just an annoyance.

I have an XP drive for the laptop too, so I may just put the games on that and swap out the harddrives when I want to game. A pain, but by no means terminal. I'm not stopping using Linux just because the odd hour here and there where I game gets in the way lol.

---

### Post by Cene on 2008-05-11
Did you get it working? I'm having a similiar problem with Wine 1.0-rc1 and Nvidia FX5200, using the propietary driver.

Initially I got GTA2 running, but the performance was just horrible. Then I found a guide for OpenGLide wrapper at Wine AppDB, and it worked well, and the performance is great, but upon entering the game bottom half of the screen is black.

Same problem existed with wine .60 and .61. On .59 and earlier I couldn't even get it to run.

---

