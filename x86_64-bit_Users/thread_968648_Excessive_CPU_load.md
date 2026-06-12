---
title: "Excessive CPU load"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by jamesbeatty on 2008-11-02
I'm running 8.04 on an Intel e6750 core 2 duo, and the CPU load seems to be way more than what it ought to be. Having a few (4 or 5) tabs open on Firefox and watching a flash video in one of them almost always causes my CPU to overheat and start beeping at me. This also happens with other programs: playing Caesar 3 on WINE causes it (I know WINE has associated overhead, but the recommended CPU for Caesar 3 is a 133 MHz Pentium), DOSbox causes it (unless dialed down), if I work too fast in GIMP that causes it, etc.

Although I probably could stand to have better airflow in my case, I dual-boot with Vista, where I am able to play games like Mass Effect and Half-Life 2 with no ill effect, so I strongly suspect that this problem is more to do with Ubuntu than with my computer.

Is there some setting that I could tweak that would artificially limit the amount of CPU power that Ubuntu has access to (i.e. when Ubuntu thinks it's using 100% of the CPU, it's only using 50%)? Or, better yet, is there maybe some way to get it to be more efficient?

---

### Post by Yellow Pasque on 2008-11-03
The bottom line is that your CPU cooling isn't up to snuff. For comparison, fire up two instances of Prime95 or CpuBurn (or whatever programs OC'ers are using to test CPU stability these days) on Windows and see if you can get your CPU to overheat there. If you can't, then I would suspect that your CPU fan isn't running fast enough in Linux. Are you controlling the fan in the BIOS or with software/PWM?

From what you describe, it also sounds like your Linux video drivers aren't as efficient as the Windows drivers (surprise..) and are forcing more load on the CPU. (Even if that is the case, your CPU shouldn't overheat.) What kind of video card do you have and what driver are you using?

---

### Post by Jouke74 on 2008-11-03
If Vista is running fine under high CPU load and Ubuntu not, I suggest first to check if your CPU fan is running at all under Ubuntu. Just open your case and start first Vista and then Ubuntu up, and check if the fan(s) start running.

---

