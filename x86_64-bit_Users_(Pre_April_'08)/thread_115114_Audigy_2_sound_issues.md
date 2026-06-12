---
title: "Audigy 2 sound issues"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by poiuytr on 2006-01-09
I have tried everything I have seen here or anywhere else on the Internet to get sound working on my AMD64 Breezy installation:

Onboard sound disabled in the BIOS?  Yes
All connections checked, and sound working properly in other distros on this multiboot machine?  Yes.
Alsamixer used to tweak settings?  Yes.
Tweaks performed in Gnome panel's Volume Control?  Yes.
ESD turned off?  Yes.
Alsa packages installed, reinstalled, reconfigured?  Yes.
etc. etc.  Still, not a peep from either sound device.

I'm using an Audigy 2 as well as a USB Logitech headset.  No sound from either, ever, and I have run out of things to try.

I'm just a desktop guy.  If anyone more seasoned can walk me through this, I would be grateful.  I will post more details (eg lspci. lsof) as requested.

Thank you very much in advance for any help.

---

### Post by BoyOfDestiny on 2006-01-10
[QUOTE=poiuytr]I have tried everything I have seen here or anywhere else on the Internet to get sound working on my AMD64 Breezy installation:

Onboard sound disabled in the BIOS?  Yes
All connections checked, and sound working properly in other distros on this multiboot machine?  Yes.
Alsamixer used to tweak settings?  Yes.
Tweaks performed in Gnome panel's Volume Control?  Yes.
ESD turned off?  Yes.
Alsa packages installed, reinstalled, reconfigured?  Yes.
etc. etc.  Still, not a peep from either sound device.

I'm using an Audigy 2 as well as a USB Logitech headset.  No sound from either, ever, and I have run out of things to try.

I'm just a desktop guy.  If anyone more seasoned can walk me through this, I would be grateful.  I will post more details (eg lspci. lsof) as requested.

Thank you very much in advance for any help.[/QUOTE]

Hmm mine worked great in Breezy (and in Dapper too), without ESD anyway... This is a longshot, but did you download the alsa-oss wrapper, and libsdl-all (something similar to those, going from memory here). It's possible the app you want to produce sound from needs these. As for system sounds, with ESD turned off you should not hear them.

Good luck!

---

### Post by poiuytr on 2006-01-10
Hmmm.  I've got alsa-oss installed, but there are a large number of libsdl packages and some are installed and some aren't.  Can you remember which one you were thinking of?

I don't know what Simple DirectMedia Level is - I need to research that now.  Thanks for the idea.

---

### Post by BoyOfDestiny on 2006-01-11
[QUOTE=poiuytr]Hmmm.  I've got alsa-oss installed, but there are a large number of libsdl packages and some are installed and some aren't.  Can you remember which one you were thinking of?

I don't know what Simple DirectMedia Level is - I need to research that now.  Thanks for the idea.[/QUOTE]

I guess it is a meta-package:

libsdl1.2debian-all

A lot of the emulators and games use SDL. Hope this helps.

---

