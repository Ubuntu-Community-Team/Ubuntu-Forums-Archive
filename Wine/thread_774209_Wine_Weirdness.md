---
title: "Wine Weirdness"
date: 2008-04-29
forum: Wine
---

### Post by jbysmith on 2008-04-29
Having a small problem with Wine that's rather a nuisance; nothing huge but it can be annoying.

I'm using a fresh install of Ubuntu 7.10, as 8.04's been giving me problems and going to wait a while till things get worked out.  Proprietary nVidia drivers via Envy.  Compiz Fusion has been completely removed, not just disabled.  (Going to compile the Git version later)  I built Wine 0.9.60 from source.  

What's happening is that if I minimize a Wine app, I can't get it back.  It does show up on the taskbar, but the only taskbar options if I right click are move or close, no restore.  Alt-tab doesn't bring a Wine app to the foreground.  I tried several different applications, and they all do it, minus RegEdit and Notepad, they work as they should.

The version in the Ubuntu repo doesn't do this.. 0.9.46 I think it is, but I have a couple apps that absolutely will bomb on that build; I need the newer version for some bug fixes. The Journal for example I use to track work; won't even start on 0.9.46.

It's not a huge deal, but gets annoying if I forget and accidentally minimize a window. Other than that everything runs just fine and fast.  (In World of Warcraft's case, stupidly fast, better than XP) 

Anyone have any suggestions/workarounds?  Or just deal with it till 0.9.61?  Thanks

---

### Post by cogadh on 2008-04-29
It could be due to some error in your compile. Have you tried using the official 0.9.59 package that is available for Ubuntu 7.10? There isn't an official 0.9.60 package for 7.10 yet, unfortunately.

---

### Post by jbysmith on 2008-04-29
Actually, no I didn't.  It's a new install of Ubuntu and I beelined right for the new version heh.  

As far as I know anyway 0.9.60 compiled without any issues. I used their scripts to pull in all the dependencies I needed, then their other script to build it, nothing special done on my part.  But since they're not supporting 0.9.60 on 7.10 I guess I should expect some issues.

I'm at work at the moment, will give 0.9.59 a spin tonight.  Was hoping to get the latest version but ehh if 0.9.59 runs my software, good enough for me.

Thanks

---

### Post by jbysmith on 2008-04-29
Just an update now that I can work on my system again.

I completely blasted any traces of Wine on my system, short of deleting the sources directory just in case, and installed 0.9.59 from the WineHQ repository.

It's actually worse now. The program doesn't even show on the taskbar now, nor the alt-tab task switcher.  Minimizing it is sure death and needs a wineserver -k to kill it.

It's a little better in 0.9.60, at least it shows on the taskbar, but still pretty busted up; minimizing still needs a kill to close.

Any ideas?  It's ok if I remember not to minimize, but I have to "manually" bring the window to the foreground by clicking it; alt-tab is useless.  Performance otherwise is just fine.

Edit -

Just fired up Guild Wars after copying over my backup.  That one is working properly.  Guess it's just the one application that's having a problem. I'll throw something on their AppDB and see if it's something that can be resolved later.

Thanks

---

