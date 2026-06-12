---
title: "drivers for HT OMEGA Claro"
date: 2008-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by on4now4 on 2008-02-25
i just reciantly installed linux on my computer but i can not find drivers for my sound card so as of right now i have no audio.  if anyone knows were i can get drivers for my HT Omega Claro sound card plz let me know

---

### Post by Jesse_hz on 2008-03-27
Just got the same card and after I compiled the latest version of alsa, it seems to be working just fine. I haven't got around to testing digital output yet though.

You will need to download and compile the latest version of alsa to make it work.
[This page]("http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen") should be able to help you.

---

### Post by on4now4 on 2008-04-06
thanks for the help

---

### Post by Jive Turkey on 2008-04-08
So how did the compiling of the driver go?  I ask because I might buy this card myself.  Is it fully functional, ie sliders for all channels in volume control, etcetera?  Are you using digital or analog, are they both working?

---

### Post by Jesse_hz on 2008-04-09
All digital and analog outputs seem to work fine for me, the volume sliders act kind of strange though, but I expect that this will be fixed in a later version of Alsa.

Also, on 8.04 you don't need to compile the latest Alsa; it comes with it.

---

### Post by dman777 on 2008-05-06
I am thinking about getting the Claro+ card. How does is this car's sound quality with the linux drivers as compared to the Windows drivers?

---

