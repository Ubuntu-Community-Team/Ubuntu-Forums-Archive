---
title: "Flash problems"
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by theh0g on 2007-10-18
I have a problem: every time I install something with Synaptic or if screen saver runs or a game, flash won't work in Firefox (Firefox freezes) and I have to reinstall flash. It's REALLY annoying. I'm running amd64 version of Gusty, I've tried to delete flash files and reinstall, also some scripts people are putting out, nothing seems to work. Can anyone please help me with this?

---

### Post by Jukums on 2007-10-18
have you tried gnash?
I'm using 32-bit firefox with flash already from feisty on 64-bit ubuntu, but then on kernel update there was no sound anymore.

Now when I've upgraded to gutsy my 

64bit firefox runs with gnash(alternate flash player) - though I think I cant rewind or fastforward on youtube, tho it still runs ok

32bit firefox runs with adobe, and it doesn't crash!

---

### Post by steveneddy on 2007-10-18
I upgraded my 64 bit Feisty to 64 bit Gutsy last night and this morning I noticed the same issue. I had to remove mozilla-firefox and the ndiswrapper and reinstall flash-nonfree. I also had to disable the Firefox extension ubufox. 

No Flash sites would work correctly and would lock up my Firefox.

:popcorn:

---

### Post by whoop on 2007-10-18
I had problems with flash in gutsy 64bit. Maybe this is what you did but it helped me.
remove nspluginwrapper via synaptic. install flashplugin-nonfree via synaptic (this will automatically install nspluginwrapper again).

---

### Post by Kilz on 2007-10-18
> **theh0g said:**
> I have a problem: every time I install something with Synaptic or if screen saver runs or a game, flash won't work in Firefox (Firefox freezes) and I have to reinstall flash. It's REALLY annoying. I'm running amd64 version of Gusty, I've tried to delete flash files and reinstall, **also some scripts people are putting out, **nothing seems to work. Can anyone please help me with this?

What scripts did you try for Gutsy?

---

### Post by theh0g on 2007-10-18
> **Kilz said:**
> What scripts did you try for Gutsy?
I dunno, I downloaded something from some Dutch website, it was linked there from this forum. I've noticed your script, but from what I read, it's not for Gutsy and reporting a bug won't help, since same bugs are already reported (and no, keep posting same reports won't help, developers hate that).

---

### Post by Slurm on 2007-10-18
Hey,  

Just wanted to let you know I am having the exact same problems.  I just installed Gutsy and my gnash is causing Firefox to hang up every time.  I am even having trouble with Synaptic because it is hanging also.  I think this is overuse and I will try to get that up and running later.  


Slurm

---

### Post by theh0g on 2007-10-19
Well my Synaptic works fine and am not using Gnash. Well, I do understand ther might be a problem, but what I don't understand is that business does Synaptic have with Flash, when I install something else? What  does flash have to do with my nvidia driver - if I run screen saver or a game (ETQW), flash won't work. Feels like Windows all over again.

---

### Post by LiMaO on 2007-10-19
If you people really want a flawless install of flash + java, the best way (for now) is still to use a 32bit browser, like firefox.

If you want a reliable script to use to get it running, check out this thread:

[http://ubuntuforums.org/showthread.php?t=575237]("http://ubuntuforums.org/showthread.php?t=575237")

Works on Gutsy. Tested by dozens of people. And I'll be here if someone happens to have any problem with it =)

If it does NOT work for you, PLEASE let me know of it. I still have not received a single complaint about it not working, but if it happens, I'll be glad to try and fix it.

---

### Post by bford16 on 2007-10-20
> **whoop said:**
> I had problems with flash in gutsy 64bit. Maybe this is what you did but it helped me.
remove nspluginwrapper via synaptic. install flashplugin-nonfree via synaptic (this will automatically install nspluginwrapper again).

I also had problems with Flash after upgrading from Feisty to Gutsy.  This method solved the problem.

---

### Post by esunday on 2007-10-21
This was making me crazy, plus sites like gmail wouildn't run for me either, but here's a so-far real good and stable solution:

With Synaptic, do a search on Firefox and install Firefox3  (I know, I know, who knows?)

Everything works, and all my add-ons and plugs are working fine.

Cheers.

---

### Post by lasanialois123 on 2007-10-21
hi,

I have problem only with flash charts on [http://finance.google.com/finance?q=NASDAQ:GOOG](http://finance.google.com/finance?q=NASDAQ:GOOG) , everything else works great (youtube etc). I use 32bit ubuntu 7.10 and cannot solve problem with methods you guys have tried. 
Any idea? 

wish you all great day,
lois

---

### Post by lasanialois123 on 2007-10-22
hi,

my soultion is that i have renamed  directory /home/yourusername/.mozilla to  /home/yourusername/.mozilla.old and restart firefox. Next time firefox see flashy webpage it will install missing plugin and start working :)

kindest regards

ps. this problem seems to be only when upgrading from ubuntu 7.04 to 7.10.

---

### Post by rknize on 2007-10-24
I have the exact same issue.  Reinstalling flashplugin-nonfree allows Adobe Flash in Firefox to work ONCE.  It locks up the next time you start Firefox and hit a page with flash on it.  The trick seems to be to clean-up the old nspluginwrapper links and binaries that are left all over the file system when you use one of the older scripts.  I upgraded from feisty.

1) apt-get --purge remove flashplugin-nonfree gnash

2) Remove all nspluginwrapper and flash links and binaries from:
/usr/lib/mozilla/plugins
/usr/lib/firefox/plugins
/usr/lib/iceweasel/plugins
:~/.mozilla/plugins

3) apt-get install flashplugin-nonfree

That did the trick for me and now it works every time.  There are other issues, like turd npviewers being left around, buy at least it works.

Russ

---

