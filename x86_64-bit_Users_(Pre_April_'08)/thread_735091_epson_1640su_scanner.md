---
title: "epson 1640su scanner"
date: 2008-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by sepia-shots on 2008-03-25
I'm running Hardy 64

I've got an epson 1640su scanner (using USB) and need to grab some images. I can't see how this is done though. I tried using OO word, but there's no recognition of the scanner. 

Please help.

---

### Post by pseudo-random on 2008-03-25
Linux driver:
[http://www.64bitdrivers.com/driver.php?id=1391&redirect=ignore](http://www.64bitdrivers.com/driver.php?id=1391&redirect=ignore)

---

### Post by sepia-shots on 2008-03-25
Sorry could you clarify as I could be missing something here. Tthe only reference to epson 1640su drivers is a dead thread.  I would have thought that under Linux, it'd see the scanner as a simple twain device, I just don't see how to access it.

---

### Post by sepia-shots on 2008-04-08
Can anyone shed some light on this problem for me? Or suggest another scanner that'll have less of an issue.

Many thanks

Pete

---

### Post by sepia-shots on 2008-06-08
Can anyone suggest how to get my scanner to work?

Many thanks

---

### Post by sicofante on 2008-06-08
I just sumbled upon this thread looking for help myself. After some research, I found that I had to install

**libsane-extras**

from Synaptic (do a search in Synaptic for "epson" and you'll find it).

After installing, I just launched X-Sane from the menu. It took quite a while to start but it finally found my scanner and I could use my Epson 2450 scanner.

Your scanner seems to be supported by the same libraries as mine, so you probably will succeed too. Just wait the long while it takes for X-Sane to detect the scanner after you have installed the extra libraries.

Good luck.

---

