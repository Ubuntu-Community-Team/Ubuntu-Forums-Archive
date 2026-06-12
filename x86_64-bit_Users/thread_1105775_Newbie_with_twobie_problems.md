---
title: "Newbie with twobie problems"
date: 2009-03-25
forum: x86 64-bit Users
---

### Post by joshjh on 2009-03-25
Ok so i am new to ubuntu and i have 2 problems. First i do not have sound. The only thing i hear is a quiter bip bip bip kind of like the drum noise over and over again. Second i do not have the cube effect i have selected the visual effect "extra" and have the wiggle but no cube just the normal pop up on the screen with 4 boxes. The more important thing is the sound. I have search for a cure and have come up empty. Any help would be great. Thanks

---

### Post by stumbleUpon on 2009-03-25
For sound problems, see these two links

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)


To get the cube effect, install compiz config settings manager

sudo aptitude install ccsm

then open that by typing ccsm in a terminal. Go to Effects. Enable Desktop cube and Rotate Cube. Middle click on desktop and drag around.

---

### Post by Sef on 2009-03-25
> To get the cube effect, install compiz config settings manager

sudo aptitude install ccsm

then open that by typing ccsm in a terminal. Go to Effects. Enable Desktop cube and Rotate Cube. Middle click on desktop and drag around.

An easier way to get Compiz Config Settings Manager is this:

Applications > Add/Remove > Show: All Available Applications > Search: CCSM > click on the box next CCSM > click apply changes > apply > close.

---

### Post by joshjh on 2009-03-25
Thanks a bunch i have cube kinda effect. I was looking on youtube and i saw that someone had the cube effect kind of zoomed out a guess and when you move a window between to desktops it show the whole cube. Right now it looksl like when you use tapmac. Also still working on the sound thing ive tried acouple things from one link but no luck. I look into it more when i get home. Thanks again

---

### Post by 3Miro on 2009-03-25
> **joshjh said:**
> Thanks a bunch i have cube kinda effect. I was looking on youtube and i saw that someone had the cube effect kind of zoomed out a guess and when you move a window between to desktops it show the whole cube. Right now it looksl like when you use tapmac. Also still working on the sound thing ive tried acouple things from one link but no luck. I look into it more when i get home. Thanks again

Look at the different compiz menus, the list of options is enormous. You can control zoom, transparency, wallpapers and so on and so on. Just have to dig around to find it.

---

### Post by joshjh on 2009-03-25
Ok bigger prob not. I tried the "if all else fails tab in the second link and that did not work either. Now what i type aplay -l it says no soundcard found. How can i fix this. Also the cube looks a little better but i want it to look like the one in this video about 1:50 in [http://www.youtube.com/watch?v=7QyyC4LRoYI](http://www.youtube.com/watch?v=7QyyC4LRoYI)

Please help with my sound prob mainly. Thanks

---

### Post by joshjh on 2009-03-25
bump.... i could really use some help here.

---

### Post by 3Miro on 2009-03-25
Don't know about the sound, could be a driver issue. Check if your sound card is supported under Linux (i.e. has a driver). You can try booting form the LiveCD to see if there is sound then, it might be the case that you messed up a setting somewhere.

For the Cube, you have to increase the zoom level, give it some transparency (decrease opaque or whatever they call it) and put some wall papers for the background behind the cube. It is all in the menus in the Desktop section of the compiz settings.

---

