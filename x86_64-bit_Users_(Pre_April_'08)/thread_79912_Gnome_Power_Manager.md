---
title: "Gnome Power Manager"
date: 2005-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by pjs_flyer on 2005-10-21
Hi

Whilst pretty much everything so far has worked "out of the box", one of the things I can't get to work properly is Gnome Power Manager.  I installed it via Synaptic and get the following message on starting it up or editing it:

"You have not got DPMS support enabled in gnome-screensaver. You cannot change the screen shutdown time using this program".  I'm actually using x-screensaver, and DPMS appears to be enabled in the options here ( tried installing Gnome-Screensaver instead, but this didn't seem to work)

(I note that another user reported this message on 5.04 - [http://www.ubuntuforums.org/showthread.php?t=73251](http://www.ubuntuforums.org/showthread.php?t=73251))

If I start it from from system>preferences>power preferences, then GPM then doesn't have any options available - the options tab is blank, for example - and it doesn't appear/cannot be put on the task bar and doesn't appear in the notification icon.  This is fixed by starting it from a shell, although the "computer sleep type" option under "advanced" is still blank.

I note on the Gnome Power web page that Hal 0.5.4 or better is needed - Breezy (or my Breezy) has 0.5.3.  Wouldn't have thought it would be, as the Breezy version of GPM seems to be an earlier one that only needs (I thnk) 0.5.2.

I've had a look in synaptic and whilst hal and hal-device-manager are loaded, hal-doc isn't (nor is dbus-glib-doc). Is this another potential cause?

For info, I'm running Breezy on an Amilo 1630 (AMD64)

Thanks in advance!

P

---

### Post by furchi on 2005-10-26
Hi,

I've got the same problem with my breezy installation on a toshiba notebook.
During the first days of use, I could solve the problem by restarting the gnome-screensaver, but after a system update restarting the screensaver has no effect anymore.

I hope that somebody has an idea how to solve this problem, because it would be really useful to turn off the display with DPMS...

thanks
furchi

---

### Post by soul_rebel on 2005-10-26
uninstall it.

It is not ready. You don't want it right now.

---

### Post by Cannedbread on 2005-10-28
I just installed it and it successfully allows my computer to suspend to ram and it recognized that i have two batteries installed. it is also giving me the DPMS error. any idea when it *will* be ready? because there doesnt seem to be anything else with this kind of functionality.

---

### Post by timetunnel on 2005-11-16
I've got the same problem on a Thinkpad R52. I definitely need gnome-power-manager, because when it's not installed, supend to RAM on lid close won't work. 

So, any news or tweaks here?

Thanks,
Jens

---

### Post by hughsient on 2005-11-27
Hi, gnome-power-manager should be run with an up-to-date HAL, as it uses lots of adavnced stuff that wasn't present (or not working properly) in HAL 0.5.3. Please open a bug in GNOME Bugzilla if there are problems with any aspect of g-p-m with HAL 0.5.5.1. Thanks, Richard Hughes.

---

