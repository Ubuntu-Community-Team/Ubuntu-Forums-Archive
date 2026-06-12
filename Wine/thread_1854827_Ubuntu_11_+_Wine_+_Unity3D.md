---
title: "Ubuntu 11 + Wine + Unity3D?"
date: 2011-10-05
forum: Wine
---

### Post by Alan_D. on 2011-10-05
Hi guys,

I'm new to Ubuntu 11, but I used a couple of other GNU/Linux distributions before.

What I would like to do is to run the Unity3D engine (unity3d.com) (not to be confused with the Unity desktop manager!) on my Ubuntu using Wine. I checked the Wine database and Unity3D got a "Silver" rating on a Gentoo machine - so I thought I might get it to work here, too.

So I installed Wine, downloaded Unity3D and ran the installer. Installation worked flawless, absolutely no problems there. Even launching Unity3D worked. However, that's where the good part ends. The window components within the Unity editor which are default components (e.g. the menu bar) work well, but the main part of the window (which gets rendered by the unity engine itself) has weird artifacts and rarely ever updates, which makes using the editor practically impossible.

Since Unity3D is one of the very few remaining reasons for me to use Windows at all, I'd like to know if anyone of you managed to get it to work and/or has some advice for me about what I can do to make it work.


Greets & thanks in advance,


Alan_D.


PS: I hope I picked the right sub-forum here, if not: I apologize :???:

---

### Post by cottfcfan on 2011-10-05
I'm having the same problem with graphics glitches using Wine.
I find the problem is mainly down to Compiz.
Try logging into the Classic Desktop Environment, then disable compiz & enable Metacity, relaunch your program & see if the graphics improve.
The same problem exists in 11.10 beta, but installing gnome-shell, and logging into that instead, resolves all of my Wine graphics glitches.

---

### Post by Alan_D. on 2011-10-05
Hi,

thanks for the reply, I'll try that - I already imagined that it could have something to do with Compiz, but I wasn't sure of it... I'll give it a shot as soon as I can and report back here afterwards.


Thanks,


Alan

---

### Post by sffvba[e0rt on 2011-10-05
*Thread moved to **Wine**.*


404

---

### Post by Alan_D. on 2011-10-05
Hi,

I tried as you said and logged in with Metacity (without effects) instead of the Unity desktop manager. After resizing the Unity3D window once, the window seems fine.

However, I get a couple of error messages from Unity itself:

-----------------------------------------------------
```
width <= 0 || height <= 0
UnityEditor.AppStatusBar:OnGUI()

width <= 0 || height <= 0
UnityEditor.DockArea:OnGUI()
```-----------------------------------------------------


This seems to be related to the editor *somehow*. The strange thing is that the game preview in the 3D screen looks just fine, navigation within the scene view works as it should, too. But when I try to launch the game, nothing happens (except for the two error messages above). Did anybody mange to solve this?


Greets,


Alan


EDIT: It would appear that this bug I'm facing is not that uncommon - I've found exactly the same bug description in the Unity3D forums, however, no one replied to the user's request, unfortunately.

---

