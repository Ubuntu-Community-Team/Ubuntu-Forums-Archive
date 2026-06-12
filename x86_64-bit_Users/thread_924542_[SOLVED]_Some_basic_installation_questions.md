---
title: "[SOLVED] Some basic installation questions"
date: 2008-09-19
forum: x86 64-bit Users
---

### Post by CaesarsAdvocate on 2008-09-19
Hi,
I am new to Linux......
Have am AMD Athlon 64 Dual Core.

I have dual boot on my machine - WinXP & Debian. The Debian has died, mysteriously, and we weren't getting along anyway, so I want to give it the boot and install Ubuntu on its partition (the second of three on my single disk).

My CD-DVD burner has died, and from what I've learned about my BIOS, there's no way of convincing it to boot from my USB stick.

My questions: is it possible to install it from a USB stick with the computer loaded into Windoze, or am I seriously misguided, and must, in fact, burn a DVD on someone else's computer first? How painful will it be to get my wireless connection working (I have a USB Ralink, RT73 being the chipset, although lsusb in Debian produced the following: Ralink Technology, Corp. RT2501USB Wireless Adapter)?

Thanks,
CA.

---

### Post by Sef on 2008-09-20
If you have internet, then check out [net boots]("https://help.ubuntu.com/community/Installation/QuickNetboot?action=fullsearch&context=180&value=netboot&titlesearch=Titles").

---

### Post by CaesarsAdvocate on 2008-09-21
I think I'll just burn a regular installation CD on my friend's machine.

One more question, if I may: I have 5 partitions on my disk: the first has WinXP, the next 3 partitions are a Debian installation, and the last one is a shared FAT32 partition. I wish to remove Debian (maybe only join and reformat the first 2 partitions it was using, leaving the swap untouched) and install Ubuntu instead.

Will the boot sector be reconfigured appropriately by the Ubuntu installation procedure? I am fearful of losing my XP installation which is, until I configure my wireless in Ubuntu, my only connection to the world : ).

Thanks,
CA.

---

### Post by Sef on 2008-09-21
> Will the boot sector be reconfigured appropriately by the Ubuntu installation procedure? I am fearful of losing my XP installation which is, until I configure my wireless in Ubuntu, my only connection to the world : ).


It should be automatically reconfigured to boot up.  As for the wireless, it may start up automatically or may need to be configured.   I will do some research if no one answers that question.

---

### Post by CaesarsAdvocate on 2008-09-21
What I was worried about is that, since I'll be formatting the space my Debian occupies, and it still has an entry in the boot sector, this might cause a confusion.

Anyway, I'll try to install it and see if it is configured automatically. If no, I'll come back here.

Thanks,
CA.

---

### Post by Sef on 2008-09-22
> What I was worried about is that, since I'll be formatting the space my Debian occupies, and it still has an entry in the boot sector, this might cause a confusion.

I would do a manual install to avoid that problem.

---

### Post by CaesarsAdvocate on 2008-09-22
Manual, of course.

I tried it, but decided to abort, since it did not seem to recognize any other OSs. On the importing data/settings screen it said that it did not recognize any system on my machine such stuff could be imported from. No mention of my XP at all. Not sure I like that....

And another question: The next release (Intrepid) is next month. Can a currently installed version be easily upgraded to the next when it comes out?

---

### Post by CaesarsAdvocate on 2008-09-22
OK, I think I have a solution:

I'll first load Ubuntu from CD and copy the contents of /boot/grub/menu.lst to some text file.

Install Ubuntu, restart. If there is no option for loading XP, I'll copy the entry for it from the abovementioned textfile into /boot/grub/menu.lst, and modify the file to suit my needs (like, making the delay longer, and stuff).

D.

---

### Post by CaesarsAdvocate on 2008-09-23
Well, it worked, and everything went OK.
Now it's time to try & connect to the Internet....

Thanks a lot!
CA.

---

### Post by Sef on 2008-09-23
> And another question: The next release (Intrepid) is next month. Can a currently installed version be easily upgraded to the next when it comes out?

Yes, it can be.  However, it is not guaranteed that every thing will work if you upgrade.  It is best to remove any binary drivers.  **Back up** your data if you do.

---

