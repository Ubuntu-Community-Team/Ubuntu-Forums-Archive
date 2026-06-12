---
title: "Scratchy audio"
date: 2008-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by sir_real on 2008-02-10
Hi,

I'm running Ubuntu 7.04 Feisty 64bit. All audio I play, no matter what program, sounds scratchy. 

Interestingly, if I log in under KDE tha audio is clear as a bell. The problem only occurs under Gnome. I've read all the other threads on scratchy audio and they either they don't apply to my situatuion or their solutions don't work.

AMD Athlon 64 X2 Dual Core Processor 5000+
nVidia Chipset MCP55 High Definition Audio AD198x Digital using digital output

Anyone got any ideas?

---

### Post by dayanandasaraswati on 2008-02-10
Have you installed ALSA driver.. If so then go to the volume icon in the system tray, right click on it and click Preferences. There try toggling the output device. This might work..

---

### Post by Modified.Reality on 2008-02-10
I had a simular problem and it was a simple driver issue.

---

### Post by sir_real on 2008-02-10
> **dayanandasaraswati said:**
> Have you installed ALSA driver.. If so then go to the volume icon in the system tray, right click on it and click Preferences. There try toggling the output device. This might work..

I assume I've got the right driver installed. As I said, the audio is perfect when logging in under KDE (same OS install, different desktop environment)

Toggling the output device does not work.

Lowering the PCM volume does not work.

Trying OSS instead of ALSA does not work.

---

