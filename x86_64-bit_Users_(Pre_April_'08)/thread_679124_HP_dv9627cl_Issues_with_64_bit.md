---
title: "HP dv9627cl Issues with 64 bit"
date: 2008-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by kabronkline on 2008-01-26
I seem to be having some difficulties using 64 bit Kubuntu on my system. I have had these same issues using Ubuntu 64 and I thought I would post here because they seem to be desktop manager agnostic, so to speak.

First, I have been experiencing random hard-locks daily. During the hard lock my caps-lock light blinks continuously until I hard reset the machine. I doubt this is a hardware issue since I have never had any hard locks running Vista. Eventually I found a way to overcome these hard-locks by passing the following arguments to the kernel via /boot/grub/menu.list:
```
noapic nolapic pci=noacpi acpi=off 
```This has effectively killed my hard-locks for the past week; however, since this is a laptop, not having power management is a bit of a headache. I don't know when my battery is charged or when it is about to die. Does anybody have any suggestions for me regarding this problem? 
Second, I have also been experiencing screen crashes. I am using the nvidia-glx-new package from the repo's and, yes, I have configured my xorg.conf file to use the driver as well. This notebook uses an Nvidia Geforce 7150 m. I am not using any composite engine, just plain KDE. Bare in mind the screen crash is rare but still nerve racking.

So these are my issues and hopefully I can get them worked out. When I do, I am going to post a complete tutorial for installing Ubuntu/Kubuntu 64 for this model laptop using the workaround fixes that the community can come up with. Thank again!

[B]UPDATE
[/B]First issue: resolved hardlocks via installing ndiswrapper from source. Since doing so I have been hardlock free for a week.
Second issue: still trying to figure out the random screen crashes.

---

### Post by kabronkline on 2008-01-31
Apparently ndiswrapper was causing hardlocks. I managed to overcome the problem by compiling ndiswrapper from source.

I am still, however, experiencing screen crashing with the nvidia-glx-new driver. During the crash, the screen goes completely gray while my mouse pointer is still movable (even though it doesn't look like a pointer). Alt-Ctrl-Backspace does nothing, and neither does trying to switch to another terminal via Alt-Ctrl-F1 (or any other F key). When attempting to switch to another console, the screen just displays black.

---

