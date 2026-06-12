---
title: "Wine keyboard &quot;sticky&quot; keys"
date: 2008-05-18
forum: Wine
---

### Post by evilviper77 on 2008-05-18
When I try to run Steam games (TF2 to be exact) or LOTRO under wine i'll have a key get "stuck" (not in reality, the computer just thinks the key is still being pressed) when playing; there is nothing I can do to stop the computer from thinking it's pressed other than exiting out of the x-server environment back to the text-based console one.

How do I fix this? It really makes playing games quite unbearable. I've already tested plugging in a usb keyboard and see if it still does it and it still has this problem.

I run under archlinux, use the xfce4 desktop manager, and use an Nvidia Geforce go 7900GS video card.

---

### Post by DoktorSeven on 2008-05-18
I've had this exact problem with Arch Linux -- it's not just wine, either, I've played around with holding down certain keys and pressing the mouse button in a terminal and getting it stuck as well.

From my research it has something to do with the version of the X server running in Arch (and maybe its interaction with certain kernels, or something -- all of the things I found were sort of inconclusive as to the exact cause, but seemed to agree that updating X to the latest versions fixed it).  Basically it's something you'd need to take up with Arch about.

---

### Post by evilviper77 on 2008-05-19
> **DoktorSeven said:**
> I've had this exact problem with Arch Linux -- it's not just wine, either, I've played around with holding down certain keys and pressing the mouse button in a terminal and getting it stuck as well.

From my research it has something to do with the version of the X server running in Arch (and maybe its interaction with certain kernels, or something -- all of the things I found were sort of inconclusive as to the exact cause, but seemed to agree that updating X to the latest versions fixed it).  Basically it's something you'd need to take up with Arch about.

Thanks. I searched the arch forums and found something but sadly the patch download server isn't giving the full file, so I can't test out the patch =(

edit: Fixed and fixed. This thread is closed.

---

