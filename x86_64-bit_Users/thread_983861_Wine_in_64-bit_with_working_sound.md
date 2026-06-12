---
title: "Wine in 64-bit with working sound"
date: 2008-11-16
forum: x86 64-bit Users
---

### Post by Ng Oon-Ee on 2008-11-16
Hi all,

I've always run Wine using aoss (the alsa-oss package for emulating Alsa in programs using OSS). The reason is simply that the Wine Alsa drivers are buggy and scratchy in sound quality, while the OSS drivers are mature. The JACK drivers are okay, but I only use that for serious sound applications (and I haven't found a windows one I really want yet).

So, anyway, when I installed Intrepid 64-bit, I realized my games had stopped emitting sound. The error I got was ```
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
```. This obviously indicated a problem with aoss, so a bit of googling found a year-old thread which suggested installing the 32-bit version of aoss, and provided a .deb.

However I didn't feel like installing that, given it WAS a year old and meant for Gutsy. So I just went to packages.ubuntu.com, searched for 'alsa-oss', downloaded the i386 deb from [this page.]("http://packages.ubuntu.com/intrepid/alsa-oss") It can be opened through the archive manager (right-click and open archive, don't install). Then, I extracted the /lib folder in data.tar.gz within the archive (you only need this, as far as I can tell). There were a bunch of files, I just put them all in /usr/lib32 (not in /usr/lib), and viola, no more error and perfectly working sound in 64-bit Intrepid for Wine.

Now, back to NWN2....

---

### Post by ubun_two on 2008-11-16
Are you using pulseaudio?  I removed pulseaudio from my Intrepid system, and the sound started working fine.

---

### Post by Ng Oon-Ee on 2008-11-16
I like PA's functionality, I use it in conjunction with JACK (there's a HOWTO somewhere round these forums for that).

And I do believe in the 64-bit case that simply removing PA wouldn't help. A 32-bit app (Wine) is still trying to access 64-bit drivers (ALSA), though I believe installing lib32sound (sp?) and stuff like that does allow it.

Slightly simpler, but I WANT software mixing, having my music playing while hearing alerts from email/chat and Skype-ing is just nice to do.

Thanks though :)

---

