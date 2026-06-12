---
title: "Why did this matter?"
date: 2007-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by siteguru on 2007-05-20
Here is an extract from my menu.lst grub menu ...

```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e1f886b8-e818-499b-89ba-cff2f5a22fb6 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e1f886b8-e818-499b-89ba-cff2f5a22fb6 ro single
initrd		/boot/initrd.img-2.6.20-15-generic
```
The first entry is the normal Ubuntu boot, and the second is the recovery mode version (where you eventually get to the root password/Ctrl-D prompt). If I tried to boot using the first option I would end up with a blank screen (no Xserver login screen), but with the second option I would see all the loading parameters and then be presented with the Xserver login screen (after doing the Ctrl-D).

I then edited the menu.lst file to remove the word **splash** from the first option ... now I see all the loading parameters but also go straight to the Xserver login screen! (And all seems to be working OK).

Whilst I am happy that this appears to have fixed the problem I was having, I would be interested to understand WHY this seems to have worked. Any ideas?

PS - this is Feisty Fawn 7.04 AMD64 install I am talking about.

---

### Post by kidders on 2007-05-21
Hi there,

I had a similar sort of issue (with a 16:9 DVI monitor) ... I figured that the unavailability of a suitable splash image was causing the problem, so I did what you did, and disabled it. After some digging, I found explanations for my particular problem, but no suggestion on an actual *fix* for it.

Anyhow, I suppose that's something like what happened to you. Problems related to the use of splash screens during boot are not uncommon, and (especially if you're like me and prefer to read the startup messages anyway), the most painless solution is to switch it off.

Do be aware though that subsequent kernel updates may re-enable your splash screen, and make things go all weird again. You should read over the commented chunks of Grub's menu.lst to make sure the "splash" kernel parameter won't be automatically used for future additions to your bootloader menu.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by siteguru on 2007-05-22
Thanks for the advice. Will do.

I'm sure the splash image will be available somewhere - maybe it just needs to be found and loaded to the correct location?

---

### Post by kidders on 2007-05-22
> **siteguru said:**
> I'm sure the splash image will be available somewhere - maybe it just needs to be found and loaded to the correct location?For me at least, I suspect that even if I created a suitable splash image, usplash couldn't use it. :-(

---

