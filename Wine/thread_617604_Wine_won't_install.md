---
title: "Wine won't install"
date: 2007-11-19
forum: Wine
---

### Post by ilh on 2007-11-19
Howdi all, had wine 0.9.48 installed in Gutsy and it was working fine. Then for some reason winecfg wouldn't open and I could only get the login screen for the SOE station launchpad, after I log it all but the left hand panel button doesn't show up and it just froze there. Opened the uninstall apps pane fine but it wouldn't let me unistall any of the programs (can't remember what it said). The only thing it would run properly was CoD2, not even putty worked. Tried uninstalling it, deleting .wine and reinstalling it which it looks like it does fine but when running winecfg from the terminal it sits there saying:

"wine: creating configuration directory '/home/me/.wine'...
Could not load Mozilla. HTML rendering will be disabled.

"

It creates .wine-randomletters folder in home and there's a load of the correct wine files in there.

Any ideas?

Thanks

---

### Post by hikaricore on 2007-11-19
Sounds like a video driver issue if things are freezing up...  that or your games/applications do not work properly under WINE.

You should probably check the WINE Application Database to see what works and what doesn't before spending too much time getting frustrated.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by ilh on 2007-11-19
It was all working fine before, could get into winecfg, launchpad (then Infantry), CoD2 and putty, but for some reason it all but CoD2 stopped working. The only thing I can thing of that's changed since is putting emerald theme manager on but I don't get why the log in screen for the launchpad would work but the screen after not.

Edit: Just tried going back and installing .48 instead of .49 and now it's naming it .wine rather than .wine-randomletters which is a good start but now running winecfg does nothing at all, not even the message about not being able to load mozilla.

---

### Post by hikaricore on 2007-11-19
You need to disable any beryl/compiz desktop effects before attempting to run 3d accelerated games, especially through WINE.

---

### Post by ilh on 2007-11-19
Well i'll be damned, that worked. winecfg opens now. Thanks.

But what I don't understand is that it was working before even with compiz fusion running.

---

### Post by hikaricore on 2007-11-19
It may have something to do with Emerald like you said it worked before installing it.  O.o

Definately a strange issue.  Be aware that Emerald was developed to run /w Beryl and not Compiz Fusion.
Beryl and Compiz merged awhile back creating Compiz Fusion.  I don't believe that work on Emerald has continued after this.

---

### Post by ilh on 2007-11-19
Argh, guess I spoke too soon, now winecfg won't open again, was an instance of 1 that I tried to open earlier as a few popped up. Have disabled compiz fusion and emerald. Tried to reinstall the launchpad and that got to near the end of the install shield and froze so I nicked the Launchpad.exe from my windows partition which opened and did a download install rather than a normal install fine and can get passed the log in screen. This is annoying -_-

Edit: argh again, now winecfg just opened randomly. Must just be taking a hell of a long time for some reason.

---

