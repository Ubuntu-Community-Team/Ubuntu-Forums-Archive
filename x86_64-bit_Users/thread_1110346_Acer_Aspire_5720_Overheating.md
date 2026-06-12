---
title: "Acer Aspire 5720 Overheating"
date: 2009-03-29
forum: x86 64-bit Users
---

### Post by H4F on 2009-03-29
Hi all.
Recently I found out my laptop is overheating. 
1. Fans are working. at least I hear them. 1 or 2 don't know.
2. Fans start at 1)65  2)70  3) sems that 3'd speed does not work
3.  cat trip_points 
       critical (S5):           110 C
  ridiculous . but can't do nothing.
4. before as I understood there was a problem in DSDT table in Acer now it should be fixed with bios v 1.42. I have it.
5. before I did not have such problem neither in linux or windows. So you can't say its design problem.

 cat cooling_mode 
<setting not supported>

If you need any more information just ask.
P.s  2.6.27-14-generic #1 SMP Fri Mar 13 19:54:51 UTC 2009 x86_64 GNU/Linux

---

### Post by 3Miro on 2009-03-29
It is still possible to be a hardware flaw, i.e. 1/2 broken fan.

Is a rouge process hijacking the CPU and forcing it to work more than needed? What does top say, everything OK?

Dust is another possibility, I know I can get 5 - 10 degrees C, on my Video Card if I have not cleaned it recently (on my Desktop). We all take our laptops to unsavory places.

What happens if you do not boot Ubuntu, but boot and go into BIOS. Can you watch the heat info from there? What about the fan speed issue, does it appear if you just run BIOS? Watch the BIOS for a while (5-10min) to see if excess heat is Ubuntu related or hardware.

You can try the LiveCD, just to run and see if it will overheat. If something about fan control got broken within Linux, it will work fine with the LiveCD.

---

### Post by H4F on 2009-03-29
Thanks for reply.
1/2 halp brocken . bad news really.

Dust ? no its clean. its nearly new.

if I boot in bios its fine. actually ater kernel shut down. I boot to bios  seems that fans are working at full speed.

you want me to check if the temp is measured correctly ? look it in bios?
Yeap i think temp is measure correctly cause when it gets 80-90 it's really hot.

Hm live cd . Did not think about that. I will try.

P.S using cpuburn to make heat.

---

### Post by H4F on 2009-03-31
Is there a way to change critical S5 from 110 to something else like 90.

where can I found the trip_points. so I want to change fans  start from 65-70 to 55-65 or something like that.

are all configuration is located at /proc/acpi/ ? (for acpi)

---

### Post by His on 2009-06-07
I don't know if you're still having this problem, but I am having it. Anyone have any ideas? I've been having it since I first installed Intrepid, I hoped that Jaunty would fix it. It's still not turning on very much.

I have a duel boot, and in Windows it doesn't get over 40 C very often because the fans blow like crazy, but not in Ubuntu.

---

