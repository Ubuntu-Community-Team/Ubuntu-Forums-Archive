---
title: "Strange crash-ish phenomenon"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by grsing on 2005-10-13
Sometimes, when I'm working with Firefox, I'll open a webpage (not any specific one, and I can't reproduce it on any page reliably) and the screen will go white, except for the borders of the windows, and not just in Firefox, but in every program.  The only way I've found to fix it is to log out and log back in, which is kind of a pain.  Also, when it is white, if I move my mouse over something that changes the cursor to a hand, that button will show back up, for a little while.  I'm running an AMD 64 system, Breezy Badger, Firefox 1.0.7, if you need more details, let me know.

---

### Post by RAOF on 2005-10-13
I remember having this problem a while ago... let me try to remember :)

Do you have an nvidia graphics card?  Do you have the nvidia-glx driver installed & running?  I think that that is what solved the problem for me.

In order to install the nvidia-glx driver you want to run (at a terminal):
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

Oh, and I remember that just changing the screen resolution worked to fix it (temporarily, at least) ;)

---

### Post by grsing on 2005-10-13
I do have an nvidia graphics card, so hopefully that fixed it.  Thanks!

---

### Post by malacoda on 2005-10-16
I had same issue. The nVidia driver does seem to fix it. Be careful though...

When I installed the nvidia drivers thru Adept a bug or something in one of the drivers would cause my machine to hang up during the boot.  Seems a bug or something in one of the drivers prevented X from starting properly.

When I installed the drivers from source per tseliot's How-To it correct both issues.

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")

---

### Post by grsing on 2005-10-16
It did fix it, good to go now, and loving Ubuntu.

---

