---
title: "Wine, no audio devices anymore."
date: 2011-10-11
forum: Wine
---

### Post by ticon on 2011-10-11
I'm not quite sure what caused the change, but I have nothing but the following options in wine under the audio tab.
[U]DirectSound
[/U]hardware acceleration:Full
default sample rate:44100 , bits per sample:16
and a test Sound button. When pressed it makes a thud..lol
But as for more info, Everything else seems to detect sound fine, im listening to music as we speak :) thanks for reading

---

### Post by ubupirate on 2011-10-12
Indeed. Not sure which version of Wine began the drop of being able to select audio devices.

If you used/use ALSA/OSS, I suppose you could still force start it in terminal:

```
aoss wine /path/to/file
```

---

### Post by l3dx on 2011-10-24
I have this problem too. 

Please help!

---

### Post by ubupirate on 2011-10-24
So I did a little research, and it appears that Wine has dropped audio device support beginning from 1.3.25 and did a total rewrite to use DirectSound and winealsa.drv driver.

If you're looking to get back the option to select between ALSA, OSS, Jack, etc.. drop down to either 1.3.24 or the 1.2.3 stable.

---

### Post by PsyclonJohn on 2011-10-26
Ubupirate is correct about this, and I find it easy to just install PlayOnLinux and in it's preferences, you're able to change the current wine version. Go down the list and select 1.2, and it will do all the downloading and installing behind the scenes. When you go back to the winecfg, you'll have all the settings again.

---

