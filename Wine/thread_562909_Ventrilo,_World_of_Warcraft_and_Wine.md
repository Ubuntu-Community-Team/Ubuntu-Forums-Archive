---
title: "Ventrilo, World of Warcraft and Wine"
date: 2007-09-29
forum: Wine
---

### Post by adw404 on 2007-09-29
Hello, I am having problems using World of warcraft and Ventrilo at the same time through Wine and aoss. I have searched the forums but couldn't find an answer that worked. My problem is that Vent works fine alone, WoW works fine alone, When the 2 are run simultaneously, only 1 application gets sound (usually vent). I'm running aoss, alsa, WoW 2.2.0, the latest wine (I forgot the version number), and the latest version of vent for windows. Any help would be greatly appreciated.

---

### Post by sunfire on 2007-09-30
Try to change wine to using OSS ( winecfg )

---

### Post by adw404 on 2007-09-30
First, I appreciate you taking the time to help me.
I changed winecfg to use OSS, and the problem still exists. Also tried using NAS driver and EsounD drivers without any luck. Anything else I can try?

---

### Post by Nehvrook on 2007-09-30
Have you tried changing your system volume to OSS (Top right hand corner if you're using Gnome)

Also they just patched voice chat into WoW, is that no good for you? (Haven't tried it myself yet, I just know they put it in)

---

### Post by Aesir09 on 2007-09-30
try messing around with all the setting in the the audio section under winecfg.

---

### Post by adw404 on 2007-09-30
Setting the system volume to OSS didn't help.
There are 2 channels in vent and WoW sound settings labelled alsa-oss which is the aoss program i'm assuming, however one disappears as soon as I start either program. I'm assuming that one goes to my external speakers and the other to my mic and headset. I gather that this means that only 1 program can use each output at a time. While I don't mind using the speakers for one program and headphones for another, I usually play WoW for long hours during the night and would rather not wake others in my household.

WoW voice chat is only on a select few servers ATM, so I need an alternate way to communicate with my guild until it is released on all servers.

---

