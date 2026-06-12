---
title: "random shut down."
date: 2009-08-12
forum: x86 64-bit Users
---

### Post by marlboroman1234 on 2009-08-12
I have an acer extensa 4420. I'm running ubuntu 9.04 64 bit, and at random times, the computer would just shut down. At first I thought it was a problem with firefox because I always had that open when it would shut down, but then it shut down while I was only on songbird. I can't figure out the problem, and I'm new to linux, so any help would be greatly appreciated. I'd hate to have to go back to windows.

---

### Post by dlstyley on 2009-10-10
I have this laptop too.   I'm on 9.04 with no real problems.  

I'm far from an expert, but the first thing I would do is check your logs to see if there is some obvious error or something that will give you some leads.  You can get there via System -> Administration -> Log File Viewer.  Alternatively, from the command line you can run "dmesg | grep <keyword>" where <keyword> is some likely suspects ("error", "fail", "warning", etc.)...

Note that there are some "red herrings" in the log files, but I'd try to find the last error before the machine is restarted.  

Good luck!

---

### Post by chipsugar on 2009-10-11
Strangely I'm on a desktop machine (Athlon64 4000, DFI Lanparty, open source radeondriver for x1800xl, creative audigy) but am also getting occasional random shutdowns. I'm on the mythbuntu karmic betas at the moment but also got them on mythbuntu 9.04.

I'll look in the log files next time I get a reboot but in the meantime any ideas anyone?

---

### Post by ubun_two on 2009-10-11
> **marlboroman1234 said:**
> I have an acer extensa 4420. I'm running ubuntu 9.04 64 bit, and at random times, the computer would just shut down. At first I thought it was a problem with firefox because I always had that open when it would shut down, but then it shut down while I was only on songbird. I can't figure out the problem, and I'm new to linux, so any help would be greatly appreciated. I'd hate to have to go back to windows.
If it is a laptop, it might not be because of Ubuntu at all.

When laptop temperature goes up high enough, many system decides that it's dangerous to stay on and shut itself off without warning to protect itself.

I've had this with one of my laptop anyways.

If this is the case, cleaning inside the laptop does the trick.  Clogged up dust inhibits the air flow, which causes improper cooling.

---

### Post by ShadowTek on 2009-10-12
Run memtest for a while, and see if that causes it to reboot. If so, it's a hardware issue.

---

### Post by PrePenguin on 2009-10-12
Random shutdowns are closely linked with power supply problems.. Otherwords Hardware and it will get worse and worse .. If you eliminate the software possibilities that would be the first place i would look..

---

### Post by mgranet on 2009-10-12
> **PrePenguin said:**
> Random shutdowns are closely linked with power supply problems.. Otherwords Hardware and it will get worse and worse .. If you eliminate the software possibilities that would be the first place i would look..

Seconded.

---

