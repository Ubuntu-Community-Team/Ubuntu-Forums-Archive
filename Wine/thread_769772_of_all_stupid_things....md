---
title: "of all stupid things..."
date: 2008-04-26
forum: Wine
---

### Post by parkland on 2008-04-26
Ok, I installed "grand theft auto III" in wine. It ran perfect!!! (minus not displaying the opening videos)

10 minutes later, nothing runs under wine, opening an exe file doesnt do anything.

Running gta3.exe at the command line does this :


[email]user@user-laptop:~/.wine[/email]/drive_c/Program Files/Rockstar Games/GTAIII$ wine gta3.exe
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
err:module:import_dll Library  (which is needed by L"C:\\Program Files\\Rockstar Games\\GTAIII\\gta3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Rockstar Games\\GTAIII\\gta3.exe" failed, status c0000135
[email]user@user-laptop:~/.wine[/email]/drive_c/Program Files/Rockstar Games/GTAIII$ 



????

It was running perfect 10 minutes ago !!! I even un-installed wine, reinstalled, nothing!

Any help much appreciated.

---

### Post by parkland on 2008-04-26
Will copying the contents of my c:\windows directory from an XP hard drive into the wine "drive_c" give wine better drivers?

---

### Post by Kinst on 2008-04-27
Uninstall wine. Delete the hidden .wine folder in your home directory. Reinstall wine. Run the "winecfg" command in a terminal.

That'll give you a completely fresh slate to try again. I dunno what happened but it looks weird.

---

### Post by DarkSim on 2008-04-27
You don't have to uninstall anything.

This page tells you what you need to do and what's going on.

[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by Mr_Congeniality on 2008-04-27
Wow, is it me, or does Hardy have an unbelieveable amount of problems?

---

### Post by Fred_E _krugar on 2008-04-27
> **Mr_Congeniality said:**
> Wow, is it me, or does Hardy have an unbelieveable amount of problems?

Not really the thing that is causing alot of problems is that stupid PulseAudio just turn off the PulseAudio server and for some mystical reason alot of things cleared up for me.

---

### Post by parkland on 2008-04-27
thanks guys, got er goin again , now for flight simulator 2004...

---

### Post by cogadh on 2008-04-27
> **Mr_Congeniality said:**
> Wow, is it me, or does Hardy have an unbelieveable amount of problems?
Actually, I've had quite a few problems with Hardy. So many that I've switched back to Gutsy. This is the first time since Breezy (5.10) that I have not stuck with the new release. I only had it for about 48 hours before I had enough of all the little annoyances I was finding.

However, this particular "problem" is not really a bug in Hardy as much as a poorly thought out and tested security measure. Its a good idea, but the implementation was not handled all that well (in my opinion).

---

### Post by andrebrait on 2008-04-27
so, without pulseaudio, what am I supposed to use? ESD?

---

