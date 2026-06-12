---
title: "Compiz"
date: 2008-06-30
forum: openSUSE and SUSE Linux Enterprise
---

### Post by n8ek on 2008-06-30
when ever i start suse compix failed to start so i went to yast>system>/etc/systemconfig editor>desktop>window manager>default_wm and changed it to compiz now when i start suse i get a black screen no text nothing?

What can I try to return my default dekstop?

Thanks in advance

---

### Post by Growbag on 2008-07-02
I had that problem with the RC version.

I resorted to deleting all the config folders in my home folder to return it to default.

I think if you enable the kwin effects (from the control center "desktop effects" thing), THEN enable Compiz, it causes a problem.

For KDE3 I would delete the .kde folder, for KDE4 delete .kde4 folder (or maybe both!).

You will of course lose ALL desktop settings!

Logout then back in again, it should fix it.

---

### Post by prshah on 2008-07-02
> **n8ek said:**
> when ever i start suse compix failed to start so i went to yast>system>/etc/systemconfig editor>desktop>window manager>default_wm and changed it to compiz now when i start suse i get a black screen no text nothing?
What can I try to return my default dekstop?


Compiz is not a desktop manager. To get back your desktop temporarily, switch to a virtual terminal with ctrl+alt+f1, log in as usual, then give the command```
/etc/init.d/kdm start
``` Switch back with Ctrl+Alt+F7 and you should find everything as it was before. Now perform the same steps as you have done, but change the default window manager back to kdm.

To get compiz running automatically, add it to your startup sessions list.

---

### Post by some-guy on 2008-07-03
To use compiz, disable kwin effects, then run 'simple-ccsm', if it's not there, install it (available in oss repo, as well as X11:XGL and home:cyberorg), then click 'Enable Desktop Effects'

---

### Post by RebounD11 on 2008-07-03
and while you're there I'd recommend installing fusion-icon too, since it is an easier way to control what WM and window decorator you are using and to configure Compiz plugins and Emerald themes... and also install compizconfig-settings-manager (ccsm) that you can start with the fusion-icon applet.

---

