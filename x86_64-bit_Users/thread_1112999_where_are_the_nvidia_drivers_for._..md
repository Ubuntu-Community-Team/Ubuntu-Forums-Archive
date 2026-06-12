---
title: "where are the nvidia drivers for. ."
date: 2009-04-01
forum: x86 64-bit Users
---

### Post by vodkashot on 2009-04-01
Nvidia GeForce GTX 295 1792MB Graphics Card, that will be running on a 64 bit system?

Is the card even supported for ubuntu/linux?

---

### Post by Monsieur Gonzalez on 2009-04-01
Well, at least they're supported in the latest ([180.44]("http://us.download.nvidia.com/XFree86/Linux-x86/180.44/README/appendix-a.html")) Nvidia driver for Linux. 

Should work out of the box with upcoming 9.04. If you want it to run in Intrepid, I'd carefully follow the directions [here]("http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html") (don't worry about the Mythtv stuff, it provides an up-to-date nvidia driver).

As always, when dealing with graphic driver updates, be prepared to fix things in case they don't work (they do for me, but YMMV).

---

### Post by RedSingularity on 2009-04-01
Yeah just get the new drivers available in the package manager.

---

### Post by steeleyuk on 2009-04-01
The 185.x series which I believe is beta might be worth a look but stability should be an issue. You'll have to install it manually as well and download the binary from the nvidia website.

---

