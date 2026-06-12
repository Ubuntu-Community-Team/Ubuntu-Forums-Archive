---
title: "Very weird Gaim behaviour"
date: 2007-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by nowhere.elysium on 2007-08-20
Hi - I don't know for definite if this is amd64-specific, but it's the only platform where I've experienced it, so I'm gonna work under the assumption that it is.
Basically, if I open my contacts list in Gaim, the window stretches off to the right infinitely. It stays on the one desktop, so it's not really messing around with X or gnome on any serious level, and it doesn't alter the functionality of it, it's just odd. Also, it won't shrink back down to a small window size, if I resize the window manually.
Any thoughts?
Failing that, what's the easiest way to install a stable version of pidgin, since this is the gaim that's in the repos...
(incidentally... I'm on Feisty amd64)

---

### Post by funrider on 2007-08-21
I  am using Fiesty 64 too. I use gaim daily for MSN, icq and irc and never have any problem. I suggest to do a clean uninstall and then re-install it.

---

### Post by nowhere.elysium on 2007-08-21
Just tried that, and it's still doing it. Thoroughly weird. I'm tempted to do a complete rebuild: I've got an awful lot of crap on here that is left over from uninstalls, and I can't be bothered to go through it all and clean it *all* off manually.

---

### Post by John.Michael.Kane on 2007-08-21
> **nowhere.elysium said:**
> Just tried that, and it's still doing it. Thoroughly weird. I'm tempted to do a complete rebuild: I've got an awful lot of crap on here that is left over from uninstalls, and I can't be bothered to go through it all and clean it *all* off manually.

To remove partial packages
```
sudo apt-get autoclean
```

To remove residual Config packages
1) Open Synaptic 
2) On the bottom left hand corner of the window, click the Status button.
3) you should now see the list below.
Installed
Installed (local or obsolete)
Not installed
Residual config
4) Click on Residual config

Note If the "Residual config dialogue does not appear. This means you don't have any Residual Config packages on your machine.

Barring the above fixing the issue. your left with three options
1) Uninstall gaim completely.
2) Try installing pidgin [pidgin deb]("http://www.getdeb.net/search.php?keywords=pidgin") 
3) Backup your data, and reinstall. **Note this should be a last resort**

Also are you running any eye candy eg:compiz fusion.

---

### Post by nowhere.elysium on 2007-08-21
Nope, not running Compiz, tried clearing all of the excess crap out, and i even took the thoroughly retarded measure of using deborphan. God, how I regret that one. My system's bordering on the borked now, because of deborphan's aggressive removal of important stuff. As such, I get to rebuild now, which is ok, because I have some idea as to how I want to lay it all out, without the original faffing about. 
I'm also going to start off with install Xgl and tuning for speed as aggressively as possible this time, too. Do you have any suggested howtos that are worth following for this?

---

### Post by John.Michael.Kane on 2007-08-21
> **nowhere.elysium said:**
> Nope, not running Compiz, tried clearing all of the excess crap out, and i even took the thoroughly retarded measure of using deborphan. God, how I regret that one. My system's bordering on the borked now, because of deborphan's aggressive removal of important stuff. As such, I get to rebuild now, which is ok, because I have some idea as to how I want to lay it all out, without the original faffing about. 
I'm also going to start off with install Xgl and tuning for speed as aggressively as possible this time, too. Do you have any suggested howtos that are worth following for this?

Heres a guide posted by s_spiff.
[HowTo: Spruce up your Desktop, for x64 users.]("http://ubuntuforums.org/showthread.php?t=530414")

Or.
[CF Installer-Updater --> Easily Install and Update Compiz Fusion]("http://ubuntuforums.org/showthread.php?t=508769&highlight=compiz+fusion")

Theres other guides for eye candy these are just two. Also it will help when you try to install compiz to make sure your gpu is supported eg: nvidia some say it's easier. Ati some say it's pain.

Also note: these composting managers are beta, and still under development.

---

