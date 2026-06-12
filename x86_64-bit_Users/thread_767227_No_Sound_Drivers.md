---
title: "No Sound Drivers?"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by Megatog615 on 2008-04-25
I have an Ensoniq AudioPCI 1371.

I installed Xubuntu 8.04 64-bit today(and installed the rt kernel) and just now noticed my sound wasn't working. So I did aplay -l and saw that it detected no sound cards.

Then I did sudo modprobe snd-ens1371 and to my surprise there is no driver by that name. Then I did sudo modprobe snd-<TAB><TAB> and got no results. Where are the sound drivers for the RT kernel?

---

### Post by Megatog615 on 2008-04-29
*BUMP*

Can anyone who runs the RT kernel tell me their sound is working?

Why are there no sound drivers for the RT kernel?

---

### Post by ironstorm on 2008-04-30
install the **linux-ubuntu-modules** package

---

### Post by Megatog615 on 2008-05-01
Now why don't I need that for the generic kernel?

---

