---
title: "Cannot talk on ventrilo"
date: 2008-04-28
forum: Wine
---

### Post by tiptip on 2008-04-28
Hello,

I'm using Ventrilo 3.0 (running Speex codec), hearing people works great but i cannot talk.
I tried using 'push to talk' and without it, the mic working great when i try to record my voice with "gnome-sound-recorder".

Another thing is when i press on the ptp key i dont see the green light near my name.

(i'm using wine-0.9.59 & ubuntu 7.10).

thanks ahead.

---

### Post by situz on 2008-04-28
are you using OSS or ALSA on your winecfg-> sound tab ?

you should be using OSS =)

edit: check out [https://help.ubuntu.com/community/WorldofWarcraft#head-9f4c9e2df7bf2ce0429e495e9e6e55f58eac4e49](https://help.ubuntu.com/community/WorldofWarcraft#head-9f4c9e2df7bf2ce0429e495e9e6e55f58eac4e49)
there you can find info of how to get multiple programs using oss for sound to work simultaneously (with oss, only one program is allowed to use sound at the time)

---

### Post by crayzeigh on 2008-05-01
Not to accidentally resurrect an old thread, but I just have a clarification question regarding the posted walk through for ALSA-OSS...

It mentions that one of the solutions to hardware mixing was to get a PCI sound card, which, conveniently enough, I actually use and prefer over my on board options. So... should I just enable OSS and my card (SBAudigy[the first one]) takes care of the rest? Or should I still set-up ALSA-OSS and let the software take care of business? Or should I actually just figure out if my sound card supports hardware mixing as it may not?

---

### Post by tiptip on 2008-05-02
Hi again,
I tryed the "alsa-oss" solution and it doesn't work :/ i can hear other people but they dont hear me.
the only way i can make it works by running Win XP on VirtualBox and installing ventrilo on that. but i dont like this solution.

---

