---
title: "problems with my sound card"
date: 2006-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by jstingray on 2006-07-24
I'm running dapper with an AMD 64, I can't get my SoundBlaster Live! 24 bit to give me any sound. Works fine in windows. If I type  'sudo modprobe snd-' in a teminal, I get the following:

WARNING: /etc/modprobe.d/alsa-base.save line 28: ignoring bad line starting with '^X'
FATAL: Module snd_ not found.
this warning shows up if I boot Kubuntu in recovery mode also
I am a relative newbe, but I've managed to get everything else to work, including burning cds, plugins for Firefox, ect


Any ideas?

---

### Post by mbrang00 on 2006-07-24
Ill be watching this thread close...Im getting ready to install 64bit version myself and i too have the same sound card...

---

### Post by AllenGG on 2006-07-25
See if you have "alsa-base" installed, use Synaptic, and "alsa-utils", apparently alsa-utils conflicts with alsa-base. Don't uninstall alsa-utils or you'll take out "Gnome" at the same time. But do remove alsa-base and try your sound card again ,say Amarok or XMMS.
Look at the "properties>dependencies".

---

### Post by jstingray on 2006-07-25
I just un-installed ALSA base and my sound came back on! Thanks!
this is the last gasp for Windows, now everything works in Kubuntu!

---

