---
title: "Best WINE Version for CS? HL2?"
date: 2007-12-09
forum: Wine
---

### Post by chris062689 on 2007-12-09
Due to the newly released Wine 0.9.50, games have become very unstable and FPS is down.  Which is the best version to use for Counter Strike Source?  What about Half Life 2 / Portal / HL2:Ep1?

---

### Post by chris062689 on 2007-12-09
> **chris062689 said:**
> Due to the newly released Wine 0.9.50, games have become very unstable and FPS is down.  Which is the best version to use for Counter Strike Source?  What about Half Life 2 / Portal / HL2:Ep1?

Sorry, I just looked on Wine HQ and realized that it was the ALSA driver messing things up.
[EDIT; I'm still getting very low FPS.  It wasn't like this before!]

Does anyone have any fixes / prefer a lower wine version?

---

### Post by MickLionheart on 2007-12-09
wierd? i see no FPS drop between 0.9.49 and .50 in CS:S or HL2, rocking a solid 120FPS settings maxed out with compiz running on an 8600GT

---

### Post by Fred_E _krugar on 2007-12-10
I am on .50 and it is working like a charm.

---

### Post by cogadh on 2007-12-10
Ditto, the fixes that were in 0.9.50 made many things run better for me (not just HL2). In fact, some things that didn't run at all just started running thanks to 0.9.50.

One thing you do need to do after updating Wine is run "wineprefixcreate" to update the registry with any modifications you may have made to the registry with the previous version of Wine. If you don't do that, Wine will still work, but you may have issues that didn't exist before the update.

---

### Post by chris062689 on 2007-12-10
What audio driver are you using?
Graphic card / driver?
What version of CS:S do you have installed?
Compiz enabled?

All of the source games get a heavy framerate drop.
The games work, but everything from HL to Portal to CS:S has a 
massive framerate drop for me...

---

### Post by cogadh on 2007-12-10
ALSA
Nvidia 7600GS / standard nvidia-glx-new from the repositories
Version? Whatever version is the default in Steam
Never run Compiz and Wine at the same time, if it doesn't prevent the game from working at all, it will severely impact the performance.

---

### Post by Fred_E _krugar on 2007-12-11
I dont even have Compiz anymore was fun in the beginning but it was just alot of hoopla now it is time to get to business playing games for me now that I took my last final Friday woohoo.

---

### Post by sirdilznik on 2007-12-11
> **Fred_E _krugar said:**
> I dont even have Compiz anymore was fun in the beginning but it was just alot of hoopla now it is time to get to business playing games for me now that I took my last final Friday woohoo.

Agreed.  Compiz was a fun toy for a while, but I got bored of it pretty quickly.  There days I run Fvwm so I can't run compiz anyway (since it would replace Fvwm as my WM).  I can still get transparency and shadows and stuff using xcompmgr if I wanted to, but I'll wait until they get everything sorted out with XRender in Xorg rather than use a hack like xcompmgr.

On topic: .50 has worked better for me than .48 or .49 ever did.  NVIDIA 7950 GT, ALSA, Kernel-2.6.24-rc3.

---

### Post by chris062689 on 2007-12-11
Just ran I speed test using Counter Strike, I got 4.86 FPS in metacity.
On a native machine (and in Ubuntu, it used to) I got full speed with all of the settings.
I've tried reinstalling wine (even wiping my .wine directory) and it still gets me the same FPS.
I'm using the Nvida 100.14.19 driver.


Anything you guys suggest?

---

### Post by sh!ft on 2007-12-13
.5 runs like a charm with driver 100.14.19, compiz disabled(or removed).

[img]http://img507.imageshack.us/img507/4965/screenshotwineconfigurasp0.png[/img]

Make sure you have the direct 3d shader support checked off, otherwise, hell yeah you're gonna get a performance decrease.

---

