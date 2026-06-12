---
title: "How to install mythtv on 5.10 Breezy 64-bit?"
date: 2005-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by SleepyHollow on 2005-11-06
Hi there,

since i convinced my PVR350 to work after the ivtv-setup, i also want to have a nicer tv-environment.

Every tipp including some hints for useful TV-recording / viewing programms is welcome. 

In the meantime i tried to install MythTV: The installation procedure via apt-get fails because of some unsolved dependencies.

Is there anyhow a way to fix this mess? Some workaround? A Guide for installing mythtv in an 64-bit environment like breezy?

Thanks in advance,
sleepyhollow

---

### Post by RAOF on 2005-11-06
The Breezy mythtv packages in the repositories are broken.  You can build them yourself from source, by using the instructions [here]("http://ubuntuforums.org/showthread.php?t=74660").

---

### Post by mcewen98 on 2005-11-06
[QUOTE=RAOF]The Breezy mythtv packages in the repositories are broken.  You can build them yourself from source, by using the instructions [here]("http://ubuntuforums.org/showthread.php?t=74660").[/QUOTE]

Just my luck.  I just formatted my machine and put breezy on with the hopes of setting up mythtv.  And of course the site to download the firmware for my hauppauge card for ivtv isn't working either.

Anyone have any idea when the breezy mythtv packages will come back?

---

### Post by RAOF on 2005-11-06
No idea.  If you desperately can't compile those source packages, I could send you the ones I've built.  They seem to work, but I can't actually test them because my DVB card is not quite supported by the linux-dvb modules yet.

I just built the packages by following those instructions, so it should be easier for you to build them yourself.

---

### Post by mcewen98 on 2005-11-07
[QUOTE=RAOF]No idea.  If you desperately can't compile those source packages, I could send you the ones I've built.  They seem to work, but I can't actually test them because my DVB card is not quite supported by the linux-dvb modules yet.

I just built the packages by following those instructions, so it should be easier for you to build them yourself.[/QUOTE]

I have no problem with trying to build them myself, but would it get recieve updates with apt-get doing it that way?

---

### Post by RAOF on 2005-11-07
Yes, actually, you should.  Because what you're actually building is the packages as they (should) appear in the repo's, they've got all the versioning information and they'll slot themselves nicely into apt's database.

---

### Post by mcewen98 on 2005-11-07
[QUOTE=RAOF]Yes, actually, you should.  Because what you're actually building is the packages as they (should) appear in the repo's, they've got all the versioning information and they'll slot themselves nicely into apt's database.[/QUOTE]


Well, I just added multiverse to my sources.list, and mythtv .18.1 showed up using apt.  I vaguely remember doing this with warty to get it to show up.  All the plugins are there too.

So my first two lines are:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted multiverse

---

### Post by RAOF on 2005-11-07
Yes, but if you try and install them, you'll find that there are dependency problems.  Some of the packages are .18.1, some are .17, and you won't be able to install mythtv.

Once you've built the main packages, you should be able to install the plugins from the repository.

---

### Post by mcewen98 on 2005-11-07
[QUOTE=RAOF]Yes, but if you try and install them, you'll find that there are dependency problems.  Some of the packages are .18.1, some are .17, and you won't be able to install mythtv.

Once you've built the main packages, you should be able to install the plugins from the repository.[/QUOTE]

Hm, well that sucks then.  I haven't yet tried installing it, but I guess I'll be building it.. unless you're interested in sending me yours and I'll test them out ofr you.  I wonder if this is the reason my upgrade to breezy broke mythtv.

---

### Post by mcewen98 on 2005-11-07
Well I decided to try installing the version from the apt multiverse repository and it seems to work fine for me.  Other than my card not tuning right and only getting static, but mythtv itself seems fine.  I had my card kinda-sorta tuning right, but now it doesn't seem to be working at all, and is just producing static.

---

### Post by RAOF on 2005-11-08
Oh, cool!  They've fixed it then :razz:

---

### Post by SleepyHollow on 2005-11-11
[QUOTE=RAOF]Oh, cool!  They've fixed it then :razz:[/QUOTE]

No they haven't, its still the same 17/18-version-mess. :confused:

---

### Post by mcewen98 on 2005-11-13
[QUOTE=SleepyHollow]No they haven't, its still the same 17/18-version-mess. :confused:[/QUOTE]

I'm not sure what to say.  It's working great for me.  I'm working from clean install of breezy.  I don't see any 17 conflicts, although I really only use mythtv's backend and access it with the mythweb plugin

---

### Post by Drain on 2005-11-13
[QUOTE=SleepyHollow]No they haven't, its still the same 17/18-version-mess. :confused:[/QUOTE]

I really wonder why they don't update the packages - with some minor tweaking, the packages can be built, and they appear to work.  After re-reading the documentation (and getting a helpful kick in the pants from RAOF ;-) ) I got the packages built. I suppose that I'll find out if there are stability issues or other problems as I go, but can anyone shed some light on why they're not being provided by Ubuntu?

---

