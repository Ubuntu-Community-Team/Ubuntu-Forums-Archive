---
title: "hp pavilion dv9000 problem"
date: 2008-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by famous3warriors on 2008-03-25
I hope someone has achieved success in this adventure but I am trying to load a 64 bit Ubuntu on my hp notebook but for some reason it doesn't like it.  When the program is loading up it freezes, it does not continue on to the log in screen.  Please help!!  Thanks for your suggestions.

---

### Post by firecat53 on 2008-03-25
From the boot menu (I assume you're using the live CD) hit the key for more options (F6, I think....not sure :_ ) then type    noapic irqfixup     and try and boot now.

Good luck!
Scott

---

### Post by Tubes6al4v on 2008-03-25
I had a bunch of problems getting Ubuntu (or any Linux for that matter) loaded onto my DV9000 CTO (64 bit Vista Ultimate). I tried the Live, Alternate; Gutsy, Fiesty, Fedora, Suse, Pendrive, and Knoppix; And Wubi, USB, and Qemu. Here is how it played out:

Ubuntu 7.10: Has a hard time with Hardware support on the DV series, espescially the 9000

Ubuntu 7.04: Kept getting an I/O Buffer Error, even in Alternate CD

Fedora: Buffer error

Suse: Couldn't even get to the Grub

Knoppix Live CD: Works great. A little slow, but it is running the live CD. If you just want to try Linux, use this, then decide if you want to do it.

Knoppix Qemu (hardware emulation for running Linux in Windows): Works, but at a good performance loss.

Pendrive Qemu: Also works, but works best if it is booted into the USB, rather than using Qemu

Ubuntu 7.04 USB to Harddrive install: Worked at getting it booted, but the installer kept looking for the CD, and I could not find information on how to mount the USB as a the CD drive



After all of that BS, a couple of re-installations of Vista, and 10 DVD's Later, I decided I would try the BETA version of Hardy Heron (Ubuntu 8.04). The great thing about this one is that it comes pre loaded with Wubi for the specific distribution you download (for me that was 64 bit). Wubi installed fine. I rebooted and it brought me to the Vista Boot menu, just select Ubuntu.

At the loading screen I had to hit ESC and choose the Install with APCI (I think that is it; the third one down) support. It finally did it. 


Ok, so what I am trying to say is: Use 8.04, even the BETA works. It has great hardware support (audio kept looping till I upgraded the video drivers to 3D), and is super user friendly. The stable version comes out in a bit, and should fix some of the bugs (like my upper bar disappearing when too many processes are being run at the same time).


I hope this all helps, I have no idea why I did not just make this short and sweet...

---

### Post by famous3warriors on 2008-03-25
Ok Thanks guys I really do appreciate your help and will give it a try with the new beta version of ubuntu.

---

### Post by Deckoh on 2008-03-25
im running 64bit on a pavilion dv9308nr with out any problems. sounds like the +noapic +irqfixup cmd line that is the problem. worked for me. but im am in no means any type of guru

---

### Post by famous3warriors on 2008-03-25
me neither I tried everything and I just went back to installing my i386 for right know.  I have a desktop that is working great with the 64 bit but just my note book that is giving me a fit.  Oh well.

---

### Post by TimelessRogue on 2008-03-26
Had no problems with a fresh install of Hardy 64 from an Alternate .iso on my HP dv9623ed other than the Broadcom wireless problem which I subsequently solved using wicd.  Runs great and runs fast ...

But I also had no problems with Gutsy on the same computer ...

Not sure what your problem might be but you might try Altenate rather that Live.  I tried Live and had problems which is why I used Alternate ...

---

### Post by famous3warriors on 2008-03-26
You know I will do that.  Just for some reason I just can't get this notebook to work well.  Right know I am out of town and when I get back home on Friday I will try hardy 64 bit alternate.

---

