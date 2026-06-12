---
title: "World of warcraft on hardy so far"
date: 2008-05-26
forum: Wine
---

### Post by Castlef on 2008-05-26
im just giving a small review here of my experience with it

I just recently installed hardy a week ago.. after a long hiatus of not using linux since about feisty or so. The reason is gaming of course and just tired of booting into windows so i just stayed there.

After hardy installed successfully.. i updated my graphics drivers so i would be able to play. I using wine 1.0 RC 2

Everything installed perfect following the howto wiki about wine and WoW. i had to run a command to unhide the exe on the CD... after that it installed normally along with burning crusade.

When i first logged in my frame rate was pretty low.. but after switching to openGL mode and making the registry hack.. now its pretty much on par with the windows version.. and i have the graphics settings about the same with the same resolution... the only minor qualm i have is it needs a little more anti aliasing due to jaggy lines but i suppose i can fix that through an nvidia control panel if install one.

My biggest problem by far however... is sound. Upon booting up hardy for the first time ... i heard the little sound at the log in prompt... but then as it went into the desktop.. there were no familiar drums... no sound at all. I have on board sound on my motherboard but im using a plain old Sound blaster live value... which is something like an 7-8 year old card... because a dedicated card simply sounds better than onboard... more power or something .

The sound is completely random.. the first time i loaded wow i actually heard sound.. and it worked. the next time it didnt... then it did... and now i just tried and there is no sound again. I have no idea whats going on there but if there is a fix.. i hope there is one for pulse audio because i dont want a bunch of different sound servers.

One thing i noticed was that my addons worked... i was pleasantly surprised. I installed healbot in the correct directory and it worked like a charm

However a minor annoyance.. when binding hot keys in the game... i could not bind alt + left click or alt + right click with healbot. It is as if the alt key is overrided because the desktop or window manager has some use for it or something. it doesn't work.. and i need to get that working.

Another minor annoyance is the mouse... it doesn't seem as smooth as in windows. as if its not sampling as often or something. i had to turn the sensitvity down some because it jumped around a little and still does.. just a little but enough to make it inaccurate sometimes.

another thing is i will need to work on the hotkeys on my house.. like the left and right tilt on the mouse wheel....

If i can get my mouse hotkeys working... my sound working... then i should be able to play wow from windows even during raids i think

I installed ventrilo and it worked like a charm... except since sound doesn't work my input doesn't work either. im not sure how to get my input working..... and also i set up the push to talk on ventrilo but i didn't see the green light for my speaker light up. i assume thats because input is still not working... but i would have to get that to work too. 

one other thing that would be nice.. i usually press the windows key to minimize out of wow to look up quests or whatever on the web browser. it doesn't work in ubuntu and alt tab doesnt seem to work.. it just makes the top and bottom bars visible but as soon as i click anywhere the game takes over again. i suppose the solution is to play in windowed mode somehow which i am sure is possible. Anways thanks for reading!

---

### Post by mccord on 2008-05-26
> **Castlef said:**
> one other thing that would be nice.. i usually press the windows key to minimize out of wow to look up quests or whatever on the web browser. it doesn't work in ubuntu and alt tab doesnt seem to work..it just makes the top and bottom bars visible but as soon as i click anywhere the game takes over again. i suppose the solution is to play in windowed mode somehow which i am sure is possible. Anways thanks for reading!
you just have to get used to virtual desktops ;) 
so much faster than alt-tabbing or minimizing on windows...

under kde ctrl+Fx switches to another workspace
under gnome i think it was ctrl+alt+left/rightcursors to switch (someone correct me if i'm wrong, haven't used gnome for a while)
rightclick the application in the taskbar should allow you to send that application to another workspace

---

### Post by strongboww on 2008-05-26
i dont have a fix for the sound but for thehotkey prob: 

the problem is that the "alt" key is bound, as you said, but its not the fault of wine, its yours, just unbind or bind it somewhere else in the preferences menu "keyboard shortcuts"

and find some mouse drivers for whatever you use
[http://www.lomoco.org/](http://www.lomoco.org/)

---

### Post by Vrekk on 2008-05-27
> **mccord said:**
> 

under kde ctrl+Fx switches to another workspace
under gnome i think it was ctrl+alt+left/rightcursors to switch (someone correct me if i'm wrong, haven't used gnome for a while)
rightclick the application in the taskbar should allow you to send that application to another workspace
To change workspaces it is ctrl + left arrow/ right arrow

---

### Post by zozoman on 2008-08-08
I went through hell the last 2 days trying to get my sound to work properly too. I recently just got it to work well, I'd say about 2 hours ago. The simplest thing you can do is in shell write

```
alsamixer
```

In the top left there will be the sound card name. If it isn't the one you want to use that is why you are having sound problems, or at least that is what I experienced.

What I had to do to fix this was to type

less /proc/asound/modules```

```

I had 2 outputs, the first one was the card I didn't want to use and the second was the one I wanted to use. 

Once I had the outputs I wrote them down and then had to use the command
```

sudo gedit /etc/modprobe.d/alsa-base
```

Then I looked for the line that said something like:
# Prevent abnormal drivers from grabbing index 0

and in the list below add
options snd_whateveryourcardnameswere index=-2

After I rebooted I heard the Ubuntu drums and everything started to work nicely.

I found this help from this website
[http://www.linuxquestions.org/questions/linux-hardware-18/default-sound-card-in-ubuntu-564006/#post2942716](http://www.linuxquestions.org/questions/linux-hardware-18/default-sound-card-in-ubuntu-564006/#post2942716)
I hope I saved you the headache I got from this experience!

---

### Post by Mahinva on 2008-08-08
> **Castlef said:**
> 

One thing i noticed was that my addons worked... i was pleasantly surprised. I installed healbot in the correct directory and it worked like a charm

Another minor annoyance is the mouse... it doesn't seem as smooth as in windows. as if its not sampling as often or something. i had to turn the sensitvity down some because it jumped around a little and still does.. just a little but enough to make it inaccurate sometimes.


Addons will work with no problem because Wine does not handle them at all. So, if you put your addons in the proper file, they'll work fine. If an addon is giving you problems, it's nothing to do with Wine - contact the addon author. :)

The mouse is sluggish because you are running in OpenGL mode. In this mode, there is no ability in the Video options menu to enable "Hardware Cursor". This means that right now, the game client is drawing the mouse's position whenever you move it. If it were possible to enable Hardware Cursor, then the cursor would be moving a lot faster. If you notice your FPS go rather high in some areas, you may notice that your mouse is less sluggish too. If the game runs better in OpenGL than Direct3d (d3d), keep it in OpenGL. Some people notice the game runs better for them in d3d, and Hardware Cursor is an option available in this mode too.

Blizzard just doesn't want to enable Hardware Cursor in OpenGL mode if you are running the Windows version of the game. If you had the mac version and were running in OpenGL, you could enable Hardware Cursor. I have no idea why Blizzard made this choice, but I haven't heard that they are going to change it.

---

