---
title: "Fallout New Vegas graphics option question."
date: 2012-10-24
forum: Wine
---

### Post by Sixgun77 on 2012-10-24
When I go into options in the FNV launcher the default setting is ultra high. Once I set the resolution, that part stays set. Every time I open advanced options after exiting the game the shadows, water reflections, draw distances, and LOD settings are reset to minimums. Also, all the dropdown menus in these advanced options are blank.

I get the same results with all the different drivers that are available in the additional drivers program in the system settings. The FPS are definitely playable, but I could swear there's an almost imperceptible leg, just enough to get you waxed in a FPS game, but not enough to matter in most other types of games. I'm running Steam through Playonlinux, and installed FNV through Stream since installing from the disc resulted in not being able to launch the game.

Is there something I need to change in Wine? FNV runs flawlessly at max settings on this computer in Win7. Here are the system specs:

Ubuntu 12.04.1 desktop 64bit
Asus/RoG Rampage 2 Extreme
6 gigs DDR2(can't remember the speed, but I want to say ddr2 1200)
Maxtor 500gb HDD
3 Nvidia 470 GTX graphics cards
Core i7 Quad core w/ HT 3.0
BFG 1200 watt PSU

---

### Post by Dlambert on 2012-10-24
Try editing the Settings file rather than the GUI, also try running in Unity2d and see if that improves your fps.

---

### Post by Dlambert on 2012-10-24
Also, see here: [http://ubuntuforums.org/showthread.php?t=2075382](http://ubuntuforums.org/showthread.php?t=2075382)

---

### Post by Sixgun77 on 2012-10-25
Ok thanks. I'll need to read up on how to find and edit that file. I also need to find out what Unity is. This stuff is all new to me, but I'm jumping in with both feet. Last night I wiped windows off my HDD completely, but might put back a minimum space install so I can watch my blu-ray 3d discs.

---

### Post by xREDEMPTIONx on 2012-10-25
You can find the settings file where Fallout keeps its saved games. Something like- /Documents/My Games/Fallout NV/Fallout.ini    or FalloutPrefs.ini, these files contain all the settings for the game and you can manually change what you need. Be careful though and make backups. 

  I have the missing text in the Fallout and Skyrim launcher, I've looked but haven't found a fix, yet:) 

  Something to note for performance- I have to manually set my video card memory in Playonlinux because it doesn't automatically detect it. Go to the configure window, select the virtual drive on left hand side then click display tab to find the video memory size selector.
  
Also, Unity(3d) is the default desktop environment for Ubuntu. If you log out and click the little gear by the login box you should also see Unity2d. This session uses less resources than Unity3d and thus should show increased performance in your games. You can also use gnome-panel to get even better performance. (type sudo apt-get install gnome-panel in terminal or search gnome-panel in software center) log out and select gnome classic (no effects). Unity3d is really the worst desktop environment for playing games right now in Ubuntu.

---

### Post by Sixgun77 on 2012-10-25
Thanks for the clarification. In Playonlinux do you put in the amount of memory for all three gfx cards(3 gigs) or just the 1 gig that each individual card has?

---

### Post by vandorjw on 2012-10-25
Put down 1GB
SLI does not increase the amount of video ram
> 
There is two ways that SLI works.

One is called split frame rendering - this is where the frame it split horizontally in half, which splits the workload 50/50 for each card. It intelligently splits the workload based on the geometry of the frame, for example if there is little to render on the top half (e.g. sky) and a lot on the bottom (smoke, debris, ground textures) the dividing line will move to balance the workload between each card. Split frame rendering is pretty poor at scaling the work when compared against alternate frame rendering (below).

The second is called alternate frame rendering. Each card renders full frames, but in sequential order, for example the master card might process even frames (2,4,6) while the slave card processes odd frames (3,5,7). When the slave card finishes work on a frame the results are sent to the master card, usually via the SLI bride (as described above). Theoretically this should result in the rendering time being cut in half, which should technically linearly scale the performance by double. This is not often the case in practice though, depending on drivers, games, etc.


I do not know how it works in linux, whether you use split-frame-rendering or alternate-frame-rendering, but as you might see, each card needs the same information as every other card to do its job, so even though you have 3 cards, each with 1GB, they do not share their memory with eachother.

EDIT: Please see attachment. Your available video memory may be even less.
Look at your "Total Dedicated Memory:"

See screenshot attached

---

### Post by Sixgun77 on 2012-10-26
Thanks very much everyone. This is kind of a struggle for me because I don't know much about code or software, but I'm having a lot of fun learning all this stuff.  I have 4 options at the relog screen:
Gnome Classic
Gnome Classic(no effects)
Ubuntu
Ubuntu 2d

Are the 2 gnome settings what you meant by "gnome-panel"? I'm guessing GC no effects or Ubuntu 2d are going to be my 2 best options.

edit: I just reread one of the posts and answered my own question.   Also, is there any drawback to launching steam on it's own instead of going through playonlinux and launching it via Wine?

---

