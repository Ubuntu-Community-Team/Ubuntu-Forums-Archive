---
title: "SBlive &amp; Fiesty"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by joshb on 2007-04-25
just installed fiesty AMD64. I have a hiss coming from my speakers. I did have have ubuntu 6.10 installed before with out any sound problems. Any clue what is wrong?

---

### Post by simonn on 2007-04-25
[http://ubuntuforums.org/showthread.php?t=410263](http://ubuntuforums.org/showthread.php?t=410263)

---

### Post by joshb on 2007-04-25
Thank you for a fast response.
That did not work. The only sound I get is hissing. Here is my lsmod |grep snd

snd_emu10k1_synth       9216  0 
snd_emux_synth         39936  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       8960  1 snd_emux_synth
snd_emu10k1           133024  2 snd_emu10k1_synth
snd_ac97_codec        117720  1 snd_emu10k1
ac97_bus                3968  1 snd_ac97_codec
snd_pcm_oss            49536  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11792  2 snd_emu10k1,snd_pcm
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      9856  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                61856  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10260  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68904  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd

The hissing starts and stop when the sound mod is loaded or unloaded. Also the microphone was picking up sound even though it is off

---

### Post by ronocdh on 2007-04-26
> **joshb said:**
> just installed fiesty AMD64. I have a hiss coming from my speakers. I did have have ubuntu 6.10 installed before with out any sound problems. Any clue what is wrong?
I solved this problem by poking around in the audio preferences (via the speaker icon in the tray, not the System>Preferences>Sound panel) and under the Switches tab, disabling the digital jack.

Hopefully it works for you, too.

---

### Post by joshb on 2007-04-26
> **ronocdh said:**
> I solved this problem by poking around in the audio preferences (via the speaker icon in the tray, not the System>Preferences>Sound panel) and under the Switches tab, disabling the digital jack.

Hopefully it works for you, too.
Now I know why i have heard that hissing before. I will look into this tonight when I get home. Thank you.

---

### Post by joshb on 2007-04-26
to get it working I had to do what simonn and ronocdh wrote. ronocdh got the hissing to stop and simonn got the sound controls to do something sane. I had bass, rear speakers and center or I could have left & right but nothing else, it depended on if sigma 4 speaker was checked or not. now its at least sane may not 100% but can deal with it.

So Thank You for your help :guitar:

---

