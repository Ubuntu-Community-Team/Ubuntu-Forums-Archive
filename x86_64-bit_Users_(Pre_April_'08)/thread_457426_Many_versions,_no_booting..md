---
title: "Many versions, no booting."
date: 2007-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lefty33 on 2007-05-28
I have Ubuntu on my laptop and love it, and I'm trying to get it to work on my desktop (AMD Athlon64 2.4 GHz, 1GB DDR RAM, ATI Radeon X700). 

Some versions, such as the Feisty alternate text-based installer will install, and others won't. After installation, GRUB comes up at boot, lets me choose XP or Ubuntu, but when I select Ubuntu, nothing happens. No hard drive access, no splash screen, no graphics output at all. Recovery mode works, that's it.

Any suggestions?

---

### Post by John Jason Jordan on 2007-05-28
> **Lefty33 said:**
> I have Ubuntu on my laptop and love it, and I'm trying to get it to work on my desktop (AMD Athlon64 2.4 GHz, 1GB DDR RAM, ATI Radeon X700). 
Some versions, such as the Feisty alternate text-based installer will install, and others won't. After installation, GRUB comes up at boot, lets me choose XP or Ubuntu, but when I select Ubuntu, nothing happens. No hard drive access, no splash screen, no graphics output at all. Recovery mode works, that's it.
Any suggestions?

It sounds as though something is wrong with the boot entry in Grub for the regular graphical boot option. For reference, here is what mine say (after the latest kernel upgrade this morning):

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8348ba8b-3f9f-455b-8213-a9491374ea9f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8348ba8b-3f9f-455b-8213-a9491374ea9f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

Yours should be similar, except your kernel might be different and the UUID will definitely be different. The important point is that in your /boot/grub/menu.lst file the two entries should be identical except for the title (one says "recovery mode") and that the "recovery mode" one ends in "ro single" where the regular one ends in "ro quiet splash." 

If there is anything else different between the two, that may be the source of the problem. If you edit anything, be sure to make a backup copy of the menu.lst file first.

Another thing that may be happening is that X is not starting, probably due to a video driver issue. However, in my experience, if X has a problem starting Ubuntu will still boot -- you'll just be dumped to a command line similar to what you get in recovery mode.

Start by taking a look at the /boot/grub/menu.lst file.

---

### Post by Lefty33 on 2007-05-28
First, thanks a lot for the idea. I didn't think of the menu.lst idea.

My menu.lst file seems to be the same. And it does the same thing, even when I've taken XP off. I've also tried 
a number of updates to the drivers and such, but nothing ever fixes the problem.

---

