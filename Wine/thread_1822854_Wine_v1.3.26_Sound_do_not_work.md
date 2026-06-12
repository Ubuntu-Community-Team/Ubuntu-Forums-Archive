---
title: "Wine v1.3.26 Sound do not work?"
date: 2011-08-11
forum: Wine
---

### Post by 8Kuula on 2011-08-11
Is it just me or has sound stoped to work in v1.3.26?

Made new default prefix (just to be sure prefix was not reason), and in winecfg audio tab I run test sound, to console I get
```
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
err:winmm:WINMM_OpenDevice Activate failed: 80004005
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
err:winmm:WINMM_OpenDevice Activate failed: 80004005
```

And pops error window with message "Audio test failed!"

Downgrading to v1.3.25 fixes problem.

OS: Ubuntu v10.04.3 64-bit

---

### Post by IPEX-731BA5DD06 on 2011-08-11
I to have problems with wine 1.3.26.

Sound will work for 5 minutes of so, then just fade out or crash.

Usually preceded by some cracks and pop's

Had this problem since wine 1.3.25

Civilization IV is the game.

Wine 1.3.24 worked fine.

2 steps backward for 1 forward...

---

### Post by FerroPower on 2011-08-11
mine is working fine in some games but goes mute after playing some time. maybe a bug or so

---

### Post by 8Kuula on 2011-08-11
Well, forward with v1.3.25 then... until next version is out.

---

### Post by Dekafox on 2011-08-11
I had the same errors.  Some searches brought me across the bugtracker for wine and ubuntu, and a comment from one of the wine-devs.  

Apparently that underrun message wasn't supported by ALSA until 1.0.24(the version in natty I think he said?) and Lucid still uses 1.0.21.  When ALSA doesn't recognize a message, it just kills the entire sound device apparently, or something like that.

Anyways, I found a PPA for ALSA 1.0.24 for Lucid, added it, updated, and my sound that had been broken since the 1.3.25 update is now working flawlessly.

The PPA I'm using is at: [https://launchpad.net/~team-iquik/+archive/alsa/+packages](https://launchpad.net/~team-iquik/+archive/alsa/+packages)

---

### Post by 8Kuula on 2011-08-11
Nice one Dekafox. Sound with v1.3.26 works now too :)

So problem was "too old alsa".

ppa:team-iquik/alsa
If someone else did not find that line from [https://launchpad.net/~team-iquik/+a...alsa/+packages](https://launchpad.net/~team-iquik/+a...alsa/+packages) page, I did not, or im just blind...

---

### Post by stinkinrich88 on 2011-09-03
You're not blind! But it does say it on this page: [https://launchpad.net/~team-iquik/+archive/alsa](https://launchpad.net/~team-iquik/+archive/alsa)

So for other Ubuntu users with this problem, follow these steps:

[LIST=1]
[*]Open "Synaptic Package Manager" from your Ubuntu menu (under System->Administration)
[*]Click the Settings menu -> Repositories -> Other Software tab
[*]Click "Add" then paste ppa:team-iquik/alsa in and press "Add Source"
[*]If you are running Ubuntu Natty, you will need to edit the last two items on the list. Click each of the two items individually, click edit, edit the "Distribution" field from "natty" to "lucid". Hit ok.
[*]Close the "Software sources" window. Click "OK" then click "Reload" in the Synaptic window.
[*]Now click "Mark all upgrades" then "Apply". 
[*]Open Configure Wine and test your audio. It should be working now.
[/LIST]

---

### Post by thatguruguy on 2011-09-03
> **stinkinrich88 said:**
> You're not blind! But it does say it on this page: [https://launchpad.net/~team-iquik/+archive/alsa]("https://launchpad.net/%7Eteam-iquik/+archive/alsa")

So for other Ubuntu users with this problem, follow these steps:

[LIST=1]
[*]Open "Synaptic Package Manager" from your Ubuntu menu (under System->Administration)
[*]Click the Settings menu -> Repositories -> Other Software tab
[*]Click "Add" then paste ppa:team-iquik/alsa in and press "Add Source"
[*]If you are running Ubuntu Natty, you will need to edit the last two items on the list. Click each of the two items individually, click edit, edit the "Distribution" field from "natty" to "lucid". Hit ok.
[*]Close the "Software sources" window. Click "OK" then click "Reload" in the Synaptic window.
[*]Now click "Mark all upgrades" then "Apply".
[*]Open Configure Wine and test your audio. It should be working now.
[/LIST]


Natty users should already have ALSA 1.0.24.

---

### Post by stinkinrich88 on 2011-09-03
Oh right.. hmmm, I'm running Natty. Don't know what alsa version I had before but the instructions I posted fixed sound in wine for me.

---

