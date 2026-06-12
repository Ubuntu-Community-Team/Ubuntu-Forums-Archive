---
title: "Live CD doesn't load on AMD X2"
date: 2008-04-23
forum: x86 64-bit Users
---

### Post by abhappy on 2008-04-23
I'm assuming this is the right forum to post this.  My PC has a AMD Athlon 64 X2 dual-core processor.  Is this compatible?  When I insert the 64-bit (I know this is correct because the i386 version - the one I installed on my laptop - doesn't work in the system) it loads to the menu where you decide such options as run Live CD and check memory.  When I select Live CD option, the screen goes blank and sits there doing nothing.

---

### Post by gsmanners on 2008-04-23
Actually, that CPU should work fine (albeit a bit slower) with the i386 version. Your problem is more likely because of some usplash incompatibility with your video card (which you should just be able to ignore for a minute or two while the disc boots).

---

### Post by lswest on 2008-04-23
try booting it in safe graphics mode (if running Gutsy), that got it booting on my laptop with an nvidia mcp67m.  If it's Hardy, hit "F6" i think it is (to change/add boot parameters) and delete "splash" or "usplash" from there (if you can), otherwise just let it run for a few minutes.

---

### Post by Ongaku86 on 2008-04-23
I couldn´t get it to boot at all to the Live CD on my system until I messed with a BIOS setting...I can´t remember just now, but I either ¨enabled¨ AMD Cool and Quiet from ¨auto¨ or ¨disabled¨ it, and then the Live CD booted.

---

### Post by melenor on 2008-05-04
I have this problem too, i have tried installing though windows and the  CD when i try live install or to try boot-up by windows it seems to show the loading bar but then it freezes and i have left it on all night, and it did nothing, i have tried downloading the disc 2 already and the disc is fine. when i try to go stright to install without liveCD it does what he said. I really need help thank you.

---

### Post by BigguD on 2008-05-04
The Live CD or DVD?

I had the same problem... Then i tried the DVD.. That worked great

---

### Post by melenor on 2008-05-04
where did you get the live DVD i only knew of the live CD where did you download it?

---

### Post by jazzman65 on 2008-05-04
This is what I did to get the LiveCD to boot:  added "mem=4096M" at the end of the grub boot line (no quotation marks of course).  I have 4 GB of RAM and until I added that boot condition, my system would not boot the CD.  I figure you can try adding the same condition, just make sure the line reflects how much memory you have in your system.  When you boot, you can go into your BIOS and confirm how much system memory you have.

Hope that helps!  :)

---

### Post by melenor on 2008-05-05
how do i add that to the CD i know that you can do that to the grub but, you need to install ubuntu to get grub in the first place.

---

### Post by jazzman65 on 2008-05-05
> **melenor said:**
> how do i add that to the CD i know that you can do that to the grub but, you need to install ubuntu to get grub in the first place.

When it's booting up and you come to the screen to select what option you want, hit "F6" to be able to modify the boot command.  I'm not sure from memory, but you may have to hit "F6" a second time to actually modify the line.  Anyway, you modify the line so that the end of it looks like this:  -- mem=4096M.  Of course, you'll enter the actual amount of memory of your system.

That worked for me anyway.  I'm not sure from your description if it's the same deal, but it couldn't hurt to try it!  Took me several days of searching before I found a post from ~2 years ago with the same recommendation.

Good luck!  :)

---

