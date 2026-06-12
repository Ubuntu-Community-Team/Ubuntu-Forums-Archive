---
title: "[SOLVED] Sound problems"
date: 2008-10-14
forum: x86 64-bit Users
---

### Post by chazn85 on 2008-10-14
Hi all,

Ive now made the total leap away from windows on my main 64 bit machine having 32 bit on 1 of my 500gb drives and 64bit ubuntu on the other.  64 bit now seems to work a lot better out of the box for me than 32 bit (only taken me an hour to get all my ssh tunnels, keys, plugins etc working) however ive got one niggly problem left.  

Once the im playing for example a you tube file or something in song it wont allow multiple channels for sound open up.  By that i mean if i have songbird open and go to you tube and try to play something i get sound no audio.  Same thing with my vbox guests i have to restart the vbox with nothing playing to enable the passthrough sound.

Any ideas?

Thanks

---

### Post by linux4life88 on 2008-10-14
Go to Preferences then to Sound and change sound to ALSA.

---

### Post by chazn85 on 2008-10-14
> **linux4life88 said:**
> Go to Preferences then to Sound and change sound to ALSA.

Would that be for all options under devices.  Its currently set to alsa for sound playback but nothing else.

thanks

---

### Post by chazn85 on 2008-10-16
> **chazn85 said:**
> Would that be for all options under devices.  Its currently set to alsa for sound playback but nothing else.

thanks

Just a note to all who may be having the same issue that this now works with Pulse audio server rather than alsa.

Thanks

---

