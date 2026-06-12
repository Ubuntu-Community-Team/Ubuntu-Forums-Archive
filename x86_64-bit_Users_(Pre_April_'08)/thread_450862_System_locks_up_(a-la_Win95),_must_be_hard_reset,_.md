---
title: "System locks up (a-la Win95), must be hard reset, caps lock light blinks Help Please!"
date: 2007-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by nickj6282 on 2007-05-21
Ok, here's what happens: nothing.

I'm just using the PC, minding my own business, and bam! It locks up. Mouse moves, nothing else works. The caps lock light blinks, but that's about it. I have to hard reboot (hold down power key) to get it back up. Everything I was doing is lost, but luckily I'm a stickler for Ctrl+S so it's no HUGE deal, but it's a big pain in the butt. Can anyone help me and tell me where to look. There's nothing of interest in /var/log/messages or dmesg. What's next?

thanks a lot!
-Nick

7.04 AMD 64
HP Pavilion DV8110us
Turion 64 1.8Ghz
1.25GB DDR
60GB Fujitsu HDD
Broadcom 4318 via Ndiswrapper

---

### Post by tgm4883 on 2007-05-21
Unfortunetley not

[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)

---

### Post by yabbadabbadont on 2007-05-21
If it were the Caps lock, Scroll lock, and Num lock lights all blinking, instead of just the one, then that indicates a kernel oops has occurred.  (kernel panic for us Unix types :))  Read the "Emergency Reboot" section of the following for details on how to minimize damage to files and filesystems:
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

As for the cause of the problem, what you describe is usually a hardware issue.  The next time you boot, take the memtest option to check your memory.  Other than that, use a CPU temp monitor (lm_sensors, conky, gkrellm, ...) to make sure that your CPU isn't over heating for some reason.

---

### Post by nickj6282 on 2007-05-21
Well, my PC doesn't have a scroll lock light since it's a laptop. The numlock key just turns off (if it's on) and the caps lock key blinks. Does this indicate a different problem maybe?

---

### Post by jpeddicord on 2007-05-21
In addition to yabbadabbadont's technique, if the mouse still works you can try pressing Ctrl+Alt+Backspace to reset the display. It will log you out and not save any work, but it is quicker than hard resetting if you can use it.

The capslock key blinking might also be a sign from your laptop's BIOS for errors, such as a core temperature overheat.

---

### Post by nickj6282 on 2007-05-21
Yeah. Ctrl+Alt+Backpace and Ctrl+Alt+F1-F6 don't work either. Nothing short of a hard reset does the job.

---

### Post by tgalati4 on 2007-05-21
Try reseating the memory.  Remove it, take an eraser to the contacts, gently wipe it clean and reinstall.  Ground yourself properly while doing this.  Could be a battery contact or power supply issue.  Laptops tend to have weak power conditioning circuits and sometimes the power-on relays wear out.  Not much to fix unless you like to tinker.

Boot from a Live CD and run from that for a few days to convince yourself of a hardware problem.  Or boot into Windows and see if it locks up.  Ignore that last suggestion.

CPU thermal halts are a possibility.  Install a thermal sensor on your Gnome panel and set an alarm when it gets hot.

Also, tighten chassis screws since a grounding problem can also cause power problems.  With a laptop, anything is possible, including loose ribbon cables.

---

### Post by gavilanes on 2007-05-30
Well, Hello everyone!
I have just the same problem; I have a laptop, Acer aspire 5000 AMD Turion 64 in which I have been running windows XP Home. I build up partitions to install linux and both distros I have used I have had a very similar problem:
- System hangs with no response to Mouse movements or clicks
- keyboard also doesn't respond
- only turning off/on the computer turns it usable again
- no output present on /var/log/messages files by the time of freeze.
As I said  before, I have run also another distribution before (openSuse) having this problem, and then having tried boot options such as disabling ACPI or apic options, disconnecting usb devices and storages without success, i resolve to install ubuntu, looking for a comparison point.
I arrived to the same problem WITH THE DIFFERENCE THAT:
- CAPSLOCK flashes when computer freezes take place.

I am about to think this could be a hardware issue, but not really convinced on what could it be the reason.
I will try also memory tests just in case and will report.
Thank you!

---

### Post by gavilanes on 2007-05-31
I did a memory test this morning, but nothing special.

Any other ideas?

---

### Post by tgalati4 on 2007-05-31
Try declocking your system in the BIOS.  Set the multiplier to half of its normal setting or take it off auto detect and set a discrete low multiplier (1X, 2X, 4X).  Try cutting the bus speed in half if possible.  

If you can run your system at a lower speed for longer period of time, then that might point to a heat/hardware issue.

---

