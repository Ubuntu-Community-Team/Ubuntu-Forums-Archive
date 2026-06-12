---
title: "Asus k8v-se deluxe freezes a lot."
date: 2005-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by valadil on 2005-05-24
Hi.  I just reinstalled ubuntu and I'm getting far more lockups than I should.  Now, I remember someone on these forums had a similar problem and someone else had a working solution.  My problem is that it seems that posts before 4/24 are gone (I'm assuming that's when the layout around here changed and the boards got moved around a bit).  

I think the freezing usually comes about during heavy file writing, but I'm really not sure.  I'd rather just fix it than figure out exactly when it takes place.  The fix from the old forums was something in grub, in the kernel line.  It was something along the lines of pci interrupt irq something or other = 1, I think.  If anyone still has that in their grub config, or knows where the old posts are kept, or has a link for grub kernel options, I'd appreciate some help.  I'm late enough for work already :-P

---

### Post by dmatrix on 2005-05-24
The problems I had were on heavy writes or heavy load I would get small freezes, but then the system would come back to normal after a short period of time. All these problems went away for me sometime before Hoary went final on the new kernel. I freshly installed Hoary as well once it went final to see if I had the same problem and sure enough it was gone for me. 

I only had the problems on Warty. Have you tried to move to Hoary or at the very least the kernel that is in Hoary?

A workaround on Warty for me was to put some acpi/noapic options in the menu.lst for grub. This worked for me as well.

---

### Post by valadil on 2005-05-24
Sorry, should have posted more background, but I was in a rush.  

I'm already in hoary.  I briefly tried breezy, but that was not a good idea.  FWIW I tried to back up my menu.lst before reinstalling, but hoary killed my /home partition.  Grrr.

In the previous install, noapic and noacpi helped a little, but this other mysterious kernel option was what made the most difference.  I haven't actually had the fresh install long enough to know if it is as prone to crashing as before.  All I know is that it froze hard at 5am when my updatedb cronjob went off.  For whatever reason whenever my ubuntu systems freeze, my file system gets hit, so I'd really like to fix it quickly

---

### Post by valadil on 2005-05-24
pci=usepirqmask

Hurray for google cache!

---

