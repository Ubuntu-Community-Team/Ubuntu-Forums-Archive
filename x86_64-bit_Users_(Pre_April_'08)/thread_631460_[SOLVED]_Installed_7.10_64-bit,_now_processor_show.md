---
title: "[SOLVED] Installed 7.10 64-bit, now processor shows up as half power"
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Goop on 2007-12-04
I'm pretty happy with my new Ubuntu install, and hope to get into the general Linux scene. However, I seem to have run into a problem. My 2.2GHz AMD64 processor works fine on Ubuntu, and on Windows too (my Windows is, I think, a 32-bit install). But on Windows, right-clicking My Computer and clicking properties tells me that I have only a 995MHz processor. Is this because it is a 32-bit install on a 64bit processor? There don't seem to be any driver updates for it, and Ubuntu works perfectly so far, it even got my local network shares running.

Has anyone else experienced this?

EDIT: Very strange, it now seems to be switching back and forth between 995MHz and 2.20GHz. I checked it 5 minutes ago and it was smaller, now it's back to 2.20GHz again. Could this be due to processor load at the time?

---

### Post by Dragos Largu on 2007-12-04
Indeed, this has to do with processor load. If you have an AMD Cool'n'Quiet enabled processor and motherboard, the processor adjusts speed according to load. This is a very good thing, as it reduces tempreture, noise, and power consumption.

I have no ideea if this technology is availible in Ubuntu though. It would be nice if it was :)

---

### Post by Goop on 2007-12-04
Ah, OK. Thanks, I was getting worried that my processor was failing on me (and I kept forgetting which one it really was!). Moral of the story: Ubuntu community rocks!

---

### Post by Jouke74 on 2007-12-04
Yes, it's also available under Ubuntu, but here it is called CPU frequency scaling.

---

