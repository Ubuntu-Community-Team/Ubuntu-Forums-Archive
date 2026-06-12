---
title: "Half Life 2 frame rate issue"
date: 2008-04-01
forum: Wine
---

### Post by HunterK on 2008-04-01
Hey all, I'm trying to run Half Life 2 and all expansions. (I've honestly never beat Ep1+Ep2!) I installed via Orange Box DVDs.  It opens and also runs just fine.  I've also installed the March2008 Direct X 9 which helps with things. (I do also use  a script that runs steam in its own  X server.)

I just want to know if there is anything else I can do to improve my frame rate? A tweak here, a tweak there....

 It seems like wide open areas kill my FPS.  I know for a fact that my PC can run this game flawlessly.

Quick Specs:
Athlon64 3500+
2GB ram
nVidia 6800GT
Gutsy 7.10 with latest nVidia drivers installed by Envy.

---

### Post by HunterK on 2008-04-02
Ok, I tried a bunch of things and seemed to get things working ok.  It all left me a little confused though.

I ended up using the following command to launch Half Life 2:

```
WINEDEBUG=-all wine steam.exe -applaunch 380 -novid -dxlevel 80 -refresh 75 -width 1280 -height 1024 -heapsize 512000
```

This worked, but it seemed like my FPS was capped at 30.  "cl_showfps 1" showed 31 all of the time.  I thought that was weird, so as a last ditch effort, I changed all of the video settings to their lowest value.

FPS shot up to 75 and stayed there! (Vsync was working and everything was butter!)

I then began to increase each video setting until I found out what was causing the slowdown.  I ended up with all of the same max settings as before but the FPS was still at 75.  I don't get it!! :confused: 

I will continue to mess with this when I get home from work.

---

### Post by Termy58 on 2008-04-02
Your settings are already kinda low, I would try dx level 7. But you won't be able to even attempt EP2

---

