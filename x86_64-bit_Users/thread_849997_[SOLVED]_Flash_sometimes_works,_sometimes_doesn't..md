---
title: "[SOLVED] Flash sometimes works, sometimes doesn't."
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by Nazty_Nayt on 2008-07-05
Ok, I think the only way flash works on my 64bit is through gnash.  Cause the install script for Hardy that's in the sticky didn't do anything for me.  And that's cool, and all, but when I go to certain pages that have I guess different variations of flash, it shuts down, all other flash programs that are running.

For instance, if I'm looking at a myspace page, and listening to an mp3 on a flash player it works fine, but if I open a new tab in firefox, and go to lets say photobucket, and use any of the editing tools that involve flash, it shuts down everything.  I just don't get it, could it be that I have the adobe flash, and gnash both enabled?

---

### Post by Kilz on 2008-07-05
> **Nazty_Nayt said:**
> Ok, I think the only way flash works on my 64bit is through gnash.  Cause **the install script** for Hardy that's in the sticky didn't do anything for me.
There is no install script for Hardy in the Flash Sticky. 

[INDENT]Flash should work on Hardy without any scripts or work arounds other than the commands above.
If flash still does not work [COLOR="Red"]**DO Not**[/COLOR] install the scripts below.[/INDENT]

> **Nazty_Nayt said:**
>  And that's cool, and all, but when I go to certain pages that have I guess different variations of flash, it shuts down, all other flash programs that are running.

For instance, if I'm looking at a myspace page, and listening to an mp3 on a flash player it works fine, but if I open a new tab in firefox, and go to lets say photobucket, and use any of the editing tools that involve flash, it shuts down everything.  I just don't get it, could it be that I have the adobe flash, and gnash both enabled? This sounds like you have multiple conflicting flash plugins installed. You can only have one.

---

### Post by nikgare on 2008-07-05
Flash on hardy 64bit is dead easy to install - just install **flashplugin-nonfree** via synaptic.
You my need to enable the restricted repository if you havn't alraeay done so.

---

### Post by Yellow Pasque on 2008-07-05
> **nikgare said:**
> Flash on hardy 64bit is dead easy to install - just install **flashplugin-nonfree** via synaptic.
You my need to enable the restricted repository if you havn't alraeay done so.
Look in System -> Administration -> Synaptic.. to see if you have both installed. Uninstall gnash if it's still on your system. Follow the directions in the Hardy section again, including the commands to purge previous installs.

---

