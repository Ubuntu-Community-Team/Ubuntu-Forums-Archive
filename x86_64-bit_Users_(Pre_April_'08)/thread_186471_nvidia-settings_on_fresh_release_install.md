---
title: "nvidia-settings on fresh release install"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by feight on 2006-06-02
If you try to apt-get install nvidia-settings it attempts to uninstall nvidia-glx. I'm guessing incompatability due to versions but I don't know how to find that out.
Any suggestions?

Thanks ahead of time.

---

### Post by Cableless on 2006-06-02
The nvidia-glx package already contains nvidia-settings.  Just hit ALT F2 and enter nvidia-settings

---

### Post by johnc4510 on 2006-06-02
nvidia settings is now included in the glx package
To start it, type this in terminal:
nvidia-settings
Applications>Accessories>Terminal   This is where to find the terminal

---

### Post by feight on 2006-06-02
Ahh sorry, I didn't realize it was inclusive now. What's the seperate nvidia-settings for these days, those that have nvidia without glx?

---

### Post by RAOF on 2006-06-02
[QUOTE=feight]Ahh sorry, I didn't realize it was inclusive now. What's the seperate nvidia-settings for these days, those that have nvidia without glx?[/QUOTE]
What do you mean?  nvidia-settings doesn't work without the nvidia driver, does it?

---

### Post by feight on 2006-06-02
I'm not sure, that's what I'm trying to figure out. There is a 'seperate' option to install nvidia-settings, I have no idea what it is for these days if nvidia-glx has nvidia-settings included inside of it.

---

### Post by JoWilly on 2006-06-02
[QUOTE=feight]I'm not sure, that's what I'm trying to figure out. There is a 'seperate' option to install nvidia-settings, I have no idea what it is for these days if nvidia-glx has nvidia-settings included inside of it.[/QUOTE]

This is probably due to nvidia-glx beeing updated, now resulting in nvidia-settings beeing a left over...

---

### Post by feight on 2006-06-02
Sounds good to me. Thanks for all the responses, now I can stop worrying about it.

---

