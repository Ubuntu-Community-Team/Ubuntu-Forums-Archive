---
title: "Help with World of Warcraft using Wine"
date: 2007-12-15
forum: Wine
---

### Post by nrockway on 2007-12-15
I've gotten to the point of the installation where I need to edit the Config.wtf. Apparently, I need to log into a character for this folder to be made. 
However, when I open WoW to log into a character, it plays the movie then closes out. 
Thanks.

Forgot to mention: I'm running Wine 0.9.51

---

### Post by nrockway on 2007-12-16
Bump

---

### Post by foolios on 2007-12-16
Does anyone have a link to the world of warcraft installation for wine/ubuntu? There are so many posts about the subject but I need one that is the tutorial on how to do it.

Thanks in advance.

---

### Post by Wiebelhaus on 2007-12-16
IT's all over the board , use the search function and you will be rewarded also....

Look into Codeweavers crossover.

---

### Post by foolios on 2007-12-16
Ok, after reading the tuts on this. Everything went pretty good.
I can get the game started but it moves one frame every 5 secs. Really really slow. I did the tweaks in the cfg file and the wtf file.

I do get sound, but when I run the winecfg I noticed the following in the terminal:
foo@foo-desktop:~$ winecfg
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:jack:JACK_drvLoad error loading the jack library libjack.so.0, please install this library to use jack
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

I can turn the sound off and I've tried emulation. I don't think it's about the sound tho.

I think it's because of the video.
When I run:
glxinfo | grep rendering

I get:
foo@foo-desktop:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I used envy to install the ati drivers. The card is listed as ati after having done so.

What can I do now?

THanks so much in advance.

---

### Post by merlyn on 2007-12-17
[Here]("http://ubuntuforums.org/showthread.php?t=579378") you are.

---

### Post by foolios on 2007-12-17
That's about where I'm at, but I'm experiencing the problems in my previous post.

---

