---
title: "Can I get fully multiplexed sound?"
date: 2007-12-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Krovas on 2007-12-08
I just noticed that I don't have it. Only one app can use the sound subsystem at a time. I tried several forum searches for a relevant thread, but no joy. I don't have catastrophic sound failure, just no multiplexing. Please assist.

---

### Post by adam.tropics on 2007-12-08
I haven't tried it so can't be of much help, but you may want to look into Pulse Audio, if I understand your question correctly.

---

### Post by jpkotta on 2007-12-08
Pulse Audio is supposed to be the next big thing in Linux audio.  It would probably be better in the long run if you played with that.  If you just want multiplexed audio, you can do it straight through ALSA.  Add this to your ~/.asoundrc file (no, I don't really know how it works, that's what the URLs are for):
```
# http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=Generic
# http://alsa.opensrc.org/index.php?page=DmixPlugin
# http://www.linux.com/article.pl?sid=04/08/09/1513255

pcm.dsp0 {
    type plug
    slave.pcm "dmix"
}


# mixer0 can stay unchanged, because
# it isn't used anyway, I guess ;)
ctl.mixer0 {
    type hw
    card 0
}
```
Then make sure applications use ALSA instead of OSS (or ESD or arts).  The advantage of PA is that (allegedly) you can set volumes individually, whereas with straight ALSA, all streams use the same volume control.

---

### Post by Krovas on 2007-12-08
Okay, it looks like I am really just having a problem with a particular app (VirtualBox), and am not experiencing a lack of multiplexed sound in general. I jumped the gun again.

---

