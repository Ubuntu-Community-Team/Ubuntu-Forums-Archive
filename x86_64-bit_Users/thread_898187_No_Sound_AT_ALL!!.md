---
title: "No Sound AT ALL!!"
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by fluxhomemade on 2008-08-23
I have a dell xps m1210 with intel sigmatel 9220 sound card.  I tried to download alsa-driver-1.0.18rc1 ; alsa-plugins-1.0.18rc2 ; alsa-utils-1.0.18rc2 and got the C complier cannot create executables error.  Kubuntu picks up the sound card but no matter what I do nothing come out. Can some one help me out.  Thanks

---

### Post by cariboo on 2008-08-23
Have you checked to see if pcm and playback master are turned up by double clicking on the speaker icon in the top panel?

Jim

---

### Post by Yellow Pasque on 2008-08-23
Before building ALSA, you'll need:
```
sudo apt-get install -y build-essential libncurses5-dev gettext linux-headers-`uname -r` alsa-oss
```

I made a script to do the dirty work:
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

EDIT: After that, open alsa-base file for editing
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Add or edit this line to read:
```
options snd-hda-intel model=dell-m82
```

---

### Post by jbor7755 on 2008-08-24
edit what line exactly?

There are a number of them which start with "options" in that file.

---

### Post by fluxhomemade on 2008-08-24
The volume is set on master but you have to right click on the speakerand click on select master channel.  I tried to switch it around and nothing helped.

---

### Post by Yellow Pasque on 2008-08-24
> **jbor7755 said:**
> edit what line exactly?

There are a number of them which start with "options" in that file.

If you don't see a line that begins with "options snd-hda-intel model=", then add a new one.

---

