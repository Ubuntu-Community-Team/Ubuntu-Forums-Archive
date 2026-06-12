---
title: "Socket AM2"
date: 2006-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by noob999 on 2006-10-03
I've been looking around and I haven't found anything on AM2 systems.  Would ubuntu work on my AM2 system?  Here are the specs:

CPU: AMD Athlon64 3800+ X2

Mobo: Biostat TForce 550 Socket AM2

RAM: Patriot Signature 1 Gb (2x 512) DDR2 667

PSU: Antec SmartPower 500 Watt

HDD: Western Digital Caviar 250 GB SATA 3.0 Gb/s

GPU: eVGA 7600GT KO

---

### Post by noob999 on 2006-10-03
Also I've had many failed attempts with installing the newest ubuntu.  It does not load after it unpacks the kernel.  I ahve the AMD x64 cd and it does not work. Help?

---

### Post by noob999 on 2006-10-03
help?

---

### Post by acheun on 2006-10-16
You mean tried Edgy?  Have you tried to acpi=off option to do the installation?

---

### Post by alphomega on 2006-10-17
I was under the impression that socket am2 was identical to socket 939, apart from the extra pin and the use of ddr2 memory.  So i thought the only difference was the memory controller on the chip, which is pure hardware controlled and thats it.

Is any one else coming accross issues with am2 as i was planning to upgrade v soon?

---

### Post by floydwaferfield on 2006-10-17
I have an AMD Athlon 64 X2 4600+ (AM2) and everything's running smoothly.

---

### Post by infinit1 on 2006-10-17
Yeah, I have had not problems running it.  Just watch out with 64bit Ubuntu.  It doesn't work with all the software I would like.  But that is not a hardware issue.  Good luck. :wink:

---

### Post by kuja on 2006-10-17
> **alphomega said:**
> I was under the impression that socket am2 was identical to socket 939, apart from the extra pin and the use of ddr2 memory.  So i thought the only difference was the memory controller on the chip, which is pure hardware controlled and thats it.

Is any one else coming accross issues with am2 as i was planning to upgrade v soon?
I'm under the impression that much of it had to be changed, because the memory controller was very deeply integrated into the processor, and couldn't  just be switched out conveniently.

---

### Post by RAOF on 2006-10-18
Ubuntu won't care whether your motherboard has an AM2 socket, a 939 socket, or a 940 socket.  It's like what brand of RAM you stick into the slots.  That sort of hardware detail is below the level at which code operates.

What's likely to be the case is that motherboards with an AM2 socket tend to be **newer**, have newer components, less well tested bios', etc.  Newer stuff tends to work worse in linux, because the kernel hackers haven't had time to work around the quirks such new stuff almost inevitably has.

---

