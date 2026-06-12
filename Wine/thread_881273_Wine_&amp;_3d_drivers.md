---
title: "Wine &amp; 3d drivers"
date: 2008-08-05
forum: Wine
---

### Post by jfooobet on 2008-08-05
I have the nvidia go 7600. Installing nvidia drivers for it in linux, makes my system too unstable. Do i need these drivers activated in linux or is there a way for only using them in Wine?

---

### Post by aoanla on 2008-08-06
Which nvidia drivers? The ones that come with Hardy, or newer ones?

You *do* need proper 3d acceleration to play modern games in Wine, and that *does* mean having the drivers working in X, not just Wine.
(However, I suppose it would be technically possible to launch a separate X session for Wine, with a separate xorg.conf... but I'm not sure it would work.)

---

### Post by dmn_clown on 2008-08-06
> **aoanla said:**
> 
You *do* need proper 3d acceleration to play modern games in Wine, and that *does* mean having the drivers working in X, not just Wine.
(However, I suppose it would be technically possible to launch a separate X session for Wine, with a separate xorg.conf... but I'm not sure it would work.)

No, it wouldn't work.  Xorg's nv driver and the blob do not co-exist.  You might be able to get away with using the vesa driver, but you wouldn't get a decent level of 2d performance.

---

### Post by aoanla on 2008-08-07
> **dmn_clown said:**
> No, it wouldn't work.  Xorg's nv driver and the blob do not co-exist.  You might be able to get away with using the vesa driver, but you wouldn't get a decent level of 2d performance.

I was thinking of vesa, yes. It's probably not worth it for fixing the original poster's problem, though.

---

### Post by jfooobet on 2008-08-08
Thanks for the replies.. I wanted to play 3d accelerated games in Wine w/o using them in linux cause they're simply not stable at all. So i guess config + restart whenever using wine, but i could live with that..:)

---

### Post by desertboy on 2008-08-09
> **jfooobet said:**
> I have the nvidia go 7600. Installing nvidia drivers for it in linux, makes my system too unstable. Do i need these drivers activated in linux or is there a way for only using them in Wine?

I assume you're using the restricted drivers, try installing the envy drivers, they're often different revisions (I get almost 10FPS more with the envy installed drivers on COD4) might solve your stability problems.

I've got a 7600go in a laptop at work at in works fine, no stability problems at all but it runs opensuse.

---

