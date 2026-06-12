---
title: "Getting microphone to work"
date: 2008-06-13
forum: Wine
---

### Post by Divide By Zero on 2008-06-13
I have an Audigy2 Platinum that I can't make work with 1.0-rc4.  The mic works in Hardy (vumeter and gnome-sound-recorder 2.22.0)  In its audio config tab, Wine shows a single Wave In Device: ADC Capture/Standard PCM Playback.  When running programs through Wine (DDO and LotRO are the two I'm concerned with), it shows the driver in-game, but no sound registers when I hit/talk/blow into the mic.  Volumes are cranked and untouched from Linux-native tests.  I know the hardware works with the game on the other half of my dual-boot, so it seems to be a config issue.  

I feel like I didn't tell Wine where to get its incoming audio, and that I might need to.

I'm sure there's a HOWTO or something around, or if there's not, can somebody please point me to the setting?

---

### Post by cogadh on 2008-06-14
What are you using for a sound driver in Wine?

---

### Post by Divide By Zero on 2008-06-14
Sorry, I figured I would have left something out.

This is the ADC Capture/Standard PCM Playback under the ALSA Driver tree, which is the only one checked.  OSS, JACK and NAS are also present, but unchecked.

The DirectSound settings are Full/44k/16/Driver Emu checked.

---

