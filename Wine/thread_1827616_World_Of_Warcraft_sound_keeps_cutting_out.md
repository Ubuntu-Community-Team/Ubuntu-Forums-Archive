---
title: "World Of Warcraft sound keeps cutting out"
date: 2011-08-18
forum: Wine
---

### Post by Arminius on 2011-08-18
in order to fix it, I have to exit out of the game, and come back in, which is a huge inconvenice if your in the middle of a raid.
wine version is 1.2.2
And sound drivers under wine are Alsa Drivers, no others, with Hardware acceleration set to full, Default sample rate 44100, Default bits per sample 16.
So any advice as to how to make it more stable?

---

### Post by cwwilson721 on 2011-08-18
[LIST]
[*]Install wine 1.3 from repos
[*]Set your 'enviornment' to run WoW as Windows XP
[*]As a last resort, try to install a Pulse enabled wine from a third-party repo
[/LIST]

---

### Post by Dekafox on 2011-08-18
Actually, if you're on 10.04, or 10.10, after installing Wine 1.3, you'll need to update alsa as well.  1.3.25 broke compatibility with the version of alsa included in 10.04(and 10.10 I believe) and Pulseaudio.

If you're on Lucid, the PPA you need to update ALSA is ppa:team-iquik/alsa
I don't know of one offhand for Maverick, and this ALSA version is already in Natty.

---

