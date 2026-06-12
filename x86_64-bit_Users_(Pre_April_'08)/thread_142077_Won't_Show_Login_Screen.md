---
title: "Won't Show Login Screen"
date: 2006-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by zeroreflex on 2006-03-09
I own a Blue/White G3 upgraded to G4 and use os X.  A few months ago I installed ubuntu and it worked fine.  Of course a few hours of messing around since these machines don't like linux much.  Well, anyway for the last few days I have been trying to install it again since I took it off.  Everytime I finish installation, it goes to load the login screen and I see the spinning cursor, then it stops and freezes.  No login. No Desktop.  I have a feeling it has something to do with the video since I sometimes see artifacts.  I have an ati 7000.  Is there anykind of generic setting I can change it to in the xorg.conf file or any other fix for this?  Maybe someway when I am installing ubunutu to manual set video prefs?  Please help, I have been working on this for days.

---

### Post by jdp on 2006-03-09
Is the date right?  There is a known bug with Gnome not starting if the date is not something sane.  Searching for **gnome date bug** will yeild results, buty it's fairly wasy to check the date and make sure it's normal, esp. if you have OS X.

If you keep losing the date/time when you unplug your tower, replace the PRAM battery.  It's a 1/2AA Lithium 3.6v, which you can find for $5-10 in various places.  Radio Shack will charge you and arm and a leg and a spare kidney for one, like $14.95 or something.

---

### Post by zeroreflex on 2006-03-09
yeah I have looked into the date bug problem.  I am set on a video driver problem.  After a clean installation, the ubuntu loadin screen comes up, then names off some errors in the top about not finding xfonts and some other things..(will find this info) then the spinning cursor comes up, spins a few times then freezes.  I was able to take the harddrive out and put it into another computer and edit the xorg.conf file.  It has ati as the driver, but there doesn't seem to be anything at the bottom of the file depicting options for the video card.  I seem to remember that last time I installed ubuntu and played around with it  I will try to attach all the errors and my xorg.conf file shortly.

---

### Post by ssam on 2006-03-10
can you press CTRL+ALT+F1 and log in?

sometimes running
```
sudo dpkg-reconfigure xserver-xorg
```
and answering the questions helps. (the default answers are usually right)

---

