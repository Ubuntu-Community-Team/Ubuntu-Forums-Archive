---
title: "Power Mac g4 450 dp"
date: 2006-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by ponzio on 2006-03-09
I am thinking of buying this model

[http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450_dp.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450_dp.html)

the one I am thinking of buying has 512 megs of ram. I would like to install ubuntu on it. I would like to hear what sort of experiences you have had with it, for instance is Gnome fast enough.

---

### Post by linear on 2006-03-09
Gnome is fine on older models, so should be fast enough on this one as well.

---

### Post by BoneKracker on 2006-03-12
I'm running nicely with G4 500 (agp version).  I've tested out Ubuntu with Gnome, KDE ("Kubuntu") and Xfce4 (unofficially "Xubuntu"), using both the 5.10 version and 6.04 (still in testing) version.

They all ran fine and were usable.  I found the following:

a) 5.10 Ubuntu had comparable performance to MacOS X.  After some tweaking of settings, it was appreciably faster.

b) 6.04 provides significant enhancements beneficial to powerpc users, in terms of ease of setup and speed

c) KDE seemed more Mac-like in terms of interface, but it seemed to squander resources on unimportant features.  I like it a lot and I actually switched back and forth three times, using each for a month.  You could probably run it just fine with the right "features" turned off, but Gnome or Xfce4 (or maybe even FluxBox) are probably better choices for your rig.

d) Xfce4 worked fine, and had even lower overhead than Gnome, offering a slightly noticable improvement in responsiveness, but not enough for me to opt for its use over Gnome.

Oh, and if you do choose to go with 6.04 ("Dapper"), first install 5.10 ("Breezy") and upgrade by way of the command line (sudo apt-get dist-upgrade) because the current flight has known problems for installing to PowerPCs.  You'll probably also want to tweak the X11 settings after install (in the file xorg.conf).

---

### Post by BoneKracker on 2006-03-12
I'm running nicely with almost the same machine.  Mine came out a few months later. (Only has a single 7410 processor vs. your dual 7400's, has the 4x version of your 2x r128 video card, and has the same amount of RAM).

I've tested out Ubuntu with Gnome, KDE ("Kubuntu") and Xfce4 (unofficially "Xubuntu"), using both the 5.10 version and 6.04 (still in testing) version.  Bottom line: they all ran fine and were usable.  I'd go with the stock Gnome version, and I'd upgrade to Breezy right away.

I found the following:

a) 5.10 Ubuntu had comparable performance to MacOS X.  After some tweaking of settings, it was appreciably faster.

b) 6.04 provides significant enhancements beneficial to powerpc users, in terms of ease of setup and speed

c) KDE seemed more Mac-like in terms of interface, but it seemed to squander resources on unimportant features.  I like it a lot and I actually switched back and forth three times, using each for a month.  You could probably run it just fine with the right "features" turned off, but Gnome or Xfce4 (or maybe even FluxBox) are probably better choices for your rig.

d) Xfce4 worked fine, and had even lower overhead than Gnome, offering a slightly noticable improvement in responsiveness, but not enough for me to opt for its use over Gnome.

e) Don't screw around trying to set up your zip drive.  Just make an entry for it in /etc/fstab and once you upgrade to Dapper it will just work.

Let me know if you have any challenges setting it up as I probably went through them too.

---

### Post by BoneKracker on 2006-03-12
I'm running nicely with almost the same machine.  Mine came out a few months later. (Only has a single 7410 processor vs. your dual 7400's, has the 4x version of your 2x r128 video card, and has the same amount of RAM).

I've tested out Ubuntu with Gnome, KDE ("Kubuntu") and Xfce4 (unofficially "Xubuntu"), using both the 5.10 version and 6.04 (still in testing) version.  Bottom line: they all ran fine and were usable.  I'd go with the stock Gnome version, and I'd upgrade to Breezy right away.

I found the following:

a) 5.10 Ubuntu had comparable performance to MacOS X.  After some tweaking of settings, it was appreciably faster.

b) 6.04 provides significant enhancements beneficial to powerpc users, in terms of ease of setup and speed

c) KDE seemed more Mac-like in terms of interface, but it seemed to squander resources on unimportant features.  I like it a lot and I actually switched back and forth three times, using each for a month.  You could probably run it just fine with the right "features" turned off, but Gnome or Xfce4 (or maybe even FluxBox) are probably better choices for your rig.

d) Xfce4 worked fine, and had even lower overhead than Gnome, offering a slightly noticable improvement in responsiveness, but not enough for me to opt for its use over Gnome.

e) Don't screw around trying to set up your zip drive.  Just make an entry for it in /etc/fstab and once you upgrade to Dapper it will just work.

f) The install will set up your graphics with a default "ati" driver, but I believe you need the "r128" driver (just correct the entry in /etc/X11/xorg.conf).

---

### Post by pfhortran on 2006-03-13
Ubuntu works great on my G4 400 (Gigabit ethernet), I think VBA and FCE Ultra run better in Ubuntu than Mac OSX.
but i'm having some problem with building binary's from their source code, I get a black screen then I'm end up back at the login screen.

---

