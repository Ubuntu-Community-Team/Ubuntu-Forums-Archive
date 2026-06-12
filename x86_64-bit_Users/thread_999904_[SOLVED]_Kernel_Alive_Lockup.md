---
title: "[SOLVED] Kernel Alive Lockup"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by lborkey on 2008-12-02
Just solved a nagging problem with the Kernel Alive lockup.  I have been building a server running an Intel MB and Intel quad-core running x86_64 Intrepid.  4GB of RAM works fine.  But as soon as I put in 8GB, the server would stop at the Kernel Alive message.  Tried the NOAPIC, NOLAPIC, NOSMP boot switches, nothing worked.  Swapped memory, processors, nothing.

The weird thing is that I had another identical server (identical in hardware down to the BIOS firmware revision) that works fine w/ 8GB.

Turns out, it's the DVMT (Dynamic Video Memory Technology) that Intel uses.  You need to turn it off when you're running more than 4GB.  I set it to FIXED and the server popped right up.

---

