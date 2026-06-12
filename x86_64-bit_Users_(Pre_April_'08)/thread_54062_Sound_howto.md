---
title: "Sound howto"
date: 2005-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by mega on 2005-08-03
Is there a sound howto for the amd64?

I tried going 64bit, but as soon as I hit the flash & sound howto's I ran into problems, packages that are not in the 64bit deb repositories

dropped back to 32bit for now, but I would really like to give the 64bit version more than 15 minutes on my machine.

I was using this..

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

but this package is not avalible
libesd-alsa0


I didnt get far into flash, opened firefox, clicked install plugin, it said there was none avalible, I didnt go any farther into flash

---

### Post by tseliot on 2005-08-03
Flash is not available for 64bit system, you could use it through a chroot though.

As far as the other files are concerned, just add Tamir's repositories to your sources.list. (have a look at the "amd64 packages" thread)

---

### Post by Tamir on 2005-08-03
[QUOTE=mega]Is there a sound howto for the amd64?

I tried going 64bit, but as soon as I hit the flash & sound howto's I ran into problems, packages that are not in the 64bit deb repositories

dropped back to 32bit for now, but I would really like to give the 64bit version more than 15 minutes on my machine.

I was using this..

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

but this package is not avalible
libesd-alsa0


I didnt get far into flash, opened firefox, clicked install plugin, it said there was none avalible, I didnt go any farther into flash[/QUOTE]
 libesd-alsa0 is available. I made it. look here:
[http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

:)

---

### Post by mega on 2005-08-03
Ouch no flash kinda hurts, macromedia/adobe suck!


Are you all noticing a speed difference in gnome or thunderbird/firefox?   I honestly could not tell the difference, this box is a 3200 amd64, only used for email/web/basic desktop stuff

---

### Post by Leira on 2005-08-14
[QUOTE=Tamir]libesd-alsa0 is available. I made it. look here:
[http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

:)[/QUOTE]

i used an "aoss esd" before, it worked find. and i installed your libesd-alsa0, restart esd, when i play sound with esd, it makes a lot of noise. then i replace libesd-alsa0 back to libesd0, and use "aoss esd", it plays clear sound again. what's wrong? should i have to change some settings?

---

### Post by kao on 2005-08-14
[QUOTE=Leira]i used an "aoss esd" before, it worked find. and i installed your libesd-alsa0, restart esd, when i play sound with esd, it makes a lot of noise. then i replace libesd-alsa0 back to libesd0, and use "aoss esd", it plays clear sound again. what's wrong? should i have to change some settings?[/QUOTE]

After libesd-alsa install, you have to write /etc/asound.conf.
There are tip how to get correct sound in ubuntuguide.

---

### Post by Leira on 2005-08-14
[QUOTE=kao]After libesd-alsa install, you have to write /etc/asound.conf.
There are tip how to get correct sound in ubuntuguide.[/QUOTE]
if u mean the dmixer's config, i've done it b4. and my config works ok with multi stream sounds, and esd use "aoss esd".

---

### Post by DancingSun on 2005-08-15
[QUOTE=Leira]i used an "aoss esd" before, it worked find. and i installed your libesd-alsa0, restart esd, when i play sound with esd, it makes a lot of noise. then i replace libesd-alsa0 back to libesd0, and use "aoss esd", it plays clear sound again. what's wrong? should i have to change some settings?[/QUOTE]
Is it crackling as if the speaker's overloaded?  If you have PCM volume on 100%, try lowering it to around 70-80%.

---

### Post by kao on 2005-08-17
[QUOTE=Leira]if u mean the dmixer's config, i've done it b4. and my config works ok with multi stream sounds, and esd use "aoss esd".[/QUOTE]

maybe it's problem with amplifier. Try to decrease level of PCM or Master channel (i have 71% and 55% accordingly)

---

### Post by Steve1961 on 2005-09-04
I've never yet managed to get alsa sound working properly on my amd64 box.  Even after editing the config files and experimenting with volume and alsamixer settings I still get static and the quality is scratchy.  I've decided to stick with esd because that seems to work well.

---

