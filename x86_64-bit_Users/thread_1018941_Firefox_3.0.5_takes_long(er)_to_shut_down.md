---
title: "Firefox 3.0.5 takes long(er) to shut down"
date: 2008-12-22
forum: x86 64-bit Users
---

### Post by whoop on 2008-12-22
Firefox takes a lot more time shutting down than it used to on my 8.10. When I shut it down it takes at least 5 seconds to shut down. While it is shutting down I can hear/see a rise in disk activity.

Anybody else have this? Any ideas/solutions?

---

### Post by dcstar on 2008-12-23
> **whoop said:**
> Firefox takes a lot more time shutting down than it used to on my 8.10. When I shut it down it takes at least 5 seconds to shut down. While it is shutting down I can hear/see a rise in disk activity.

Anybody else have this? Any ideas/solutions?

I have noticed that FF 3.0.5 also takes longer to close on my 8.04 system, so I assume it is some new code that they have added to clean up any potential security holes etc.

If it is a major problem, report it as a bug and it may get addressed on the next release.

---

### Post by Thelasko on 2008-12-23
Do you actually see Firefox open during this time?  When hit the close button, the "window" closes fast.  I don't know what it's doing after that.

---

### Post by whoop on 2008-12-23
Firefox is open during this time.

---

### Post by Thelasko on 2008-12-23
> **whoop said:**
> Firefox is open during this time.

Mine is very fast, but I'm running Flash 10 for 64-bit Alpha, as well as the new 64-bit Java plugin.  Perhaps your issue is related to one of those?

---

### Post by fjgaude on 2008-12-23
How many tabs are open when it takes so long... I've noticed the more tabs the longer times.

---

### Post by stchman on 2008-12-23
I notice that Firefox takes no longer to close than before no matter how many tabs are open.

---

### Post by stchman on 2008-12-23
> **Thelasko said:**
> Mine is very fast, but I'm running Flash 10 for 64-bit Alpha, as well as the new 64-bit Java plugin.  Perhaps your issue is related to one of those?

I too run the 64 bit Flash 10 and it runs extremely well.  No gray, no covering up menus, etc.  For Java plugin I use Icedtea and for the very few Java enabled sites I go to I find it works very well.

---

### Post by tomdkat on 2008-12-23
I've noticed Firefox 3 takes much longer to close now that I've got the 64-bit Flash 10 plugin from Adobe installed.  I usually have 5 tabs (at least) open at any given time and now when I exit Firefox, I get the "wait/force quit" box as the disk churns madly.  Eventually Firefox closes on its own.  This never happened before installing the Flash plugin from Adobe so I'm attributing the behavior to that.

One of the tabs I have open is for my Hotmail e-mail account and Flash ads display in it, which means the Flash plugin is active when I close Firefox.

Peace...

---

### Post by whoop on 2008-12-23
I can not confirm that completely tomdkat. when I close all firefox windows but keep my firefox download window open and close it as the last window; it will also take a long time and I can also detect disk activity.

---

### Post by tomdkat on 2008-12-24
> **whoop said:**
> I can not confirm that completely tomdkat. when I close all firefox windows but keep my firefox download window open and close it as the last window; it will also take a long time and I can also detect disk activity.That's because the download window keeps the Firefox process fully loaded.  When you finally close that, the Firefox process will terminate and the disk activity is Firefox releasing resources back to the OS in an attempt to terminate gracefully.

I guess a "good" test would be to make your home page something that doesn't have any Flash or Java content on it, like [http://www.mozilla.org/](http://www.mozilla.org/) .   Start Firefox with this "bland" home page, don't visit any sites, then close Firefox and see how long it takes for the window to close.  Then, restart Firefox and open a terminal window and enter the command "top" to see how much memory Firefox is using when you first start it WITHOUT loading any Flash or Java content.

Peace...

---

### Post by fredbird67 on 2009-01-14
I too am having something similar -- no big deal, but it is annoying.

In my case, I've got Firefox 3.0.5 running Ubuntu Hardy Heron, but I'm on 32-bit hardware.  Anyways, whenever I close Firefox, I've noticed a delay of 3 or 4 seconds, and then it gives me the dialog box that has buttons labeled "Wait" and "Force Quit".  However, that window is up for like only a second or so, and then Firefox gracefully quits on its own.  Weird...

Fred in St. Louis, MO USA

---

### Post by sonicb00m on 2009-01-25
All my computers that have been updated now display this behaviour. I usually get a "force quit" dialog but if i click "wait" it shuts down normally after a while.

---

### Post by Ev1L on 2009-02-11
same behavior for me as well.
this happens independently by the number of tabs.
if for someone it's not happening, then i assume it's due to some plugin

---

### Post by Clancy_s on 2009-02-12
Just passing, but for the record it's not happening for me.  Ubuntu 8.10 64 bit, all updates, FF 3.0.6

plugins: noscript, flashblock, flashget, adblock plus, leetkey, foxmarks, Ubuntu extras.

---

### Post by blisterpeanuts on 2009-02-17
Same here.  It takes so long to shut down that Gnome posts a dialog saying it's "taking too long--terminate or wait?"  I just ignore it and after about 10-15 secs it's gone.  Strange.

---

### Post by ubun_two on 2009-03-06
My wife experiences this on her laptop (was on Hardy...now on Intrepid).

On my 64bit desktop, I don't experience this issue, however...

---

### Post by ceverett on 2009-04-04
I have a different problem.  The window closes right away, but firefox stays running in the background, soaking up RAM :mad:

---

