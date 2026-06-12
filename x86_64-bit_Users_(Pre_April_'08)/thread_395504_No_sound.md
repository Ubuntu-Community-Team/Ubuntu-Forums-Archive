---
title: "No sound?"
date: 2007-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by andy_blah on 2007-03-28
I am a newby and I donnot know what the principal symptoms can be. I have the speakers turned on and the master volume is at 80% (standard), so that`s not the problem if you wanted to ask me this :lolflag: . In the volume control I have 3 devices :
- Via 8237 (Alsa Mixer) (the onboard soundcard)
- C-media PCI CMI-8738-MC6 (Alsa Mixer) (the device I would want to use)
- Via Technologies 1617A (Oss Mixer) (still the onboard soundcard?)

I have XMMS player and I am listening to mp3 music but I have a plugin for it so that`s not the problem.
I also run the Ubuntu 6.10 x86 version.
So, can anybody tell me what the reason could be?

Thanks,
>-Andy-<

P.S.: Mods/Admins, please move this topic to the area of the forums for x86, because I don`t have 64 processor

---

### Post by goghgoner on 2007-03-28
Sorry, my sound actually worked shortly after install. I had to go into Administration -> Sound and play with different settings but this probably won't work the same for a different soundcard.

This [ thread ]("http://ubuntuforums.org/showthread.php?t=205449") should help 


If the general troubleshooting stuff doesn't work, I usually google the piece of hardware with ubuntu (ex. CMI8738-MC6 ubuntu).

---

### Post by lprofil on 2007-03-28
Hi there,

i am experiencing the same problem with my CMI 8738 soundcard.
After i ugraded to kernel-version 2.6.20-12 i have no more sound.

[Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bugs") should be the right platform to complain and file a bug report. 
I have to search for my account password first and file a report for this particular card later.

/lprofil

```
lspci | grep audio
04:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
```

---

### Post by andy_blah on 2007-03-28
Thanks for the help, the problem was that XMMS used the wrong device. Anyway does anybody know how to set one device to be default? I tried to do it as the that troubleshooting page you suggested me but I got confused. I modify that file and when I try to edit it again the settings are back as they were.

Thanks,
>-Andy-<

---

