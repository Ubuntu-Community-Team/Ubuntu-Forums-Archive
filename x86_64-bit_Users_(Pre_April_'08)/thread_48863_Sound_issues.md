---
title: "Sound issues"
date: 2005-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by tyfius on 2005-07-14
Hi,

I have a MSI K8N SLI Platinum Socket 939 Soundblaster Live mobo, and following the guide posted by eubuntu_geek (i think).
I have sound, but i can't change anything via the gnome windows. If I want to adjust it I have to open a terminal and go via alsamixer.
Imo, that's not the way to keep doing it.

I also tried the nforce driver made by nvidia, downloaded it on their site, installed it, but it didn't work. I have no idea howto uninstall it, so it still remains on the system.

If anyone knows how to solve this.

tnx

---

### Post by mo_x on 2005-07-14
From a console type:
sudo sh NFORCE-Linux-x86-1.0-0301-pkg1.run --uninstall
type:
sh NFORCE-Linux-x86-1.0-0301-pkg1.run -A
to see all te options.

To get the nvidia driver working I created the file /etc/modprobe.d/nvsound with the following line in it:
alias sound-slot-0 nvsound
I added the module that was loaded by default (snd-intel8x0 in my case) to the file /etc/hotplug/blacklist.
The nvsound module is for OSS and not ALSA so your applications should use OSS.

Mo X

---

### Post by cafevincent on 2005-11-13
[QUOTE=mo_x]
I added the module that was loaded by default (snd-intel8x0 in my case) to the file /etc/hotplug/blacklist.[/QUOTE]

You say "in my case", how do I figure out if it can be something else in my case?

---

