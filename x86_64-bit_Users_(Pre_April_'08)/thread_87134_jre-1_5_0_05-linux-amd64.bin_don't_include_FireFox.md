---
title: "jre-1_5_0_05-linux-amd64.bin don't include FireFox Plugin"
date: 2005-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by JuanC on 2005-11-07
I downloaded jre-1_5_0_05-linux-amd64.bin from Sun website and install it.

I search into jre installation folder for a Java FireFox plugin , but i don't find.

Is Sun waiting for FireFox 1.5 release?

Where i can download a Java AMD64 FireFox plugin?

---

### Post by uniko on 2005-11-07
AFAIK Sun doesn't have a 64bit plugins. You can however install Blackdown Java which includes the plugin, choose Applications --> More Applications -->Internet -->More.. and Blackdown Java Webstart. Or search for Blackdown in synaptic.

---

### Post by SleepyHollow on 2005-11-07
[QUOTE=uniko]AFAIK Sun doesn't have a 64bit plugins. You can however install Blackdown Java which includes the plugin, choose Applications --> More Applications -->Internet -->More.. and Blackdown Java Webstart. Or search for Blackdown in synaptic.[/QUOTE]

Alright (got the same problem) but where is the package located. Synaptic doesn't find it.

I have all from main until multiverse.

---

### Post by uniko on 2005-11-07
It's in development branch in multiverse. You might want to do 

```

sudo apt-get update
sudo apt-cache search j2re1.4
```

Search shows both the Blackdown Java Runtime and mozilla-plugin in my computer.

---

