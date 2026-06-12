---
title: "Problems with sound in wine"
date: 2008-07-19
forum: Wine
---

### Post by hexxa on 2008-07-19
Hey, Was supposed to test a game through wine
However, it seems, not that I get any sound when I start winecfg
so do I get these errors

[I][COLOR="DimGray"][SIZE="2"]hexxa@leol:~$ winecfg
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer[/SIZE][/COLOR][/I]

	
It may be due to that I have 2 sound card plugged into the computer, can i disable one of the cards. In such cases, how would perhaps be a little easier to set up wine if I did it.

Mvh:
Hexxa

Edit:
	
When I had disabled my sound card so the sound functioning of wine
However, do I mass erros and no "wave in / line in" so mice will not work hope someone knows the way to do this for mice is important.
In Winecfg i dont have anny input on alsa only out

ALSA:
Wave out
Midi out
Midi in

**Error's from winecfg:**
[I][COLOR="DimGray"]> ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: Filen eller katalogen finns inte
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: Filen eller katalogen finns inte
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: Filen eller katalogen finns inte
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: Filen eller katalogen finns inte
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit[/COLOR][/I]

---

