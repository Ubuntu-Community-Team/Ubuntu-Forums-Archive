---
title: "Wine sound cracks"
date: 2008-11-24
forum: Wine
---

### Post by aaargh486 on 2008-11-24
I recently did a clean install of Intrepid Ibex. I downloaded Wine and reinstalled my games. Sadly enough, when I start, for example Half-Life 2: Deathmatch, all sound cracks and repeats itself partially. Also, performance is reduced severely, rendering the game unplayable.

After I killed pulseaudio, everything was practically fine.
I tried Wine versions 1.1.7, 1.1.8 and 1.1.9, all the same.
On the same computer, everything ran fine on Hardy.

In my winecfg, I have ALSA selected as audio driver. My DirectSound options are:
Hardware acceleretion: "Standard"
Default Sample Rate: 44100 Default BPS: 16
Driver emulation unchecked.
Can anybody please help? I'm perfectly fine with the way it "worked" under Hardy. It just blocked all other audio, but my Wine applications worked. Having to kill pulseaudio everytime is really unelegant.

Thanks in advance.

---

### Post by iheartubuntu on 2008-11-24
Im having the same problem with my dads computer. He has had this problem for months now with all his wine games (those BigFish games).

---

### Post by habelman on 2008-11-24
aaargh trying disabling the ALSA driver in wine config and enabling the OSS driver worked to get rid of my sound problems with wow.

---

### Post by iheartubuntu on 2008-11-24
> **habelman said:**
> aaargh trying disabling the ALSA driver in wine config and enabling the OSS driver worked to get rid of my sound problems with wow.

That fixed it thanks!

---

### Post by habelman on 2008-11-24
glad to hear:) enjoy.

---

### Post by aaargh486 on 2008-11-25
> **habelman said:**
> aaargh trying disabling the ALSA driver in wine config and enabling the OSS driver worked to get rid of my sound problems with wow.

Sadly enough, it didn't fixed it for me. OSS just means no sound.

Now I found out ALSA on Intrepid reroutes all audio into the Pulseaudio server. That'll probably explain why it crackled and delays so much.
I found no way to disable it, so I had to remove pulseaudio.

And guess what? It solved all my problems! Seriously, I don't understand why such a horribly broken product was included in the first place and more importantly, why everything wasn't fixed since Hardy. Especially since everything works without it.

---

### Post by cogadh on 2008-11-25
aaargh486, I'm right there with you on the inclusion of PulseAudio. It was not ready when they included it in Hardy and it is still not ready with Intrepid. I actually switched to using Kubuntu and Xubuntu for my machines, since those still use ALSA as the default instead of Pulse. However, you can usually get around Pulse's limitations by simply running "pasuspend" with Wine:
```
pasuspend wine foo.exe
```
I just find it easier to not deal with it at all.

---

### Post by Dark9204 on 2008-11-26
All games that is based on the source engine. Like HL2, Must run with the -dxlevel 81 tag in linux/wine to get good performance. I myself play CS:S just fine.

Oh, and one more thing. Wine 1.0.1 + PulseAudio gets along just fine. But if you don't want PulseAudio you can always disable it on startup and change sound output to ALSA in System->Preferences->Sound.

I find it strange that there is no official PulseAudio plugin in wine yet. Since the three biggest distros are all using PulseAudio as standard.

---

### Post by Eviljim on 2008-11-26
> **aaargh486 said:**
> Sadly enough, it didn't fixed it for me. OSS just means no sound.

Now I found out ALSA on Intrepid reroutes all audio into the Pulseaudio server. That'll probably explain why it crackled and delays so much.
I found no way to disable it, so I had to remove pulseaudio.

And guess what? It solved all my problems! Seriously, I don't understand why such a horribly broken product was included in the first place and more importantly, why everything wasn't fixed since Hardy. Especially since everything works without it.

Try doing the things mentioned by Trap3d on this thread

[http://ubuntuforums.org/showthread.php?t=968179]("http://ubuntuforums.org/showthread.php?t=968179")

---

### Post by cogadh on 2008-11-26
> **Dark9204 said:**
> All games that is based on the source engine. Like HL2, Must run with the -dxlevel 81 tag in linux/wine to get good performance. I myself play CS:S just fine.

Oh, and one more thing. Wine 1.0.1 + PulseAudio gets along just fine. But if you don't want PulseAudio you can always disable it on startup and change sound output to ALSA in System->Preferences->Sound.

I find it strange that there is no official PulseAudio plugin in wine yet. Since the three biggest distros are all using PulseAudio as standard.
I think this stratement from the PulseAudio website explains why Wine doesn't support it:
> The PulseAudio daemon and utilities are still under heavy development. Although they are generally considered stable, they haven't seen enough testing to warrant a first completely stable release. 
So even though those three distros have chosen to switch to a basically unstable sound system, there is no real reason, at this time, for software developers to even think about supporting it. I find it strange that those distros actually chose to go with PA, considering PA's own developers don't consider it ready for a stable release.

---

