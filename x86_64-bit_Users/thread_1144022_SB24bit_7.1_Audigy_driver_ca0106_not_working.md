---
title: "SB24bit 7.1 Audigy driver ca0106 not working"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by krishnansrinivasan on 2009-04-30
[LEFT]I'm new to linux .I have a SB24bit 7.1 Audigy sound card.I have installed ubuntu 9.04 64bit.it's working fine.but not my soundcard drivers. Ubuntu recognizes my hardware , ca0106 was working fine till i installed  audacity.after which there was no sound.I uninstalled audacity,there is no change even when mute is unchecked.I tried most of the methods said in forums but still it shows no sign of recognizing sound.

[LIST]
[*] totem movie player
[*] mmplayer
[*]vlc
[*] real player
[*] rhythm box nothing plays with sound.
[/LIST]
 mmplayer says some PCM error when i play a movie. i adjusted etc/modules by adding snd-ca0106 @ the end..but no use. when i did this sudo modprobe snd-ca0106 ,i get these messages..

[LIST]
[*] WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release. WARNING: All config files need .conf: /etc/modprobe.d/sound.save, it will be ignored in a future release. WARNING: /etc/modprobe.d/alsa-base line 8: ignoring bad line starting with 'AD1988/AD1988B/AD1989A/AD1989B' WARNING: /etc/modprobe.d/alsa-base line 9: ignoring bad line starting with '6stack' WARNING: /etc/modprobe.d/alsa-base line 10: ignoring bad line starting with '6stack-dig' WARNING: /etc/modprobe.d/alsa-base line 11: ignoring bad line starting with '3stack' WARNING: /etc/modprobe.d/alsa-base line 12: ignoring bad line starting with '3stack-dig' WARNING: /etc/modprobe.d/alsa-base line 13: ignoring bad line starting with 'laptop' WARNING: /etc/modprobe.d/alsa-base line 14: ignoring bad line starting with 'laptop-dig' WARNING: /etc/modprobe.d/alsa-base line 15: ignoring bad line starting with 'auto'
[/LIST]
Is there any possibilities..????[/LEFT]

---

### Post by krishnansrinivasan on 2009-04-30
I have a dual boot with windowsSp3 32bit in seperate HDD.
and my motherboard has cmedia6501 sound card inbuilt ...is that have anything to do with my other soundcard..??
SB24bit 7.1 Audigy works perfect with windows.

---

