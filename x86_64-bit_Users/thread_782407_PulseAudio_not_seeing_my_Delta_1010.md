---
title: "PulseAudio not seeing my Delta 1010"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by millie95 on 2008-05-04
(Hardy AMD64)

When I run PulseAudio device chooser, it only shows one sound card

[IMG]http://stashbox.org/112143/Screenshot-PulseAudio%20Manager%20%5Bunix%3A-tmp-pulse-a-native%5D.png[/IMG]

System > Preferences > Sound, on the other hand shows both sound cards

[IMG]http://stashbox.org/112144/Screenshot-Sound%20Preferences.png[/IMG]

Why?

---

### Post by timeoff on 2008-05-05
See [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442") for the details of the bug and the workaround. Basically HAL based detection doesnt seem to work too well for slightly exotic cards.

---

