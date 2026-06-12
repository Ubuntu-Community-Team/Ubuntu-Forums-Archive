---
title: "Crashed GUI on AMD x64 dual core"
date: 2006-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by trebor10810 on 2006-11-01
I am up and running 6.06 on AMD X64 dual core +3800 (Gnome) and now trying to configure my graphics (onboard NVIDIA 6100)to run wine and blender.

After following various threads all without achiving success I managed to crash my whole GUI. Just before the fatefull ctrl-alt-backspace I seem to remeber a backup of /etc/X11/xorg.conf being mentioned but finger trouble took over. My knowledge of commandline is limited to nothing!
Is there a way to restore to back up? 
Then proceed to get this baby working to run wine
Thanks in advance

---

### Post by kuja on 2006-11-01
I would assume to get the graphics working you would do something similar to this:

```

sudo apt-get install nvidia-glx
sudo nvidia-xconfig
startx

```

See if that works for you, kay?

---

### Post by trebor10810 on 2006-11-02
Sir/Madam, you are a master, scholar and gentleman/lady and I am indebted to you. You saved about 8 hours of re-installation.
Thank you

---

### Post by kuja on 2006-11-02
You're welcome :) Glad to hear that it fixed it for you.

---

