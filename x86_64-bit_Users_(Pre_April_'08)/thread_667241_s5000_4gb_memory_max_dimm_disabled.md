---
title: "s5000 4gb memory max dimm disabled"
date: 2008-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by jpwoodbridge on 2008-01-14
Hi all,

i have an issue which ive failed to come across anywhere on the web, so, with fingers crossed i turn to the trusty ubuntu forum, it is after all a ubuntu server box, so here goes:

s5000pal server board, 4 x 2gb ddr2667 ram sticks, only 2 will work. whichever order / configuration i put them in, only 2 will work, the others show in the bios as disabled, as opposed to enabled, or 'na' (or similar, cant remember right now) for those not plugged in.

all mirroring and sparing has been disabled, and there are no other obvious options or things we've overlooked. if only there was an option 'mess with me' and it was turned on....

the sticks of ram themselves are ok as they can be swapped around, and even though they are meant to be placed in order, a1,b1,c1,d1,a2,b2,c2,d2, ive tried all combos possible. the sticks are also all the same make and model and are obviously compatible with the board as the two on their own will work. and the board supports up to 32gb so im not pushing any boundries there.

this has had me stuck for a couple of months now and the time has come where it needs to get sorted, so any advice is much appreciated.

thanks in advance
jp

---

### Post by dcstar on 2008-01-15
> **jpwoodbridge said:**
> Hi all,

i have an issue which ive failed to come across anywhere on the web, so, with fingers crossed i turn to the trusty ubuntu forum, it is after all a ubuntu server box, so here goes:

s5000pal server board, 4 x 2gb ddr2667 ram sticks, only 2 will work. whichever order / configuration i put them in, only 2 will work, the others show in the bios as disabled, as opposed to enabled, or 'na' (or similar, cant remember right now) for those not plugged in.
...........

It seems an obvious issue with the motherboard/BIOS and the memory you are using, so you will probably have more luck contacting the board manufacturer.

Ubuntu will only use the hardware resources the environment makes available to it, and all the RAM issues I've seen reported here seem to relate to the BIOS mapping a small part of it so I don't really know what you are expecting to gain from this forum with your problem.

---

### Post by jpwoodbridge on 2008-01-16
thanks David, i was trying this forum as ive had no luck anywhere else so thought id give it a shot.

which includes absolutely no help what so ever from intel or kingston. yay! and all parts are compaitble, even listed in the approved and tested memory sheet. 

oh well, thanks anyway

---

