---
title: "Ubuntu freezes if I have 2 gigs installed"
date: 2007-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by dodgydavec on 2007-06-12
I recently, successfully, installed Ubuntu Studio into my PC. Specs:

AMD64 Athlon 3500+
250gig SATA (installed on here)
250gig IDE(MBR here)
500gig IDE
Radeon 9250 128 (yeah, crap, I know)
and sadly ONE gig of RAM

I say sadly because my windows installation and SimplyMEPIS64 both work fine with BOTH of my 1 gig sticks installed. Ubuntu tries to boot but always freezes at some point while booting up. I'd dearly love to use all 2 gigs with Ubuntu. Can anyone help me? BTW... I am VERY new to Linux so please be gentle ;)

---

### Post by zsouthboy on 2007-06-13
It's quite possibly a bad stick of RAM, rather than a problem with Ubuntu.

Simply being able to boot into Windows and MEPIS doesn't rule that out.

Have you tried booting one gig of RAM in Ubuntu, but only using the other stick?

If that works fine, it may be a motherboard problem.

---

### Post by Trueno22 on 2007-06-13
yeah it's most likely a bad stick you should run memtest+86 on them see if you turn up any errors

---

### Post by jespdj on 2007-06-13
memtest86+ is included on the Ubuntu Live CDs if I remember correctly, it's one of the options you can choose in the menu when you boot from the CD.

It's a memory testing program that runs all kinds of tests on your RAM. Let this run for a few hours or so and see if it reports any errors. If it does, then most likely one of your RAM sticks is broken, or you're possibly running your RAM at the wrong speed or voltage (things that you can set in the BIOS setup of your computer).

(NOTE: Don't change the memory speed or voltage without knowing what you're doing! Setting the voltage too high can permanently damage your RAM!).

---

### Post by dodgydavec on 2007-06-13
I have indeed tried both sticks of RAM separately. Ubuntu works with both sticks. Just not both sticks together. I have also tried the memtest with no failed results. As for changing the speed/voltage setting - I'm not brave enough to push my PC like that lol.

I can tell you that the two sticks are different brands but the same speed. And that they go in slots 1 and 3 on the motherboard, or the motherboard won't boot at all. I believe this is something called dual channel but my knowledge on the subject is very limited.

I used to run the system on two sticks of 512MB with no problems in slots 1 and 2.

Thanks for the responses :D

---

### Post by timcredible on 2007-06-13
have you only tried booting from hd?  if so, try the livecd - in case the installed version is still thinking the pc only has 1gb.  i'm writing this from a machine with intel duo core and 2gb of memory, and ubuntu runs fine on it, sees both cpus, sees all the memory.

---

### Post by darknightuk on 2007-06-13
reading thru your post the memory is two diff brands, i would say 99% that's your problem whilst they may be the same speed memory has a kind of control bios thingy on it these in theory  all sticks are built to one strict standard but in practice that doesn't happen, if u want to run dual channel buy specific dual channel packs or at least by them both at the same time, u might want to play with the settings and slots a bit but may be more trouble than it's worth

---

### Post by capecove on 2007-06-13
Yes, I know that this kind of thing can happen in any OS really. I have seen it in Windows 2000, XP, Linux servers (Fedora), etc. Matching RAM is important now a days.

---

### Post by dodgydavec on 2007-06-13
> **timcredible said:**
> have you only tried booting from hd?  if so, try the livecd - in case the installed version is still thinking the pc only has 1gb.  i'm writing this from a machine with intel duo core and 2gb of memory, and ubuntu runs fine on it, sees both cpus, sees all the memory.

A good idea with two slight flaws.

1) Ubuntu Studio doesn't have a live CD and
2) Ubuntu Studio doesn't have a live CD.

All joking aside, I have tried other Ubuntu Live CD's, 64 and 32 bit, and they work fine until I run them from the hard drive. I feel the matched pairs of RAM is probably the right way to go. Thank you all for your help. I will return when I fail again ;)

---

