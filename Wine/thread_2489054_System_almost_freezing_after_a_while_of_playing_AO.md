---
title: "System almost freezing after a while of playing AOEII through Wine"
date: 2023-07-17
forum: Wine
---

### Post by lordpuppet on 2023-07-17
I have an AMD computer (ryzen 7) with radeon gpu. I think that fact may be important because it was in the past for some crashes.

Whenever I am solely playing Age of empires 2 the hd version, my computer and the game start to lag really bad. It keeps happening well after exiting the game. 

For some reason only a full shutdown makes it go away. A restart doesn't. 

At some point I've been left on an initramfs console. [Here's what was on screen that time]("https://photos.app.goo.gl/CE9hf9kV7fPiH3x87").

Some people suggest to show what's been on the var/log/syslog file right until that point so I printed the last 100 lines before the crash and you can see it [here]("https://justpaste.it/bcf05").

PD: maybe its unrelated but I sometimes get SIGILL and SIGSEGV errors in chrome. Also when sharing screen it sometimes does the same that when playing AOEII.

Details of my computer
ThinkPad E15 Gen 2
OS: Ubuntu 22.04.2 LTS x86_64
Kernel: 5.19.0-46-generic
CPU: AMD Ryzen 7 4700U with Radeon G
GPU: AMD ATI 04:00.0 Renoir

Using Xorg ($XDG_SESSION_TYPE = X11)

---

### Post by QIII on 2023-07-17
Moved to Wine sub-forum.

---

### Post by lordpuppet on 2023-07-17
I don't think it's related to wine though.

---

### Post by lordpuppet on 2023-07-17
> **QIII said:**
> Moved to Wine sub-forum.

Please move back to General Help. This isn't related to wine exclusively.

---

