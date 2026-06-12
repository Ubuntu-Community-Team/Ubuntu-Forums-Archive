---
title: "World of Warcraft Frame Rate rare issue"
date: 2007-12-06
forum: Wine
---

### Post by Jasoii on 2007-12-06
I am haveing an issue with running my World of Warcraft through wine in Linux Fedora Core 5. I have updated to the latest versions of wine, and the latest drivers for my NVidia GeForce4 MX 440. I can get the game to run just fine in Windows so I know that my hardware isn't the issue. I am experiencing a framerate issue that no one else seems to be experiencing anywhere. I am getting exactly 3 FPS. I am not getting any varience on this. I can set my video setting all the way up or all the way down, I can be anywhere in the world, inside outside Orgrimmar, doesn't matter. I get exactly 3 FPS at all times. I have tried running with -opengl and -d3d. I have tried the reg hack tricks, and any other fps tweak i can find. I have tried all the fps tweaks listed in all the forums i can find and i am still getting exactly 3 FPS. Everything i have read says that WOW should be running better in Linux then in Windows. It runs just fine on this same machine with a windows install but i can't gat anything other than exactly 3 FPS on my linux install. I know I'm not running Ubuntu but i've completly run out of ideas on what could be thortlling my frame rate so. If anyone has had anything like this before, please let me know what you did to correct it. Thank You.

---

### Post by Ferrat on 2007-12-06
That is an odd problem.. 

what framerates do you get from running glxgears in terminal?

---

### Post by short3000y on 2007-12-06
i have same issue, and when i run that in terminal i get 7208.448 FPS

---

### Post by Jasoii on 2007-12-06
[Captain@localhost ~]$ glxgears
3573 frames in 5.0 seconds = 714.518 FPS
3614 frames in 5.0 seconds = 722.717 FPS
3607 frames in 5.0 seconds = 721.205 FPS
3614 frames in 5.0 seconds = 722.652 FPS
3615 frames in 5.0 seconds = 722.949 FPS
3608 frames in 5.0 seconds = 721.545 FPS
3614 frames in 5.0 seconds = 722.666 FPS
3615 frames in 5.0 seconds = 722.949 FPS
3612 frames in 5.0 seconds = 722.339 FPS
3616 frames in 5.0 seconds = 723.079 FPS
3617 frames in 5.0 seconds = 723.349 FPS
3614 frames in 5.0 seconds = 722.724 FPS
3615 frames in 5.0 seconds = 722.944 FPS
3617 frames in 5.0 seconds = 723.299 FPS
3614 frames in 5.0 seconds = 722.747 FPS
3615 frames in 5.0 seconds = 722.946 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by Jasoii on 2007-12-06
I thought it might also be helpful to explain that when i first load the game, and on the charecter select screen, It runs very smoothly. I don't get the exactly 3 FPS until I select a charecter and the world loads.

---

### Post by MacLeod9 on 2009-11-27
> **Jasoii said:**
> I thought it might also be helpful to explain that when i first load the game, and on the charecter select screen, It runs very smoothly. I don't get the exactly 3 FPS until I select a charecter and the world loads.
Sorry to bump an old post, but I am having this exact same issue in Ubuntu 9.10 karmic koala. Tried numerous suggestions with no luck. here are my specs:

**System Specs:**
Intel D845EPI board, 2.4Ghz proc, 1.5 Gb DDR RAM, and Nvidia GeForce 6200 512mb Video card with restricted drivers enabled and installed
**OS: **Ubuntu 9.10 Karmic Koala with Wine1.2

---

### Post by MacLeod9 on 2009-11-28
> **MacLeod9 said:**
> Sorry to bump an old post, but I am having this exact same issue in Ubuntu 9.10 karmic koala. Tried numerous suggestions with no luck. here are my specs:

**System Specs:**
Intel D845EPI board, 2.4Ghz proc, 1.5 Gb DDR RAM, and Nvidia GeForce 6200 512mb Video card with restricted drivers enabled and installed
**OS: **Ubuntu 9.10 Karmic Koala with Wine1.2
bump

---

### Post by brian70809 on 2009-11-28
that frame rate in glxgears is pretty low.

here's mine and I'll give my WoW fps..

110793 frames in 5.0 seconds
111029 frames in 5.0 seconds
111231 frames in 5.0 seconds
111315 frames in 5.0 seconds


In the WoTLK I get from 60-20 fps.. depending on if I'm in Dalaran etc..

Did you put the Open GL setting in the wow.cfg file?  sometimes the switch doesn't work properly when called from wine...

If you cannot set any shadows.. it's in openGL

Also.. Use the latest Nvidia drivers.. they have helped out a lot!

Good Luck!

---

