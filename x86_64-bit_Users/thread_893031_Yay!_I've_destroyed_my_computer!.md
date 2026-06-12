---
title: "Yay! I've destroyed my computer!"
date: 2008-08-17
forum: x86 64-bit Users
---

### Post by bobthecheese on 2008-08-17
Ok, so I'll do a quick cap:

I got two new 24" LCDs to replace my 17" CTR.

My ubuntu installation didn't want to autodetect them, so I (stupidly) attempted to force the issue by reinstalling the nvidia drivers.

when I rebooted from uninstalling the nvidia drivers, my screens just... didn't display anything useful (One showed 'Out of range', and the other showed varyingly either one colour blanket across the entire screen, or diagonal junk across the screen. Neither would show any signs of response to interaction.

After regenning xorg.conf a few times I decided to try running a live disc.

One disc (for an older version of ubuntu) refused to let me into ubuntu, and instead loaded the kernal, and rebooted the system rather than starting up. This was the disc that I originally used to install ubuntu from.

The other disc loaded into live, but had similar junk on the screens.

I tried to reinstall using the second disc, then relaised that the only way I would be able to see what I was doing was to do it through the text-based install interface.

This was fine until it got to installing the base system (after it had been through the partitioner) when it failed because pretty much every package it tried to open it claimed was corrupted. This disc had been used to install for two other friends previously, and the disc check came through clean.

Once it had tried to install once, grub had been destroyed, and every time I boot comes up with "Error 15" and stops. I can't get into my linux partition or my windows partition.

I'm trying to install the 64 bit version of hardy.

The monitors are plugged into a 6600GT.

I had managed to get both monitors working correctly in windows before I destroyed grub.

So my questions:

1 - Why would a live CD be unable to handle simple display of both (or even one) monitor(s)?
2 - Can I repair/remove grub?
3 - In the off chance that I get this working again, how do I get it to actually properly detect both my monitors?

---

### Post by Loaded.len on 2008-08-17
repair issues aside, how are the displays connected? Dual head video card, break out cable (Y), seperate video cards (one not being on-board), seperate (one being on-board)?

EDIT: ahh, just saw the 6600GT.

---

### Post by bobthecheese on 2008-08-17
yeah, both connected to a 6600GT.

No hardware in the system changed, other than the monitors.

---

### Post by cariboo on 2008-08-18
It is probably because your monitors are not being detected properly. I would suggest disconnecting one monitor until you get things reinstalled. You will propbably have to boot up in safe graphics mode to install you operating system. To do this hit F4 at the menu screen and select safe graphics mode, then hit enter, and you should be on your way.

Jim

---

### Post by Thelasko on 2008-08-18
> 2 - Can I repair/remove grub?
[You can repair it.]("http://www.supergrubdisk.org/")

---

### Post by bobthecheese on 2008-08-18
Cheers. I had thorught it might be something to do with the3m both being plugged in, but then discounted that because they both displayed.

If only I'd figured/found this out before I formatted the drive...

Yes, I'm an idiot.

Thanks, though. I've now got both my monitors up and running properly.

---

### Post by Thelasko on 2008-08-19
Please mark the thread as solved.  Glad we could help.

---

