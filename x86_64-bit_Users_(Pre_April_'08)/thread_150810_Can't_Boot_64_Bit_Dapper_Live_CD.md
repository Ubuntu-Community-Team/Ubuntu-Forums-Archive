---
title: "Can't Boot 64 Bit Dapper Live CD"
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by carney1979 on 2006-03-26
AMD 64 3500 CPU
1 Gig Ram
200 Gig SATA HD (Not that that really matters :-|)

I downloaded the iso twice and checked it with md5sum. So far, so good.

Burned it to a CD-Rom (not a CD-RW). Done this a thousand times before with no problems. The first burn was done with a WinXP install; the second with a Dapper 32 bit install.

If I put the CD in the drive while using XP, K-Meleon boots and offers some free Open Source Windows programs.

If I reboot the machine, then it boots from the CD drive and I see the Ubuntu splash screen.

If I try to boot into the Live CD or if I try to check the CD (the only two options I've tried), it first boots the kernel, then it go to loading the essential drivers, or something like that. 

Then, everything comes to a screeching halt. System is locked, keyboard is completely unresponsive. Can't even change the status of the Caps Lock or Num Lock keys.

Any suggestions?

David

---

### Post by skylark on 2006-03-31
Hmm, hard to tell what the problem is. Some suggestions:

1. Try passing the noapic and/or nolapic as boot options when trying to boot with your CD (search these forums for noapic to get more info)
2. Download the 32-bit live CD - it should work on your system and I've heard ppl sometimes have more success with this
3. Download the latest Dapper "flight" live CD or wait till Dapper is released and try again.

---

