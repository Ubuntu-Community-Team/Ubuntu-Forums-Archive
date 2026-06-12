---
title: "very strange and worrying problem"
date: 2007-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ruzle0 on 2007-05-27
hi,
i am running 6.10 amd64 and have now a few times, had the gnome logout screen appear randomly and uninitiated, and then the computer completes a hard off. no shutting down just straight to off, then i must press the power button again to restart.
A couple of times i have managed to press the cancel button of the log out dialog with the mouse but then the logout dialog reappears immediately and the power outs again before it allows me to press cancel a second time.
I'm assuming its not hardware as the computer would just crash/panic/power off with out firing off the logout/shutdown dialog. i have tried searching on Google but have not managed to find anything similar.

does any one have any suggestions to find the cause or know of log files that may give clues is greatly appreciated.

athlon 4200 X2
asus m2n sli delux
nvidia geforce 7600gt

---

### Post by ruzle0 on 2007-05-27
the only thing i can think of is if the computer thinks that the power button is pressed, as a short press brings the log out/shutdown screen and an extended press will hard power off, but how can i check if this is the case
and more importantly fix it.
any ideas?

---

### Post by Kilz on 2007-05-27
> **ruzle0 said:**
> hi,
i am running 6.10 amd64 and have now a few times, had the gnome logout screen appear randomly and uninitiated, and then the computer completes a hard off. no shutting down just straight to off, then i must press the power button again to restart.
A couple of times i have managed to press the cancel button of the log out dialog with the mouse but then the logout dialog reappears immediately and the power outs again before it allows me to press cancel a second time.
I'm assuming its not hardware as the computer would just crash/panic/power off with out firing off the logout/shutdown dialog. i have tried searching on Google but have not managed to find anything similar.

does any one have any suggestions to find the cause or know of log files that may give clues is greatly appreciated.

athlon 4200 X2
asus m2n sli delux
nvidia geforce 7600gt

Overheating can cause this to happen, you are not overclocking your processor are you?

---

### Post by ruzle0 on 2007-05-27
nope, i am a mere mortal who lives within his means

---

### Post by incubus on 2007-05-27
ruzle0,

I have a suggestion.  How about going to the basement and taking a look at some log files?  They are all in /var/log/.  At least on KDE, we have a kdm log there.  I assume you will have one for gdm.  I would be good to check syslog for events, and dmesg for hardware issues.

If I couldn't figure it out, I would try a few things like creating a new user and seeing if you get the same behavior, or installing an alternative window manager and checking that.  These would rule out something wrong with gnome.

incubus

---

