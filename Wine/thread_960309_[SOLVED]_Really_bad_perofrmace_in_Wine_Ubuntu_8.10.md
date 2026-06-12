---
title: "[SOLVED] Really bad perofrmace in Wine Ubuntu 8.10"
date: 2008-10-27
forum: Wine
---

### Post by Dark9204 on 2008-10-27
Hi. Im using ubuntu 8.10 64 bit.
I have a Nvidia EN8500GT Card. And the performance in 3D apps are really bad. I mean really, really bad. I cant even get around 30 FPS at lowest settings in CS:S. And yes, I am running in dxlevel 81.
I know this isn't a Wine issue because in ubuntu 8.04 i had about 80FPS all the time!
I am running the latest drivers and Wine stable. Tested wine dev 1.1.7, and the performance were even worse, the sound were very garbled.

---

### Post by YokoZar on 2008-10-27
Double check that you're using the closed source rather than the free drivers.  There was a period of time (especially if you upgraded to the beta or RC version) where proprietary drivers weren't available for Intrepid for some nvidia cards, and users were defaulted to the free (and slower) version.

---

### Post by Dark9204 on 2008-10-28
Hi
Thanks for taking your time.

I have just reinstalled Ubuntu 8.10 with the hardware drivers from ubuntu (not the EnvyNG ones that i used before. Even tho i switched to the ubuntu ones, but the probem still remained) and that solved the problem. The FPS is now at the levels it should be.

---

