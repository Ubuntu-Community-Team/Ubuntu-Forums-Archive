---
title: "New Alsa Testing -- CMedia 8788 chipset -- need help"
date: 2007-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anaximander Thales on 2007-08-16
I have agreed to test the new Alsa Driver that they tiwai and clemens ([PW Req'd - alsa bugtrack ticket](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2633)) are working on.

Seeing as how I'm posting here, I'm obviously running the 64-bit version -- and it's xubuntu.

Seeing as how I have to install the new driver to do this testing, I'm thinking I'm going to run into problems.

So, my questions right now, really center on what I need to do to be able to test this new driver.  I'm interested in testing this, for several reasons.  One, I have a sound card that has the CMI 8788 chipset.  Two, this will really help me in learning linux.

Here are the problems I see right now:
possible loss of gui, and definitely gdm, due to having to remove alsa-base and alsa-utils.

I have no problems working command line, though it'll make it difficult running back and forth between different computers to research changes.

But, is it necessary for me to remove the alsa-base and alsa-utils.  Should I remove all of alsa (I also have ia32-alsa-oss installed).  What about libasound2?

Additionally, my assumptions are that because this is a binary tar gz file (as opposed to a .deb or .rpm), there should be no problems installing the test driver.  But, since I've never done anything like this before, I don't know.  Will there be something special that I'll need to do to make the test driver compatible with the 64-bit os?

---

### Post by Anaximander Thales on 2007-08-17
Would there be a better place to submit this question?  Multimedia & Video perhaps?

Any help on this would be greatly appreciated.

---

### Post by Anaximander Thales on 2007-08-23
Alrighty -- So, seeing as how no one has an idea as to whehter or not I need to remove items to test them out ... I'll chronicle my adventures here ...

---

### Post by epsilon72 on 2007-08-23
I just signed up on this site to see how your testing goes.

I don't even have ubuntu installed (FC6 instead), but FINALLY getting the 8788 to work at all in Linux is something I'm very interested in.

---

### Post by Anaximander Thales on 2007-09-01
All right.

So far, nothing is working.

I d/l'd and  attempted an install of the alsa module  per an [e-mail](http://mailman.alsa-project.org/pipermail/alsa-devel/2007-August/002717.html).

Didn't work.  lspci still lists the device as unknown.  lsmod doesn't show the module loaded.

Removed the module, noticed that some of the files were still resident.  Assumed that the files were still on there due to the alsa-base being installed.  Removed it.  Files still listed, removed a bunch of other packages that seemed to deal with sound and the files are still listed.  Couldn't find the files -- can't be on the system, so why are they still listed??  Ran across a site that said that after removing modules, I should run depmod -a (which it seems will update the dependency file for modules).  Problem solved.

Attemted the install again.  Same problem.

On a happier note, a person that is signed up with the bugrack from alsa  has installed the driver and it's somewhat working on his machine.

I am not sure what problems I am encountering that he isn't, but I intend on asking.

---

### Post by Anaximander Thales on 2007-09-02
Made some progress for sound on my end.

removed the alsa-driver from the august e-mail.  Downloaded the mercurial September first snapshot.

Installed (./configure, make, make install), modprobe snd-cmi8788 -- and I hear that distinct pop from my speakers as the sound card engages.  Woo hoo.

So, from there, I open up Amarok to play a song.  I get a repeating note and Amarok freezes.

Kill amarok, reboot, I get a sound when the gdm screen comes up that literally sounds like some one knocking from inside my monitor -- never having had sound at startup, I have no idea what the sound should sound like.  Can't tell if it's an actual problem, but I think it is.

Try amarok again, and get the same results.

Going to look for tutes on other things to do to make sure that there isn't a problm on my end.

(this post repeated in alsa bugtrack ticket 0002633)

---

### Post by Anaximander Thales on 2007-09-18
Installed today's daily snapshot (alsa-driver-hg20070918), and got sound.

Tested in amarok and kaffeine -- both are running a little slower than normal. Gorillaz sounds a little like Isaac Hayes. Not sure how to change sample rates on anything so, not sure if I can correct that on my end. Did attempt to set playback from 2.0 stereo to 5.1 -- still only played through the left/right front speakers, but looking at your 'todo list' I see that you still haven't got that updated yet.

---

### Post by Anaximander Thales on 2007-11-07
Not much going on in the efforts on teh alsa driver --

Clemens Ladisch was having problems with getting consistent test results and had no card to work with.

To date, he has gotten a card and is working on creating a driver for it.

---

### Post by Anaximander Thales on 2007-11-12
Noticed an update on the Alsa project site -- cladisch is doing a complete rewrite of the drive for CMI8788.

It's imcomplete -- so, no point in trying out the drivers right now from the daily's.

---

### Post by Anaximander Thales on 2007-11-13
New Driver update today --

[quote="Alsa Project - Bug 0002633"]A new beta driver package is available[/quote]
[Download](http://www.alsa-project.org/main/index.php/User:ClemensLadisch)

---

### Post by Yellow Pasque on 2007-11-13
> I don't even have ubuntu installed (FC6 instead), but FINALLY getting the 8788 to work at all in Linux is something I'm very interested in.
What about the OSS driver?
[http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)

---

### Post by Anaximander Thales on 2007-11-15
Well, OSS has drivers for the CMI8788 sound chip.  The same chip in the X-Meridian and several other sound cards.

The article you posted shows the CMedia CMI8788 in the Open Source Driver section.

You can download it from [here](http://www.opensound.com/download.cgi).

The biggest problem that I have is intermittent clicks while nothing is playing, plus while they say that there is a way to record, I've not investigated it fully as to how to get it to work on my machine.  Not saying you'll run into those, but those are what I've run into.

Clemens Ladisch has released a beta driver today (which corrected a problem from yesterday's compile).

If you're set on alsa, give the alsa team some time, they are working hard on getting it out -- but if you need sound now, go with OSS and, if you want, switch to ALSA later on.

---

### Post by proteo on 2007-11-19
Anyone else trying the new Beta Alsa drivers? i'm currently using them, but have a few problems with some apps that doesn't work, and other work flawless.:confused:

---

### Post by epsilon72 on 2007-12-01
I'm thinking about trying them, but I'd have to recompile my kernel first and leave out the alsa module (and probably do a portage overlay for the new driver package)

What apps don't work correctly?

edit: I installed the driver package and I have sound with the 8788! (I'm using gentoo amd64)

Video and firefox audio work fine, but I have not tried anything in wine yet.

One thing I've noticed though - the audio quality is REALLY bad - I have a good set of speakers and on those it sounds like I'm listening to streaming audio.  Is this an alsa issue or an issue with this (not-yet-finished) driver?
EDIT: Nevermind about the sound quality - I hadn't configured mplayer correctly.  Now sound quality is spot on.
To the dev who is working on this driver - keep up the good work!

---

### Post by Anaximander Thales on 2007-12-11
Checked out the alsa project for the CMI 8788 driver today -- seems Clemens is near complete.  Looks like the last little bit is for midi sequencing -- which is currently 1/4 done, whtil the total project is 98% done.

---

### Post by proteo on 2007-12-20
I forgot I had subscribed to this thread; The apps that work are Rythmbox, Totem, Miro and the system sound, the apps that doesn't are: MPlayer, XMMS, Last.FM, Helix Player.

---

### Post by Bartichello on 2008-05-05
don't know if anyone still is working on this but i have tried getting my soudcard to work on the newest ubuntu(razer barracuda AC-1 with this chipset) but i can't get any sound out of it at all(oss doesn't seem to work properly) and i was wondering if anyone could help me getting it to work?

i get one sound when i just booted and before i have to log in and that's it...

---

### Post by proteo on 2008-05-06
my sound card work just fine on 8.04, but I can´t do anything untill I fix gnome, but before breaking it, it worked fine, did you do a fresh install or a update?

---

### Post by Bartichello on 2008-05-06
it's a fresh install. i get system sounds and sound in Enemy Territory(a game i installed) i don't get sound out of any of the media players however.(vlc and the standard music players and videoplayer in ubuntu).

i haven't been using linux that long yet either. this entire thing is one big test for me. even as i type this i'm back at windows because i wanted to listen to some music...

---

### Post by proteo on 2008-05-06
Did you disabled the onboard sound card from your bios?, maybe the other sounds are being routed to the onboard if it's still enabled, I used to do that to get diferent programs send sound to diferent devices, like voice calls, voice recognition (only win XP) to my headphones, and the music and games to my speakers.

---

### Post by Bartichello on 2008-05-07
i'll give it a try could very well be that is the problem. i'll have a look tomorrow.



seems to work. thanks for the help.

---

### Post by more10 on 2008-05-17
> **proteo said:**
> my sound card work just fine on 8.04, but I can´t do anything untill I fix gnome, but before breaking it, it worked fine, did you do a fresh install or a update?

How did you do that? I can't get my Razer Barracude AC-1 to work on my Ubuntu Studio 8.04. 

I have downloaded the beta 2008-04-15 driver from [http://www.alsa-project.org/main/index.php/User:ClemensLadisch]("http://www.alsa-project.org/main/index.php/User:ClemensLadisch"), as well as Alsa 1.0.16 lib and utils sources. I followed the guide [http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen]("http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen"), adding some packages in order to compile. More details on [crosspost Ubuntu Studio 8.04 x64 + cmi8788, help wanted]("http://ubuntuforums.org/showthread.php?t=785630").

I would be so grateful for a guide on how to get a cmedia 8788 to work on ubuntu 8.04.

---

### Post by krylon on 2008-05-20
My X-Meridian ( CMI8788 ) ALSA playback works on 8.04 fresh install. I can't record from the mic though.  Has anyone got a CMI8788 with a working microphone in Ubuntu?

---

### Post by krylon on 2008-05-23
Anyone with a working mic in Ubuntu with their CMI8788 (Razer Barracuda, Auzentech X-Meridian, Bluegears b-Enspirer, etc)??

---

