---
title: "Trouble with Warcraft 3"
date: 2008-03-15
forum: Wine
---

### Post by forw4rd on 2008-03-15
I recently switched to ubuntu gutsy and I was trying to play warcraft 3 with wine. This really isn't a big problem, but I can't seem to minimize or alt-tab out of warcraft 3.  I run w3 in full-screen, and no matter what I try to do to go to another window, w3 just stays on top and doesn't do anything else.

I've tried using ctrl-alt-d to minimize everything, but w3 stays up and I can't see my desktop.  Even alt-tab and ctrl-alt-tab don't do anything.

---

### Post by Larrxi on 2008-03-15
Atleast you can run Warcraft 3 in windowed mode. That allows you to minimize it.

Just run Warcraft with the flag -window.

wine ~/.wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -window

or if you are in the directory

wine Frozen\ Throne.exe -window

---

### Post by forw4rd on 2008-03-16
Well, now I can minimize w3, but I have another problem.  My mouse cursor doesn't stay locked in the warcraft window, so I have trouble when I try to move the view.  I've tried changing the wine configurations, but my mouse won't stay in warcraft 3.

---

### Post by mad_max0204 on 2008-03-16
move screen with keyboard. there is also wine option to let apps to capture mouse. try winecfg

---

### Post by Coretron on 2008-06-13
You cant use arrows cause you need to hotkey.

---

### Post by Coretron on 2008-06-13
Interesting... I tried opening wc3 on a different workspace and then when i ctrl+alt+<left> to change workspaces i get a normal desktop like we'd hope. but then when I try to go back to workspace 2 it's as if the game isn't even open. Under sysmonitor it still shows it running.

---

### Post by illumi on 2008-06-13
Just open it in the first work space and swich to a new one if you need to do anything, works perfectly for me.

---

### Post by hsushi22 on 2008-08-19
heyz, i recommend toggling on/off compiz. there's a program called compiz-switch that helps with scrolling. On a side note, you won't be able to alt-tab, still... 

i've tried the maximized window mode, but the top bar is really annoying. is there a way to make that disappear when maximized? thanx in advance.

---

### Post by shae on 2008-08-19
I suggest you take a look at the wine version in my signature.  It should allow you to minimize/maximize as well as host with compiz on or off.  Plus it has snoopy to help you with hosting (pinging, banning, autorefreshing, etc).

---

### Post by k1ngb0b0 on 2008-08-20
> **illumi said:**
> Just open it in the first work space and swich to a new one if you need to do anything, works perfectly for me.


Can you give a little more information on your setup?  This is exactly how I want my game to work (and how I have it working with WoW) but I can't get it to work with War3.  I have the same problem as the OP.

---

### Post by Ng Oon-Ee on 2008-09-01
Instead of toggling Compiz or using an alternate desktop (though the second option supposedly helps with performance, i've always disliked it for some reason), why not just tweak Compiz such that things run reasonably perfectly without all the rest.

I've posted something [here]("http://ubuntuforums.org/showthread.php?p=5703907#post5703907") which would hopefully satisfy most people's requirements.

---

