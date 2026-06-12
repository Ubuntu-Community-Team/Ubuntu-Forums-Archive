---
title: "Odd freezing/display problems"
date: 2006-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Clock Sabre on 2006-05-05
I've just recently installed ubuntu, and I'm having a few strange problems occasionally. At random times, when opening up a program (it seems to happen with firefox the most), my computer's display will quite literally 'shoot' geometric lines across the computer's screen. They don't do anything, but they are thin lines that cover the current window. Usually they go away if I minimize the program that started them in the first place. It's just something odd, not harmful, that keeps happening to me.

Another thing that seems to happen is the computer itself will just decide to freeze completely when I choose to open a program. It doesn't always do this, just at random times it seems. 

Any ideas?

---

### Post by Clock Sabre on 2006-05-06
I noticed, upon shutting down Ubuntu, that when it says "Turning off GNOME display manager..", it said right below it, "GNOME display manager not running".

Could that perhaps be the problem for the glitchy display?

---

### Post by jgsfcaus on 2006-05-16
I've had the same problem, primarily on my Athlon64 machine with either the intel or AMD64 versions of Ubuntu installed. I also got the same problem on this machine when I had Fedora 4 core installed. Methinks it might be a problem with on-board video, pehaps attributable to on-board graphic "adapters" that use "shared" memory (i.e. they use main RAM instead of their own VRAM).

Can anyone else concur?

Jack

---

### Post by burzum on 2006-05-16
[QUOTE=Clock Sabre]I've just recently installed ubuntu, and I'm having a few strange problems occasionally. At random times, when opening up a program (it seems to happen with firefox the most), my computer's display will quite literally 'shoot' geometric lines across the computer's screen. They don't do anything, but they are thin lines that cover the current window. Usually they go away if I minimize the program that started them in the first place. It's just something odd, not harmful, that keeps happening to me.

Another thing that seems to happen is the computer itself will just decide to freeze completely when I choose to open a program. It doesn't always do this, just at random times it seems. 
[/QUOTE]

I have nearly the same problem except that i dont see any weird lines. It seems that it mostly crashes while using firefox. But it happens also when firefox is closed.

---

### Post by FluffyElmo on 2006-05-17
There was a problem with Nforce chipsets and PCI Express graphics cards which resulted in problems like this. Try installing the latest proprietary Nvidia drivers and the problem should be solved. 

Search this forum for instructions on updating your Nvidia video driver...TSEliot has a good how-to out there somewhere. I'm assuming you're all running Nvidia chipsets since the description is so similar, but if not perhaps it's something else.

Keep us updated with any progress/setbacks and Good Luck!

---

