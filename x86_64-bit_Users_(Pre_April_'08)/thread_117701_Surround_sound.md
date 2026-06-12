---
title: "Surround sound"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by tszanon on 2006-01-15
Hi,

I'm using a 6 channel built-in sound card (Motherboard: Asus A8V, chipset:VIA VT8237, Audio: Realtek ALC850).
When using speaker-test, I hear noise from every channel, which tells me that everything is working fine.

But when I use xmms (or anything else, like gxine), I only get sound from the front speakers. I've already changed the xmms configuration to use ALSA, changed the Multimedia Systems Selector both to ALSA, but nothing helps.

In Doom3, if I select ALSA, I can't even get any sound until I select OSS and restart the game.

I've read other threads about it, but nothing written there helped me.

It seems that the system knows it should use 6-channel audio, but the sound comes just from the front speakers. It's not like it's using 2-channel, because the sound that comes from the front speakers is exactly what it should be.

The channels are unmuted and set to the loudest volume. The problem isn't in the mixer settings.

I've read in the Doom3 installation FAQ that AMD64 users may need to have the module snd-ioctl32. I don't have it, for sure. I tried to compile ALSA source code, but it keeps giving me an error about an unsupported sound card.

Anyone has any ideas to solve it? If anyone could send me the module snd-ioctl32, I could try to load it.

---

### Post by tszanon on 2006-01-16
Ok, people.

[Here]("http://alsa.opensrc.org/FAQ028") I found out how to make xmms play 2-channel audio files using all 6 channels. It's not perfect, but it's very nice. :D :cool: 
But the problem with Doom3 persists...but we'll solve this problem too, no matter how long it takes. :) 

If you've got an idea, please don't be shy: share it with us. :wink:

---

### Post by MaX on 2006-01-18
[QUOTE=tszanon]Hi,

I'm using a 6 channel built-in sound card (Motherboard: Asus A8V, chipset:VIA VT8237, Audio: Realtek ALC850).
When using speaker-test, I hear noise from every channel, which tells me that everything is working fine.
[/QUOTE]

Could you please tell me what settings you have in gnome-volume-manager?
Cause I have the same Realtek chipset and I only get the front speakers.

---

### Post by tszanon on 2006-01-19
Sure!

Playback:
- All unmuted
- IEC958 Playback AC97-SPSA set to zero
- Others (Master, Master Mono, PCM, Surround, Center, LFE and PC Speaker) as you like

I think Master Mono and IEC958 didn't have any effect, but I should do some more tests.

Capture:
- Line-in, CD  and Aux all the way up;
- Microphone, Phone and Capture set to zero;
- Line-in, CD, Aux and Capture unmuted for playing, but muted for capture;
- Microphone muted for playing only;
- Phone all muted;

Switches:
- Mic boost off;
- Mic front input off;
- IEC958 Output on; (any effects?)
- Duplicate front off;
- External amplifier on;

Options:
- Surround jack mode: independent;
- Mic select: Mic1;
- IEC958: PCM; (what is it?)
- Mono Select output: Mix; (what is it?)
- Channel mode: 6ch;
- Input Source Select: Input1 (I read it must be Input1);

And, as written in the link I posted, here's my ~/.asoundrc file:
```
pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1

    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}
```

Don't forget to set xmms to use Alsa and ch51dup. :)

---

