---
title: "Should I Be Worried?"
date: 2008-09-02
forum: Wine
---

### Post by Samizdat on 2008-09-02
The following pertains to my Hardy Heron 8.04 installation.

I followed the Hardy wine installation guide [http://www.ubuntu1501.com/2008/04/installing-wine-in-hardy-heron.html]("http://www.ubuntu1501.com/2008/04/installing-wine-in-hardy-heron.html") (using installation method 2).  When I entered the command `winecfg` in a terminal, the message returned was:

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/rick/.wine' has been updated.
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer

Should I be worried?

---

### Post by ad_267 on 2008-09-02
I don't think so. I get the line "ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave" too. Are you having any problems with wine? Did the window pop up where you could set the wine settings?

---

### Post by aoanla on 2008-09-02
I found that happens to me if I run winecfg the first time - before I've configured Wine's sound settings. Then it sometimes goes away...

---

### Post by Samizdat on 2008-09-02
> **ad_267 said:**
> I don't think so. I get the line "ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave" too. Are you having any problems with wine? Did the window pop up where you could set the wine settings?
 
I haven't tried wine yet, so no problems other than those disturbing messages on winecfg -- the wine configuration settings window did pop up, but going on the theory that if you don't know what's going on, don't do anything, I simply hit "OK."

I did note that there were two highlighted items in that window: "Default Settings," and below that was "foobar2000" (probably an artifact from a failed wine attempt I made several weeks ago).

---

