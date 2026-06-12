---
title: "Can't shutdown, restart, hibernate or suspend"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by Hooya on 2008-05-04
Running a pretty clean install of Hardy Heron x64 on Asus A8N-SLI Deluxe board, with Nvidia restricted drivers from the package manager for my video card.

When I try to shutdown or restart all my program windows will go away but it'll hang there, with just a mouse cursor and desktop background.  If I hit ctrl+alt+backspace to "restart" the xserver, it continues to shutdown or restart, but won't complete on its own.

On a related problem, I found that my issues with Hibernate and suspend aren't in coming out of hibernate, but it never actually completes the hibernate or suspend routines.  In Windows if I suspend the machine goes totally quiet and the power LED on my tower blinks instead of staying solid.  With Ubuntu it never gets to the point of blinking the LED, it stays solid, making me think it isn't getting all the way into hibernate.  Unlike the shutdown/restart bug, this is something that I have to Hard power down to get out of or hit the reset button on my tower.

I'll try turning off the restricted driver, but I don't honestly think that's the issue. - edit, it's not the issue.  But I also just tried logging off for the first time (why would I when I'm the only user) and found that I get the same hang spot when logging off as I do when I try to shut down, so the issue must be in the log off sequence.

Anyone else have this issue?

Monitor power saver settings work just fine, and on my x86 installation on a laptop (Toshiba A15) all the power functions work properly.

---

### Post by Didjit on 2008-05-04
I ran into some strange problems not being able to resolve the machine name or local host. Try pinging localhost and the machine name to make sure you are not having the same issue.

Re: suspend. I never had luck w/stock Ubuntu suspend (PMI).  I use s2ram. From a console, try "sudo s2ram -f" if it works like expected, then I will tell you how to hack it to make it the default.

Didjit

---

### Post by Hooya on 2008-05-10
hmm... s2ram isn't a valid command and I couldn't find a package for it in the package manager.  I installed uswsusp after doing a quick google search, but the command still doesn't work.  Any ideas?

---

### Post by Didjit on 2008-05-10
Need to get the Debian version, see here.
[http://leoslog.wordpress.com/2008/03/29/putting-the-thinkpad-t60p-to-sleep-in-ubuntu-hardy-heron-beta/](http://leoslog.wordpress.com/2008/03/29/putting-the-thinkpad-t60p-to-sleep-in-ubuntu-hardy-heron-beta/)


Didjit

---

### Post by SatanClaus on 2008-05-10
> **Hooya said:**
> 
When I try to shutdown or restart all my program windows will go away but it'll hang there, with just a mouse cursor and desktop background.  If I hit ctrl+alt+backspace to "restart" the xserver, it continues to shutdown or restart, but won't complete on its own.


Make sure that gnome-power-manager is running, re-enable it if not.

---

### Post by Hooya on 2008-05-11
> **SatanClaus said:**
> Make sure that gnome-power-manager is running, re-enable it if not.

It's running twice!  Is that a problem?  After a reboot it's only got one process, but I still can't shutdown or sleep properly.

I was able to get the uswsusp from those repositories.  I'll try it in a little while and report back.  I don't need hibernate on my desktop, just sleep, so this is fine if it works.  Strangely enough hibernate and sleep work beautifully on my aging laptop (Toshiba) that I put Hardy on.  That's the x86 flavor though, so that could have something to do with it as well.

Of course, this still doesn't solve my "need to ctrl+alt+backspace to reboot" issue, but whatever.


Edit:
Bah, exact same result with s2ram as with letting ubuntu do it on its own.  Power light never indicates sleep mode, can't wake the machine up so I have to hit the reset button.  The s2ram command shut the hard drive off immediately, no hesitation whatsoever, which frightens me a little bit.  I'll be removing that package until further comment.

---

