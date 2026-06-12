---
title: "Sound in chroot for Flash/Youtube?"
date: 2008-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by whit on 2008-03-09
I'm running Firefox in a chroot, partly because I needed Sun's own Java, which works well there. But after fiddling with various suggestions in old threads here about getting sound to work in the chroot (it does outside it), I'm wondering if my problem in the chroot isn't one those threads address. Specifically, trying to play a Youtube video gives these errors in the console that "dchroot -d firefox" was started from:

```
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
```

It's an onboard sound card (a Shuttle XPC) that I know zilch about, except that Ubuntu finds it just fine outside the chroot. I've got /dev mounted to the chroot. Is there something else obvious I should be mounting or otherwise configuring so the sound card will be found?

---

### Post by whit on 2008-03-12
(Bump) Anybody? I like Ubuntu, but I'm noticing the community is far less capable when it comes to solving its shortcomings than the communities around the other major distros.

---

### Post by ferdostar on 2008-03-12
Take a look of [this thread]("http://ubuntuforums.org/showthread.php?p=3446685") and especially at the post #5

---

### Post by whit on 2008-03-13
> **ferdostar said:**
> Take a look of [this thread]("http://ubuntuforums.org/showthread.php?p=3446685") and especially at the post #5

Since I don't have the file it suggests should be renamed, in either my real or chrooted home directory, the suggestion there isn't the trick for me. But thanks for pointing to it. There are obviously lots of ways sound can fail to work in a chroot - I did spend several hours searching old threads here. The ones mentioned aren't the problem I'm seeing. There's no full description I can find on what it takes to really get it up and working. All the advice is about solving some particular glitch, without giving the big picture about Ubuntu's several ways of dealing with sound, and how those are affected in a chroot environment.

I like the core Ubuntu system. But because it is the most-used by the least sophisticated, the level of community support lags that of the other distros. Too much stuff just goes unanswered here. Shuttleworth might devote some of his staff to actually dealing with the issues users have. It would end up improving the distro, if they fed that back into the development team, and used what they learn to improve the official documentation.

---

