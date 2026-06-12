---
title: "screensaver and xscreensaver"
date: 2006-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by TWFJR on 2006-06-07
Screensavers are freezing up.  Removed screensaver and installed xscreensaver. Both freeze up.  Now I've got a post about printer spitting out paper with no print. Ubuntu says that it is ready.  What is wrong with Dapper Drake 6.06?

---

### Post by Peepsalot on 2006-06-07
Screensavers are crashing my system as well, though I am not running 64bit.  I think it is set to choose a random screensaver, and it seems there is one with chess pieces that it always freezes on.  I installed Ubuntu 6.06, but later installed xubuntu-desktop and now use that.  I have turned off screensaver in gnome-screensaver-preferences, but I can't find the screensaver preferences for xfce.  I wouldn't mind just disabling screensavers entirely if only I knew how.

I am guessing my problems come from the fact that I have an onboard video card that has little to no 3d acceleration(S3 Unichrome i think it is called)

---

### Post by TWFJR on 2006-06-08
My system is not crashing.  You could go to "Synaptic Package Manager" and remove screensaver apps altogether.  And later reinstall them there too.

---

### Post by Peepsalot on 2006-06-08
[QUOTE=TWFJR]My system is not crashing.  You could go to "Synaptic Package Manager" and remove screensaver apps altogether.  And later reinstall them there too.[/QUOTE]
Well, you said freezing.  To me freezing and crashing are the same.  I don't know your definition of the words.  When my screensaver freezes, I don't know any way to get out of it but to press the power button on my computer.

---

### Post by MKova on 2006-06-13
same thing here... only I don't use 64 bit ver
amd athlon64 3000+, ati x800gto

---

### Post by Peepsalot on 2006-06-13
[QUOTE=MKova]same thing here... only I don't use 64 bit ver
amd athlon64 3000+, ati x800gto[/QUOTE]
MKova, I was able to solve my problem.  You can read my solution in posts #11 and #12 in [this thread](http://ubuntuforums.org/showthread.php?t=189836).
Hope that helps some.

---

### Post by benteveo on 2006-06-14
I'm seeing the same thing.

The problem isn't new, it existed in 5.10 (breezy) as well albeit in a slightly different way which made it easier for me to workaround.

*xscreensaver* (or *xscreenserver-gl*) starts while the KDE screensaver is running (in my case it is *kslideshow.kss*). The bad (x) screensaver grabs the mouse pointer and locks up the whole system.  The mouse pointer is released if you ssh from remote and kill the xscreensaver process. However, if the bad screensaver is the GL one (*xscreensaver-gl*), the result is much worse, a hardware lockup occurs after which I cannot even ssh remotely to kill the bad process.  The whole system seems to be locked up and frozen and the only way to get out is a hard reset.

In breezy I solved it by doing an ugly thing and renaming */usr/bin/xscreensaver* to */usr/bin/xscreensaver.disabled.*  In Dapper I see multiple xscreensaver-<some-variation> instead of only one because the package *xscreensaver-gl* is installed as part of *ubuntu-desktop*

Part of the problem is that you cannot remove the *xscreensaver-gl* package because it has a dependency on *ubuntu-desktop*

This is by far the worst problem I encoutered in Ubuntu since switching from Mandrake.

Any easy workaround appreciated :-(

---

### Post by benteveo on 2006-06-14
Oops!, shoud have done more reading before posting.

Ubuntu user **shamrock_uk** had the solution in another thread:
    [http://ubuntuforums.org/showthread.php?t=189836](http://ubuntuforums.org/showthread.php?t=189836)

I can remove **ubuntu-desktop** safely, it is not a real package but a meta-package.

So I just removed **xscreensaver-gl** and said OK to the dialog that said **ubuntu-desktop** is going to be removed too.

There was another suggestion for ATI radeon users to avoid 3D ati/radeon X driver lockups in the same thread (see link above) so a backup plan2 may exist as well.
 
Anyway, let's see if this solves the problem.  I'm happier now. :D

---

