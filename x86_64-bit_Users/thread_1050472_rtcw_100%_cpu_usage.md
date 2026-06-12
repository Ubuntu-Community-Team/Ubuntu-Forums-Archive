---
title: "rtcw 100% cpu usage"
date: 2009-01-25
forum: x86 64-bit Users
---

### Post by xoros on 2009-01-25
Hmm.. when I play the linux version of rtcw on my xubuntu 8.10 64bit install,  gnome-system-monitor shows 100% cpu usage on just 1 core (I have 4 total.)

Yet, in htop it doesn't show 100% usage,  any ideas why this is happening?  No big deal I guess, just would like to know.

---

### Post by janu002 on 2009-11-06
If you've tried all of the above and nothings worked, the next thing to try is to see if:
a)  is  there some corrupted file running loose in the background,
b)  is the machine simply bogged down with too many apps. running concurrently.
 
First, hit CTRL-ALT-DEL and look at the Task Manager processes to see if any odd item is bogging down the processor. If it's just the game doing that, I wouldn't be surprised, but that's normal. Games do that. I would look for some other file and if there is one, make a note of it's name. It could be useful in the next step.
 
The next thing I would do is run Msconfig and either un-check the "Load startup items" under the General tab, or hit the Startup tab on the far right then selectively un-check the various programs which start at boot time. 
 
Reboot then see if the problem still occurs. If not then you know that either too many things are running at one time, or one of the programs you prevented from starting has a problem and needs to be uninstalled or reinstalled.
 
This method works for me most of the time, and if there is a virus, spyware, or simply a corrupted file, you can narrow down your list of checked items till the one you're looking for becomes apparent.
==============================
[shapewear](http://www.laurensilva.com)
[Unsecured Business Loans](http://www.cashwf.com/small-business-loans)

---

### Post by P.KO on 2009-11-06
Hi,

Since when is xubuntu being a Windows version? :lolflag:

And this is a rather old thread.

---

### Post by JugglinPhil on 2009-11-06
> **janu002 said:**
> Task Manager
Msconfig

Haha dude this is not Windows, did you get lost?

---

