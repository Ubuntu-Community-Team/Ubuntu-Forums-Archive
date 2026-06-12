---
title: "amd64 &amp; ati xgl problems"
date: 2006-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by bbbbbtony on 2006-09-17
hi, i'm running an amd64 laptop with an ati 9700 128mb vidcard. i've tried a few different howto's for xgl and i found [http://www.tectonic.co.za/view.php?id=1153](http://www.tectonic.co.za/view.php?id=1153) was pretty good. when i type in compiz-manager it gives me the following output in the terminal:
bbbbbtony@apt:~$ compiz-manager
bbbbbtony@apt:~$ Couldn't load settings.  Reverting to defaults.

** (cgwd:17018): WARNING **: Cannot open pixmap: unshade

** (cgwd:17018): WARNING **: Cannot open pixmap: above

** (cgwd:17018): WARNING **: Cannot open pixmap: unabove

** (cgwd:17018): WARNING **: Cannot open pixmap: sticky

** (cgwd:17018): WARNING **: Cannot open pixmap: unsticky
XGL Absent, assuming AIGLX
compiz: No composite extension

so i try to select compiz through the manager again and it gives me the following output:
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
XGL Absent, assuming AIGLX
compiz: No composite extension

when i first log into ubuntu it tells me that the xserver is messed up so i tell the error message that i don't want to look at the output, then another message pops up saying gdm has been stopped, start up again when i correct erros. i hit ok and it loads into ubuntu perfectly. well except for all the errors. 

it'll load the manager just fine but when i try to change from metacity to compiz it gives me that output. any ideas what the problem could be? thanks.

---

