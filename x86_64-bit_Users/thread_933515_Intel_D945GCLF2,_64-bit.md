---
title: "Intel D945GCLF2, 64-bit?"
date: 2008-09-29
forum: x86 64-bit Users
---

### Post by felldin on 2008-09-29
I'm going to install ubuntu on an Intel D945GCLF2. I can't find any information if I should go for the 64- or the 32-bit version of ubuntu. Is the atom 330 even compatible with the 64-bit version and will there be any other problems?

---

### Post by bawilson2 on 2008-09-29
> **felldin said:**
> I'm going to install ubuntu on an Intel D945GCLF2. I can't find any information if I should go for the 64- or the 32-bit version of ubuntu. Is the atom 330 even compatible with the 64-bit version and will there be any other problems?

Not sure if you'd come across other problems but the atom 330 does support 64 bit.  Issue I see is that the motherboard only supports 2GB of ram.  If that's the case I don't know if there's a whole lot of need to go to the 64 bit OS.  I'm currently running Hardy AMD64 but it can take a whole lot more work to get some things running compared to the 32 bit version.

---

### Post by felldin on 2008-09-29
The board only supports 2GB RAM. Will I se any difference in performance if I use the 64-bit version instead of the 32-bit version?

---

### Post by prshah on 2008-09-29
> **felldin said:**
> I'm going to install ubuntu on an Intel D945GCLF2. I can't find any information if I should go for the 64- or the 32-bit version of ubuntu. Is the atom 330 even compatible with the 64-bit version and will there be any other problems?

Yes, the atom 330 is a 64-bit capable processor.

However, there were some [early problems with the Gigabit Ethernet on the D945GCLF, which did not allow ubuntu 8.04 to boot]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239602"); they have since been resolved with 8.04.1 onwards; so remember to use 8.04.1 and above.

The current [(Alpha6) of Intrepid also have a problem with (some) Intel Gigabit interfaces]("http://www.ubuntu.com/testing/intrepid/alpha6"); do not try the Alpha 6 of Intrepid on this system until you are sure it will not affect anything permanently.

---

### Post by Artemis3 on 2008-09-29
Oh, the one that corrupts the firmware? Happens to intel e1000e, avoid Intrepid Ibex Alpha 6 like the plague :)

As for using 64 bit, i simply always boot with the 64bit version, if the cpu isn't capable, it will tell you very quickly :)

---

### Post by prshah on 2008-09-30
> **Artemis3 said:**
> Oh, the one that corrupts the firmware? Happens to intel e1000e, avoid Intrepid Ibex Alpha 6 like the plague :)

That's a little strong. There is no need to _avoid_ the Alpha 6. Just apply a little foresight and investigation, the check, resolution and recovery are well documented. I'm running Alpha 6 on an Intel D965 board, without any problems.

If people jumped away from Alphas at little (well-documented) trouble, then how does the Alpha get tested?

---

### Post by cariboo on 2008-09-30
The beta version of Intrepid should be out sometime thursday. The problem does not only affect Ubuntu, but Fedora and Opensuse also have problems with e1000e

Jim

---

### Post by udegel on 2009-09-08
Hello,

I'm trying since days now to get Ubuntu run on this board.
Did you manage to setup Ubuntu stable? If yes, which version and which TRICKS???

Thanks!

Rgedards
Uwe

---

