---
title: "Firefox 3.0.8 download problems"
date: 2009-04-02
forum: x86 64-bit Users
---

### Post by kneewax on 2009-04-02
Is anyone else suffering with a problem with the download manager of FF3.0.8 in x64 Intrepid?

I cannot download any file type using right+click save, save as,save image, save image as etc.

All was working fine until the recent update from the repos?

Anyone else getting this?

---

### Post by philinux on 2009-04-02
Just tested and working fine here.

Try running in safe mode.

```
firefox -safe-mode
```

---

### Post by Sef on 2009-04-03
Ubuntu has updated to firefox 3.08.   If you are current with your updates, then you will have that version.

---

### Post by yperiard on 2009-04-08
Same thing here, no save at all. Tried with safe-mode, didn't change anything

Firefox 3.0.8
Ubuntu 8.10 64 bit

anything else that might help?



thanks

---

### Post by kneewax on 2009-04-09
Hey I came up with something!  Not sure if this effects you, but my FF had reset the default download folder to a volume I removed from the machine some months back - guess an update must have confused it or something.  Rather than give an error saying the folder was unavailable FF just opted not too download it!  

Try resetting the default download folder to another location and see if FF corrects itself, if the download location is still available you can switch it back after testing the new settings!

---

### Post by _khAttAm_ on 2009-04-10
> **yperiard said:**
> Same thing here, no save at all. Tried with safe-mode, didn't change anything

Firefox 3.0.8
Ubuntu 8.10 64 bit

anything else that might help?



thanks

me too with the same software versions and no problems..

try disabling all addons (or run in safe mode) to see what happens.

---

### Post by mrf76 on 2009-04-22
Thanks kneewax, your solution working for me :-)

---

