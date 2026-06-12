---
title: "Soundblaster Live! 24-bit drivers"
date: 2005-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by kobur on 2005-12-31
Does anyone have drivers for SoundBlaster Live! 24-bit card?  Ubuntu AMD64 does not recognize this card.  And, uh, could you include instructions on how to install them? :confused:   I am totally new to Linux and barely have the know how to install drivers of any kind.  Took me hours and hours to figure out how to install ATI drivers yesterday. :(

---

### Post by nothreat33 on 2005-12-31
It looks like SoundBlaster.com doesn't have a driver available for you.

I went here: [http://www.soundblaster.com/language.asp?sDestUrl=/support/downloads]("http://www.soundblaster.com/language.asp?sDestUrl=/support/downloads")

and put in your card type and os and nothing showed up.

---

### Post by handy on 2005-12-31
I am new2.

I had no sound, (this is very common in Ubuntu), in the beginning.  Find the info' that sorted out my sound problems here:

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

I also use an SBLive card.  

There is a shell command that will tell you if your sound card is being recognised, I don't recall what it is?  Someone else will tell you shortly I'm sure.

In the mean time if you look in the Menu:
System/Preferences/Sound

Do you have a listing for "Default Sound Card:"  ??

Cheers,

handy

---

### Post by kobur on 2006-01-01
> Do you have a listing for "Default Sound Card:" ??

It says CA0106.  I don't have a clue what that is.

---

### Post by ArcaneRaven on 2006-01-01
The way I got it to work was to go to the volume control applet, right click and select Preferences. In the window that pops up, make sure it says 'CA0106 (Alsa Mixer' and in the list below, select 'Analog Front' instead of 'Analog Center/LFE'. Close the window and then increase the volume (the channel seems to be muted by default). That should give you sound.

---

### Post by kobur on 2006-01-02
[QUOTE=ArcaneRaven]The way I got it to work was to go to the volume control applet, right click and select Preferences. In the window that pops up, make sure it says 'CA0106 (Alsa Mixer' and in the list below, select 'Analog Front' instead of 'Analog Center/LFE'. Close the window and then increase the volume (the channel seems to be muted by default). That should give you sound.[/QUOTE]

You win the prize! :KS That finally got me music.  Thanks, very much.:D

---

