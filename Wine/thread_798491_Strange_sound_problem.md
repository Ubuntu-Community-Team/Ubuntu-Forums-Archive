---
title: "Strange sound problem"
date: 2008-05-18
forum: Wine
---

### Post by Kazurik on 2008-05-18
I am having a strange problem with Wine. I can not get it to play any sounds unless I have another none Wine program already playing them. Then when I do have Wine playing sounds no other program can, which leads to programs such as Pidgin to break and use all of my RAM. I have the default settings for Wine with the exception of having the OSS audio check box being checked along with ALSA in the audio tab.

I am using Wine version 1.0-rc1
I get this terminal output when I run foobar with wine...
```

$ wine "C:\Program Files\Foobar2000\Foobar2000.exe"
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on USB Audio, disabling mixer

```
My wine configuration is what ever it gives you the first time you run winecfg with the exception of the audio tab.

Any help you can provide would be great!

---

### Post by Kazurik on 2008-05-18
bump

---

### Post by igster on 2008-05-19
Does your volume control list more that one device?  If you double click on the volume icon it will open the mixer window.  Look under the File menu to see what other devices are listed.  Maybe the wrong one is selected?

I just had this problem.  None of the applications running in Wine had sound and changing the sound options in Wine config had no effect.  It turns out I had the wrong device selected in the mixer and one of the volume controls was all the way down.  Until I switched to the correct device I couldn't see that.

Not sure if this will work for you just thought it was worth mentioning.

---

### Post by Kazurik on 2008-05-19
In the "Change Device" menu of the mixer that you told me to open I see...
0: USB Audio (Alsa Mixer)
1: Playback: ALSA PCM on surround71:1 (USB Audio) via DMA (PulseAudio Mixer)
2: Capture: Monitor Source of ALSA PCM on surround71:1 (USB Audio) via DMA (PulseAudio mixer)
3: Capture: ALSA PCM on front:1 (USB Audio) via DMA (PulseAudio Mixer)

In that list of radioboxes 0 is the one that is checked.

I hear sound fine in other non-Wine programs such as Rhythmbox. In fact to even get wine programs to make any noise I have to start up Rhythmbox and start playing a sound. If a wine program opens while Rhythmbox is playing it will be able to play sounds however every non-Wine program starts filling up my RAM really fast till the computer eventually crashes.

---

