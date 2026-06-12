---
title: "how to use wine command line arguments?"
date: 2007-12-16
forum: Wine
---

### Post by luke16 on 2007-12-16
I've read most of the faq, wine man page and how-tos about wine, but there must be something that I'm still not seeing.
I want to be able to launch certain programs in wine under a virtual desktop and others in fullscreen without having to go into wine config every time to change this. I would think that this could be done by putting something like a "-fullscreen" after the wine command when launching a game or program, but wine seems to think of any such args as belonging to the game that its launching instead of interpreting them itself. Is there any way to do this, from a command line or otherwise? If possible I would also like to be able to tell wine what res to use with certain games, such as "-width 1280 -height 1024" type stuff and have wine force the game to launch in that res, stretched or otherwise for the games that would launch in a window, so I can at least see some of the details of some of the older 640x480 games.

---

### Post by luke16 on 2008-01-05
bump?

---

### Post by cyberkost on 2008-01-06
I just installed HOMM3 and I would too like to know how to tell wine to run it in a 1600x1200 window (virtual desktop) and not fullscreen (1920x1200).

---

### Post by mike-laptop-dot-local on 2008-01-06
IANAWP (I am not a Wine pro) :), but this is how I simplified using my command line args:

- install software via the wine command line line (eg. wine setup.exe)
- Find the software's new icon in the ubuntu main menu, then click-and-drag it to your desktop to create a launcher
- Right-click the new desktop launcher icon and select Properties
- Click the Launcher tab in the Properties dialog box
- edit the Command line (with your command line args). When I have something up and running, this is where I turn off Wine's verbose error messages (insert  WINEDEBUG="-all" just before the wine command).

If you're running Portal, HL2, etc. via steam, there are extra args you can insert from within Steam:

- In the My Games tab, right-click your game and select Properties
- Click the Launch Options button in the Properties box and insert your extra options here (eg., -heapsize 512000 -novid -width 1280 -height 800 -dxlevel 81).

This works for me. Rather, this doesn't wreck anything for me. :)

---

### Post by shad0w_walker on 2008-01-06
If you want to force a desktop size at launch use this command:

```
wine explorer /desktop=1024x768 whatever.exe
```

Obviously replace the desktop dimensions with whatever you want and the exe name with the program you're trying to run. This should work fine for most things,

Its performance when forcing a fullscreen game to a window is lacking. I got maybe 1-2FPS on Portal when I forced it into a window. I get perfectly smooth gameplay when its fullscreen.

---

### Post by luke16 on 2008-01-06
> **shad0w_walker said:**
> If you want to force a desktop size at launch use this command:

```
wine explorer /desktop=1024x768 whatever.exe
```Obviously replace the desktop dimensions with whatever you want and the exe name with the program you're trying to run. This should work fine for most things,

That doesn't really work if whatever your running has its own res settings, it just overrides that. And as per the original question, what is the arg for fullscreen vs desktop so one doesn't have to go to wine config every time one wants to launch a different program/game?

---

### Post by hikaricore on 2008-01-06
There really isn't one.  Hence why you havn't gotten the response you were looking for.

Either you run it as is, or you run it with explorer and the /desktop flag.
The desktop flag works just fine in most cases, and it sure as hell stops the app from going fullscreen 99% of the time.

---

### Post by luke16 on 2008-01-07
> **hikaricore said:**
> There really isn't one.  Hence why you havn't gotten the response you were looking for.

Either you run it as is, or you run it with explorer and the /desktop flag.
The desktop flag works just fine in most cases, and it sure as hell stops the app from going fullscreen 99% of the time.

Okay, I now see it as a way of making things launch in window even if wine is configured for no virtual desktop, albeit at their own res.

Is there anyway to do the opposite? Have wine default everything to a virtual desktop and use the explorer argument to make certain apps go fullscreen?

---

