---
title: "trying to run team fortress 2 in wine"
date: 2008-04-21
forum: Wine
---

### Post by nucnuc on 2008-04-21
I installed steam and downloaded team fortress 2.
When I tried to run the game it would crash after the opening video, but before the menu shows up.

I updated wine following this guide [http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)
Do I need to reinstall steam after updating wine (the steam part still seems to work)?

Now when I try to start the game it freezes in the same place. I cannot get to the terminal output, because the game is frozen. Is there a way to stop the game that doesn't involve shutting the computer down?

Wine is version 0.9.59 (tried both XP and 2000 other settings are default. I think wine was version 0.9.46 before, but I'm not sure)
video card is ati radeon x1650 pro - Drivers are whatever was automatically provided with the restricted drivers manager. Are these recent? or is there a way to manually update?
Do I need to install DirectX, or is this part of wine?

If I change the version of windows that wine is not emulating do I need to reinstall steam/tf2? (if so is there a way to do this without having to redownload the game each time?)

Has anyone else had this problem? How did you fix it?

---

### Post by nucnuc on 2008-04-21
I have sound now, so I can tell that the game doesn't actually freeze.
I can hear when I mouse over menu items, but I cannot see anything. The screen after the video turns completely black.

The console outputs this:
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
over and over and over again

---

### Post by nucnuc on 2008-04-22
I downloaded the most recent ati driver, and now the menu loads, but the game doesn't.

I can join a server, download whatever, watch the map intro movie, the game freezes with a partially loaded view of the map (before I pick a team)

I can see the center control point of badlands, and some of the scenery. The sky and some of the other scenery is black, and the game doesn't respond.

---

### Post by nucnuc on 2008-04-22
Yay I got it to work
used -dxlevel 81 to get it to work. (didn't work before, but did after I updated the drivers)

I have some minor problems
[LIST=1]
[*]It looks and runs bad (which I kind of expected). 
Are there any tweaks I can try that might improve the performance?
[*]The screen goes black (except for the particle effects of dust/explosions/grenades) randomly. Sometimes it just happens for a second, and sometimes it happens for the rest of my life.
[*]The killcam thing shows something that appears to be distorted code rather than the guy who killed me.
[*]Only 3 buttons on my mouse work. Is there a way to make it so they all work (actually this seems to be true with the main part of ubuntu too...)?
[/LIST]

The awesome part:
The microphone works. On appdb it said that it wouldn't. Did it get fixed, or am I just lucky (or rather less unlucky, considering all the other problems my computer has been giving me)?

---

### Post by perixx on 2008-09-06
"Yay I got it to work 
used -dxlevel 81 to get it to work. (didn't work before, but did after I updated the drivers)"

What do you mean by this, how'd you do it? Still running wine 0.59? You updated you graphic card's drivers? To which version? Did you install DirectX or used the original dll's?


I'm using an x1950gt, which turned out to be somewhat problematic from the beginning, but from what I've seen in forum posts - seems like most ATI users and many Nvidia users are having big problems with TF2 and wine...

I can't get any more than what you've described (invisible menu, black screen) or the loading background pic, when using DX-level 70 (for 1-2 secs, then crash). Tried various Wine-versions with all kinds of settings-variants via 'Playonlinux' as well - no workie!

Thanks for any hints...

Btw., you could maybe add -heapsize [halfyourmemory] to the starting parameters of TF2, e.g.:
-heapsize 512000 (at 1GB RAM)
If you haven't already tried that. 

greetz,


perixx

---

