---
title: "instaling wine on 64"
date: 2007-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by MadMax08 on 2007-11-22
hey  all...
is there a way to install wine on Gutsy 64 without the Gutsy cd? i dont have access to the cd right now, and downloading it again at my location will take hours. when i run
```
sudo apt-get build-dep wine
``` it prompts me to insert my Gutsy cd. is there a way around this?

---

### Post by delphiguy on 2007-11-22
not too familiar with b4 bits but have you tried
sudo apt-get install wine

---

### Post by Sukarn on 2007-11-22
do a ```
sudo nano /etc/apt/sources.list
``` and remove or comment out (by putting a # before the line) the line that has cdrom in it.

---

### Post by Ehtetur on 2007-11-22
You can add the repos from WineHQ to your sources.list and install the latest and greatest version... They have x64 & x86 versions for Gutsy....
Here are the details:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by rune0077 on 2007-11-22
I have wine running, and I'm pretty sure I just installed with Synaptic by searching for it, and it works fine so far (well I think it works fine, I don't really use it that much).

---

