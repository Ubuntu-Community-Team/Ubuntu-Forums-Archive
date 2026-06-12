---
title: "is wine running out of graphics memory ?"
date: 2012-05-22
forum: Wine
---

### Post by Shadowstripe on 2012-05-22
I have a gts250 512mb and I boot between 64 bit editions of win7 and xubuntu (xubuntu I like the interface ;))

anyways here comes the oddity I tried 2 games on wine the first played fine for a while but after 4 or so hours in at random intervals the framerate would just tank to like 1 frame every couple of seconds with lots of tearing at the top of the screen.

I also tried mass effect 3 and played it all the way through with only 1 minor graphical glitch showing up at a specific point but it wasn't game breaking that lead me to believe the first game I tried was a one off until I tried skyrim. 

same thing at random points the frame rate just dies but if left long enough sometimes springs back into action, after upgrading drivers and doing a bit of research I found someone else with the same problem that was solved by upgrading to a new graphics card he said the old card was running out of memory ?

so after reading about the memory thing I set to tweaking settings putting textures etc. to lower than I have in windows (to save memory) the problem went away so I added a few mods.

adding less blocky faces and better hairstyles then scrolling through them in character creator was all it took to kill the framerate again but it sprung back to life after creating/saving the character. (at 1 fps) 

my questions

is the assumption I reached correct and the problem is as simple as the card running out of graphics memory then killing the frame rate ?

even with all the hair mods, and high definition faces ,a high quality body and the official high definition textures and generally all round higher settings it runs fine in windows and I suppose gets a little slower the higher I go but never just randomly dies or drops to a 1 fps on windows, what is win7 doing that wine is not?

is there anything to stop this happening? (apart from playing in win7 I wanted something to try get me using linux more)

I was considering upgrading to a dx11 card since nvidia have released a new set of chips or maybe wait till they come down a little in price

Thanks

---

### Post by Shadowstripe on 2012-06-06
update

upgraded my card to a 560 ti (long overdue upgrade imo) now and again the framerate will still die on me (less than before) the last time was when equipping some new items in an indoor location so memory usage should not be that high.

to fix the game I have to use the console to zone to a different cell and back (which is kind of annoying and hard to do running under a fps).

any suggestions on how to fix this or how to even start troubleshooting this ? there isn't anything unusual on the console when it happens.

Thanks

---

### Post by Dlambert on 2012-06-07
[LIST=1]
[*]In a terminal, type wine regedit and hit enter
[*]Open the tree on the left to the section where you need to add it (e.g., HKEY_CURRENT_USER\Software\Wine)
[*]Select the section you are going to add the new key to (e.g., Wine)
[*]Right click and select New->Key
[*]VideoMemorySIze (Case Sensitive)
[*]Hit enter
[*]Then right click and hit modify, then enter the MB of vram for your card.
[/LIST]

---

### Post by Shadowstripe on 2012-06-07
thanks I will give it a shot and see how it goes ;)

---

### Post by Dlambert on 2012-06-08
ALso you could do a variety of tweaks such as, GSGL=disabled, DirectDrawRenderer=opengl, OffScreenRenderer=fbo. Source: [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

