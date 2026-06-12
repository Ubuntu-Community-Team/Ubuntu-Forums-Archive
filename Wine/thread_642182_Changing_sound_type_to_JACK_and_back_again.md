---
title: "Changing sound type to JACK and back again"
date: 2007-12-16
forum: Wine
---

### Post by Ryan Marcus on 2007-12-16
I installed CNC3 today, and after much pain, finally got it to work with JACK audio -- but not ALSA or OSS.

As CNC3 is the only WINE application that requires JACK sound, I've already grown tired of opening winecfg and changing it every single time.

Is there any way, from the command line, to change the sound type in WINE?

---

### Post by sandy8925 on 2008-12-03
Maybe.
Another thing you could try for sound is to replace the wine dsound.dll with native(Windows) dsound.dll.

Then in winecfg set it to use native dsound.dll.

Unfortunately I only got stuttering sound with this.Could be because my computer is slow.

---

