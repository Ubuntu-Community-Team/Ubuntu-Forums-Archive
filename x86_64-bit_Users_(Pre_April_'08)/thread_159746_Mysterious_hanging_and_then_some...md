---
title: "Mysterious hanging and then some.."
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by VoiceOvGod on 2006-04-13
I have Breezy 5.10 for my amd64 3400+ installed, and every time that I lock the workstation, it freezes (Unsure how long it takes before it actually does freeze). When I do a hard shutdown and reboot (in an attempt to recover the logs) I get an error stating that the keyboard is not detected. After I manually remove and replace the keyboard, it will load quickly, but, once GNOME starts, it runs rather slowly. It takes a few minutes to load a browser window, and it took several more minutes to load the log viewer.

I have only installed the base system for workstations, all updates, the nvidia driver that came in the package manager, and firestarter. Firestarter was installed after the first time it hung up.

I have not been able to check the logs yet, so I don't know what the cause is. 

As a relatively new user of Linux, I have no idea where to actually start looking to properly troubleshoot and then resolve this issue. Any assistance would be greatly appreciated.

X-posted from beginers area

*Edit* : Trying first with different keyboard. Current one is an old one (having to use adapter to convert to PS2)

---

### Post by VoiceOvGod on 2006-04-15
Update: Swapped keyboard. Still produced same results.

Checked logs, unsure of what I should be looking for in logs, did not see anything that seemed to raise a mental flag.

---

### Post by VoiceOvGod on 2006-04-15
Is it possible that this could be related to the Nvidia drivers? I only used the ones from the package manager. I have not used the drivers provided by nvidia.

---

### Post by skylark on 2006-04-15
[QUOTE=VoiceOvGod]It takes a few minutes to load a browser window, and it took several more minutes to load the log viewer.[/QUOTE]I think you have already worked out something is very wrong. I've got a 3200+ and it takes only a few seconds to launch a browser.

System freezes are _usually_ an indication of a hardware problem, although if they only occur when you Lock the screen (I assume this is what you are doing) it might possibly be something else. What motherboard are you using? Have you run your system through a memory diagnostic eg Memtest86+ ? Your symptoms are very odd, I'm only stabbing in the dark here...

---

### Post by VoiceOvGod on 2006-04-15
I use an Nvidia Chaintech VNf4 Ultra, my video card is an Nvidia ASUS n6600 GT. 1 gb ram.

Sometimes the slow load times do not occur, sometimes they come up at a much more acceptable rate. When attempting to bring up an FTP client, it comes up quickly. But firefox is sometimes slow.

Previous installs of 5.10 have not had this before. I am thinking that it is somehow related to the generic nvidia drivers I am using.....

---

### Post by VoiceOvGod on 2006-04-18
Got it fixed.

edited the /etc/X11/xorg.conf.

Replaced the nvidia driver with vesa.

---

