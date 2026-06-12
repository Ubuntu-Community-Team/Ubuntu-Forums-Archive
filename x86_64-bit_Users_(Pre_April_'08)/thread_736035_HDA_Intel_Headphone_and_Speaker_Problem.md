---
title: "HDA Intel Headphone and Speaker Problem"
date: 2008-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by remu on 2008-03-26
Hello Guys,
I just got a new HP dv2700t laptop and installed Gutsy on it. Everything worked perfectly out of the box, except for the audio which is HDA Intel. The sound out of the speakers works no problem, however, when ever I plug my headphones in, the speakers don't turn off, I get sound out of both the speakers and the headphones.

I've searched around, and this seems like a common problem, one which I haven't been able to find a fix for yet. I tried what the wiki said, which was to add "options snd-hda-intel model=laptop" to "/etc/modprobe.d/alsa-base" and then reboot, that did not work. I then tried to update alsa to 1.0.15 using a script I found in the forums, it did not fix the issue, but I don't know if it actually upgraded alsa properly or not.

I installed the Hardy beta because I heard that the issue was solved in there, and to my surprise it was. However, I'm new to Ubuntu (switched over in December), and am not too comfortable running a beta, I don't know I'm just paranoid that I'll end up with problems I won't be able to handle.

So, If anyone could help me out with this, that would be GREAT!

---

### Post by Yellow Pasque on 2008-03-26
Try upgrading to ALSA 1.0.16 and/or using different model= settings (try model=hp, model=3stack, model=lenovo)
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

You should also try OSS4 before upgrading/reinstalling your distro.

---

