---
title: "Hoary-&gt;Breezy on iBook G4 1.2 GHz?"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by O'Blomov on 2005-10-18
Has anyone done this successfully?

I'm a little wary to because of the difficulties we had with the upgrade on Intel boxes...

---

### Post by sulobanks on 2005-10-18
Upgrade on a 400mhz imac was successful except for my decision to keep an old configuration file rather than installing the new one.  I get an error every time gdm loads telling me it's reverting to defaults.  But otherwise, everything seems to work like it should.  I'm about to try an upgrade on my ibook g4 later today after I've backed up everything. I'll post the results here.

---

### Post by refdoc on 2005-10-18
I upgraded weeks ago. Everything is working just fine.

---

### Post by refdoc on 2005-10-18
[QUOTE=refdoc]I upgraded weeks ago. Everything is working just fine.[/QUOTE]

Sorry, forgot to mention what I am running it on - ibook 12" G4 1.2 MHz 768MB, 80GB HDD, bluetooth and sleep working all fine

---

### Post by sulobanks on 2005-10-18
My upgrade today failed miserably.  Crashed trying to upgrade openoffice 2.  Tried to uninstall openoffice 2, but at that point I had a halfway upgraded system and things weren't very stable.  So every time I tried to uninstall openoffice, synaptic crashed.  This was no problem except being a huge waste of time.  I'm sticking with my tried and true method of doing a fresh install rather than upgrading.  I keep a separate /home partition on my disk for just this purpose (I still back up anyway, just to make sure).  I also had plenty of universe and multiverse apps installed on my system, so I actually would have been very surprised had it worked.

The imac I upgraded was a recent install of hoary and had very few additional apps installed, so that upgrade went fairly painlessly.  But my ibook (which I use constantly) was not the same story.

---

### Post by refdoc on 2005-10-18
And I just realised i had told a lie - bluetooth has ceased working during one of teh recent upgrades. 

The device is not anymore found for reasons unknown to me...

---

### Post by craks on 2005-10-18
i have upgraded from hoary to breezy successfully using breezy iso, you may follow the step of official update guide.

i removed openoffice and install openoffice, i works fine for me.

ibook, new g4, 1.2hz

---

### Post by O'Blomov on 2005-10-25
Hi all,

It's beholden upon me to give feedback - so here's my experiences:

This is probably a dupe but it might be valuable to document it:

[LIST]
[*]Firstly I downloaded the installation ISO and burned it.
[*]Then I removed all of the non-supported packages for re-installation.
[*]Inserting the installation CD caused synaptic to detect it as a repository support.
[*]By marking and installing all upgrades I nearly * had a clean upgrade
[/LIST]

* Complaints about the local appeared in several package installs.
A quick 
$ sudo locale-gen 
fixed this (same thing on Intel install, curiously!)

Working and tested so far:
[LIST]
[*]- Autosuspend when closing the lid and re-opening it now works!!! Mucho kudos to Ubuntu/Debian/kernel developers for this.  It's never easy but you got there! :KS 
[*]- Function keys for sound, brightness and ejection of CDs
[*]- Open Office 2 - big improvement here IMHO.:D   Still crashes on certain long and complex Word documents however :( 
[*]- Not sure but power and fan management seems a little better.
[/LIST]

---

