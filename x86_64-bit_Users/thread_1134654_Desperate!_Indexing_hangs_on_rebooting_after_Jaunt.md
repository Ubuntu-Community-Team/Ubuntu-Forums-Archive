---
title: "Desperate! Indexing hangs on rebooting after Jaunty upgrade"
date: 2009-04-23
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2009-04-23
Today I upgraded Intrepid x86_64 to Jaunty. After restarting it announced that it was going to index the file system. The hard disk worked for a while and then an error message popped up:

Tracker
There was an error while performing indexing:
Index corrupted

There are three buttons on the error message: Reindex all contents, Cancel, and OK. If I click on Cancel or OK the error message box just pops back up again. If I click on Reindex all contents I get another message box that says:

Reindex your system?
Indexing can take a long time. Are you sure you want to re-index?

This dialog box has two buttons, No and Yes. If I click on No the dialog box disappears, but the other dialog box remains on the screen and I still can't get past it. If I click on Yes the second dialog box disappears leaving the first dialog box on the screen, but nothing at all happens. The disk drive light does not come on.

I can boot to recovery mode, but I need a command line option to disable the Tracker or whatever fool utility this is. I'll index later. Right now I can't get Gnome to come up and my computer is useless.

---

### Post by John Jason Jordan on 2009-04-23
OK, I found the bug report on this here:

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560")

By deleting all the files in ~/.cache and waiting over an hour for it to reindex, I managed to get past the indexing stuff.

But now I can't get the Gnome panel to appear. X comes up, I get the desktop background that I had before with Intrepid, but the Gnome panels do not appear. I cannot even get a terminal open because I can't click to launch anything.

I booted to Recovery Mode and edited xorg.conf to use nv instead of nvidia, but it didn't solve the problem.

I have a dead computer until someone can come up with an answer. Any suggestions welcome! I'm desperate!

---

### Post by brallan on 2009-04-24
I guess the above solution may not work so well if it bricked your gnome. instead, try installing the tracker-utils package:

sudo apt-get install tracker-utils

it worked for me. perhaps jaunty is working on the assumption that tracker-utils will get installed, as suggested packages (and not just dependencies) get installed by default now in jaunty (can anyone confirm?), unless you have upgraded from 8.04 then to 8.10 then to jaunty, as i have.

as for getting to a terminal, alt-F2 will still get you there. your problem is now is not X, it is something with gnome or with panel. I'm not sure what to suggest. best of luck!

---

### Post by John Jason Jordan on 2009-04-24
> **brallan said:**
> I guess the above solution may not work so well if it bricked your gnome. instead, try installing the tracker-utils package:

sudo apt-get install tracker-utils

it worked for me. perhaps jaunty is working on the assumption that tracker-utils will get installed, as suggested packages (and not just dependencies) get installed by default now in jaunty (can anyone confirm?), unless you have upgraded from 8.04 then to 8.10 then to jaunty, as i have.

as for getting to a terminal, alt-F2 will still get you there. your problem is now is not X, it is something with gnome or with panel. I'm not sure what to suggest. best of luck!

I solved the problem, which was caused by numerous things.

First, I discovered that the login screen had an option to boot into KDE instead of Gnome. I did, and KDE worked fine. Once I was able to get online I asked for help in a local LUG e-list that I subscribed to. I received various suggestions, all of which failed except one. The suggestions that didn't work included:

Right-clicking on the desktop to open a terminal 
   (Couldn't get anything to pop up by any kind of clicking)
Going to the command line with Ctrl-Alt-F1 and typing "gnome-panel"
   (Can't open a GUI applet when you're not in a GUI)
At the same command line adding the --display=:0.0 option
   (Just got error messages)

The winning suggestion was to install Gnome-do. From the non-GUI command line I installed it with apt-get. When I restarted the computer and logged into Gnome there was the Gnome-do window in the middle of the screen. (Bear in mind that prior to this the screen was utterly blank.) The Gnome-do window said to start typing, so I typed "gnome-panel" and hit Enter. The panel appeared! Yay!

Then I launched my e-mail client, and quickly discovered that I had no window borders, no - and X in the corner, that I couldn't drag windows around, and that right-clicking on the desktop still didn't work. I knew enough to realize that this was a missing window manager. A few minutes googling revealed that the default Gnome window manager is Metacity. So I opened a terminal and typed "metacity." Presto, the windows appeared normal again.

So then I rebooted and logged into Gnome. The panel and window manager were not running. So I used Gnome-do to start them, then went into System > Administration > Startup Applications and added Metacity and Gnome-panel. When I rebooted my desktop was back to normal.

The big question is, why in the world would the dist-upgrade from Intrepid x86_64 to Jaunty x86_64 decide that I didn't need a Gnome panel or a window manager? Very strange, that.

---

### Post by sergius248 on 2009-07-12
I had a very similar problem with my set-up (AMD-64).
I could not find the causes. Using Alt-F2 I however managed to launch "RUN" with the command line "gnome-panel --replace". My gnomepanels returned and I installed using Ubuntu Tweak -> Autostarts a new command line "gnome-panel --replace"(I guess the same would be possible by manually editing "/home/*user*/.config/autostart")that restart the Gnome-Panels everytime the system start.
As a stopgap solution it seems to be working.

Serge

---

### Post by grikdog on 2009-07-30
FWIW, 8.04 -> 8.10 -> 9.04 killed my Tracker too (corrupted index).

---

