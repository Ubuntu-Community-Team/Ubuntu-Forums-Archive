---
title: "cputemp K8?"
date: 2007-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by nalleballe on 2007-08-14
HI! Im a new AMD64 user and im trying to get my CPU temperature visible. Its not possible.... Im getting the hickups when im running dvdauthor cause its on 100% at all time. I have an ASUS K8V MX board and a AMD 64 3100 Sempron. Do any one know any good driver for me? No one in Ubuntu seems to work... :(

---

### Post by John.Michael.Kane on 2007-08-14
You have two options.

See if your temps are picked up via acpi using the program below.
1) ```
sudo aptitude install sensors-applet
```
After it's installed right click on your panel/menu bar, and click add to panel  select hardware sensors monitor

If above does not show your temps. use option two below.

Use the guide below to see if lm-sensors picks up temp monitoring devices.
2)[HOW TO: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780")

Also running dvdauthor or any other encoding programs will cause your single core AMD 64 3100 Sempron to run at 100%,That should be expected, As it is creating a dvd/etc.

Since your doing this kind of work on a low budget system I would suggest you run that or any other encoding type programs at night while sleeping.

---

