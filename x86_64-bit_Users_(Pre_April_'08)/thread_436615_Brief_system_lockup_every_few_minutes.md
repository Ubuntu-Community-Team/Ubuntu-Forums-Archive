---
title: "Brief system lockup every few minutes"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cappy on 2007-05-08
My computer has a weird glitch happen every few minutes but only while I am using it. I will be using something in GNOME - Firefox, Opera, Nautilus, etc. and the windows will stop responding to my keyboard and mouse. I can Alt+Tab and the Alt+Tab window will briefly flash without showing anything and the system will be back to normal. Every couple of days the same thing happens except the mouse is stuck in as a unique icon like the "window dragging hand" or the arrow icon you get when you drag a file. At that point, the screen is still updating but I can't interact with it at all. I have to kill X or restart.

I've tried adding things on my kernel:
```
noapic nolapic acpi=off apm=power_off pci=assign-busses
```
but none of them helped.
ACPI is off on my BIOS or my computer won't boot.
Both of my CPUs show up normally in the System Monitor. 
I checked all of my system's logs and nothing shows up.
I have Option          "RenderAccel"           "False" for my nvidia 7900 in xorg.conf.
I'm out of ideas.

Has anyone encountered anything like this on an AMD X2 system?

---

### Post by tgalati4 on 2007-05-08
Did you examine all of the log files in /var/log?

If it is a hardware problem (a wonky motherboard bus) some errors should show up in dmesg or syslog or Xorg.0.log.

It could also be a failing mouse or keyboard or keyboard controller.  Sometimes reseating memory and ribbon and power cables help.

Don't forget to clean dust out of the machine.  You could be getting thermal halts.

---

### Post by Jouke74 on 2007-05-08
Check your Dmesg log if there are any USB problems (EHCI).

---

### Post by Cappy on 2007-05-09
There weren't any messages when I had this problem. I was going line by line through dmesg and I found a message when my computer first boots up:
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override

I used this acpi_use_timer_override and I havn't had a "lockup" in 24 hours. Sweet!
Thanks guys =)

---

### Post by Cappy on 2007-05-16
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301)

This bug has been around for over a year .. geesh.

---

