---
title: "Temperature how to fix sensors"
date: 2008-07-28
forum: x86 64-bit Users
---

### Post by gretarsson on 2008-07-28
Hi 
My computer is running 52°c and can go up but when it goes to 55°c it shut down I have disable the warning system in bios but it is some thing ales controlling this maybe some softwear in ubuntu if so where can I make temperature level be higher?

---

### Post by cariboo on 2008-07-29
You should be able to set the threshold higher in your bios, turning it off completely is dangerous, did you save the changes when you exited the bios?

Jim

---

### Post by Yellow Pasque on 2008-07-29
I see a few possibilities: as cariboo said, you may not have saved the changes in the BIOS. It's also possible that the BIOS has a bug and doesn't write to the ACPI table.
Does the following command output anything?:
```
cat /proc/acpi/thermal_zone/THRM/trip_points
```

While 55C isn't critical, it's hotter than most desktop CPU's get (unless you have a power-hungry processor like a Pentium 4/D). What kind of hardware do you have? Make sure the heatsink is free of dust/hair and the fan is working properly.

---

### Post by Jouke74 on 2008-07-29
Depending on which temperature sensor you are looking at, the 55 degrees is likely the max for your processor (my AMD also starts to complain at this value). To avoid damage it will shut down. I strongly suggest you NOT to mess with the temp values of your BIOS. Instead make sure your airflow and cooling of the computer system are ok (fans are working, no things blocking the airflow inlets & outlets)! 52 degrees, unless you are running 100% CPU all the time, or currently having an outside temperature of about 42 degrees is too much.

---

### Post by knightcoder on 2008-07-29
Laptops get to overheat a lot more. Mine goes upto 65-70.

I'm planning to get one of those laptop coolers. Think its worth it ? Which one(s) is(are) good ??

---

