---
title: "One CD install is a joke"
date: 2007-10-07
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 67GTA on 2007-10-07
I was expecting to install opensuse with one cd like most other distros. I didn't add or remove anything in the software section, and I noticed it was downloading packages to install. After going back and looking through the software to be installed by default, there were hundreds of apps that I didn't need. I tried to mark them as "do not install", but I guess the way the system is built there are too many dependency problems to just get a base install. I downloaded the KDE CD, and over half of the apps were under Gnome. I give up on SUSE.

---

### Post by -grubby on 2007-10-07
there is no reason anything would need over 2 CDs if it's supposed to be a "normal" 1 app for 1 thing install

---

### Post by 67GTA on 2007-10-07
I thought opensuse was going for that idea with the 1 CD install, but they still have all the software and apps marked for default installation that the 5CD/1DVD install does. I was going to buy a DVD because I was at 11,000 MB of my 12,000 MB limit for bandwidth usage this month. I got bored today and I figured I would have enough bandwidth left to finish getting my install setup after downloading the CD iso without going over. It wanted to download an additional 650 MB of stuff to finish the install.

---

### Post by RedDwarf on 2007-10-07
> **67GTA said:**
> I was expecting to install opensuse with one cd like most other distros. I didn't add or remove anything in the software section, and I noticed it was downloading packages to install.
When the installer asks if you want to add online repositories say no and it will no download anything.

---

### Post by coffeecat on 2007-10-07
> **67GTA said:**
> One CD install is a joke

Could you tell us the punch-line? I need cheering up. :(

---

### Post by twinklellon on 2007-10-09
I did install openSUSE by openSUSE-Gnome CD only; There really was a option that you can choose not to add online repositories so that it would not download anything during the installation.

> **RedDwarf said:**
> When the installer asks if you want to add online repositories say no and it will no download anything.

---

### Post by 67GTA on 2007-10-09
One would assume that it would only setup the online repos before installation, and not try to install everything from a DVD installation. They are misleading with this. Just because you are given the option to set up your repos before installation, shouldn't  mean that the installer automatically tries to download anything else besides what it on the "one cd". You are given the same option with the DVD install. Maybe they should have included a box to check if you REALLY only wanted to do a one cd install with your one cd.

---

### Post by RedDwarf on 2007-10-09
> **67GTA said:**
> One would assume that it would only setup the online repos before installation
It's the first step... obviously is placed there because it wants to download things from it.

Anyway... yes, it could be better handled.

---

### Post by 67GTA on 2007-10-09
> **RedDwarf said:**
> It's the first step... obviously is placed there because it wants to download things from it.

Anyway... yes, it could be better handled.

I always assumed that it was just to make setting up the repos, and updating easier, and not to download everything to emulate a DVD installation when you clearly wanted a "one cd" install. I bet this will piss a few people off. This is their first one cd install. Maybe I'm being a little too hard on them, but I just expected more.

---

### Post by igknighted on 2007-10-09
> **67GTA said:**
> I always assumed that it was just to make setting up the repos, and updating easier, and not to download everything to emulate a DVD installation when you clearly wanted a "one cd" install. I bet this will piss a few people off. This is their first one cd install. Maybe I'm being a little too hard on them, but I just expected more.

Anyone who has ever used Suse should know that the "default" setup has way too much installed.  That's the beauty of the suse installer, because you can go in and select the bare minimum of what you want installed.  You could install a base, cli only system or install everything, your choice.  You just need to take advantage of all the tools the installer gives you.

---

### Post by 67GTA on 2007-10-09
I guess Ubuntu has spoiled me. I have tried every suse release since 10.0. I want to, but I just can't get into it. I'm downloading Mandriva 2008 now.

---

### Post by igknighted on 2007-10-09
> **67GTA said:**
> I guess Ubuntu has spoiled me. I have tried every suse release since 10.0. I want to, but I just can't get into it. I'm downloading Mandriva 2008 now.

I just installed it... very impressed so far.  Recognized all hardware (including the widescreen that other distros *cough*gutsy*cough* don't), runs quick, looks great, and the config tools are excellent as always.  I have found a few annoying bugs (aspell tried to use russian despite my english localization, repo's don't seem to all be up yet), but I'll give it a bit to work them out because this release seems top notch.

NOTE: I am using the KDE One CD.

---

### Post by coffeecat on 2007-10-09
> **igknighted said:**
> including the widescreen that other distros *cough*gutsy*cough* don't

:) 

I should imagine that's down to the graphics card you're using. I had no problem with my 1680x1050 WS monitor + Nvidia Geforce 6200 card with Gutsy Beta. Well - once I had changed the resolution in System > Preferences that is. At least I didn't have to go rummaging around in xorg.conf with a text editor.

Anyway - downloading the Suse DVD atm. I gave up on Suse after the 10.1 update manager debacle and I'm looking forward to trying this one out.

---

### Post by Erunno on 2007-10-09
> **67GTA said:**
> I'm downloading Mandriva 2008 now.

Same here. I'm really curious about Mandriva since I actually never used it before and it is lauded as one of the last great KDE distributions. Thank god I still have that partition with openSUE 10.3 GNOME on it ;-)

EDIT:

I almost aborted the download when my eyes spied "XFS no longer used" in the release notes. But they were talking about the X Font Server *phew*

---

### Post by igknighted on 2007-10-09
> **coffeecat said:**
> :) 

I should imagine that's down to the graphics card you're using. I had no problem with my 1680x1050 WS monitor + Nvidia Geforce 6200 card with Gutsy Beta. Well - once I had changed the resolution in System > Preferences that is. At least I didn't have to go rummaging around in xorg.conf with a text editor.

Anyway - downloading the Suse DVD atm. I gave up on Suse after the 10.1 update manager debacle and I'm looking forward to trying this one out.

Yeah, it worked after using the xorg config tool... but Mandriva did it automatically.  I don't much care for that clumsy config tool in gutsy, I want a smooth one like in mandy or else forget it, let me just edit the file myself.

The problem is perhaps partially to do with the vid card (nvidia), but more to do with Gutsy doing a poor job querying the monitor for its capabilities.  The vid card is more than capable, and the tools are out there for xorg to query the monitor properly for its ideal resolution and use it... distro's like Mandriva and Fedora get this, others (and Ubuntu is just one of many examples here) do not.

---

