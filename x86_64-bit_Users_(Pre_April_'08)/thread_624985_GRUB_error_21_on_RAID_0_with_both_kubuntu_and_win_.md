---
title: "GRUB error 21 on RAID 0 with both kubuntu and win xp"
date: 2007-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zupper on 2007-11-27
PC specifications: 2 HDD Western Digital 250 GB, in a RAID 0 array. I have 6 NTFS partitons, one ext3 for kubuntu and a swap one, obviously. I had a lot of problems making kubuntu to work on this raid array with win xp, but finally i did it, with a tutorial on the net( i basically installed the dmraid package and then i installed GRUB on (hd0,2) if i remember well)
A couple of days ago, I was on the net in kubuntu and the power went off. After I cursed the damned electric company a few times, the power went back on and I reopened my pc, when I noticed that my bootloader, GRUB got the error 17 in stage 1.5 . OK then, I took my livecd and searched the forums for solutions. I found a couple of tips, but they all didn't work in my case:
1) changes in BIOS: the Primary Master (Type:user, Mode:LBA), Primary Slave(Type=Auto, Mode=Auto)
2) configuring the menu.lst file
  This could seem the ideal solution, but I cannot find the /boot/grub folder. I also used locate to find the menu.lst file, but nothing. Very weird, but I said it's probably because of my RAID 0 array.
3) the worst solution: reinstalling kubuntu and GRUB. I used the same steps as before, I installed dmraid on RAM with the livecd, but all the ntfs and the swap partitions were recognizied, except the ext3, which was there(i recognised it by its size), but it wasn't recognised as ext3. I tried to format it and used / as mount point, but I got error every time, when it started doing the formatting.

After trying these with no use, today the error changed and now it says error 21 instead of 17. Strange, but still , it's the same for me. Tongue
Can you give me any advice or point me into the right direction? I still think the error is somewhere with the linux partitions , but i don't understand why and why i cannot format it!
PS: The Windows XP cd is borrowed to a friend, i hope to get it back tomorrow. I haven't tried to boot from it yet.

---

