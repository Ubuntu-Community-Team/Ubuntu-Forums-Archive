---
title: "New X session not starting from script"
date: 2007-12-11
forum: Wine
---

### Post by bentonian on 2007-12-11
I am using the following script (lifted from "Stuff I've learned about Wine"):

> #!/bin/sh
#sudo /etc/init.d/gdm stop
X :2 -ac
cd "$HOME/.wine/drive_c/Program Files/Starcraft Shareware(ED)/"
sleep 2
DISPLAY=:2 WINEDEBUG=-all wine "C:\Program Files\Starcraft Shareware(ED)\Starcraft.exe"


When I run the script I am dropped into a gray-black screen with wavy lines and a black 'X' cursor.

Is the new X session not starting? What am I missing? Thanks!

---

### Post by cogadh on 2007-12-11
That is the new X session, that's what X looks like without a window manager on top of it. It's the game that is not launching. Are you sure the paths and executable name are correct? Were you able to run the game in the normal X session before trying to run it in a separate one?

---

### Post by bentonian on 2007-12-11
Aha! Thanks for the clearing up the part about the session.

I lifted the path directly from the desktop launcher icon. And I've double-checked the path and syntax several times, just to make sure. I've also messed with the front and back slashes, as the launcher did back slashes, but your article (many thanks, btw) indicates front slashes.

Here's my directory listing:

> ralph@ubuntu:~/.wine/drive_c/Program Files/Starcraft Shareware(ED)$ ls -l
[snip]
-rwxr-xr-x 1 ralph ralph   970752 2007-11-27 20:54 Starcraft.exe


Any thoughts? Since X is starting, I don't know what the problem could be.

---

### Post by cogadh on 2007-12-11
But did the game actually run in your standard X session before you tried using the launch script?

---

### Post by bentonian on 2007-12-11
Well, I think I'm getting closer. I tweaked the script a little:

> #!/bin/sh
X :2 -ac
cd ".wine/drive_c/Program Files/Starcraft Shareware(ED)"
sleep 2
DISPLAY=:2
WINEDEBUG=-all wine Starcraft.exe

Now, if I comment out the "X :2 -ac" and "DISPLAY=-2", then the game runs in full screen (virtual desktop is off in Winecfg).

But if I include the X lines in the script and run it, I drop into the X session, but the game never starts.

I see one error message when I get back to the desktop:
(EE) AIGLX: Screen 0 is not DRI capable

Does that have any bearing on this?

---

### Post by cogadh on 2007-12-11
What video hardware/driver are you using? Do you have Compiz enabled?

---

### Post by bentonian on 2007-12-11
I'm running on Fluxbox, so I don't think Compiz is enabled - I looked at my system monitor, and didn't see it there.

For hardware I've got an onboard Rage chip with 4MB SDRAM. What's the best way to find out the exact hardware and drivers I'm using?

It's an old machine, just trying to squeeze some last life out of it for the kids.

---

### Post by bentonian on 2007-12-13
Any other thoughts on this? It seems odd that I can get the game to run full-screen from the desktop, but can't get it run in a new X session.

---

### Post by CarpKing on 2007-12-14
I seem to be having the same sort of problem.  Is there any way to access a terminal or something in the new X session?  That way I might be able to see some sort of error message.

---

### Post by CarpKing on 2007-12-14
Not sure if this is significant or not-  No matter how long I let it sit in the new X server, once I kill that one the terminal has a bunch of stuff in it about "tv restore."  A few seconds later, I get the same bunch of ALSA messages that I get whenever I use WINE.  After that, the terminal spits out a bunch of blank lines followed by:
```
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

---

### Post by CarpKing on 2007-12-18
Does anyone have any ideas?  

(And yes, the game does work in the normal X session.  I just wanted to see if I could get better performance)

---

### Post by cogadh on 2007-12-18
You could try running the game from a console session instead of from the terminal. Logout, then do CTRL-ALT-F1 to get to the console. Log in at the console, then kill the normal X session by running "sudo /etc/init.d/gdm stop" (if you use KDE/Kubuntu do "sudo /etc/init.d/kdm stop" instead). Then run your launch script normally and any error messages will be output in the console session.

---

### Post by one_equals_two on 2007-12-24
place an '&' after your X command and try it out.  When I was string together the command it was stopping there because it's waiting for X exit before starting the next command.  It should look like this when you are done:

#!/bin/sh
X :2 -ac &
cd ".wine/drive_c/Program Files/Starcraft Shareware(ED)"
sleep 2
DISPLAY=:2
WINEDEBUG=-all wine Starcraft.exe

---

### Post by hOmerscousin on 2007-12-25
THANKS SOOO MUCH!!! That lil "&" has caused a lot of frustrating!!! Now, my starcraft runs like a dream. Happy Holidays everyone!!!

---

### Post by CarpKing on 2007-12-28
Awesome!  It works perfectly now.  As expected, it's a significant performance boost.

---

