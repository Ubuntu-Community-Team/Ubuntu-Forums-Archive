---
title: "Sound won't work in Counter-Strike 1.6"
date: 2007-12-11
forum: Wine
---

### Post by SquallLeonE on 2007-12-11
For some reason, Counter-Strike is not playing any sound.  Whenever I start winecfg and go to Audio, I get the following in the terminal:
```
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

```  Also, for the audio settings in winecfg, the only sound driver I have check marked is OSS.  And then at the bottom of the audio tab, I have hardware acceleration set to full, default sample rate to 22050, default bits per sample set to 8, and driver emulation unchecked.  

If anyone knows, what things do I need to change/download in order to get sound to work?

---

### Post by chrism66 on 2007-12-12
Try ALSA setting. I get no sound with OSS selected, and locks up with ALSA selected.

---

### Post by boast on 2007-12-12
use ALSA + hardware emulation

---

### Post by SquallLeonE on 2007-12-12
> **boast said:**
> use ALSA + hardware emulationThat worked, but I was getting around only 3fps.  Argh.

Also, I recently found out that it's not only in Counter-Strike.  Sound won't work for Battle for Wesnoth and Wolfenstein:ET, neither of them running in wine.  But sound works for Open Arena and Gnometris.  What's up with that?

---

