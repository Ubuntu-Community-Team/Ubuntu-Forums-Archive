---
title: "[SOLVED] Silent Hunter III"
date: 2008-03-14
forum: Wine
---

### Post by Rytron on 2008-03-14
Hi,
Has anyone got this game to work under wine?
If so is there a specific method to it?

It is a really great WWII Submarine Sim.

---

### Post by foxmulder881 on 2008-03-14
I guess it works. Afterall, it is featured on the WINE Application Database.

[http://appdb.winehq.org/appview.php?iAppId=3793](http://appdb.winehq.org/appview.php?iAppId=3793)

---

### Post by Rytron on 2008-06-09
I will stay with using Silent Hunter III on Windows XP.

---

### Post by foxmulder881 on 2008-06-16
Way to dig up an old thread there Rytron!

---

### Post by blampars on 2008-06-18
> **Rytron said:**
> I will stay with using Silent Hunter III on Windows XP.
not running so well through wine i take it?

---

### Post by Rytron on 2008-06-19
> **blampars said:**
> not running so well through wine i take it?

I cant get it to run.

---

### Post by Cannaregio on 2009-01-29
Runs fairly well in intrepid with wine 1.1.13, see
[http://ubuntuforums.org/showthread.php?p=6610951]("http://ubuntuforums.org/showthread.php?p=6610951")
(threads also on the "uluga" argentinian server: [http://www.uluga.ubuntuforums.org/showthread.php?p=6610951]("http://www.uluga.ubuntuforums.org/showthread.php?p=6610951"))

---

### Post by Neural oD on 2009-01-29
thanks - might have to check this game out

---

### Post by Rytron on 2009-01-29
Cheers to you Cannaregio.

:popcorn:

---

### Post by bgeorgalas on 2009-02-24
Hi to everyone and sorry for bringing this thread up again....

I am new to the ubuntu world so please be patient.
I am trying to run silent hunter 3 on ubuntu 8.10 but although the game installs and runs normaly only in the interior (crew management is working, navigation map, control room and TDC working too) but whenever i jump to an external or periscope view the game freezes and it is necessary to hard reset the pc....

I have tried both with wine 1.1.15 (latest version) and with wine version 1.1.13 that canareggio said that was working fine.
I followed the instructions from [http://ubuntuforums.org/showthread.php?t=1047058](http://ubuntuforums.org/showthread.php?t=1047058) to the letter except that i didn't install GWX 2.0 (first i wanted to make sure the game runs)

I am trying to run sh3 in an amilo a1667g notebook (amd64bit 2.6ghz, 2gb ram, ati x700 mobility radeon) using ubuntu 8.10 32bit.
I have also installed (i hope corectly) the most recent proprietary drivers for my graphic card (if i am not mistaken is catalyst 9.1)

Any suggestions would be mostly welcome!

---

### Post by NightMKoder on 2009-02-25
If you need a hard reset to bring your computer back, its most likely a kernel panic (the keyboard leds should flash). Its most likely due to your graphics drivers (ATI doesn't have the best drivers).

Try the following:
disable desktop effects
play around with graphics options inside the game
switch to non-proprietary drivers

If the game just crashes on at least one of these, then a log would be nice. Hopefully some of that will help.

---

### Post by bgeorgalas on 2009-02-25
Thank you very much for your fast response. I will try to

1.disable desktop effects
2.play around with graphics options inside the game
and post back the results, 

Unfortunately i am not sure of how to disinstall the catalyst drivers from ati's website, any clues on this one?

---

### Post by bgeorgalas on 2009-02-25
Ok, i have tried to:
1. Change in-game settings: no effect (computer freezes upon jumping on deck, keyboard not responding, no flashing keys)
2. Turned off desktop effects without effect
3. Changed screen resolution to 1024x768 (same as the game) and tried to run the game: no effect.

I will now try to disinstall the proprietary drivers and see if that works.

fglrxinfo gives me this:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.1.8087 Release

and DISPLAY=:0 glxinfo | grep render this:
direct rendering: Yes
OpenGL renderer string: ATI MOBILITY RADEON X700

i also attach a copy of my xorg.onf file.
Any help would be really appreciated.
thank you all for your time!

---

