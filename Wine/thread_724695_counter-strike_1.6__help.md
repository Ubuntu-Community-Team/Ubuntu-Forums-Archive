---
title: "counter-strike 1.6  help"
date: 2008-03-14
forum: Wine
---

### Post by phoenix5002 on 2008-03-14
There is 1 bug that I have with counter-strike 1.6 using wine.
It's actually several bugs, but they all seem related and it seems like a fix for one of them is a fix for all.

The problem is that some images don't show up right.  Here are some screenies:
[http://img150.imageshack.us/img150/4750/imagebuglp7.jpg](http://img150.imageshack.us/img150/4750/imagebuglp7.jpg)

I am only concerned with the ones on the right.  The two on the left just demonstrate other areas the the (possibly same bug) appears.
now...the 2 images on the right, while obstructive, aren't too dramatic and in fact I would actually be happy if I could get it to look like that all the time.  However, 80-90% of the time while looking through a scope the entire screen is black and it occasionally goes to one of the screens you see in the image.  I didn't take a screenshot of the black screen because I'm sure you can imaging what that looks like (NOTE: when the screen goes "black" it's just the area where the scope would be, the HUD is still completely intact.)

the image in top left should have a "VAC secured" image thingy there.  and the one beneath that should have an add in the top left corner of the screen.

I don't mind if the scope looks like crap, I just would like to make it at least useable, but when the screen goes black it's impossible to use.

I something in the terminal that might help pinpoint the problem:
**Corrupt JPEG data: 57 extraneous bytes before marker 0xdb**

please offer any suggestions.

---

### Post by phoenix5002 on 2008-03-14
...perhaps a hack that removes the scope image?.... :-& :-$

---

### Post by Vadi on 2008-03-14
Oof. This should go into the wine subforum ([click]("http://ubuntuforums.org/forumdisplay.php?f=313")), or even better, the appdb page for CS ([click]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507")).

Try doing "wine --version" in the terminal, what does it say?

---

### Post by phoenix5002 on 2008-03-15
of course, I can't believe I didn't put this in the wine section, after all that's more than likely what I'm having issues with.

Well anyway...

*wine --version*
**wine-0.9.46**

---

### Post by schlorri on 2009-01-30
Hello,

I have the same error on Debian Lenny with wine-1.1.13. I've got no idea how to fix it. 

I need Help!

best regards

schlorri

---

