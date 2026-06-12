---
title: "Half-Life 2"
date: 2008-11-29
forum: Wine
---

### Post by supernova1 on 2008-11-29
I just installed half-life 2 in 1.0.1, I am running Ubuntu 8.10 64-bit.  I am having a couple of different problems.

-My first problem is that when I run half-life 2, it goes to a black full screen, there is no sound or any sign of any of the graphics loading.

-If I run with the virtual desktop emulation, the graphics for half-life 2 load fine and I am able to play, but I get no sound.  I have ALSA and JACK checked in wine, OSS is not checked.  However I did play with the options and try everything and I still get no sound.

Does anyone have any suggestions?

Thanks,

David

---

### Post by Skripka on 2008-11-29
> **supernova1 said:**
> I just installed half-life 2 in 1.0.1, I am running Ubuntu 8.10 64-bit.  I am having a couple of different problems.

-My first problem is that when I run half-life 2, it goes to a black full screen, there is no sound or any sign of any of the graphics loading.

-If I run with the virtual desktop emulation, the graphics for half-life 2 load fine and I am able to play, but I get no sound.  I have ALSA and JACK checked in wine, OSS is not checked.  However I did play with the options and try everything and I still get no sound.

Does anyone have any suggestions?

Thanks,

David

Lemme, guess-you have an ATi card in your machine?

---

### Post by supernova1 on 2008-11-29
No, I do not have an ATI.  I have a Nvidia GeForce 6200 and am running Nvidia driver 177.80.

---

### Post by Skripka on 2008-11-29
> **supernova1 said:**
> No, I do not have an ATI.  I have a Nvidia GeForce 6200 and am running Nvidia driver 177.80.

Wired...1st place to start messing with things is in Steam, and playing with game options...start out toying with DirectX settings.


I guessed ATi-because those cards are known for only supporting Steam games in DirectX7 mode (IIRC).

---

### Post by supernova1 on 2008-11-29
I will play with the settings and let you know what I come up with.  I just installed my second program in WINE, and sound is not working in it either, so I am guessing that sound is not working in any of my WINE programs, it works fine playing MP3's, and works fine playing other linux games.  Do you have any clue why sound would not be working in WINE?

Thanks,

David

---

### Post by supernova1 on 2008-11-29
Good news, I got my sound working by disableing my onboard sound in the bios, I have onboard sound and a pci sound card.  My sound is very choppy though in half-life.  I am also still having the full screen video problem.

Thanks,

David

---

