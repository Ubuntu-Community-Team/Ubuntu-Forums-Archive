---
title: "Xorg Wont Start PPC Ati Rage 128"
date: 2005-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by zappa86 on 2005-12-01
Ive installed ubuntu 5.10 on a G3. X will not start. It gives a fatal signal 7. I'm using the r128 driver in my Xorg.conf. Right before the fatal signal it says:

(EE) r128 (0): Cannot Read V_BIOS (5).
(EE) r128 (0): No DFP Detected
Skipping [....] libfb.a:fbmmx.o No Symbols Found

(I had to type thoes errors in so the text may be a little bit off)

Also, I know the computer has an agp4x rage 128 and a 17in monitor connected to it through mac DVI (which Ive never seen before, the power goes through the regular cord from the computer to the monitor).
Any help would be greatly valued. Thanks.

---

### Post by linear on 2005-12-01
I don't claim to understand it all, but you might try:

- The "ati" driver instead of r128.

- Disabling DRI.

Judging by the forums, many ATI Rage problems have been solved by finding the right settings for xorg.conf.

---

### Post by zappa86 on 2005-12-02
hmm. Nope (but thanks for the idea). I think it has to do more with some driver issue that will take more than an xorg change to fix. It says it cant read the video bios so that makes me think that the drivers are wrong or something. Its frustrating.

---

### Post by ssam on 2005-12-02
have you had a good google for it. you often find that some debian or gentoo user has posted their xorg.conf somewhere. it may help.

---

