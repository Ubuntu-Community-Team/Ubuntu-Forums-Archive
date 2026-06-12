---
title: "Odd wine problem"
date: 2008-11-11
forum: Wine
---

### Post by doctorwho? on 2008-11-11
Alright for starters i'm on 8.04 LTS just installed wine 1.1.8 and my sound stopped working after a certain point, i'm not sure where to start with the debugging, but where would be a good place to start ? 

Running Asus A8V delux mobo, AMD operton processor, Creative Sound Blaster Audigy Ex, Asus G4 4800 vid card, 
Am i missing anything else because i'm plum lost here.
I may as well add, it doesn't matter what windows software i add i can't get sound, no matter how i tweak the settings

---

### Post by cogadh on 2008-11-11
Its because of PulseAudio. From the Wine FAQ:
> **Why isn't PulseAudio available?**

The Wine project has decided not to pursue a Pulse driver for Wine, at this time. We feel it is best to keep working on the more mature Wine Alsa driver. We are aware that some distributions use Pulse as the default, and this is unfortunate. PulseAudio is also known to be buggy when emulating Alsa/OSS and should be disabled for Wine.

There is an unofficial [PulseAudio](http://wiki.winehq.org/PulseAudio) driver for Wine, but it is unsupported and do not submit bug reports while using it

---

### Post by doctorwho? on 2008-11-11
> **cogadh said:**
> Its because of PulseAudio. From the Wine FAQ:

link didn't work dude :(

---

### Post by Dark9204 on 2008-11-12
Change to wine 1.0.1 and it will work fine.

---

### Post by cogadh on 2008-11-12
> **doctorwho? said:**
> link didn't work dude :(
Talk to the WineHQ people, it their link. I copied it verbatim from the Wine FAQ and I just double checked it. It also doesn't work on their site:
[http://wiki.winehq.org/FAQ#head-5d0b06ede012970adb6b0c2b08c7b144a58ce331](http://wiki.winehq.org/FAQ#head-5d0b06ede012970adb6b0c2b08c7b144a58ce331)

---

