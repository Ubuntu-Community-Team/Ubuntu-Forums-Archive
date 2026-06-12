---
title: "Kubuntu Audigy 2 ZS Issue"
date: 2007-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by MyDalRiley on 2007-01-25
Hello all!

Still working on getting Edgy AMD64 up and running smoothly on my machine and need some hardware assistance.  I am getting no sound from my Audigy 2 ZS card.

Tyan K8WE
Dual Opteron 246's
2GB RAM

Kubuntu Edgy
2.6.17-10 kernel

lspci reports the card as present

09:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
09:04.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
09:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

alsamixer reports the card as present.

Card: Audigy 2 ZS [SB0350]                
Chip: SigmaTel STAC9750,51           

The Analog / Digital switch in the alsamixer is on (not [MM] ) and flipping it on and off results in a click in my speakers.

kmix shows the analog/digital input as green and reports Audigy 2 ZS [SB0350]

Within the KDE sound settings I can click the test sound and get nothing.  Volumes are up.

The following modules are loaded per modprobe.

/lib/modules/2.6.17-10-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.17-10-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.17-10-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.17-10-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.17-10-generic/kernel/sound/oss/emu10k1/emu10k1.ko
/lib/modules/2.6.17-10-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/input/gameport/emu10k1-gp.ko

Do I need to blacklist snd-ac97? And if so is it simply adding 'blacklist snd-ac97' to the modprobe blacklist file?

/lib/modules/2.6.17-10-generic/kernel/sound/pci/ac97/snd-ak4531-codec.ko
/lib/modules/2.6.17-10-generic/kernel/sound/pci/ac97/snd-ac97-bus.ko
/lib/modules/2.6.17-10-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.17-10-generic/kernel/sound/oss/ac97.ko
/lib/modules/2.6.17-10-generic/kernel/sound/oss/ac97_codec.ko

Any help is appreciated. I think I have tried all of the suggestions in previous messages and have gotten nowhere.

Thanks in advance!

Scott

---

### Post by The Keeper on 2007-01-26
Your problem is because ALSA selects your onboard audio as default audio device even if it is disabled in BIOS. This problem did not exist in (K)Ubuntu 6.06.

See this topic here: [http://www.ubuntuforums.org/showthread.php?t=207664](http://www.ubuntuforums.org/showthread.php?t=207664)

---

### Post by MyDalRiley on 2007-01-26
> **The Keeper said:**
> Your problem is because ALSA selects your onboard audio as default audio device even if it is disabled in BIOS. This problem did not exist in (K)Ubuntu 6.06.

See this topic here: [http://www.ubuntuforums.org/showthread.php?t=207664](http://www.ubuntuforums.org/showthread.php?t=207664)


I followed the instructions there and still nothing. :-(

Here is /proc/asound/version
ALSA 1.0.12rc1....

output of cat /proc/asound modules
0 snd_emu10k1

added the sound file in /etc/modprobe.d with the following:
options snd_emu10k1 index=0

So the proper driver is in the index 0 slot so I am starting to believe the 
issue isn't the "edgy keeps re-assigning the default card to the ac97" 
problem

Within /proc/sound I see the following:
Audigy2 -> card0 

Here is /proc/asound/cards
0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0350]
                      Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0x2000,
 irq 66

Here is /proc/asound/hwdep
00-00: EMU10K1 (FX8010)
00-02: Emux WaveTable

Here is /proc/asound/pcm
00-04: p16v : p16v : playback 1 : capture 1
00-03: emu10k1 : Multichannel Playback : playback 1
00-02: emu10k1 efx : Multichannel Capture/PT Playback : playback 8 : capture 1
00-01: emu10k1 mic : Mic Capture : capture 1
00-00: emu10k1 : ADC Capture/Standard PCM Playback : playback 32 : capture 1

Perhaps that p16v is the problem?  If so how do I killit?

Here is the output of /proc/asound/oss/sndstat

Sound Driver:3.8.1a-980706 (ALSA v1.0.12rc1 emulation code)
Kernel: Linux workstation 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x
86_64
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0x2000, irq 66

Audio devices:
0: ADC Capture/Standard PCM Playback (DUPLEX)

Synth devices:
0: Emu10k1

Midi devices:
0: Audigy MPU-401 (UART)

31: system timer

Output of asoundconf list
Timers:Names of available sound cards:
Audigy2

I even did asoundconf set-default-card Audigy2

Attached is my alsa-base file...any ideas what else I can try?

Thanks again!

Scott

---

