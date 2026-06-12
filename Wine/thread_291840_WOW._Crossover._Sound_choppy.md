---
title: "WOW. Crossover. Sound choppy"
date: 2006-11-03
forum: Wine
---

### Post by weasel fierce on 2006-11-03
managed to install WOW with crossover, and it seems fine, except the sound is extremely choppy.

I have it set to use OSS and the config.wtf file includes the 3 lines
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "opengl"

I've tried changing the buffer size but nothing helps. Any ideas ?

---

### Post by Ferrat on 2006-11-03
> **weasel fierce said:**
> managed to install WOW with crossover, and it seems fine, except the sound is extremely choppy.

I have it set to use OSS and the config.wtf file includes the 3 lines
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "opengl"

I've tried changing the buffer size but nothing helps. Any ideas ?

I've noticed something funny with my sound in wow, when ever the FPS goes down a bit the sound gets worse, if I just reposition the camera so that the FPS goes up, the choppyness in the sound totally goes away

---

### Post by reiki on 2006-11-03
Also try running winecfg and choosing Alsa. I have mine using Also and it seems fine. Oh.... wait... you said Crossover. I'm not familiar with Crossover at all. You can also try changing your SoundBufferSize to 150.

---

### Post by NickRich on 2006-11-03
You may need to increase your sound buffer.  Also Wine's ALSA support sucks, use OSS instead. :D

---

### Post by Ferrat on 2006-11-03
> **reiki said:**
> Also try running winecfg and choosing Alsa. I have mine using Also and it seems fine. Oh.... wait... you said Crossover. I'm not familiar with Crossover at all. You can also try changing your SoundBufferSize to 150.

Crossover is just wine in nicer wrapping =)

---

### Post by wozzinator on 2008-12-30
> **NickRich said:**
> You may need to increase your sound buffer.  Also Wine's ALSA support sucks, use OSS instead. :D

Agreed. Switching to OSS made my sound not be choppy like it was with ALSA. Thanks!

---

### Post by Ketara on 2009-01-11
When I switch from ALSA to OSS I don't get any sound at all. Also, the sound in ALSA is not only choppy, but after a while of playing it just cuts out altogether.

---

### Post by flyonthewall on 2012-02-25
Yup. I have this exact same issue. =(

The Ubuntu guide [here]("https://help.ubuntu.com/community/WorldofWarcraft#Audio") says:
> The optimum value for Sound_SoundBufferSize varies depending on you setup. It may be anything from 50 to 300.


In that case I wish there was some way of finding out what that magical value would be. =(

---

