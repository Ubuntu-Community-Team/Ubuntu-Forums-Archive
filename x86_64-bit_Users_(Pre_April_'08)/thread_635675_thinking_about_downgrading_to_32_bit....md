---
title: "thinking about downgrading to 32 bit..."
date: 2007-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by mma8x on 2007-12-09
actually, everything is working find running 64 bit gutsy...except for the lack of a tickless kernel.  i tried installing a patched kernel from  another distro (gentoo?), which worked ok, except that i've been unable to get my ipw3945 wireless up and running.  i did notice a significant improvement in power consumption with the tickless kernel.  sooo....
do i have to do a fresh install from a 32 bit disk, or is there an easier way to downgrade?

---

### Post by dewey on 2007-12-09
If you choose to downgrade, you must reinstall Ubuntu using the 32 bit disc.

If your /home was on a seperate partition, you will be able to keep it.

---

### Post by tighem on 2007-12-09
Even if /home is on the same partition you can copy over to another disk, reinstall, and copy back. Worked great for me when I went from 32 to 64 (and worked pretty well when I put hardy on a separate disk and copied the /home directory over there).

Tickless is going to be available in the 2.6.24 kernel for 64-bit.  And Virtualbox absolutely craters under it, so if you can wait or are using VB there is no reason to move.

---

### Post by mma8x on 2007-12-09
yeah, i was using a hacked 2.6.24 kernel (it was actually fedora) to give me tickless.  like i said, very nice except for the wireless support.  iwl3945 support was compiled as a module in the kernel, but i wasn't able to pull up the interface.  sadly, i don't have a separate /home partition (i can never get the sizes right, and always run out of room on an unexpected partition).  

maybe i'll go 32 bit until 2.6.24 comes out--i feel like i'll have the same wireless issues until ubuntu supports the new kernel, which may not be for another 6+ months...

---

### Post by mma8x on 2007-12-09
hmm, on second thought...
doing some more testing, it doesn't look like the tickless kernel is giving me any power savings; minimal if so.  idling at minimum brightness, i was getting 13.8 W with both, though wakeups from idle were significantly different (~450 v. 120).  if there's a difference, i guess it probably isn't worth the hassle.  i'll wait for 2.6.24 from ubuntu; i can always get the new kernel from the hardy repos when it comes out.

---

