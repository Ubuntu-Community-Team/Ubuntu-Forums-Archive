---
title: "How do I Play DVDs (w/MPlayer, Totem)?"
date: 2006-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-09-09
Hi,

Totem is the default dvd app. When I insert a dvd totem gives the message:

Totem could not play 'dvd:///dev/hdd'
No URI handler implemented for "dvd".

I've given up on Totem and tried MPlayer. MPlayer reads the DVD fine initially. But I have the following problems which I hope you can help me with:

1) MPlayer displays the following msg. and after a while I lose audio:

Too many video packets in the buffer: (4096 in 8243930 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

(This also happens when watching TV from my PVR-150 card)

2) When trying to navigate the DVD menu with the mouse button, I get the following error in MPlayer:

No bind found for key 'MOUSE_BTN0'

If you could help me resolve these issues, I'd appreciate it.

Thanks.

---

### Post by hajk on 2006-09-09
The easiest way to get what you want is to follow the recipe in the RestrictedFormats page of the Ubuntu wiki. I recommend that you start at the top and work your way to the bottom without skipping a step, and take particular heed of the remarks for AMD64.

Note: it is possible to do it differently, and with fewer steps, but that will almost inevitably cause hiccups on the way and the need to ask for more advice on the forums...

Signed: been there, done that!

---

### Post by bper on 2006-09-09
Thanks,following those steps resolved most of the issues, but I'm still having some difficulty with MPlayer and viewing TV signal with my TV card.

I'll post the messages to this thread.

---

### Post by hajk on 2006-09-10
> **bper said:**
> Thanks,following those steps resolved most of the issues, but I'm still having some difficulty with MPlayer and viewing TV signal with my TV card.

I'll post the messages to this thread.

There are some comments on MPlayer in the "sticky" at the top of this subforum. As to using a TV card with AMD64 specifics, I guess you're on your own...

---

