---
title: "recovery mode?"
date: 2006-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by maxdevis on 2006-03-12
how do i acces the recovery mode?
with the x86 and grub you press esc, but what with yaboot?

---

### Post by kittycatsexycat on 2006-03-12
does it not work when you press esc when it prompts...

you should get a screen that has your kernal andd another the same below but with recovery mode next to it...

---

### Post by suoko on 2006-07-19
dont' see any recovery mode!!

 is there any way to manually say to yaboot to boot in recovery mode?

---

### Post by linear on 2006-07-19
I don't think there is one, directly.

It's possible to use the Dapper alternate install CD to boot and then get into a recovery mode.

---

### Post by jerm.quinn on 2006-08-06
> **linear said:**
> I don't think there is one, directly.

It's possible to use the Dapper alternate install CD to boot and then get into a recovery mode.

How?
I have a G4 Cube (with a non-standard Geforce 2 card). I had managed to install 6.0.2 Desktop and get it set up.
It would occasionally whitescreen on shutdown or kernel startup, but now it does it all the time. 

The whitescreen comes up right after the 'ramdisk' message. The HD or CD keep seeking for anothere minute or so, then nothing, server processes have not started up.

What is really strange is that now it does the same from all 3 CDs Desktop, Server and Alternate! I used the same Desktop disk when I originally installed, with no problems :-? 

How do you get from the yaboot prompt to wherever you can try the 'dpkg-' tip mentioned earlier?

---

### Post by linear on 2006-08-06
If you can get as far as the alternate install CD menu, there is a "Rescue a broken system" choice. If you can't... :(

---

### Post by jerm.quinn on 2006-08-07
> **linear said:**
> If you can get as far as the alternate install CD menu, there is a "Rescue a broken system" choice. If you can't... :(

If this is **after** using yaboot to select the kernel to run, then no I cannot reach the rescue choice as it always hangs starting the kernel (no matter what options I choose).

Is that what you meant ?

Or is there some way of selecting rescue mode from the yaboot menu?

---

### Post by linear on 2006-08-07
The menu comes up after the system has successfully booted from CD. No way that I know of to get a rescue/recovery mode from the yaboot menu.

---

### Post by jerm.quinn on 2006-08-08
> **linear said:**
> The menu comes up after the system has successfully booted from CD. No way that I know of to get a rescue/recovery mode from the yaboot menu.

Many thanks for the clarification.

---

