---
title: "Can't get splash to work at startup..."
date: 2007-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by jeremy1138 on 2007-10-28
I've looked all over and I can't seem to find any kind of direct answer to my problem.  I recently installed Ubuntu 7.10 (clean install) on my HP dv5020us notebook.  It has an AMD Turion 64 Bit processor (1.8 GHz) with the ATI Radeon Xpress 200M video card and 1GB of RAM.  When I start up I see first the GRUB boot loader (I have a dual boot system), then I see the Ubuntu progress bar with the black background, then all I see is a black background with an "X" cursor, then some flickering and my desktop pops up never having shown the Ubuntu splash screen.  This splash screen used to work for me when I had v7.04 but it doesnt work now.  My native resolution is 1280x800 and I've changed that in my usplash.conf file and I've also installed the start-up manager.  I'm not really sure what else to do.  Does anyone have any idea how I might fix this?  Please keep in mind that I'm still fairly new at this so use small words...  :)  Thanks for the help!

---

### Post by Therion on 2007-10-28
It appears to be a bug in the 64bit version of Gutsy.  Lots of people are reporting this problem.  

You can read through some of [[color=blue]these threads[/color]]("http://ubuntuforums.org/search.php?searchid=30045563") though, and maybe find a solution.  I gave up and just live without a boot-screen.  Maybe you'll have better luck.

---

### Post by jeremy1138 on 2007-10-28
Thanks for the info!  So no word on how to fix it?  Do I just have to wait until there's an update to fix it?

---

### Post by devzero on 2007-10-28
Hi,

Be glad, that your pc boots trough a bugged splash screen.
Mine hangs at all if it wants to show it.
So i needed it to entirely disable it

---

### Post by jeremy1138 on 2007-10-28
That's rough.  Did you change the resolution in your usplash.conf file?  Mine kept hanging until I did that...  The splash still doesn't work but at least it doesn't hang up on me...

---

### Post by Excalibre on 2007-10-28
> **Therion said:**
> It appears to be a bug in the 64bit version of Gutsy.  Lots of people are reporting this problem.  

You can read through some of [[color=blue]these threads[/color]]("http://ubuntuforums.org/search.php?searchid=30045563") though, and maybe find a solution.  I gave up and just live without a boot-screen.  Maybe you'll have better luck.
What did you search for? (VBulletin only caches search results for a short period but I'd like to see those threads myself.)

A fresh install of Gutsy 64-bit shows no splash screen for me, either, but I don't see a progress bar either. The resolution was already set correctly for me, but nothing displayed and my monitor shut off. I ended up turning off "quiet" just so at least I'd have something to look at . . .

---

### Post by Saint Angeles on 2007-10-28
> **jeremy1138 said:**
> That's rough.  Did you change the resolution in your usplash.conf file?  Mine kept hanging until I did that...  The splash still doesn't work but at least it doesn't hang up on me...

this worked for me too... i have a widescreen monitor and usplash.conf was set at 1440x1440 instead of 1440x900. for somereason, my computer detects 1440x1440 as a possible screen resolution.

---

### Post by DaveRM on 2007-10-28
This post solved the problem for me.

[http://ubuntuforums.org/showpost.php?p=3603872&postcount=35]("http://ubuntuforums.org/showpost.php?p=3603872&postcount=35")

DaveRM

---

### Post by jeremy1138 on 2007-10-28
Yeah I tried that before and it didn't make it any better.  Thanks though.

---

### Post by Excalibre on 2007-10-28
Doesn't work for me. My monitor is 1280x1024 and I tried the settings for both that and 1024x768 and nuthin'.

---

### Post by Therion on 2007-10-28
> **Excalibre said:**
> What did you search for? (VBulletin only caches search results for a short period but I'd like to see those threads myself.)
Go into Advanced Search and use Black+Screen as your search criteria in the x86-64bit section.  There are a lot of people experiencing problems with getting a "black screen of death" or other problems getting a boot-screen.

Personally, I've tried everything, and still no joy.  I've just learned to live without a boot-screen for now.

---

