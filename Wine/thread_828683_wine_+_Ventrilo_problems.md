---
title: "wine + Ventrilo problems"
date: 2008-06-14
forum: Wine
---

### Post by chuugokujin on 2008-06-14
Ubuntu 8.04 + wine rc4 + Ventrilo 3.x

I know Ventrilo sucks but all of my friends are using it under Windows.
I must make it work so I can completely switch to Linux gaming.

winecfg->audio has Alsa and Esound Driver. I tested with both on, or either on.

I wined the ventrilo which was previously installed under Windows. It can connect to the server, but it's just no sound. I went to Setup, no matter what I choose Esound or Alsa at Winecfg before, none of the Output Device/Input Device works. I tried to click the button "Playback (output)" and it says Unable to open the system sound control panel "C:\windows\system32\sndvol32.exe".

Please help me with this, Thanks!

---

### Post by Ptero-4 on 2008-06-14
Do you have the proper backends (alsa-esd, pulse-alsa and pulse-esd)?

---

### Post by Fred_E _krugar on 2008-06-14
I use Ventrilo also But I use Kubuntu now because of that stupid PulseAudio 
, But you can just shut PulseAudio server off before starting any Audio devices like Vent and games.

---

### Post by chuugokujin on 2008-06-14
> **Ptero-4 said:**
> Do you have the proper backends (alsa-esd, pulse-alsa and pulse-esd)?

What are they? I remember I have pulseaudio-esound-compat installed only.

---

### Post by chuugokujin on 2008-06-14
> **Fred_E _krugar said:**
> I use Ventrilo also But I use Kubuntu now because of that stupid PulseAudio 
, But you can just shut PulseAudio server off before starting any Audio devices like Vent and games.

I know...this is gay, but new things come out with risks. It will be good in the future, but it makes troubles to noobs like me.

---

