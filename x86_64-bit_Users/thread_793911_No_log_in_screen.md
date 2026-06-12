---
title: "No log in screen"
date: 2008-05-14
forum: x86 64-bit Users
---

### Post by jdswift on 2008-05-14
Hi,

I have a pc running Gutsy 64bit that was working, but now it does not boot properly. I'd be really grateful if someone has a fix for this (hopefully it's simple)!

It brings up the loading splash screen (with the progress bar), then goes to a blinking cursor, then goes blank (black screen).

I have left it like this for 20mins to see if it was just being slow, but it doesn't change.  I also can't switch to a text terminal. I can log into the machine using SSH from another pc however.

The boot log appears to be empty.
I tried the [splash screen fix]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen") and tried removing the "splash quiet" bit altogether but it's no better.

Cheers,
Jarrod

---

### Post by philinux on 2008-05-14
Install startupmanager from synaptic, nice little gui. Tick the option to display text during startup. Hopefully you'll be able to post back any error messages that are displayed.

---

### Post by jdswift on 2008-05-14
Is there a non-gui way to do that, I only have my putty command line terminal.

---

### Post by cacycleworks on 2008-05-14
I noticed this, too ... only I noticed the LCD screen dim, so I CTRL-ALT-Backspace which then brought up the login screen. If this becomes a habit, I'll work harder to quantify it and then learn about launchpad...

Hope this helps,
Chris

---

### Post by cacycleworks on 2008-05-14
OH! Another "no login screen" trick I have done in the past is CTRL-N ... in KDM (the kde login manager), it reverts to a virtual terminal mode instead of X windows.

I do not know the gdm equivalent for ctrl-n or if there is one.

---

### Post by jdswift on 2008-05-15
Thanks for you reply, unfortunately this didn't do anything.

Also, I've noticed that now it's a black screen (instead of no-signal which I'm sure it was originally). Strange since I haven't done anything...

---

### Post by cacycleworks on 2008-05-16
Hmmm... something is happening with the kdm/gdm ... just now, I had to Ctrl-Alt-Bksp 2 or 3 times before it woke up.

Same symptoms as you: boots to black screen but does keep signal.

I need to remember to disable splash and quiet so I can try to see more. I don't like those anyway, because they turn the monitor on and off like 3 or 5 times ... each time, it takes my 24" monitor a while to come back. Also, when it does fsck, I don't like staring at black screen for a minute not knowing what's happening. When you get to see the text, you know what's happening. :)

Chris

---

