---
title: "[SOLVED] New Kernel made my Sound Card Dissapear!"
date: 2007-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by very_japi on 2007-08-29
OK, so this is the deal. My wireless card, and my CD-RW / DVD-RW were not working under Ubuntu 7.04 AMD64. After many depressing days of having to mount cd's from another computer trough the network, i finally... almost accidentally solved the problem.

I was reading a tutorial to get my wireless going (did NOT work). In the structions the tutorial asked you to update your linux-image and linux headers to 2.6.22-10 by downloading suck packages from the gutsy repositories. And so i obediently updated my kernel.

when i rebooted, my wireless still did not give any signs of life, but i noticed there was a CD mounted on my desktop. And i rejoiced.

My happiness did not last long, cuz when i tried to listen to an audio CD using my freshly fixed drive... i notice my sound card was flashing a tiny red light, and the volume control on top of the screen gave me this notice:

```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```

... isn't  there like a way to copy the old kernel's setting to the new kernel?

im just speculating about the solution, but i bet there's some genius out there who actually knows the answer.

help? anyone?

---

### Post by Jouke74 on 2007-08-29
It might be wise to install the whole gutsy distribution then.

Your alsa drivers are probably still configured for the older kernel end may depend on files which are not loaded.

---

### Post by Kilz on 2007-08-29
Be aware that if you do go all the way to Gutsy, its still under heavy development. Sometimes packages are released before others they depend on during development, when this happens the update manager likes to remove things. sometimes what it removes will make the system unusable. You are going to have to look at each update to make sure that it doesnt uninstall something important, like say your x server(graphics) or nautilus(file manager). These are just examples, there are lots of other things that could make it unusable.

---

### Post by Jouke74 on 2007-08-29
Yeah I agree with Kilz, if you want a stable system, you have to wait still. **Or** hold back on any updates and hope that this alpha Gutsy works for you.

---

### Post by very_japi on 2007-08-29
Im not really confortable with the idea of going Gutsy all the way, i think im having enough trouble as it is.

So basically, the advise is, wait until Gutsy is released?

---

### Post by Kilz on 2007-08-29
> **very_japi said:**
> Im not really confortable with the idea of going Gutsy all the way, i think im having enough trouble as it is.

So basically, the advise is, wait until Gutsy is released?

No, Id install Gutsy full. Just be careful of updates. Look at whats the update is doing. Dont just blindly click ok. In the update you will see a list of what its going to do, if its going to delete a lot of stuff, dont install it.

---

### Post by very_japi on 2007-08-29
OK, thanks. I guess i coudl try it. Even though i dont partcularly like the sound of "Alpha"--- scary.

---

