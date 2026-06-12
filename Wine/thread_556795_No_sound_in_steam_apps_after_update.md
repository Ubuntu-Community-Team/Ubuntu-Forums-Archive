---
title: "No sound in steam apps after update"
date: 2007-09-21
forum: Wine
---

### Post by AntiRush on 2007-09-21
Yes, after the update that added Steam Community I've been unable to get sound to work in counterstrike source or half life 2.  

At first I figured I messed something up so I tried some different sound settings - I had been using alsa but I tried oss and also some different alsa configurations.  Nothing worked.

It seems like the main steam app is grabbing the audio output stream for some reason - my sound card doesn't support hardware mixing so that prevents all other apps from playing sound it seems.

That's just a theory and I'm open to any suggestions at all.  I'm running the very newest wine release compiled from source.

---

### Post by AntiRush on 2007-09-23
I did another purge + reinstall of wine - I still can't get this working.  Any ideas?

---

### Post by quadomatic on 2007-09-23
Looks like you're not the only one with this problem:

[http://ubuntuforums.org/showthread.php?t=557896](http://ubuntuforums.org/showthread.php?t=557896)

---

### Post by sneezweasel on 2007-11-17
I have the same exact problem, Sounds on all other programs work fine until I open up steam through crossover. Everything goes silent :(

---

### Post by chaddiesel on 2007-12-11
I have the same problem with steam/ counterstrike. As soon as you run steam, no other application can make sound.

---

### Post by cogadh on 2007-12-11
What soudn hardware do you have? What version of Wine are you using? What do you have configured for a sound driver in Wine?

---

### Post by blackdragon1157 on 2008-02-14
Steam does indeed grab the sound device and won't give it back (greedy little process).  The easiest fix I've found is to play an .mp3 while steam loads, then close it when its finished.  Your game will grab the sound device when it launches.

---

### Post by frodon on 2008-03-11
The best IMO is just to use ALSA since wine support it really well now, a lot of progress as been made on it lately. I've got this problem too and just use alsa, i've not noticed any lag because of it.

---

### Post by perfeng702 on 2009-03-29
I'm having some sound issues to. was this resolved?

---

