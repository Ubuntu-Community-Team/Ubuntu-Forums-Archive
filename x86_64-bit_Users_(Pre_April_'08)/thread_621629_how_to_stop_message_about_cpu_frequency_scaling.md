---
title: "how to stop message about cpu frequency scaling"
date: 2007-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-11-23
My processor does not have cpu frequency scaling, so how can I get this message to stop displaying every time I start gnome?

---

### Post by go_beep_yourself on 2007-11-23
My processor does not have cpu frequency scaling, so how can I get this message to stop displaying every time I start gnome?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=51187&d=1195873308[/IMG]

---

### Post by Unspeakable Horror on 2007-11-24
Untick in the Services control cpu frequency scaling. Or using bootup manager look for powerd (or something like that) or cpu-freq and untick either of them (you should only have one or the other in there)
Don't touch anything else unless you know what you are doing or you will mess up your system.

---

### Post by kiev on 2007-11-25
[http://ubuntuforums.org/showthread.php?p=3829425](http://ubuntuforums.org/showthread.php?p=3829425)

---

### Post by vrangforestillinger on 2007-11-26
I had the same problem. The message went away when I removed a "CPU frequency scaling monitor"-applet. Its was a thing on my gnome panel that showed the CPU-frequency.

---

### Post by go_beep_yourself on 2007-11-27
> **vrangforestillinger said:**
> I had the same problem. The message went away when I removed a "CPU frequency scaling monitor"-applet. Its was a thing on my gnome panel that showed the CPU-frequency.

Actually, that is why I have the pop up too. Since my cpu is overclocked, the cpu frequency scaling is disabled. I'd still like to keep the applet though, looks cool and lets me know how fast my cpu is overclocked too.

---

