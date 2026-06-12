---
title: "CD-ROM read problem"
date: 2006-10-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by asfpf on 2006-10-10
Hello guys,

I use Ubuntu 6.06 LTS on AMD64 Compaq Presario R3240CA, and I have a estrange problem I hope anyone could help me. I am not able to read some CDs on my linux box (just some CDs - even if they were burned by linux) but when I try to read the same CD on Windows XP (running in the same box - dual boot) or on my friends machine it works. This are the errors I got: 

Oct 11 00:21:07 localhost kernel: [   92.393492] hdc: irq timeout: status=0xd0 { Busy }
Oct 11 00:21:07 localhost kernel: [   92.393496] ide: failed opcode was: unknown
Oct 11 00:21:07 localhost kernel: [   92.393500] hdc: DMA disabled
Oct 11 00:21:07 localhost kernel: [   92.489440] hdc: ATAPI reset complete
Oct 11 00:21:26 localhost kernel: [  100.112305] hdc: irq timeout: status=0xd0 { Busy }
Oct 11 00:21:26 localhost kernel: [  100.112309] ide: failed opcode was: unknown
Oct 11 00:21:27 localhost kernel: [  100.208252] hdc: ATAPI reset complete
Oct 11 00:21:46 localhost kernel: [  107.818326] hdc: irq timeout: status=0xd0 { Busy }
Oct 11 00:21:46 localhost kernel: [  107.818330] ide: failed opcode was: unknown
Oct 11 00:21:46 localhost kernel: [  107.914273] hdc: ATAPI reset complete

Any ideas?

Thanks a lot.

---

### Post by John Jason Jordan on 2006-10-11
> **asfpf said:**
> Hello guys,

I use Ubuntu 6.06 LTS on AMD64 Compaq Presario R3240CA, and I have a estrange problem I hope anyone could help me. I am not able to read some CDs on my linux box (just some CDs - even if they were burned by linux) but when I try to read the same CD on Windows XP (running in the same box - dual boot) or on my friends machine it works. This are the errors I got: <snip> 

Omigod!

I have the same exact computer (except US version), and I just now ran into the same problem!!

I did not run the test you did, so I don't have any error codes to share. However, I can add that I have been using the drive for CDs and DVDs, both reading and writing, for over a year and never had a problem until just the other day.

For what it's worth, the CD in question came with a textbook for a Phonetics course. At first I thought the CD was defective. But I had made a backup copy right after taking it out of the sleeve in the book, and the backup copy behaved exactly the same. The behavior is that it fails to display several folders, yet the folders are there. In addition to Nautilus, I have installed Konqueror, Krusader, XFE File Manager, Thunar, and Endeavour2. All failed to display the folders.

Eventually I solved the problem by using a Windows computer at a university computer lab to copy the whole thing to my thumb drive (which it did perfectly), and then move the files to my computer's hard drive.

I might also add that I now think there is something funny about this CD. The professor and several students say they cannot copy the CD to their hard drives, yet others can do so, and the university's Windows computer had no problem. I don't know what the students are using, but the professor has a Windows XP computer.

I know I'm not much help, but at least you know now that you are not alone.

---

### Post by kuja on 2006-10-11
asfpf, it's potentially a problem with linux interacting with the drive. It's also however even more likely that there is a problem with the disks it's reading, or a problem with the disk drive itself. For example, my cheap piece of junk Samsung DVD-ROM drive has trouble reading lots of things. On the other hand, I try the same media with my other drive and they read fine.

---

### Post by asfpf on 2006-10-11
John, it´s really nice to know I´m not alone in the dark... In my case, the first occurence was with the Ubuntu 6.06 LTS AMD64 Install CD! Do you beleave me?! I had to use the Alternative CD version to install the system, but after the installation (it was done smothly), I had the problem again reading the disk. 

kuja, it is for sure nothing realated to the disk itself, because I can read the same disk using Windows XP on the same box. And I didn´t have this problem with previous versions of Ubuntu, so something is definitely broken with this version. My guess is that there is something odd with the IRQ mapping/usage for the CD device. But it´s just a thought...

---

### Post by kuja on 2006-10-11
Rather than pull hair out over having issues getting the drive working, why not pay $10 and get another one that works? less frustration with this route. But it's just a thought...

---

### Post by asfpf on 2006-10-12
Hello kuja,

You're right. It would be much easier just buy another CD drive for my laptop and finish this thread off. However, I am in Brazil, and here it's not easy neighter cheap buy this things. I'll have to keep searching... Besides this, this is an opportunity to fix another little bug in this bealtiful distribution, so I think it is worth a try.

---

### Post by John Jason Jordan on 2006-10-12
> **asfpf said:**
> You're right. It would be much easier just to buy another CD drive for my laptop and finish this thread off. However, I am in Brazil, and here it's not easy nor cheap to buy this thing. I'll have to keep searching... Besides this, this is an opportunity to fix another little bug in this beautiful distribution, so I think it is worth a try.
I have the same issue. Our problem is with the drive in our Compaq R3240 laptops, and HP wants $70 for a replacement drive here in the US. I'm sure it would be worse in Brazil. Besides, the drive has always worked flawlessly with everything else I've ever put into it, so I suspect it is some kind of bug. On the other hand, asfpf is having problems with lots of CDs, where I have encountered only one that didn't work right.

---

