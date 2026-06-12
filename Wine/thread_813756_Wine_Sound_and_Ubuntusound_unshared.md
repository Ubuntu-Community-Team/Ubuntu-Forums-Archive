---
title: "Wine Sound and Ubuntusound unshared"
date: 2008-05-31
forum: Wine
---

### Post by rjarl on 2008-05-31
Hi,


I did a Hardy Heron x64 fresh instalation.
I installed wine from the repositories.
I Installe World of warcraf using the nice How-to.

Everything works:
video nvidia 8800GT
audio ALSA ( 82801I (ICH9 Family) HD Audio Controller)

But, if I'm running wine with an application that uses sound i cannot use any other sound in the main system (For example Totem) or Teamspeak

Otherwise, if I start Totem player and then I open Wow with wine, then I don't get any sound..., and it drops an error:

```
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```

Seems to be an ALSA sharing problem between wine and the main sound control.

Before posting, I tried to find someone with the same problem, I find some post talking about using a "asoundrc" file, I try but no luck.

Also I try to use a registry key, but no luck.

Can please someone help?

**Edit:**
Today I updated to wine 1.0 (Becouse the suggestion of the Ubuntu updater), no change :( same issue.

Regards
rjarl

---

### Post by Shaitok on 2008-06-01
There is a fix for this that is an OSS overlay for ALSA if i remember correctly. If you do a search in you synaptics package manager for alsa-oss you should find it. I'll try to find the information that I had gotten this from and link it for you (I think it is elsewhere on these forums)

---

### Post by Shaitok on 2008-06-01
Ubuntu Community page for alsa-oss
[https://help.ubuntu.com/community/alsa-oss](https://help.ubuntu.com/community/alsa-oss)

can't find the source from where I pulled the information, but I read that Ventrilo and WoW both use OSS and cannot both have sound at the same time with it, therefore the alsa-oss fix should allow them to both work simultaneously. (haven't gotten it working myself yet, but i'm researching fixes to the same problem while I'm not at home and therefore cannot implement the possible fixes yet)

---

### Post by rjarl on 2008-06-01
Shaitok, thanks, but I have alsa-oss installed, but it doesn't work. :-(

I have readed that ubuntu 64bits version have problems managing  32 bits  sound programs.


I Try to change the  System/Preferences/Sound options from "Autodetect" to "ALSA- Advanced Linux Sound Achitecture", now i can play wine+wow amd use totem.

But I can not use flash player inside firefox.., or vlc linux, just Totem.. why?

regards
rjarl

---

