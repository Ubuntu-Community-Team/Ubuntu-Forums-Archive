---
title: "Title Bar and emerald --replace"
date: 2009-10-15
forum: x86 64-bit Users
---

### Post by yedidyah on 2009-10-15
Every time I start my computer I have to:

Alt + F2
emerald --replace

Because the title bar that contains Minimize Window, Restore Window, Close Window is gone.

I looked in my ccsm settings and Window Decorations is checked.

Because of the way it happened I suspect that I simply pushed the wrong button or combination of buttons that caused this to default to this lack of title bar.

---

### Post by yedidyah on 2009-10-18
anyone?

---

### Post by Shpongle on 2009-10-18
just add it to your startup applications and it should work , iv only briefly tried kubuntu so i cant exactly say where the startup options are , shouldnt be hard to find tho

---

### Post by yedidyah on 2009-10-19
Thanks DillByrne for the lead.

I ixquicked it (searched using ixquick.com a non-intrusive search engine) and came up with the following web site:

[http://seogadget.co.uk/how-to-run-emerald-at-startup/](http://seogadget.co.uk/how-to-run-emerald-at-startup/)

so I went to the k menu -> applications -> settings -> CompizConfig Settings Manager

Under the Title "Effects" I clicked on the highlighted "Window Decoration" (don't remove the check mark in the box associated with "Window Decoration")

Then under the area that says: "Command"
I removed something similar to this /usr/bin/compiz
and replaced it with:

emerald --replace

I restarted and now I have the title bars back (but they are not the same as what was originally there, the new ones are clear). 

I would like to find out what the original command was (under "Command") and find out why it stopped working as when I followed the path /usr/bin/ there was only .directory there.

If anyone knows drop a note.

Whatever caused the file in the path /usr/bin/compizwhatever to cease to exist is the culprit. Perhaps an update or something else. Now it is no longer a compiz thing but an emerald thing.

---

### Post by dabl on 2009-10-19
kwin is the default Kubuntu/KDE window decorator.  Emerald is an alternate window decorator (I use Emerald too).

You already figured out (correctly) how to set Emerald as the default decorator.  You can also simply issue "emerald --replace" in a Konsole window.

So, in Settings > Emerald is the utility to change window decoration styles.  I like the default ruby red style, but there are many.  You might need to use "help" or Google -- it's been quite awhile since I fiddled with the alternate Emerald styles, but there are a lot of them including cool clear/glassy/translucent ones.

BTW, GLX must be working, as a prerequisite for Emerald to work.  You can check it by running glxgears in a Konsole window.  If glxgears won't run, then you know Emerald won't run, and you prolly have to reinstall your video driver, or fix xorg.conf, to make sure glx is enabled and working.

Hope this helps.

---

