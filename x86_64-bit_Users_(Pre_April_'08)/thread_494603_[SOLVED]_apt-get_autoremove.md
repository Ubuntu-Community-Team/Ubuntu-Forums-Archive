---
title: "[SOLVED] apt-get autoremove"
date: 2007-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-07-07
How can I get apt to stop saying this.

The following packages were automatically installed and are no longer required:
  ia32-libs-sdl

I don't think I should remove that package, so I want apt to keep it next time I do apt-get autoremove.

---

### Post by crush304 on 2007-07-08
sudo apt-get autoremove
sudo apt-get install ia32-libs-sdl

that should take care of it, there is probably a better way but I'm not sure

---

### Post by fakie_flip on 2007-07-14
That worked! Thanks a lot.

---

### Post by Mr_bleu on 2007-07-14
Could you mark this thread as Solved?  It's listed in the grey tool bar.

---

