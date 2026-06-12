---
title: "[SOLVED] Installing Wine through Add/Remove..."
date: 2008-11-08
forum: Wine
---

### Post by chazdraves on 2008-11-08
Greetings, all! Quick question! I had previously installed Wine through Add/Remove. I decided to try out the new 1.1.8 to see if it fixed performance issues (slowdown and audio glitches) with Dawn of War: Dark Crusade. Needless to say, it didn't and actually made them worse.

Anyhow, I ran apt-get purge wine to get rid of wine and then ran apt-get install wine (after removing the entry from software sources) to re-install 1.0.1. The, just for kicks and giggles, I ran apt-get build-dep wine because I know that two packages were deleted when I purged wine 1.1.8. Well, I expected a list two items long, but I got a list of more than a hundred totalling about 400MB... Why weren't these installed through Add/Remove the first time? Additionally, are these necessary?

Thanks,
- Chaz

---

### Post by cogadh on 2008-11-08
It came up with all those extra packages because running "apt-get build-dep wine" installs all the dependencies you would need to compile Wine from the source code, not all of which are needed to just run the precompiled version of Wine.

---

### Post by chazdraves on 2008-11-08
Yeah, I guess I earn a "noob" slap for that one. I didn't think it through. Now that you say that, I see that running apt-get autoremove wants to remove all of those items. Thusly, what you say makes good sense.

Thanks,
- Chaz

---

### Post by cogadh on 2008-11-09
Hey, if asking that question is your "noob slap" moment with Ubuntu, be happy. Some of us have done much worse. I think mine was when I ran an apt command to remove a particular package, but didn't pay attention to what the additional packages to be removed were and it uninstalled my entire desktop.

---

### Post by chazdraves on 2008-11-09
Lol. I see that every now and again in Synaptic where you select a package to remove and it recommends uninstalling the kernel, X-Org, Ubuntu-Desktop et al. What's with that, anyway?

Thankfully I never went through with it :)
- Chaz

---

### Post by Brynster on 2008-11-10
> **cogadh said:**
> Hey, if asking that question is your "noob slap" moment with Ubuntu, be happy. Some of us have done much worse. I think mine was when I ran an apt command to remove a particular package, but didn't pay attention to what the additional packages to be removed were and it uninstalled my entire desktop.



Been there done that. Asking a question isn't a noobie thing, its a sensible thing.

---

