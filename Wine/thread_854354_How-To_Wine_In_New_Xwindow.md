---
title: "How-To: Wine In New Xwindow"
date: 2008-07-09
forum: Wine
---

### Post by Felson on 2008-07-09
For a number of games, you can't change the screen resolution in the game. Eg. Might * Magic 6, 7, 8 and 9. Starcraft, Dungeon Keeper 1 and 2 etc etc. I am sure you can all think of many others. To deal with this, we have 3 options. 
1) Leave "Emulate a Virtual Desktop" unchecked.
Issues: Some games really don't like this setting. If a game crashes (as is common with windows apps) I can leave your desktop at a bad resolution. No access to any other workspaces.
2) Check "Emulate a Virtual Desktop"
Issues: The game plays in a window, and can sometimes be to small to be worth playing. Or at the very least, hard to read.
3) Create a new xwindow display.
Issues: Generally a pain to do. You need to have some idea how to use XWindows at a command line level.

Well, this is focused on option 3, and making it less painful for the average user.
The key to this, is a script I made that you can get [here]("http://www.myte.ca/cgi/myte/main.pl/other.html#xwine"). Just right click xwine, and save it to your desktop. It may also be worth while to read the rest of what I have written under the download about usage and requirements, though the requirements are pretty common. 
After you have downloaded it, open a terminal and run the following.
```

sudo cp ~/Desktop/xwine /usr/bin/
sudo chmod 755 /usr/bin/xwine
rm ~/Desktop/xwine

```
Now, before we can use this script, we need to tell Ubuntu that you are aloud to create new displays.
```

sudo gedit /etc/X11/Xwrapper.config

```
You need to change the line that looks like "allowed_users=console" to "allowed_users=anybody". There may be security issues with this, so if you don't feel comfortable letting any user open a new display, you will not be able to use this method.

From here, the rest is simple. Edit/Create a Launcher in your Gnome or KDE menu, and set the execution line to something like the following.
```
/usr/bin/xwine -s 640x480 "/g/Games/MM8/mm8.exe"
```

And that is all there is too it. When the app is finished, it should close the new display automatically. If you are in your game, and you want to access your original display press "Ctrl-Alt-F7" and to get back to the new display press "Ctrl-Alt-F9". If the app in the has hung, you can either go back to your main display and kill it, or press "Ctrl-Alt-Backspace". Be careful not do that last in your main display, or it will kill X.

Bugs:
If you try and set the display smaller then the size the program wants, it will crash the program and go back to your original display. If you make a new launcher, and are finding that it is not working, make sure that you check that the size is correct. I good way to test, is set the size to 1280x1024 and work your way down until you find the right one.

---

### Post by M4rotku on 2008-07-09
When I try to follow the link, it tells me that I have to enter a username and pass for Authorization.

This will probably be a problem.

---

### Post by Felson on 2008-07-09
oops.... should be good now... Sometimes I am a dumb@ss...
Thanks.

---

### Post by mriedel on 2008-07-09
I tried a similar approach with starcraft a few months back. Giving your script a try tomorrow. In any way thanks a lot for your effort, it's very much appreciated :)

---

### Post by M4rotku on 2008-07-09
I'm kinda confused about the last part where you say it's easy from here and to just create a launcher.  The only launcher I know how to create is one from the desktop and I have no idea how to use it to launch an actual game.  In the normal wine menu, I would just select the game from the list after I put the disk in.

Is there any way you can further simplify that part of the instructions?

Much thanks,
M4rotku

---

### Post by mriedel on 2008-07-10
> **M4rotku said:**
> I'm kinda confused about the last part where you say it's easy from here and to just create a launcher.  The only launcher I know how to create is one from the desktop and I have no idea how to use it to launch an actual game.  In the normal wine menu, I would just select the game from the list after I put the disk in.

Is there any way you can further simplify that part of the instructions?


For Gnome, go to System -> Preferences -> Main Menu. Go to the submenu where you'd like the launcher / menu item to reside, then click New Item. Fill out all the fields as you see fit, entering */usr/bin/xwine -s 640x480 "/g/Games/MM8/mm8.exe"* in the line labeled "Command".

Edit:

> **Felson said:**
> 
You need to change the line that looks like "allowed_users=console" to "allowed_users=anybody". There may be security issues with this, so if you don't feel comfortable letting any user open a new display, you will not be able to use this method.

Could you explain the security issues in a little more detail?

---

### Post by Felson on 2008-07-10
@M4rotku
What mriedel said, except change "/g/Games/MM8/mm8.exe" with the actual executable that runs your game. And "640x480" with the resolution your game runs at. A good place to find the path and executable is the wine menu item that was generated when you installed the game. In fact, I usually just change that one, since it tends to have the right Icon already.


@mriedel
To be honest, I am not 100% sure. Changing that will make it so any user logged in to that computer can open a new X display. That would also mean that any program you run can do this also, if some nut decided to make it do so. I personally see that as a touch unlikely. The reason that I warn, is I am thinking there is probably a reason that the default setting is "console". If anyone else knows the why, I would love to be enlightened.

---

### Post by mriedel on 2008-07-10
I just tried your approach. Issues:

- As soon as I run xwine to start a game (StarCraft in my case), I can't hear sound from programms running on my primary X any more (Rhythmbox). Sound from the second display (StarCraft) can be heard even after switching back to the first one.

- Your script seems to be doing something it shouldn't. When I switch back to my primary display, the console from where I run xwine [...] StarCraft.exe contains a billion prompts and an error message in the last line:

[...]
$
$
$
$
$
$ FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

---

### Post by Felson on 2008-07-10
I will have to play with the sound thing. I never tried that. The bazillion prompts is because you ran it in terminal (Which is ok) and the last key you pressed was the Enter key, when it immediately switched to the new desktop, it still thought that the enter key was down, so it kept repeating the Enter just like if you held it down yourself. That error is an X error. You are probably getting it on boot up as well, and are just not seeing it. I have a few of those myself.

---

### Post by Felson on 2008-07-10
Just updated the program on my site to a version that shouldn't do the newline thing anymore.

---

### Post by mriedel on 2008-07-10
Thank you.

Still contemplating though. Most disadvantages of just running a fixed resolution game on your primary display without wine desktop emulation remain with this solution. You can't access other workspaces or use your second monitor. Additionally, new problems arise (security issue, sound issue). The only advantage apparent to me is that the wine / the game doesn't keep your display at a low/wrong resolution upon exit or failure.

Would it be possible to do some scripting magic and switch from a dual monitor TwinView setup to display 0 on monitor 0, display 1 (wine/game) on monitor 1 automatically? Sounds possible to me at first glance. I have virtually no experience with X though.

---

### Post by Felson on 2008-07-10
You can switch back and forth, use "Ctrl-Alt-F7" to go back to your main Display. Since you have dual monitors, I am not 100% sure what the return would be back to the game, but with a single monitor it's "Ctrl-Alt-F9". I "Think" it should be the same, but since I have no experience with dual monitors I have no idea if the use another TTY to operate the second monitor.... 

I will have to check on the sound thing once I get home from work and see what I can figure out. ATM, I can't play with sound or I might get caught doing stuff that isn't "work"... :p

It does make sense that it "should" be a simple matter, but I don't have a second monitor to try this with. And I also have no experience with running a second monitor under X. I am sure if I had one I could figure it out, but that will have to wait for now.

---

### Post by jackashe on 2009-09-30
Hi.  This idea sounds great.  I plan to use it for games that cannot be minimized in wine - it would be ideal to have that game on Ctrl-Alt-F9 while my primary X is on F7.  Did you ever get to look into the sound issues?  My game loads and it says it cannot access the sound device, and then the xwine script kills it.  Here is the error messages I get:



```
(II) Initializing extension GLX
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.48" is not allowed to own the service "org.x.config.dis
play3" due to security policies in the configuration file)

```

---

### Post by Felson on 2009-10-04
Sorry, I have never had the sound issue. I suspect that it "may" be a hardware issue. That is, some soundcards (most) can only be accessed by 1 process at a time. This is normaly solved with software. It is possible that that there may be a difference Between the the ALSA and OSS implamentations that will allow More then 1 X session too access sound. 

I actualy don't use this script anymore, since I got a second monitor. I couldn't solve the problem with haveing the game on 1 screen and still haveing access to the othre X session on the other.

The way get around it now, is that I leave WINE in "windowed" mode, and try and make the game I am running have at the same resolussion. Then I run "wmctrl -r :SELECT: -b toggle,fullscreen" and click on the WINE window. I have that command setup with an icon on my task bar.

---

### Post by jackashe on 2009-10-12
the sound issue is really that the 2nd copy of X tries to initialize everhything itself - sound, wlan, bluetooth, etc, but the first instance already has all of those... It seems like there should be some way to get them to "share" and this is what happens on the terminal screens.  I want to use this for Warcraft III, and here is my use case:  You cannot alt-tab out of the game, since it permanently messes up the graphics.  So I'd like to have a 2nd X where I can browse the web, play music, do anything while Warcraft III is searching for an online game.  On Windows, you can do this by alt-tabbing.  when the game matches you to an online game in Windows, the minimized Warcraft III process pops back to full screen.  On ubuntu, you can Ctrl-Alt-F1 and log into a terminal to do text based commands.  once you log in, the sounds you hear come from X, so when Warcraft III finds an online game, you hear the dramatic music playing and can press Ctrl-Alt-F7 to go play.
My friends suggested that we can run Warcraft III on the primary display (F7) and then browse the web etc in a 2nd X session.  This does work somewhat, but it suffers from the sound problem - the 2nd X session has no sounds and so you can't tell when Warcraft III finds an online game.  I was running a 2nd copy of KDE following this site.
[http://maketecheasier.com/run-multiple-x-sessions-without-virtualization/2009/07/11](http://maketecheasier.com/run-multiple-x-sessions-without-virtualization/2009/07/11)

---

